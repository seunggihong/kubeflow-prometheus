![Static Badge](https://img.shields.io/badge/kubernetes-1.30.0-%23326CE5?labelColor=white)
![Static Badge](https://img.shields.io/badge/kubeflow-1.9.0-%233B66BC?labelColor=white)

# kubeflow + Prometheus

### kustomize install

```bash
brew install kustomize
```

### kubeflow install

```bash
git clone https://github.com/kubeflow/manifests.git
cd manifests
git checkout v1.9.0

kustomize build example | kubectl apply -f -
```

### kubeflow dashboard

```yaml
ports:
  - name: status-port
    port: 15021
    protocol: TCP
    targetPort: 15021
  - name: http2
    port: 80
    protocol: TCP
    targetPort: 8080
    nodePort: { your port } # # # add # # #
  - name: https
    port: 443
    protocol: TCP
    targetPort: 8443
selector:
  app: istio-ingressgateway
  istio: ingressgateway
sessionAffinity: None
type: NodePort # # # change # # #
```
