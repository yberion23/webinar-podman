# webinar-podman

podman run -d --pod npm-pod \
  -e MYSQL_ROOT_PASSWORD=your_root_password \
  -e MYSQL_DATABASE=nginxproxymanager \
  -e MYSQL_USER=nginxproxymanager \
  -e MYSQL_PASSWORD=nginxproxymanager_password \
  --name mariadb \
  mariadb:latest

# Starte Nginx Proxy Manager im Pod
podman run -d --pod npm-pod \
  -e DB_MYSQL_HOST=mariadb \
  -e DB_MYSQL_PORT=3306 \
  -e DB_MYSQL_USER=nginxproxymanager \
  -e DB_MYSQL_PASSWORD=nginxproxymanager_password \
  -e DB_MYSQL_NAME=nginxproxymanager \
  --name nginx-proxy-manager \
  jc21/nginx-proxy-manager:latest