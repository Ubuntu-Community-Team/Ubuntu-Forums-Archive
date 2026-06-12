---
title: "How to host a web page from my New Volume"
date: 2015-09-07
forum: Networking &amp; Wireless
---

### Post by Jayapramod on 2015-09-07
[Ubuntu 14.04].  I have done the following steps in order to host my web page [on local network] from mounted Volume1:

  
Step #1

  **/etc/apache2/sites-available/mysrv.conf**

<VirtualHost 192.168.2.104:4100>
        ServerName mysrv
        ServerAdmin [email]admin@rhithu.net[/email]
        DocumentRoot /media/user/volume1/www/mysrv

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /media/user/volume1/www/mysrv>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
  Step #2
  **/etc/apache2/apache2.conf**

<Directory /media/user/volume1/www>
       Options Indexes FollowSymLinks
       AllowOverride None
       Require all granted
</Directory>
Listen 4100
  Step #3:
   /media/user/volume1/www/
  Created directory & files: /mysrv
with index.html, images, and all other files.

  restarted the service.
  Already I have 2 other web pages hosted from /var/www/html directory in port 80 and 4000.

  While browsing the mysrv page like "192.168.2.104/mysrv" its showing:

  [INDENT]   Not Found
      The requested URL /mysrv was not found on this server. Apache/2.4.7   (Ubuntu) Server at 192.168.2.104 Port 80
 [/INDENT]  is there any mistake? or there is no possibility to host web pages from Local drive?
  -Jay

---

### Post by jtdemille on 2015-09-08
Try connecting via port 4100 or 4000.
ex: "192.168.2.104/mysrv:4100"

---

### Post by Bucky Ball on 2015-09-08
*Thread moved to **Networking & Wireless**.*

Please use code tags for terminal output. See the last link in my signature. Thanks.

---

### Post by Jayapramod on 2015-09-08
Thanks for your advice...
"192.168.2.104/mysrv:4100" showing not found, "192.168.2.104:4100" showing my home page but sub directory files [links to another .html files] are showing:

[h=1]Not Found[/h] The requested URL /mysrv/files/2048-master/index.html was not found on this server.

 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at 192.168.2.104 Port 4100

-Jay

---

### Post by Jayapramod on 2015-09-10
thanks for your support... Its worked through local domain.  In mysrv.conf file ServerName mysrv.com & DocumentRoot /media/user/volume1/www/mysrv.com. In /etc/hosts I have added "192.168.2.104:4100 mysrv.com".  Now I can access my page through "http://192.168.2.104:4100/index.html". Working fine... thank you very much.  -Jay

---

### Post by Jayapramod on 2015-09-10
hi... problem has been solved. How to change the status to [Solved]?

---

### Post by Bucky Ball on 2015-09-10
See first link in my signature to mark as solved. Good luck.

---

