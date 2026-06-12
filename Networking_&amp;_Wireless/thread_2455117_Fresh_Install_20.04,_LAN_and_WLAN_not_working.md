---
title: "Fresh Install 20.04, LAN and WLAN not working"
date: 2020-12-12
forum: Networking &amp; Wireless
---

### Post by meise21 on 2020-12-12
Hi,
I just installed 20.04 on my new PC alongside Win10. Neither my LAN nor my WLAN are working. When booting my Win10 both are working.
My computer is a Asus rog strix b550-i with onboard LAN.

LAN:
Ethernet cable is connected and working in Win10. In Ubuntu the device shows up as unavailable in nmcli dev status.

Device name is enp7s0

lshw -C network shows:
description: Ethernet interface
product: Intel Corporation
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:07:00.0
logical name: enp7s0
version 02
serial: 3c:7c:3f:d5:fa:67

I did google around a bit. The driver that's supposed to work with the lan chip of my board is igc

dmesg|grep igc shows the following from:

igc 4.000 Gb/s available PCIe bandwidth (5 GT/s x1 link)
eth0: MAX: 3c:7c...
enp7s0: renamed from eth0

WLAN:
I entered my home WIFI during installation but it failed to connect (I triple checked the password and it was correct). I asked it to continue the install as I assumed that my LAN would be working so no need for WIFI. On my Win10 install WIFI is working.

I noticed when setting up Win10 my WIFI was not working straight out of the box either. I had to install some Asus drivers first before it was working. However my LAN worked straight out of the box so I could just download the Asus suite from the web.
Thanks in advance,
Markus

---

### Post by TheFu on 2020-12-12
Onboard 2.5 Gb Ethernet according to asus.  Seems ubuntu has issues with that.  Intel has updated drivers on their support site.  Previous posters here failed to get those working and most ended up buying intel pro/1000 NICs as the easiest, surest, solution. Welcome to the bleeding edge.

I can't say much about wifi.  I don't use it, but that also appears to be bleeding edge. Perhaps in a few months the HWE kernel or ew release will address those issues.  [https://rog.asus.com/us/Motherboards/ROG-Strix/ROG-STRIX-B550-I-GAMING-Model/](https://rog.asus.com/us/Motherboards/ROG-Strix/ROG-STRIX-B550-I-GAMING-Model/)

I have an asus strix b450 w/ i211 nic and looked at a fresh build with a b550, but the 2.5Gbps nic worried me. 
[LIST]
[*][https://downloadcenter.intel.com/product/184676/Intel-Ethernet-Controller-I225-V](https://downloadcenter.intel.com/product/184676/Intel-Ethernet-Controller-I225-V)
[*][https://ubuntuforums.org/showthread.php?t=2445791](https://ubuntuforums.org/showthread.php?t=2445791)
[*][https://www.phoronix.com/scan.php?page=news_item&px=Intel-2.5G-Ethernet-Prep-4.20](https://www.phoronix.com/scan.php?page=news_item&px=Intel-2.5G-Ethernet-Prep-4.20)
[*][https://community.intel.com/t5/Ethernet-Products/Intel-Network-I225-V-Nework-issue-persist-even-after-FW-upgrade/td-p/1189493](https://community.intel.com/t5/Ethernet-Products/Intel-Network-I225-V-Nework-issue-persist-even-after-FW-upgrade/td-p/1189493)
[/LIST]

---

### Post by meise21 on 2020-12-15
Thanks for your reply. You are right all of my other machines are 10+ years old i-Macs and notebooks so I up until now I was more like living on the bled out edge:-)

I did some more research on my particular issue and found several other people with the same problem. So at least I am not alone. One post mentioned that he switched to the current Pop OS version and there the board's ethernet and wlan controller were working out of the box. So I gave the current PopOS a go and my board is working without problem. So just in case someone stumbles upon this post with the same problem give it a try maybe it also works in your case.

Thanks for your helpful reply!

Bye,
Markus

p.s.: Is there any chance that in ubuntu 20.10 the issues are fixed or are the kernel/driver version the same?

---

