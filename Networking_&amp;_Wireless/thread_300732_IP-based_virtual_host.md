---
title: "IP-based virtual host"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by denday on 2006-11-16
Hi...

Anyone know how to configure IP-based virtual host, and set the IP aliasing? My hope is my server can have more than one proxy for different domain name.

thanks

---

### Post by mark_g on 2006-11-16
Yup. Here's an example. Added to apache.conf:
```

LoadModule vhost_alias_module modules/mod_vhost_alias.s

NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
ServerName www.domain1.com
ServerRoot "/etc/apache2/"
DocumentRoot "/web/website1"
ErrorLog /var/log/apache2/error1
CustomLog /var/log/apache2/access1 common
</VirtualHost>

<VirtualHost 127.0.0.1>
ServerName www.domain2.com
ServerRoot "/etc/apache2/"
DocumentRoot "/web/website2"
ErrorLog /var/log/apache2/error2
CustomLog /var/log/apache2/access2 common
</VirtualHost
```

Don't forget to setup your dns (bind) too.

---

### Post by denday on 2006-11-17
Thanks for reply, 
But what I need is Ip-based virtual hosts, say my machine has ip number 128.0.0.1, And I need run some webserver that has Ip address 128.0.0.2 and 128.0.0.3 (in my machine). so every time someone type 128.0.0.2 point to my machine.

Someone say using ip-alising, but i don't know what ip-aliasing is? ](*,) 

Any help would be appreciate.

thanks :D

---

### Post by bjd on 2006-11-17
With ip aliasing you can have multiple ip addresses on the same network interface.
You can add ip aliases by adding to /etc/network/interfaces something like:

auto eth0:0
iface eth0:0 inet static
address 128.0.0.2
netmask 255.255.255.0

auto eth0:1
iface eth0:1 inet static
address 128.0.0.3
netmask 255.255.255.0

...etc

Then setup apache as mentioned above, but using a different ip for each VirtualHost section.
Apache config is not really my area, so you may also want to refer to the apache documentation on virtual hosts:
[http://webauth.stanford.edu/manual/vhosts/ip-based.html](http://webauth.stanford.edu/manual/vhosts/ip-based.html)

---

