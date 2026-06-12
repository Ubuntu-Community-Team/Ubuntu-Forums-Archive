---
title: "Apache2 and RSA certificate configuration"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by SonorDrummer on 2015-07-22
Hi All,
Sorry if this is posted under the wrong section.

I am under a directive to restrict all secure traffic on my 14.04 server running apache2 to use TLSv1.2 only.  I have verified that Apache is 2.4.7 
and openssl is 1.0.1f-4.4.  I did the “a2enmod ssl” and it was already enabled.  I then created the /etc/apsche/SSL directory and ran the command, 
“sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt” and answered the 
questions that followed.  I edited the /etc/apache2/sites-vailable/default-ssl.conf file by placing in the command, “ssl_protocols TLSv1.2;” 
and restarted apache.  It fails to load stating that the line with the ssl_protocols could be a typo.  In the error.log file it states that, 
“RSA certification configured for xxx:443 does not include an ID which matches the server name.” Any suggestions to troubleshooting or correcting this would be appreciated.

---

### Post by SeijiSensei on 2015-07-22
Does the computer have a fully-qualified domain name like server.example.com?  Did you use that name when you created the certificate?  SSL certs are tied to the hostname.

---

