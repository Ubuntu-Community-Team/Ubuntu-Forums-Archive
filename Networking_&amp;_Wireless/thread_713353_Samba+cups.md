---
title: "Samba+cups"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by damichi on 2008-03-02
HI everybody!

I got SAMBA & CUPS up running. I can acces my SAMBA SHARES and stream video and studd. And I can print a Testjob on my printer (HP Laserjet 1200) via the CUPS Webinterface IP:631

How can I add this Printer to the Samba shares? It's installed on my Linux Ubuntu server and I want to print from my macbook and my mac pro

---

### Post by kidders on 2008-03-04
Hi there,

OSX has native support for IPP, so there's no need to involve third party (ie Microsoft's) networking protocols. Assuming your CUPS is configured the way OSX likes it, your printer should "just work". You can ignore Samba.

---

