---
title: "usb ethernet card connection"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by eders19 on 2009-07-12
hey guys, 

just installed ubuntu via wubi and i need help with my ethernet card (not wireless btw)

my internal lan card is broken so i got myself a cheap china knock-off usb card to get me by. i've installed the drivers via ndiswrapper and all, but i still can't seem to get a internet connection. i've searched the net and i can't seem to find the solution. maybe i'm using the wrong search queries, so there. or maybe i really can't use this lan card and will have to get the internal card repaired (warranty ran out so it'll probably cost me more than the usb card which i got for about US$5).

any help would be much appreciated! thanks!

---

### Post by schwascore on 2009-07-20
I'm assuming this is for a laptop, because it would be much easier to just get a new NIC ("network card") if you're on a desktop.

If you want support for your USB NIC, you'll need to post the model number and brand at the very least.  You should also post the output from lsusb (run from a terminal).

---

### Post by cariboo on 2009-07-20
I have a D-Link usb network device, it is detected and the driver loaded as soon as I plug it in. Could you open an Applications-->Accessories-->Terminal and type:

```
lsusb > lsusb.txt
```

This command will show if the device is detected when you plug it in. Next in the same terminal type:

```
sudo lshw -C network > network.txt
```

this command will print a listing on screen of your network devices. Both commands create a text file that you can copy to your windows partition so that you can paste the output in your next post.

---

### Post by eders19 on 2009-07-21
sorry for not posting additional details. the brand is cd-r king (a local brand in the philippines) but i'm sure it's just repackaged. probably came from china as that sort of thing is common here. 

lsusb

Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0fe6:8101  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lshw -C network

  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e4:c1:58
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:0b:06:d5:ad:a1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

