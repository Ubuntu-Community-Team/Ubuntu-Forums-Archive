---
title: "Apache access from different computer"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by stinkytofu on 2008-03-14
I have a problem accessing Apache from a computer other than my own on my home LAN.  When I am using my own computer, I can access the Apache site by typing [http://localhost/](http://localhost/).  However, when I try to access it from a computer other than my own, I receive a 404 Not Found error.  

I have tried adding the following lines to the top of the apache2.conf file:

<Directory "/var/www">
Order Allow, Deny
Allow from all
</Directory>

But am still receiving the same error message.  Not sure what I am doing wrong.  I also have some virtual servers setup in the sites-enabled/default file as follows:

NameVirtualHost 127.0.0.1

<VirtualHost localhost>
ServerName localhost
ServerAdmin [email]admin@test.com[/email]
DocumentRoot /var/www/
ErrorLog /var/log/apache2/error.log
</VirtualHost>

<VirtualHost sg>
ServerName sg
ServerAdmin [email]admin@test.com[/email]
DocumentRoot /var/www/sg/
</VirtualHost>

Is there something in this file that may be causing the problem?

Thanks for your help!

---

### Post by sillyxone on 2008-03-14
I assume you typed the IP address of Apache machine instead of localhost ([http://192.168.0.4](http://192.168.0.4), for example)

Check the Apache machine's firewall, make sure port 80 is opened.

---

### Post by jackiewky on 2008-03-20
Can I use the domain name (eg. [www.example.com](www.example.com)) instead of using the ip address of the apache server?

---

