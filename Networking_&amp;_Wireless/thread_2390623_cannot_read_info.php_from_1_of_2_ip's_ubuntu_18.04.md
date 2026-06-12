---
title: "cannot read info.php from 1 of 2 ip's ubuntu 18.04"
date: 2018-04-30
forum: Networking &amp; Wireless
---

### Post by starpaly on 2018-04-30
After setting up two sites, testing reads **info.php **only from second site directory.
But it reads **index.html** from both site directories

info.php located in root directory of each site

**_site 1:_**

# Default server configuration
#
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/site1.com/public_html;

    index index.php index.html index.htm index.nginx-debian.html;

    server_name site1.com [www.site1.com;]("http://www.site1.com;")

    location / {
        try_files $uri $uri/ =404;
    }


    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    }
}

_**site 2:**_

# Default server configuration
#
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/site2.info/private_html;

    index index.php index.html index.htm index.nginx-debian.html;

    server_name site2.info [www.site2.info;]("http://www.site2.info;")

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    }
}

**network settings:**

file: **01-netcfg.yaml**

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      addresses: [ xx.xx.xxx.153/29 ]
      gateway4: xx.xx.xxx.xxx
      nameservers:
          search: [ site1.com ]
          addresses:
              - "75.75.75.75"
              - "75.75.76.76"
              - "8.8.8.8"
    eno3:
      addresses: [ xx.xx.xxx.154/29 ]
      gateway4: xx.xx.xx.xxx
      nameservers:
          search: [ site2.info ]
          addresses:
              - "75.75.75.75"
              - "75.75.76.76"
              - "8.8.8.8"

---

### Post by starpaly on 2018-04-30
Solved - needed to add ip address to **listen** directive, **listen XX.XX.XXX.153 **to site1 and **listen xx.xx.xxx.154** to site2

---

