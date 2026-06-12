---
title: "OpenVPN and security"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by mastablasta on 2013-10-30
it seems openVPN is a bit easier to vonfigure now. Though still unecessarily difficult. why does one has to put in any commands? even in cli there could be a menu of quesiton offering you to create key or not etc. the commands are needed unnecessarilly for "normal user". 

Anway my main question is how secure is OpenVPN? we plan to create small VPN server to set up LAN so we can play a few older games. at the moment we use hamachi, but while it works for plenty games it doesn't work for some. :-(

---

### Post by mastablasta on 2013-11-04
wow, no reply. 

bump and additional question can i make it so that server is running only when certain user is active? to have a special user that would run VPN server.

---

### Post by Lars Noodén on 2013-11-06
Upstart might be used to make the OpenVPN server run only when some other service is running:

[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

You'd have to also run that first service under Upstart, too.

Just a guess.

---

