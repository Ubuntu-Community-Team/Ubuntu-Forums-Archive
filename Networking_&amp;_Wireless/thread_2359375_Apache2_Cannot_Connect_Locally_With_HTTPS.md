---
title: "Apache2: Cannot Connect Locally With HTTPS"
date: 2017-04-23
forum: Networking &amp; Wireless
---

### Post by 1candydoesgames on 2017-04-23
Hello everybody, this is my first post so I'm sorry if it's not the correct area. I have a dell poweredge server which has a few minecraft servers and websites. On the websites, I can unable to access them locally from my domain name when I have https enabled on them with letsencrypt. When I remove the certificate I am then able to access them. I thought maybe it was a DNS issue so I tried changing both my PC's and the server's DNS to googles and that has not seemed to help. Also I constantly clear my browsing data and cookies to see if it is fixed. I will attach some of my configs.

Ubuntu Server 16.04 LTS, LAMP, SSH

.htaccess
```

RewriteEngine On 
RewriteCond % 80 
RewriteRule ^(.*)$ https://xeonrealms.com/$1 [R,L]

```

Network Interface
```

auto lo
iface lo inet loopback


# The primary network interface
auto eno1
iface eno1 inet static
address 192.168.1.34
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4

```

Website Config
```

<VirtualHost *:80>
    ServerName xeonrealms.com


    ServerAdmin donotreply@xeonrealms.com
    DocumentRoot /var/www/html


    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined


    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
RewriteEngine on
RewriteCond %{SERVER_NAME} =xeonrealms.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,QSA,R=permanent]
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

PC Interface
```

Address 192.168.1.2
Subnet 255.255.255.0
Gateway 192.168.1.1
DNS 8.8.8.8 
Alt. DNS 8.8.4.4

```

I've been struggling with this for months, thank you for taking your time to try to assist me. Let me know if you need any more info.

Thanks

---

### Post by TheFu on 2017-04-23
Some routers don't allow WAN IP connections they own from inside the LAN. They don't like it when you leave, but try to come back inside.

The most likely issue is that you need to access the site using internal LAN IPs, not the WAN IP.  Just modify your /etc/hosts to map the internal IP be returned for the dns-name you want to use.  Put this on all the PCs on your LAN inside the /etc/hosts file(s) [or the equiv file]:

```
192.168.1.34   xeonrealms.com
```

---

### Post by 1candydoesgames on 2017-04-23
I tried adding that to my /etc/hosts and the server and on my PC. So far it seems to be working. Much thanks.

---

