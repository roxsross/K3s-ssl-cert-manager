# k3s-ssl-cert-manager

Lightweight, easy, fast Kubernetes distribution with a very small footprint

https://k3s.io or https://k3d.io for the dockerized version of k3s.

## Demo

Estoy usando Linode para la demo.

### Install Master

`curl -sfL https://get.k3s.io | sh -s - --no-deploy traefik --write-kubeconfig-mode 644 --node-name k3s-master-01`

### Install Worker

Guarda el token para agregarlo en el worker: 

`cat /var/lib/rancher/k3s/server/node-token`

Install k3s en el worker node y agregalo en el cluster:

`curl -sfL https://get.k3s.io | K3S_NODE_NAME=k3s-worker-01 K3S_URL=https://<IP>:6443 K3S_TOKEN=<TOKEN> sh - `

### Install nginx ingress controller


Website: https://kubernetes.github.io/ingress-nginx/

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.1/deploy/static/provider/cloud/deploy.yaml`

### Additional information

Asegura de reiniciar: `systemctl restart k3s`


### Deploy demo application nginx

`kubectl create deployment nginx --image nginx:alpine`

`kubectl expose deployment nginx --port 80 --target-port 80`


⌨️ con ❤️ por [roxsross](https://github.com/roxsross) 😊

No olvides revisar mi blog [roxsross](https://blog.295devops.com) 😊

y mi linktree [roxsross](https://roxs.295devops.com) 😊

"No se trata de cambiar el mundo, creo que creas un cambio pequeño, pero que te importe estás cambiando las cosas".
