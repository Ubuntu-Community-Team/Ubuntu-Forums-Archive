---
title: "Resolution of BCM4318 (rev 02) wireless on Feisty"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by rmarc71 on 2007-06-24
I've been beating my head against the wall with my wireless setup on Fiesty since I upgraded from Dapper
(where it had been working perfectly for over a year).  I had just been using wpa_supplicant and a manually configured conf file in Dapper (left over from my Gentoo install).

Since my pain seems to have ended and I have a combination that works, I thought I'd share.

First, my laptop is an Acer 5002 Wlmi.


```
 lspci| grep Broad
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I had tried the bcm48xx-fwcutter stuff, which made  my wifi light come on, but that's about it.  I also tried various combinations of ndiswrapper with wpa_supplicant and had all sorts of failures.  The problem seemed to be isolated to WPA-PSK though.

Long story short, here's my config that seems to work:

I upgraded my kernel, first, which seemed to have no affect, but I kept it anyway.  I booted up into
standard kernels with my compiled ndiswrapper and works there too, but just thought I'd mention it.

Kernel: 2.6.21.3-custom
NDiswrapper (1.46...compiled these myself):

```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.21.3-custom/kernel/drivers/net/wireless/ndiswrapper.ko
version:        1.46
vermagic:       2.6.21.3-custom SMP mod_unload 586 

```

wpa_supplicant v0.5.8 (compiled this as well)

Broadcom Driver I got from acer's driver download for my laptop.

I also downloaded and used wicd, instead of network-manager, since I couldn't seem to make
that work with WPA.  wicd seems to just be a wrapper around wpa_supplicant, nothing special about
it other than a nice interface to the config (v 1.2.9).  There's a debian package for this one.

---

### Post by scrooge_74 on 2007-06-24
You should post that[ here]("http://www.ubuntuforums.org/showthread.php?t=185174") too

---

### Post by biscuits on 2007-06-24
removed comment

---

