---
title: "Help!  Wireless networking!  88w8335 [Libertas]"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by albs on 2007-03-02
Hi everyone,

I've been trying for about 4 hours on this... but no luck.  Basically, I've decided to migrate my computer to Edubuntu from Windows.

I have a new wireless card, a Netcomm NP542.  It works with windows.

I can see an entry for it in Edubuntu's device manager, but can't select it in my networking manger.  There simply is no entry for wireless, just my on-board ethernet card.  I can't Add a new device either, despite the help reference saying I could.

Below is the output of a "lshw -C network" command - any solutions anyone?


  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@00:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       resources: iomemory:f0800000-f080ffff iomemory:f0000000-f000ffff irq:209

---

### Post by chili555 on 2007-03-02
Welcome to the wonderful world of ndiswrapper! Have a look here: [https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Post back if you get stuck.

---

