---
title: "PPPD Connected to Internet, Firefox won't browse web, NSlookup works."
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by mk4umha on 2008-05-13
Hi all, i got pppd to work with the ATT broadband wireless in 8.04 but I can not browse the web with firefox. If I [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx) it won't connect. I can do nslookup to domain names and ping with no problems.

If I load windows up in virtualbox, the firefox inside windows works fine.

I also noticed that if I connect to my home wireless router first, then do a "route del default" and connect to ATT Broadband Wirless, firefox will resolve domain names with no problems.

Does anyone know how to fix this? thanks.

---

### Post by ScorpKing on 2008-05-13
firefox 3 will start in offline mode on 8.04 if you use dialup. close networkmanager and edit /etc/network/interfaces. change lo to this:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

it should now work (you might have to update the routing table or just restart)

---

### Post by mk4umha on 2008-05-13
THat worked after I unchecked "work in offline mode". I didnt know it defaults to that. THanks!

---

### Post by Nikitas350 on 2008-05-28
See [http://ubuntuforums.org/showthread.php?t=800179&highlight=offline+networkmanager](http://ubuntuforums.org/showthread.php?t=800179&highlight=offline+networkmanager)

---

