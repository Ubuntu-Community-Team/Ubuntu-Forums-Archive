---
title: "amd64 + bcm4318(native) + 1.5GB = freeze"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by muanis on 2006-10-09
I'll post more details tomorrow (I'm not in my laptop right now), but here are the facts:

The Machine:
HP DV5130 - amd64 with 1,5GB memory with Dapper wiht the latest updates as of today.

What i've reached:

using the autoinstall for native that's available out of the box I just get a freeze on boot, after digging around, I found that the it also (!) freezes with the following sequence:

modprobe bcm43xx
ifconfig eth1 up <- wlan light turns on and off with up/down
iwconfig eth1 ap any
iwlist eth1 scan <- here it freezes, no logs, nothing

Any ideas? I've read a bunch of tutorials here at ubuntuforuns but still couldn't manage to get wifi working. I'm almost waiting for the next release.

I don't have ndiswrapper loaded, but bcm43xx also appers on lsmod with something like ieee80211 and another one with the words softmac.

I will continue to try tomorrow. Thanks in advance for any help.

---

### Post by elektrolott on 2006-10-10
Running wpa_supplicant with 2.6.15-25 / bcm34xx causes hard lockup
[https://launchpad.net/bugs/50432](https://launchpad.net/bugs/50432)

---

### Post by compwiz18 on 2006-10-20
I've only got 1GB, and it locks up for me too...

---

