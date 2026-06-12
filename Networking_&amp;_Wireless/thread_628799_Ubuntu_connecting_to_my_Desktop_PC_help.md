---
title: "Ubuntu connecting to my Desktop PC help"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by brucem91 on 2007-12-01
Hello. I am almost a complete noob to ubuntu. I have ubuntu installed on a laptop, and windows xp installed on a desktop PC, which stays on all day long(not night, since the computer is in my room and I dont like to hear anything when I sleep). Say I want to go downstairs to watch TV, but I still want to access all the programs, files, ect from my desktop. How would I remote connect to the XP desktop from the Ubuntu. Both computers would be on a wired connection, in the same network. Yes, I do use a router. I have been able to do this before, but it was an XP to XP connection using MSN.
Please help.
Bruce

---

### Post by njparton on 2007-12-01
Install a vnc server on your xp box and a vnc client in ubuntu.

---

### Post by victorbrca on 2007-12-01
You can also use RDP, built-in to XP and Ubuntu.

Go to XP, right click on My computer => Properties and allow remote connection (remote desktop, not remote assistance)

[IMG]http://screenshots.modemhelp.net/screenshots/Windows_XP/System_Properties/SP2/Remote/Index.jpg[/IMG]


Them go to Ubuntu, Alt + F2, tsclient.

Choose RDPv5, put the IP or hostname of the XP box and you are done deal. You can even play around with things like resolution, color and image caching...


PS: Make sure port 3389 is not open on your router for security..  ;)

Vic.

---

