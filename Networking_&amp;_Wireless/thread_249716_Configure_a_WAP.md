---
title: "Configure a WAP"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by persev on 2006-09-02
Okay searching has turned up no results for me so here is my post.  I have  a home network, cable modem>router>WAP.  The linksys WAP11 was given to me by a friend but I had to have him (windows IT pro) come over and set it up for me (humiliating to say the least) because I couldn't access the hardware from linux.  I even downloaded the setup utility from linksys and ran it under wine but the setup util couldn't see the WAP from any of my linux boxes.  I am stumped.  The reason I want to access the WAP is because at this point it is running with no encryption, this is bad I think, I would like to setup wpa if supported by the WAP but even wep would be better than nothing.  Hopefully someone here can help me not to have to be humiliated again by having my windows buddy come back and fix everything for my "linux crap" as he calls it.

---

### Post by Uluen on 2006-09-03
Is the AP a DHCP server? Did you try [http://192.168.1.1/](http://192.168.1.1/) ?
If the AP is not the default gateway, you could try setting one of your computers to static IP (192.168.1.10, 255.255.255.0, gw 192.168.1.1), connect the cable to the AP and try the URL above again, see if you can get to the Linksys managment interface then.

---

