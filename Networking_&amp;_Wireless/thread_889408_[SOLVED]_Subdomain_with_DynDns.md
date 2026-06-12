---
title: "[SOLVED] Subdomain with DynDns"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-08-14
Hi, I have an account at [www.dyndns.org]("http://www.dyndns.org"). I enabled wildcards so I get all the subdomains forwarded to my server. That works fine.

At my apache server I added this to my** */etc/apache2/httpd.conf***
```
Port 80
ServerName account.dyndns.org
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /var/www
ServerName account.dyndns.org
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/subdomain
ServerName subdomain.account.dyndns.org
</VirtualHost> 
```If I check the site*** subdomain.account.dyndns.org*** I always get the the main page (***account.dyndns.org***). Actually with any subdomain (*blabliblu.account.dyndns.org*) I always get the main page. That means to me that my ***httpd.conf ***doesn't work.

Can someone help me please?

---

### Post by borobudur on 2008-08-14
Okay, if I take out the first line (***Port 80***) it works with these errors:
```
[Thu Aug 14 09:22:55 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 14 09:22:55 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 14 09:22:55 2008] [warn] NameVirtualHost *:80 has no VirtualHosts 
httpd (no pid file) not running
[Thu Aug 14 09:23:05 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 14 09:23:05 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 14 09:23:05 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                        [ OK ]

```If I remove all the ports 80 (:80) I get these warnings 
```

[Thu Aug 14 09:24:10 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Aug 14 09:24:20 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                                                                        [ OK ]

```Well the nice thing is that it works...

---

