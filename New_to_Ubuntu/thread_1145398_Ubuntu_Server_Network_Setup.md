---
title: "Ubuntu Server Network Setup"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by akkad on 2009-05-01
i have successfully convinced my friends to jump to windows to ubuntu server :) on our home server-like PC, now the thing is that we want to setup our network, and as am not familiar with network stuff, i will list the network setup we are looking for and here i really need your guidance how to accomplish it, what am looking for is :

- set our ubuntu server as dhcp server so it will issue IP addresses to every connected client on the network, where the server is connected to the internet so it should also let the clients to be able accessing the internet.

- the server will receive http/ftp requests from the internet, where we want the server to translate the request and depending on the request the server will forward the request to the client that has his own http/ftp server.

any idea about those??

---

### Post by jbrown96 on 2009-05-01
There is a really good GUI app for DHCP. It's called gadmin-dhcpd, and it's in synaptic. It's very easy to setup and works really well. There is a help section if you are having trouble setting the values.

---

### Post by arapa on 2009-05-01
If I understand what you're looking to do - you want to set up your ubuntu server as a gateway/router? 

Something like this:
HOWTO: Internet sharing with Ubuntu (NAT Gateway)
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

---

### Post by akkad on 2009-05-01
am not sure what ip forwarding means but, is it possible to assign URLs to IPs? 

so in some configuration file can i write something like this:
[ftp://PC1.ftp.com:21](ftp://PC1.ftp.com:21)  forward to  10.1.1.12
[ftp://PC2.ftp.com:21](ftp://PC2.ftp.com:21)  forward to  10.1.1.23
......

thats what exactly am looking for, which is to let my server decide to which PC forward the request.

---

### Post by The Cog on 2009-05-01
You need a proxy server for that - to accept http requests and forward them depending on the URL. I know that apache can do that. Probably other software too.

---

### Post by gsp8181 on 2009-05-01
Sounds like you want a DCHP server and NAT, NAT can be achieved in most router configurations, I think it is possible to achieve in Ubuntu by making the server a DMZ and installing some package (Hunt around in Aptitude :D). A DCHP server can be gotten through sudo tasksel afaik

Hope this helps :)

---

