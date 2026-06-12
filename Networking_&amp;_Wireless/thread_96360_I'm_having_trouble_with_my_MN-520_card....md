---
title: "I'm having trouble with my MN-520 card..."
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by dswatuga on 2005-11-28
I am very much a beginner and have found a lot of help on this site, but my MN-520 wireless card doesn't seem to want to work.

I installed the NdisWrapper that came bundled with the Ubuntu release and have tried to install a 520.inf file I have. When I try to work with this driver(sudo ndiswrapper -i MN520.inf) though I keep getting "Invalid Driver!".

Does anyone have any advice or a MN-520 driver they might be able to email me?

Thanks for any help you can give me.

---

### Post by Lambert on 2005-11-28
When you do the install command are you in the directory where the driver is?
Is there also a .sys file in that directory? Usually there is a .sys file that needs  to accompany the .inf file.

I also show the 520 using the prism2 linux-wlan-ng driver which is in breezy. Have you tried that driver?

---

### Post by dswatuga on 2005-11-28
"I also show the 520 using the prism2 linux-wlan-ng driver which is in breezy. Have you tried that driver?"

I have not tried that driver (Partly because i didn't know it exsisted), but I would greatly appreciate it if you gave me some simple directions on how to try it. :)

---

### Post by Lambert on 2005-11-28
Make sure ndiswrapper is unloaded so there's no driver conflict. But I believe it's not with what you explained.

lsmod | grep ndis

No output is good.

Then see if wlan-ng loaded automatically, it usually does.

lsmod | grep wlan

If not you can load it by

modprobe wlan-ng

To see if the device is using a driver run these commands

sudo lshw -businfo

Look for the device in the list and notice it's class. then

sudo lshw -C <class>

where <class> = the class you saw in previous command.

Look for the configuration: line you should see something like this.

configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0

Of course driver will be different. The just try to configure connection.

---

### Post by dswatuga on 2005-11-28
"If not you can load it by

modprobe wlan-ng"

When trying to load it I keep getting the message "FATAL: Module wlan_ng not found". Is there anyway I can correct this?

---

### Post by Lambert on 2005-11-28
Try 

modprobe p80211

---

### Post by dswatuga on 2005-11-30
Thanks alot for your help to this point, but I am still having some dfficulties.

Upon entering "sudo lshw -C network" I get :

*-network
      description: Wireless Notebook Adapter MN-520
      vendor: Microsoft
      physical id: 0
      version: 1.0.3
      slot: Socket 0
*-network
      description: Fast Ethernet 10/100 PC Card
      product: 3.0
      vendor: Network Everywhere
      physical id: 0
      version: AX88190
      slot: Socket 1


How do I install both of these? or differentiate between the two in the code?

---

### Post by Lambert on 2005-11-30
Looks like the driver is not going to work for you and I vaguely remember somebody else saying the wlan-ng was not set properly in ubuntu for certain situations. I'm not sure or remember exactly though.

So try the ndiswrapper route. there's a link in my signature.

---

