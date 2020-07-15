server{
  listen 80;
  server_name ahlev.com;
  server_name www.ahlev.com;
  return 301 https://$server_name$request_uri;
}

server{
  listen 443 ssl;
  server_name ahlev.com;
  server_name www.ahlev.com;
  location / {
    proxy_pass http://127.0.0.1:2403/;
    include proxy_params;
  }
  ssl_certificate /etc/letsencrypt/live/ahlev.com/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/ahlev.com/privkey.pem;
  
  error_page 404 502 /maintenance.html;
  location = /maintenance.html {
     root /var/www/error/;
     internal;
  }
}
