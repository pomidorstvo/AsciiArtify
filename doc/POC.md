![argocd](https://github.com/pomidorstvo/AsciiArtify/assets/149612749/0f1b1acd-4b7f-4fa2-8f60-e1a614599a75)

1. Запускаємо minikube
`minikube start --driver=docker --force`
2. Для зручності додаємо аліас
`alias kk='kubectl'`
3. Створюємо неймспейс
`kk create namespace argocd`
4. Перейдкмо в неймспейс який створили
`kk config set-context --current --namespace=argocd`
5. Встановимо argocd 
`kk apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
6. Прикиномо порт
`kk port-forward svc/argocd-server -n argocd 8080:80&`
7. Та отримаємо пароль
`kk get secret argocd-initial-admin-secret --namespace argocd --output jsonpath="{.data.password}" | base64 --decode && echo`
