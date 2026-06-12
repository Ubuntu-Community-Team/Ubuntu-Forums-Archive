---
title: "Cant connect"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by Big4wheeler on 2008-07-21
Hello guys! I recently finally installed Ubuntu along side Vista, so im dual booting. I would love to make a full transition over to Ubuntu, but my wireless card is not working, I tryed following MANY tutorials. (I dont even see the network to connect to, I also made it un-encrypted, and it still did not work) All though none worked, on my restricted drivers, I see the HAL thing, and the Atheros 802.11b/g driver. I can get you any specs you want, just ask!

Thanks for any help

---

### Post by Nokkis on 2008-07-21
What model is the card?

---

### Post by Big4wheeler on 2008-07-21
I opened my case, and its very hard to see, and it doesnt want to come out, from device manager I came up with this:

Atheros Communications Inc.

HP 802.11b/g Wireless Network Adapter.

It is in a PCI slot.

---

### Post by superprash2003 on 2008-07-22
in your terminal type lshw -C network and post output , that would give a clear info on the model no

---

### Post by Big4wheeler on 2008-07-22
Heres what I got:

> chris@chris-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:e0:f5:2f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=96 maxlatency=28 mingnt=10



---

### Post by Big4wheeler on 2008-07-23
Bump

---

### Post by Big4wheeler on 2008-07-28
Bump again, its been 5 days.

---

