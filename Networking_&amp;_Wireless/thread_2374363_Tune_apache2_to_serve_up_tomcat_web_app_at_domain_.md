---
title: "Tune apache2 to serve up tomcat web app at domain without timeouts"
date: 2017-10-15
forum: Networking &amp; Wireless
---

### Post by TE7 on 2017-10-15
I have a domain that is hosted on an unmanaged VPS server with Ubuntu 16.04  I have configured my Java EE Tomcat web app to be served up at my domain name. But the response times for the app are way too slow, progressively going toward timeouts in the browser. If I stop the apache2 service and access my web app through domain:8080 the web app performance is perfect. How do you correctly configure apache2 to serve up the tomcat web app at the domain name with good performance? I realize that the easy solution is to link all references to my web app to domain:8080, but I would like to know how to correctly configure apache2 to serve up the Tomcat web app at the domain with the same performance as using domain:8080. Thanks in advance for any help. 

This is my apache2 sites-enabled file for the domain:

```

<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin webmaster@lae-laeweb.com
  ServerName  lae-laeweb.com
  ServerAlias www.lae-laeweb.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /var/www/html


  # Custom log file locations
  LogLevel warn
  ErrorLog /var/log/apache2/error-lae-laeweb.com.log
  CustomLog /var/log/apache2/access-lae-laeweb.com.log combined

    #ServerName www.lae-laeweb.com

     ProxyRequests On
     ProxyPass / http://lae-laeweb.com:8080/LAEWeb/ keepalive=on ttl=60
     ProxyPassReverse / http://lae-laeweb.com:8080/LAEWeb/

    <Location />
        Order allow,deny
        Allow from all
    </Location>


</VirtualHost>

```


This is a script I use after uploading a new .war file for my web app to tomcat:

```

#!/bin/bash

cd ../usr/local/apache-tomcat-8.5.23/bin

./shutdown.sh

./startup.sh

cd ../../../..

service apache2 reload

service apache2 restart

service=apache2

if (( $(ps -ef | grep -v grep | grep $service | wc -l) > 0 ))
then
echo "$service is running!!!"
else
/etc/init.d/$service restart
fi

```

z

---

