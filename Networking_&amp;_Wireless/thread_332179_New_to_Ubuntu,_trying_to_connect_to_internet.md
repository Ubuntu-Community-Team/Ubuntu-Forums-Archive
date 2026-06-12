---
title: "New to Ubuntu, trying to connect to internet"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by joshdb on 2007-01-05
Hey there.  I'm a new Ubuntu user.  I just got a new Windows PC and switched my old over to Ubuntu.  Later on I'll delve into the finer intricacies of Linux, but for now I'm stuck at setting up a wireless connection!

My old PC still has it's wireless card in it (unknown brand, was in when I bought it, sadly), and it was connecting to my wireless network fine before the switch.  I'm posting this off of my new PC now.  I've already done quite a bit on Ubuntu by downloading files onto a thumbdrive and moving it over, but I really just want to use app-get :rolleyes:

Can anyone help me out?  I've already trying using Network Manager, but my card isn't detected in the first place ](*,)

EDIT:  I've found out that my wireless card is most likely a Linksys Wireless-G with Speedbooster #2

---

### Post by scrooge_74 on 2007-01-05
look for linux drivers, if not use the windows drivers using ndiswrapper

---

### Post by stupidkid on 2007-01-05
Run lspci in the command line and see what the chipset for your wireless card is. For example, you should see soemthing like

```

...
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
...

```

---

### Post by joshdb on 2007-01-05
With the lspci command I got

> 02:07:0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 18)

What do I do with this?

By the way - I'm so very sorry for sounding noobish.  I am, in fact, new to this, though.  Bah!  :???:

---

### Post by mxrten on 2007-01-05
That's a ordinary network card and not the wireless one.

---

### Post by joshdb on 2007-01-05
Alrighty...  I went back and got this

> 02:08.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 10)

---

### Post by stupidkid on 2007-01-06
Seems like this thread is the howto for that card. The one they have is rev 03, but it should work for rev 01.

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by joshdb on 2007-01-06
Yeah...  I looked there.  Installed Network manger, cutter, etc. but Network Manager still doesn't detect the card

It has to do with the firmware, I think

Frustrating

---

