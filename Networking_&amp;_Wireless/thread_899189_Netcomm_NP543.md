---
title: "Netcomm NP543"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Neochick on 2008-08-24
Hi everyone, a ubuntu newb here :)

i have ubuntu on my desktop, works fine, love it. Now ive decided to take the leap on a acer travelmate 213tx which i had an extr hard drive for. after multiple googlings i have resorted to asking the ore experienced users.

My wireless card is a Netcomm NP543. I have found [another thread](http://ubuntuforums.org/showthread.php?t=46495) where they got it to work, but the method is not described.
My inbuilt dial up modem shows up in the network settings, but not my pcmcia wireless card. After looking around i have determined that it has a ACX111 chipst (but dont quote me XD) and advice on another site was to disable the automatic network manager. done. so now, if i run the 'hardware testing' app, it happily tells me that i have a 'Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)"

also, in terminal, (i cant remember what site i found this on) typing 'sudo lshw -C network' results in"
*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.1b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 1
bus info: pci0000.:02:00.0
version: 03
width: 32bts
clock: 66MHz
capabilities: pm cap_list
configuration: latency=0.

i have tried using NDISwrapper with the 'tnet1130.inf' file from my windows drivers (device works fine in winXP with it) but im being told its an invalid driver.

Any help would be much appreciated! ive been trying to make this go for a good 4 hours or so XD times just flys by when you have a computer problem your trying to fix doesnt it?

Edit: Forgot to add, I'm running with Hardy

---

