---
title: "Can i have Apache2 only accept a connection based on the domain?"
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2014-11-05
As of now i have been running everything on different ports
i intended to setup a small folder that will be publicly accessible on a alternate subdomain from the main one i use
lets say i have subdomain ABC from my ddns provider, and i want to add XYZ
i want to prevent the XYZ/IP urls from being accepted on apache2 under port 443 (only accept via ABC)
while i am confident my passwords are strong enough to prevent someone from accessing my owncloud server, what i really need to prevent is someone from trying to get in thus eating 90-99 percent of my extremely low power server's processing power
what line to i need to add/change in my /etc/apache2/sites-advailable/owncloud file?

if using a firewall rule would be better i can have my ddwrt router handle that

---

### Post by pqwoerituytrueiwoq on 2014-11-06
i figured it out
to permit ONLY a single domain to have access
```
RewriteEngine On
#%{HTTP_HOST} also includes the port number if it is in the url, remove the $ to allow all ports or specify the port for a perfect match
RewriteCond %{HTTP_HOST} !^subdomain\.example\.com$ [NC]
RewriteRule ^ - [F]
```
i had to add that inside the [FONT=courier new]VirtualHost[/FONT] element of my config file in [FONT=courier new]/etc/apache2/sites-available/[/FONT]
also needed to enable the rewrite model 
```
sudo ln -s ../mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load
```

---

