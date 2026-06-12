---
title: "Steam Doesn't Work With Squid"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Hovercat on 2011-02-13
Well, after I had some other issues with my network this morning, I re-installed Ubuntu and copied my old configuration over to the new installation. Everything has been working fine earlier, but now Steam won't connect to Steam servers. I looked up their requried ports on their website and allowed them in Squid and restarted Squid, but Steam still won't connect.

Edit: Minecraft does not work either, it says "cannot connect to minecraft.net" when I can easily open up [www.minecraft.net](www.minecraft.net) in my web browser.

Changes I've made to squid.conf (From the original):

```
acl SSL_ports port 443        # https
acl SSL_ports port 563        # snews
acl SSL_ports port 873        # rsync
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl Safe_ports port 631        # cups
acl Safe_ports port 873        # rsync
acl Safe_ports port 901        # SWAT
acl Safe_ports port 2217

acl Safe_ports port 27000
acl Safe_ports port 27001
acl Safe_ports port 27002
acl Safe_ports port 27003
acl Safe_ports port 27004
acl Safe_ports port 27005
acl Safe_ports port 27006
acl Safe_ports port 27007
acl Safe_ports port 27008
acl Safe_ports port 27009
acl Safe_ports port 27010
acl Safe_ports port 27011
acl Safe_ports port 27012
acl Safe_ports port 27013
acl Safe_ports port 27014
acl Safe_ports port 27015
acl Safe_ports port 27016
acl Safe_ports port 27017
acl Safe_ports port 27018
acl Safe_ports port 27019
acl Safe_ports port 27020
acl Safe_ports port 27021
acl Safe_ports port 27022
acl Safe_ports port 27023
acl Safe_ports port 27024
acl Safe_ports port 27025
acl Safe_ports port 27026
acl Safe_ports port 27027
acl Safe_ports port 27028
acl Safe_ports port 27029
acl Safe_ports port 27030
acl Safe_ports port 27031
acl Safe_ports port 27032
acl Safe_ports port 27033
acl Safe_ports port 27034
acl Safe_ports port 27035
acl Safe_ports port 27036
acl Safe_ports port 27037
acl Safe_ports port 27038
acl Safe_ports port 27039
acl Safe_ports port 27040
acl Safe_ports port 27041
acl Safe_ports port 27042
acl Safe_ports port 27043
acl Safe_ports port 27044
acl Safe_ports port 27045
acl Safe_ports port 27046
acl Safe_ports port 27047
acl Safe_ports port 27048
acl Safe_ports port 27049
acl Safe_ports port 27050
acl Safe_ports port 4380
acl Safe_ports port 3478
acl Safe_ports port 4379

acl purge method PURGE
acl CONNECT method CONNECT

acl bad url_regex "/etc/squid/squid-block.acl"
http_access deny bad

acl allcomputers src 192.168.0.0/255.255.0.0
http_access allow allcomputers
```Contents of Squid-block.acl:

```
.4chan.org
.redtube.com
.brazzers.com
.brazzersmobile.com
porn
sex
prox
.hidemyass.com
.co.nr
.tk
.co.cc
```Thanks to anyone that can help.

---

### Post by Hovercat on 2011-02-14
Bump

---

### Post by Aoude on 2011-02-14
Hey have you tried using Wine?

I'm using it on my laptop and can run steam fine.

Give it a try ;)

---

