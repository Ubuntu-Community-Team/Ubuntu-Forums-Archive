---
title: "[SOLVED] wireless connection problematic"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by charonred on 2008-09-27
I have several PCs I'm trying to get the wireless to work on, but I've lost track of where I am at (I've tried all sorts of suggestions from this forum); so below is a summary of PCs and problems (sorry it's a bit jumbled).

There are 2 PCs at a friends which connect via wireless or ethernet in XP, but won't in Hardy by either ethernet :confused: or wireless without re-selecting the network settings - a 3rd one connects fine by ethernet in XP or Hardy (it's located next to Netgear wireless G router, and has identical PC components to one that won't connect) ??? These are using DHCP and no encryption.

At home I have my IBM laptop running Hardy and it connects via Minitar PCMCIA card in KDE perfectly, yet it has occasional problems in Gnome - I think that Network Manager is buggy, yet kcmwifi seems to make things work - this uses a static IP and WEP, and is the only Hardy install using KDE as default session (the others all use Gnome).

At home everything gets Internet access via a Billion 743GE 4 port/wireless/router/ADSL modem (yeah it's an older unit, but I can't get anything faster than a 1.5Mbit connection from my local exchange, so there's no point getting anything newer/faster).

I also have a Zyxel wireless client in the garage hooked up to a TP-link 5 port switch. The Zyxel connects via wireless to the Billion router/modem and has share privileges so that anything plugged into the TP-link switch has internet access and home network access to shared folders - Zyxel uses a static IP and WEP.

In the garage I've a newly assembled PC (using identical components as my friends 2 PCs); that connects via TP-link/Zyxel fine, but if I pull the ethernet cable from PC and try it's wireless Linksys WMP54G PCI, there's no connection; and no amount of fiddling with Network Manager/Connection settings will get it to work. I also have an older Celeron 900 (XP/Hardy) connecting fine via ethernet to Zyxel.

Apart from my main PC (XP/Hardy) which is connected via ethernet to router, I also have 2 other PCs in house connecting fine; 1 by ethernet (ubuntustudio/XP/Vista), the other by wireless Minitar PCI (plain XP only  machine).

_So my main problem is getting wireless to work in Hardy using Linksys WMP54G PCI card (have RT61.inf installed in NDISwrapper)._

I'm just plain confused by it all now; hopefully someone can help my brain unscramble this wireless networking mess.
(with exception of stated brands, all PCs are current AMD & Gigabyte based)

thought; should I be using static IP, and can the PC have the same IP in both wireless and ethernet?

---

### Post by charonred on 2008-09-30
bump

---

### Post by charonred on 2008-10-02
Seemed to have a work-around to get wireless networking functioning in Hardy.

First NOTE: I wouldn't remove 'Network Manager' as that may kill your ethernet connection (it may not, but it has on one PC).

My laptop which runs Hardy, but with the KDE instead of Gnome, gave me a hint on how to get wireless working - it connects fine as it uses 'kwifi' and not 'Network Manager'.

As I use Gnome on my other PCs I went looking for something similar.

I used Synaptic to install 'wifi-radar' - I then put in the relevant settings and presto, I have wireless networking; and then I rebooted, and yep I still had wireless - after several reboots I still had wireless, so I recommend using 'wifi-radar' instead of Gnome's sometimes buggy 'Network Manager'

---

