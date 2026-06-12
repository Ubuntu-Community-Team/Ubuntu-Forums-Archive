---
title: "Proxim Orinoco 8480-WD"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by jgcamp99 on 2007-02-28
Wireless on my Dell Latitude L400 has been a struggle with Edgy. The issue, no bootable cdrom, so I installed Edgy over a PXE internet installation. The Linux restricted modules had to be added afterwards. And the version I added was the generic kernel since that is the kernel I had installed by default. Anyway, this wifi card uses the Atheros 5212 chipset. Does anyone have a step by step that will get this card functioning properly for edgy ?

Ohhhh, It's an Proxim 8480-WD abg gold card.

---

### Post by jgcamp99 on 2007-03-02
Good news or so I thought. I added the restircted Edgy modules/kernel from Synaptics and it worked for a moment, that is, I saw my wireless network in the gnome networking applet and tried to connect to it. Unfortunately it was WEP protected, so that wouldn't connect when I tried to put the WEP key in. I've found it'll connect to non-WEP networks which is a quantum leap for what I was experiencing before. 

Anyway, what the issue was that allows me to have "ath0" after adding the restricted kernels, it was default booting into a 386 kernel, I cleaned the grub boot menu to only have the generic kernels 2.6.17.10 and 2.6.17.11 (as I recall) and that's when I started having some relative success with this. The card will work. But what has me perplexed, shouldn't the etc/pcmcia/config have a specific entry for this or any other supported card and bind a driver ?

---

### Post by jgcamp99 on 2007-03-05
It works, I don't know what I did, but I have internet connection right now. The two network applets, one works, but the Network Manager applet 0.6.3 (Red Hat/Novell) indicates no network connection. The other, Network Monitor 2.12.0 (Sun) works and indicates transmission/reception level, even configures ath0. The other day it was the other way around. I was seeing my DI-614+ router on the Network Manager applet and not the Network Monitor applet.

---

### Post by jgcamp99 on 2007-03-05
I'm wondering if resetting the router had anything to do with it ? I have an Apple PB as well and it wouldn't connect, until last night as well. I still haven't figured a way to get the applet working. This is the one I'm talking about:

[http://www.thinkwiki.org/images/b/b7/Available-accesspoints.jpg](http://www.thinkwiki.org/images/b/b7/Available-accesspoints.jpg)

Mine shows up, but it's strictly limited to wired (10/100) aspect of networking, no wireless.

---

