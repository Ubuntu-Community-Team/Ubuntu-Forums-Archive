---
title: "Broadcom Wireless Bonanza"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by slackwarespy on 2008-02-14
Hello, I have a problem with my wireless card(BCM4318 Broad Com Corporation) which when I type in "lshw -C network" I get:
*-network:1 Unclaimed
description: Network controller
product: BCM4318[Airforce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: b
bus info: pci@0000:00:0b.0
version: 02
width: 32 bits
clock: 33 MHz
configuration: latency=64

this is interesting because it says it is unclaimed and i have no logical id.
When i first tried to fix my wireless card I used apt-get to install ndiswrapper and installed the windows driver from a forum thread. When I put in the command "ndiswrapper -l" It tells me this:
bcmwl5 : driver installed
device (14E4:4318) present (alternate driver:bcm43xx)

But when i use ifconfig the wireless device does not show up even if I use -a after.
When I try iwconfig it doesn't list the device either. Now I also installed wicd in order to manage my networks better, which has worked out just fine. Usually wicd just says "no wireless networks found" suggesting that it doesnt use the wireless card either. But when i reinstall my firmware driver the terminal text for wireless says,"
eth1 0 0 0   0  0 0 ... etc which makes me believe that problem has to do with drivers. Sadly even with this new output wicd tells me that there are no wireless networks detected and ifconfig along with iwconfig still detect no wireless card.
If my ndiswrapper says the driver is working then how come I can't even see the device unless I use lshw. Installing the firmware driver was done through the restricted driver's manager, and wicd was done through DARKNOOb's _broadcom the easy way_ installer.

If my problem is a driver problem how do I fix this so that my device is claimed and not unclaimed?

---

