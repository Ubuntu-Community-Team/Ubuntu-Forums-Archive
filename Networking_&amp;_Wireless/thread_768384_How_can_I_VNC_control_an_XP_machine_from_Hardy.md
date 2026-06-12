---
title: "How can I VNC control an XP machine from Hardy?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by trubshac on 2008-04-26
Hi

I have:
1) A laptop running Hardy with the default "remote desktop applicatoin" and also "vnc-java" package installed.
3) A PC running windows XP with TightVNC v1.3.9.

I have no problem controlling the laptop with the XP machine, but I am unable to control the XP machine from the laptop.  I can however control another Ubuntu machine from the laptop.

Does anyone know if this should work?  If not, is there a better version of VNC that I should be running on my XP machine.

Any suggestion gratefully received.

Thanks.

---

### Post by nhandler on 2008-04-27
TightVNC works fine. The first thing I would check is whether or not the Windows machine is behind a firewall. If it is, read [this]("http://www.tightvnc.com/faq.html#portfwd"). It explains how you need to set up port forwarding for ports 5800 and 5900. Another thing you can try doing is runninc a vnc client on the windows machine. Using that client, connect to "localhost". If it allows you to connect, it means that the server is working fine, and that your firewall is preventing other computers from connecting to it.

---

