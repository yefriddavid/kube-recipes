# kube-recipis

## Commands to start

minikube start

kubectl run hello-minikube --image=gcr.io/google_containers/echoserver.1.4 --port=8080

kubectl expose deplooyment hello-minikube --type=NodePort



kubectl create -f deployment.yml




## Basic commands

kubectl apply -f ./deployment.yaml

kubectl expose deployment tomcat-deployment --type=NodePort

minikube service tomcat-deployment --url

curl <URL>


## Several helpful commands

kubectl get pods

kubectl get pods [pod name] 


kubectl expose <type name> <identifier/name> [—port=external port] [—target-port=container-port [—type=service-type]

kubectl expose deployment tomcat-deployment --type=NodePort 


kubectl port-forward <pod name> [LOCAL_PORT:]REMOTE_PORT] 


kubectl attach <pod name> -c <container> 


kubectl exec  [-it] <pod name> [-c CONTAINER] — COMMAND [args…]


kubectl exec -it <pod name> bash 


kubectl label [—overwrite] <type> KEY_1=VAL_1 ….

kubectl label pods <pod name> healthy=fasle 


kubectl run <name> —image=image

kubectl run hazelcast --image=hazelcast/hazelcast --port=5701
### the hazelcast docker image has been moved to hazelcast/hazelcast (https://hub.docker.com/r/hazelcast/hazelcast 
 
kubectl describe pod




## General advance commands

Linux:  
 
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl 
 
MacOS:  
 
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/darwin/amd64/kubectl 
 
Windows:  
 
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.8.0/bin/windows/amd64/kubectl.exe 

```sh
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version 
 ```
 
Linux:  
 
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.23.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/ 
 
macOS:  
 
```sh
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.23.0/minikube-darwin-amd64 && chmod +x 
minikube && sudo mv minikube /usr/local/bin/
minikube start
kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
kubectl expose deployment hello-minikube  --type=NodePort
kubectl get pod
curl $(minikube service hello-minikube --url)
kubectl delete deployment hello-minikube
minikube stop
```


## Replicas and loadbalacers

kubectl scale --replicas=4 deployment/tomcat-deployment  
 
kubectl expose deployment tomcat-deployment --type=NodePort
kubectl expose deployment tomcat-deployment --type=LoadBalancer --port=8080 --target-port=8080 --name tomcat-load-balancer 
 
kubectl describe services tomcat-load-balancer




## Deployment commands

kubectl get deployments

kubectl rollout status

kubectl set image

kubectl rollout history



minikube start -p donkey
minikube start -p neddy

sensible-browser $(minikube service tomcat-deployment --url)

kubectl set image deployment/tomcat-deployment tomcat=tomcat:9.0.1

kubectl set image deployment/tomcat-deployment tomcat=tomcat:9.0

sensible-browser $(minikube service tomcat-deployment --url)

kubectl describe node minikube

kubectl describe node



minikube dashboard


run a mongo in 27017 port
kubectl run mongo-excercise-1 --image=mongo --port=27017
kubectl scale --replicas=4 deployment/mongo-exercise-1






