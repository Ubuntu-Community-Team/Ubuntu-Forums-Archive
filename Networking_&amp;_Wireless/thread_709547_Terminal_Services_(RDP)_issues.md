---
title: "Terminal Services (RDP) issues?"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by jschramm97 on 2008-02-27
I'm attempting to RDP from my Ubuntu 7.10 to my WXP SP2 machine. I'm able to RDP to the XP machine from other Windows workstations successfully. 

From Ubuntu i go to Terminal Server type the DNS name and my username/password click Connect, i instantly receive an error that it's unable to connect to the XP Box. 

Now i can browse file shares that are on this box from my Ubuntu machine, but when i try to us Network Tools to ping the DNS name i also receive an error, any idea what could be causing this? I guess i could try the direct IP address next. 

Thanks!

---

### Post by dca on 2008-02-27
In TSClient, put the IP address of the XP machine you're trying to connect to, next make sure RDP is selected as protocol.  Username & p/w are very important....

---

