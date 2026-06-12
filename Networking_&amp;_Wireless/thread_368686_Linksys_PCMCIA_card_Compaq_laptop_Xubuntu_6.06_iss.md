---
title: "Linksys PCMCIA card Compaq laptop Xubuntu 6.06 issue"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by XW5000 on 2007-02-23
Hi,
I'm not very good with linux yet but I want to learn it badly.
I have 3 computers running Ubuntu 6.10/Beryl and I'm very happy w/it.

I installed Xubuntu 6.06 on a Compaq 1255 laptop few days ago. 
The installation process worked fine but I have the following issues:

1-No network: This laptop has a wireless linksys pcmcia card (WPC11).
Before the installation (live cd) the network card was alive (both lights blinking) but after the installation (reboot) the card is dead (just the red light solid, no gree light).
Any hint how to troubleshoot it ?
I tried the lspci command, I found the controllers but nothing about the wlan card ...

2-No Audio: The laptop had Aureal 3D when it was loaded with "w...... 98" (I do not curse in public). 
Xubuntu did not load anything for audio.
Any hint how to troubleshoot it ?

I tried forums and other sources but I could not find any hint that worked for me. I tried to reload Xubuntu a couple times with the card in/out w/o luck.

Any help is greatly appreciated.
Thanks in advance.

---

### Post by chili555 on 2007-02-23
I believe the WPC11, if it's v.3 is a Prism 3-based card that uses the orinoco_cs driver. You should look at sudo lsmod to see if orinoco_cs is loaded.

In my own experience, and this is based on experimentation, not actual science, sometimes the prism2 module gets loaded, too. In my case, my Prism-based card works great with orinico, hostap, and hermes, but *not* prism2.

I withdrew the card, did a sudo rmmod prism2 (might have been prism2_cs), added it to /etc/modprobe.d/blacklist and re-inserted the card. It works fine.

YMMV

---

