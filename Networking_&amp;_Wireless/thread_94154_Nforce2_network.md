---
title: "Nforce2 network"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by marrek13 on 2005-11-23
Hi all, i have big problem with nforce2 network drivers.
I installed drivers from nvidia.com site.
After that I use "modprobe nvnet" to load network driver. 
I want to configure it, but it not present in network-admin.
I looked at the log of installer, but I don't see any problems, and if I list loaded modules, nvnet is loaded...
My motherboard is Abit NF7-S2.
Help me, please;)

P.S - my english is not excellent:)

---

### Post by Lambert on 2005-11-23
If module is loaded but not showing in network-admin (or with the command iwconfig) then there is a problem at the driver level. Usually it means that it's an incorrect driver.

You need to verify you're using the correct driver for the device.

What's the make and model number of your device. Is it internal/card/usb?

---

### Post by marrek13 on 2005-11-23
It's internal device, LAN.
I used correct driver from official site.

---

### Post by h3avyarms on 2005-11-23
my nforce2 network cark is always detected and installed automaticly on my desktop. I can boot up DSL, Ubuntu, or Gentoo and have a net connection automaticly.

---

### Post by Lambert on 2005-11-23
Run the command

sudo lshw -businfo

Look for the device in this simple list. Notice it's class. Then

sudo lshw -C <class>

where class = the devices class from the first command.

Post that output here.

---

### Post by marrek13 on 2005-11-24
```
  *-network:0
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@02:08.0
       logical name: wlan0
       version: 20
       serial: 00:30:4f:38:ae:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=192.168.1.10 link=yes multicast=yes wireless=IEEE 802.11b
       resources: ioport:b000-b0ff iomemory:e8011000-e80110ff irq:16
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Sundance Technology Inc
       vendor: Sundance Technology Inc
       physical id: b
       bus info: pci@02:0b.0
       version: 31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:b400-b47f iomemory:e8010000-e80101ff irq:5

```

First device is my wireless pci card.

---

### Post by Lambert on 2005-11-24
If the first device is your wireless then it's not using the nvet driver it's using ndiswrapper

configuration: broadcast=yes [B]driver=ndiswrapper

[/B]maybe there's a driver conflict with whatever ndiswrapper has loaded and the driver you're using.

run ndiswrapper -l to see what driver is loaded and then remove it. Restart network with sudo /etc/init.d/network restart (I believe that's correct)

Check lshc -C <> again to see if nvnet is allocated to the device and then try network-admin again to see if it's there.

---

### Post by marrek13 on 2005-11-24
I check this, but without any changes...
I tryied to unload ndiswrapper, than load nvnet.
Then I load ndiswrapper, but now this not working, so I unload it and nvnet, and load ndiswrapper and it working...
I don't have any ideas to make them working:confused:

---

