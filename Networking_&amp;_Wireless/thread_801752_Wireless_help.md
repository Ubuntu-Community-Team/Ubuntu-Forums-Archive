---
title: "Wireless help"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2008-05-20
You know it's my nature to be a wise a.. and usually it get's a smile, laugh but this is a bit different as I am going to ask for some help (but be a wise guy 1st).  I have switched from Fedora to Ubuntu and had some video issues, nice descriptive title, a lot of detail and not so much as one response, yet people post (after being told again and again not to), post things like Help me, and get responses (even from moderators!)  

This is rediculous, so by putting a nice vague title, maybe I too will get some help (and a chuckle from someone)

Well, as the subject states, a little wireless help here is appreciated.  I have a Dell XPS M1330, and the past dictated an ndiswrapper install, but this is a clean 8.04 intall and there is a section under System -> Administration -> Hardware Drivers.  In there showed the card, so I clicked enable (have I mentioned I am almost a genius).  Well it opt'd to install the firmware, now it shows a nice green light saying "in use" and the check box enabled.

What else (if anything) has to be done, I am sitting next to my older Dell (*cough* XP), but connected to my wireless network fine (I have 2 other neighbors broadcasting).  I used to use a simple app which there was a package for ubuntu called wlassistant and it works great (when things work).  When I start it at the command line I get the following;

scan: /sbin/iwlist wlan0 scan
No networks found!

Not sure what else I can provide, so I will just dump a few more things I can think of;

**sudo lspci |grep Broadcom**
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

[B]dmesg |grep Broadcom
[/B][   27.552665] b43-phy0: Broadcom 4311 WLAN found

I have read through numerous things, all earlier versions of ubuntu where the card was never seen, so this "Hardware Driver" thing finding and installing firmware makes me hesitate going the windows driver route.

Thanks for any posts, hate replies, etc...

: Lr :

---

### Post by Ayuthia on 2008-05-20
> **xkaliburx said:**
> You know it's my nature to be a wise a.. and usually it get's a smile, laugh but this is a bit different as I am going to ask for some help (but be a wise guy 1st).  I have switched from Fedora to Ubuntu and had some video issues, nice descriptive title, a lot of detail and not so much as one response, yet people post (after being told again and again not to), post things like Help me, and get responses (even from moderators!)  

This is rediculous, so by putting a nice vague title, maybe I too will get some help (and a chuckle from someone)

Well, as the subject states, a little wireless help here is appreciated.  I have a Dell XPS M1330, and the past dictated an ndiswrapper install, but this is a clean 8.04 intall and there is a section under System -> Administration -> Hardware Drivers.  In there showed the card, so I clicked enable (have I mentioned I am almost a genius).  Well it opt'd to install the firmware, now it shows a nice green light saying "in use" and the check box enabled.

What else (if anything) has to be done, I am sitting next to my older Dell (*cough* XP), but connected to my wireless network fine (I have 2 other neighbors broadcasting).  I used to use a simple app which there was a package for ubuntu called wlassistant and it works great (when things work).  When I start it at the command line I get the following;

scan: /sbin/iwlist wlan0 scan
No networks found!

Not sure what else I can provide, so I will just dump a few more things I can think of;

**sudo lspci |grep Broadcom**
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

[B]dmesg |grep Broadcom
[/B][   27.552665] b43-phy0: Broadcom 4311 WLAN found

I have read through numerous things, all earlier versions of ubuntu where the card was never seen, so this "Hardware Driver" thing finding and installing firmware makes me hesitate going the windows driver route.

Thanks for any posts, hate replies, etc...

: Lr :

The only thing that I am thinking right now is to install Wicd and see if it makes a difference.

I have been seeing a lot of people who cannot see any wireless and I am unable to tell if it is because of Network Manager or something else.  As far as I know, the 4312 rev 01 should work with the b43 driver.

---

### Post by xkaliburx on 2008-05-20
Nope, not only that, it broke my wired network!  Wicd had a nice dropdown and I tried all (naturally the broadcom first) and got the following in the debug screen;

use default profile
setting: broadcom
refreshing...
Number of wireless networks detected: 0

Then eth0 was gone, I had to goto System/Admin/Network, configure and the wired network device was no longer enabled... odd!  So I re-enabled and that came back, but nothing on the wireless.  Also read a diff post, did the *sudo lshw -C network* and got the following which someone may see and might also help.

*-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb


*-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

The search continues but thanks for a quick idea!

Lr

---

### Post by santhony on 2008-05-20
I think allot of us are having problems getting the Broadcom wireless to work... I have a BCM4306 ver 2...

---

