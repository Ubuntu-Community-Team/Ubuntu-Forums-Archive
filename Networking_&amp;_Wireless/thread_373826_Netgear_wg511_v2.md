---
title: "Netgear wg511 v2"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by shiznatix on 2007-03-01
Ok so I bought this wireless card and I have been trying to install it without luck. I have tried a few of the tutorials including this one: [http://ubuntuforums.org/showthread.php?t=76804](http://ubuntuforums.org/showthread.php?t=76804)

but even thought I get top the point of 'hardwear present, driver present' from ndiswrapper the card still will not show up in my network manager nor will the lights light up.

The biggest discrepency that I have read is that there is something that I need to 'blacklist'. The file they say to edit is /etc/hotplug/blacklist but that file/directory did not exist so I created it and added in the line prism54 but that does not seem to do anything so now I removed it again.

lspci shows this as my card:
> 0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

If anyone can help me out that would be awesome.

---

### Post by chili555 on 2007-03-01
That tutorial is for a v3, using a Prism chipset and you have a v2 with a Marvell chipset.

Please look here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)

Especially here: Card: Netgear WG511 v2 54Mbps Cardbus adapter (Made in China)

and this:> Driver: Windows XP driver available on the Netgear CD: WG511v2.INF

And this:> Clashes with mrv8k driver at system startup. Blacklist mrv8k by adding 'blacklist mrv8k'(without quotes) in /etc/modprobe.d/blacklist. This solves the problem at startup.

Several listings here are troublesome.

---

### Post by shiznatix on 2007-03-01
Ok I uninstalled ndiswrapper then re-installed it then I installed the drivers for windows 2000 but when I do modprobe ndiswrapper it just hangs. I tried installing the windows xp drivers and the same thing happens.

Any advice?

---

### Post by chili555 on 2007-03-01
Did you yank out the card, sudo rmmod mrv8k and then blacklist mrv8k first?

---

### Post by polypus on 2007-03-07
have a look at this it might help:

[http://e-lehmann.de/index.php/2006/12/23/wlan-on-ubuntu-via-netgear-wg511v2/](http://e-lehmann.de/index.php/2006/12/23/wlan-on-ubuntu-via-netgear-wg511v2/)

i'm stuck because i lost my CD and only have the card. anybody know where i can get those drivers?

---

### Post by chili555 on 2007-03-08
The easiest way is to go to Netgear's support page and download the driver for your exact version. v1, v2 v3, etc. use different or improved chipsets, so grabbing the wrong file will not work.

Here is a post about the process to get the .inf file out of the driver file for a v1 card. Your process will be very similar. [http://www.ubuntuforums.org/showthread.php?t=375182&highlight=WG511](http://www.ubuntuforums.org/showthread.php?t=375182&highlight=WG511)

---

### Post by foofi22 on 2007-03-12
I have managed to get the WG511 v2 (China) card working.  I did not use the Netgear drivers (although that is not to say they do not work) I used the mrv8335 drivers along with ndiswrapper 1.8  However this did not work straight away.  This only managed to get the green light on the card blinking.  From there I stumbled upon some method to get the card connecting to the router.  Have you got to the stage where the green light is flashing and you can "see" you AP using sudo iwlist wlan0 scan?

---

### Post by obnoxious1 on 2008-02-14
just installed Ubuntu alternate cd, 6.06.1 dapper drake.  i have the netgear WG511 v2 (China) pci card.
installed ndiswrapper 1.8.  have the driver cd.  but when i go to install drivers i get a message that says couldn't copy WG511v2.INF at /usr/sbin/ndiswrapper line 135. and couldn't copy WG511v2XP.sys at /usr/sbin/ndiswrapper line 135.  asking for some help getting online.  seem to be getting nowhere with this.  btw, brand new to the linux world.

---

