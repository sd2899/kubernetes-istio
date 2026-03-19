# kubernetes-istio

curl -L https://istio.io/downloadIstio | sh -

cd Istio-directory

export PATH=$PWD/bin:$PATH

istioctl x precheck

istioctl install --set profile=default

kubectl get pods -n istio-system

cd samples/addons/

kubectl apply -f kiali.yaml
kubectl apply -f prometheus.yaml

kubectl port-forward svc/kiali 8081:20001 0n istio-system


kubectl create ns demo-webapp
kubectl label namespace demo-webapp istio-injection=enabled
