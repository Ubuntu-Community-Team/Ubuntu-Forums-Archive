---
title: "Cannot view apache web server from external IP on ubuntu 14.04"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by heath2 on 2014-05-28
[COLOR=#000000][FONT=Arial]**I did a search and looked for an answer all over the web for the past two days. None of the other answers I've found have worked for my issue**, so I'm here hoping someone can offer new insight. Thanks in advance. Some quick info:

**1)** I have a server box running ubuntu 14.04. I'm running LAMP. Everything is updated/upgraded to latest.

**2)** I have a basic index.html file located at /var/www/mysite.com/public_html, which I can view from my**internal** IP (192.168.1.139) in a browser window with zero problems. However, the **external IP**([http://76.xx.xx.xx/](http://76.xx.xx.xx/)) will **NOT** load in the browser.

**3)** I've disabled the firewall on the ubuntu server completely (this is only temporary until I can fix this issue). So this:
[INDENT]sudo iptables -L -n[/INDENT]

Returns:
[INDENT]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination [/INDENT]

And this:
[INDENT]sudo ufw status[/INDENT]

Returns:
[INDENT]Status: inactive[/INDENT]

**4)** I've properly added the port forwarding rules to my linksys router for port 80 (among others such as 21 and 443) for both UDP and TCP, which forwards to my internal IP (192.168.1.139). I've checked this via [http://www.canyouseeme.org/](http://www.canyouseeme.org/), and verified port 80 is **open**.

**5)** It appears apache is listening to port 80, because this:
[INDENT]sudo netstat -napW | grep apache[/INDENT]

Returns:
[INDENT]tcp6   0   0 :::80     :::*         LISTEN      1827/apache2[/INDENT]

**6)** /etc/network/interfaces looks like this:
[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.139
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 8.8.8.8

# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto[/INDENT]

**7)** Both the 000-default.conf and the mysite.conf file contain the following:
[INDENT]<VirtualHost 192.168.1.139:80>
    ServerAdmin [EMAIL="admin@mysite.com"]admin@mysite.com[/EMAIL]
    ServerName mysite.com
    ServerAlias *.mysite.com *mysite.net
    DocumentRoot /var/www/mysite.com/public_html/
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>[/INDENT]

**8)** I can, however, use the external IP (76.xx.xx.xx) to access the server by FTP, just not by HTTP. This lets me know the external IP is correct, just not properly resolving when using HTTP.

I'm stumped. Any ideas? Much thanks!


[/FONT][/COLOR]

---

### Post by TheFu on 2014-05-28
It looks like apache is listening on IPv6, but not IPv4. Does some other process have port 80 taken before apache starts up? Perhaps a different web server or proxy?  netstat or lsof can find that.

---

