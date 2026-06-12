---
title: "Why does 8.10  - BCM4328 refuses to work"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by EmmDoubleEw on 2008-11-27
Hey everyone,

I recently upgraded from Hardy Heron and I like a lot of the new features but for some reason, *everything that worked well and out of the box about my internet connection went kaput*. My wired connection suffers from random drops every 4 minutes, and my wireless connection doesn't work at all even though I've tried installing enough drivers to make a rock receive a signal. 

I've tried wl turned on, BCM43xx turned on (both through Hardware Drivers) and ndiswrapper with no luck. The wireless troubleshooting guide is completely unhelpful.

I think if I could get ndiswrapper to actually work it'd be fine, but ssb persistently takes control of the card. I've tried the "Hardy Heron fix" proposed here with no luck: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Here is some useful outputs:

**sudo lshw -C network**
*-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

**dmseg** (relevant part)
[ 1438.022960] b43-phy0: Broadcom 4321 WLAN found
[ 1438.064072] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
[ 1438.066349] b43: probe of ssb0:0 failed with error -95
[ 1438.067929] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]

Thanks so much for any help you guys are willing to offer. I really don't want to revert to Heron for something dumb like this.

---

### Post by Idefix82 on 2008-11-27
I haven't upgraded so I will only be able to try and help from my limited experience with Hardy.
When you tried the ndiswrapper route, did you blacklist anything that could interfere? In particular, ssb taking control should be easily fixable. Can you just blacklist ssb, BCM43xx and anything else that could interfere and then try the ndiswrapper route? Then do
```
lshw -C network
```
and see which driver is loaded for your wifi card.

By the way: your title *used to be* an unnecessary flame and if 8.10 really "sucks so much" then you should just go back to 8.04. I am sure that you would receive more responses and people would be friendlier if you just asked for help instead of flaming.

---

### Post by EmmDoubleEw on 2008-11-27
> **Idefix82 said:**
> I haven't upgraded so I will only be able to try and help from my limited experience with Hardy.
When you tried the ndiswrapper route, did you blacklist anything that could interfere? In particular, ssb taking control should be easily fixable. Can you just blacklist ssb, BCM43xx and anything else that could interfere and then try the ndiswrapper route? Then do
```
lshw -C network
```
and see which driver is loaded for your wifi card.

I tried that before. The network just goes "UNCLAIMED"

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0

However, the driver is clearly installed:

**ndiswrapper -l**
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: wl)

As far as the flame, a flame is technically directed against a person. Not being able to connect to the internet is *extremely* frustrating, in case you've never experienced it, so I don't think my anger is unwarranted or misdirected.

---

### Post by Idefix82 on 2008-11-27
Can you try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart

```
and let me know if that works?

Your anger is completely misdirected since the only people who will read it here are those whom you are asking for help. If you really want to piss those off who have given you this free software and who therefore, according to you, deserve your anger, then post according sentences on Launchpad.

---

### Post by EmmDoubleEw on 2008-11-27
Thanks idefix, that worked. My remark was just an offhanded expression of my frustration and I didn't mean to direct it at anyone, so I apologize for it.

---

### Post by Idefix82 on 2008-11-27
You are welcome! I'm glad it worked. This solution is not permanent. To make it permanent, you need to have a script that runs at startup and that makes sure that the modules wl and b44 are loaded in the same order.

See here for an explanation of what is going on: [http://ubuntuforums.org/showthread.php?t=959451]("http://ubuntuforums.org/showthread.php?t=959451")
Or alternatively, google for BCM4328 Intrepid and click on the first search result ;)

---

