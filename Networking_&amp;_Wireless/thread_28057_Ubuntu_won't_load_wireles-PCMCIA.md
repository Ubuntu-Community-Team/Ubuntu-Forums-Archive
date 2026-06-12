---
title: "Ubuntu won't load wireles-PCMCIA"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by niels on 2005-04-18
I have an odd problem. Last friday Ubuntu sudently stopped loading my Linksys PCMCIA wirelessnetwork card. I't has worked with no problem for servel month, but after my internet was down it won't load.
After opgrading to Ubuntu 5.04, I saw that ndiswrapper was loaded during the 'Configuring Network Interfaces' of the startup. But now it doesen't do anything. The 'Power' light turns on during startup, but the 'Link' light never gives a blink.
When I tyes the ndiswrapper -l command, I get the following message:
```
 root@niels:/home/niels # ndiswrapper -l
 Installed ndis drivers:
 net8180 driver present, hardware present 
```

What might the problem be, and how do I solv it?

/ Niels

---

### Post by az on 2005-04-18
Maybe this?
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

### Post by niels on 2005-04-18
[QUOTE=azz]Maybe this?
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)[/QUOTE]

No, this can't be the problem. The Linksys PCMCIA-card is activated during the 'Starting hotplug subsystem' part of the startup. The card is also registered as present by ndiswrapper.

---

