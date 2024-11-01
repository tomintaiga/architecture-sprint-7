Для создания сертификата пользователя:

```bash
openssl genrsa -out user1.key 2048
openssl req -new -key user1.key -out user1.csr -subj “/CN=user1/O=admin”
openssl x509 -req -in user1.csr -CA ~/.minikube/ca.crt -CAkey ~/.minikube/ca.key -CAcreateserial -out user1.crt -days 500


kubectl config set-credentials user1 --client-certificate=user1.crt --client-key=user1.key
kubectl config set-context user1-context --cluster=minikube --user=user1
```


