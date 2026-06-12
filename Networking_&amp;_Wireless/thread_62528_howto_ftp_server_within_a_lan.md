---
title: "howto ftp server within a lan"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by bootlinux on 2005-09-05
We have 4 computers on a home network with a router which is hooked up to broadband modem. I've installed a ftp server on one of them runing Ubuntu. It works great on the local network but I can't link to the internal address over the Internet. I don't really need a domain name as I just plan on sharing files with friends on a Email list group. I can email a IP address so they can hook up to my server but the computer I'm using is on a LAN. Is this possible and how would they get through my router to the internal address? Thanks for any information you can enlighten me with.

---

### Post by dJnEvS on 2005-09-05
you sould forward port 21 in the router to your comp.. ;)
dunno if you have exp with router configuration..
if you know your defaultgateway, you sould http it in browser.. (mostly)
my gateway is 192.168.1.1, so if i want to config my router, i sould go to [http://192.168.1.1](http://192.168.1.1)...
try something ;)

---

### Post by bootlinux on 2005-09-05
Would I then use the default gateway as the IP address for anyone who want's to use the ftp server?

---

### Post by dJnEvS on 2005-09-06
no, you sould open port 21 in your router (if you have one).
then ppl can connect to your ftp server with your WAN ip..
[http://whatismyip.com/](http://whatismyip.com/)
:)

---

### Post by operator.40 on 2005-09-06
[QUOTE=bootlinux]Would I then use the default gateway as the IP address for anyone who want's to use the ftp server?[/QUOTE]

People would connect to your public IP as provided by your ISP. You're router would then route that request to port 21 of your ftp server.

log into your router and configure port 21 to go to the correct server. Then ftp to your public address.

---

