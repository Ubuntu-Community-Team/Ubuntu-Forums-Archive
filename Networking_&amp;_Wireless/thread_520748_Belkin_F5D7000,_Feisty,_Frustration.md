---
title: "Belkin F5D7000, Feisty, Frustration"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by acavella on 2007-08-08
I'll just preface this with, I am an inexperienced user.  I feel myself quite computer literate and have a basic knowledge of Linux and it's operation.  Recently I installed Feisty on my computer and attempted to install ndiswrapper and the drivers for my Linksys card, w/ no success.  So, rather than continue that route, I decided to consult the Wiki and purchase a new wireless net card that was listed as "out of the box" compatible.  

I have arrived at this point w/ a Belkin F5D7000 wireless network card, which does not work out of the box.  When I looked in System > Admin > Network all I see is my two wired network cards.  So, I originally thought I had messed something up previously attempting to configure the Linksys card.  I deleted the partitions and reinstalled Ubuntu Feisty.  Upon logging in, again no wireless lan card visible.  

I have since then followed multiple guides to install (using ndiswrapper) the win drivers for this device.  According to ndiswrapper -l, the drivers and device are both installed/present.  However, still no wireless lan device is present.  Please, I hope someone has some quick fix that I have looked over w/ my limited knowledge.

---

### Post by spd106 on 2007-08-08
Unfortunately there are multiple different versions of this card with different levels of support and different drivers. So we need to know which specific model and chipset you have. When you were looking at the [list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") it asked you to run the lspci -v | less command to see which chipset your card has, could you please post that information here? Just the first line of the network controller will do.

It would also be useful if you could provide the relevant output of this command too.
```
sudo lshw -class network
```

If you have a Broadcom card then try this [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") page or if it's a Ralink go [here]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")

---

### Post by acavella on 2007-08-09
RE: Requested output.

lspci -v | less :
01:07.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

sudo lshw -class network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 7
       bus info: pci@01:07.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:ac00-acff iomemory:fdeff000-fdeff1ff irq:3

---

### Post by spd106 on 2007-08-09
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=507791](http://ubuntuforums.org/showthread.php?t=507791)

It looks like you have the same card.

---

### Post by acavella on 2007-08-09
I had not previously seen that thread.  However, I followed the various ndiswrapper install steps their using the net8185 driver.  Still no success!  With ndiswrapper -l, it shows the driver installed and associated to the belkin card (device present).  However when I go to the network admin window it shows no wlan device, only eth0 eth1.  I must say this is becoming a bit frustrating.  

Any further thoughts on how to get this to fixed?

---

