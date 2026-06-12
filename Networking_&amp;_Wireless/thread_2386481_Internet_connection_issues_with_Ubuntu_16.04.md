---
title: "Internet connection issues with Ubuntu 16.04"
date: 2018-03-06
forum: Networking &amp; Wireless
---

### Post by zachg2 on 2018-03-06
I had this problem since 16.04 was first released but I haven't look into it because I didn't had time .

Anyway all my machines both desktop and laptop have trouble connectiing to the Internet,even the Network installer won't work.

First in Firefox it would take forever to load a page but this seems to be fixed by disabling the ipv6 even though my router uses ipv4.

Even though the problem is fixed in Firefox most installed programs( including the installer and updater)  would think that I'm not connected to the internet Wirelessly or with Ethernet.

Trying to install programs via the command like would return with an error or connectiing to the repository would take forever.

My modem is a ZTE H208N locked by my ISP (CYTA GREECE) so I can't firmware update it, but the same thing happens at my parents home with a TP Link Modem.

I need Ubuntu for my Robotics class and I also want to replace Windows in my laptop (a IdeaPad 100s)
Can someone please help I would appreciate it :-)

---

### Post by kc1di on 2018-03-07
please install inxi from software center or via terminal with this command```
sudo apt-get install inxi
``` 
once installed run this command and post the output here:
```
inxi -Nn
```

Thanks.

---

