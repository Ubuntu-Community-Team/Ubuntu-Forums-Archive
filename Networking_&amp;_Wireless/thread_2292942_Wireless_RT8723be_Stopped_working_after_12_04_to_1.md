---
title: "Wireless RT8723be Stopped working after 12_04 to 14_04 upgrade"
date: 2015-09-01
forum: Networking &amp; Wireless
---

### Post by matthew109 on 2015-09-01
Hello there,

I recently upgraded from 12_04 LTS to 14_04 LTS trusty. Unfortunately in doing so a number of things stopped working including wireless. I think this is the drivers for my Realtek wireless RTL8723be.

```

matthew@matt-linux-hp-355-g2:~$ lspci | grep Network
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

```

When I am booting using the new 3.13.x kernel then the wireless does not work, but wired network continues work.

```

matthew@matt-linux-hp-355-g2:~$ lspci -nn

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader [10ec:5227] (rev 01)

matthew@matt-linux-hp-355-g2:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 5c:b9:01:af:cb:13
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:78 ioport:3000(size=256) memory:f1004000-f1004fff memory:f1000000-f1003fff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0400000-f0403fff

```

"Interestingly" (?) when I boot into the 3.11.x kernel then the wireless works

```


matthew@matt-linux-hp-355-g2:~$ sudo lshw -C network
[sudo] password for matthew: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 5c:b9:01:af:cb:13
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:77 ioport:3000(size=256) memory:f1004000-f1004fff memory:f1000000-f1003fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: c4:8e:8f:d0:4d:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.11.0-34-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:81 ioport:2000(size=256) memory:f0400000-f0403fff



```


In preparing to post to the forum and run the wireless-info script I ran

```

sudo apt-get update
sudo apt-get dist-upgrade

```

and on restart i now get a kernel panic error after a line entry referring to the RTL wireless card. Which feels like a step forwards as the driver may now being loaded, but a step back as I now cannot boot into Ubuntu, only the recovery mode for this kernel.

This thread: [http://ubuntuforums.org/showthread.php?t=2245876](http://ubuntuforums.org/showthread.php?t=2245876) looks like it contains some similar helpful for a different kernel. But I am now getting to the limit of any 'expertise' that I would not ever have claimed to have. And added to the inability to boot I am nervous of going further. Could you point me towards the right steps to take to move forwards, please.

Regards

Matthew

---

### Post by mörgæs on 2015-09-01
Hi, welcome to the fora.

When that happens the first question should be: How long time does a fresh install of 14.04 take and how long time are you prepared to put into troubleshooting?

---

### Post by matthew109 on 2015-09-02
Hi Morgaes, thanks for the reply. 

I wonder where to start.  To me, I appear to have a working kernal 3.11.x on a 14_04 version (with wireless working) ... or I can try to go back to the same kernel on 12_04. 

I'll try starting from that first position and upgrading again and see where I get, but I would expect I'd have the same issue. I'm not sure if i'd be happy to get a different result or not :).  I'll reply when I'm done.

Thank you.
Matthew

---

### Post by howefield on 2015-09-02
Is it [this]("http://www.ebuyer.com/705954-hp-355-quad-core-laptop-with-ubuntu-l8b55es") machine ?

---

### Post by matthew109 on 2015-09-02
that is the very machine ...which makes me nervous as to what you'll say next :)

thanks for the reply.

---

### Post by howefield on 2015-09-02
Just that the wireless card does not work out of the box with recent kernels. Now you know why it came with Ubuntu 12.04 and not the current 14.04.

You may get it to work, one "reviewer" on the site wrote..

> "iommu=soft" boot parameter needs to be added for wifi to work on later Ubuntu installs. I have confirmed this works with 15.04 install when iommu=soft is added to grub; and also works with 14.04 & 15.04 live DVD when added to the boot command on a live DVD (tap the keyboard when the DVD starts and pick your language; tap <F6> then <esc> then type " iommu=soft" (without quotes) and tap <enter>. You will still need to add this to grub after an install.)

There are also some threads in these forums regarding the RT8723BE that you might want to search out.

I had purchased the 455 model and experienced the same issue so I RMA'ed it for a refund on the basis that the advertised hardware specifications did not match the actual specifications. No quibble.

Other options include swapping out the wireless card for another (it is easily accessible, at least on the 455) or you purchase a wireless adapter, neither are terrifically enticing propositions though :)

---

### Post by matthew109 on 2015-09-04
I haven't (quite?!) fixed this yet. But neither have I given up.

Following Howefield's reply below (thanks) I tried without success adding the 

> 
iommu=soft


parameter to the boot parameters. I used this link: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) as a guide to adding the parameter temporarily. Even with this however, I still cannot boot successfully without error. (The older kernel continues to boot successfully).

As Howefield suggests it is unlikely I'll 'win' given the lack of support for the this wireless card with newer versions of Ubuntu, but just as I learning exercise I'm now just wandering my way through the suggestions for upgrade fixing from Morgaes at [http://ubuntuforums.org/showthread.php?t=1946145](http://ubuntuforums.org/showthread.php?t=1946145) 

After that it is a return to sender or new wireless card ...

---

