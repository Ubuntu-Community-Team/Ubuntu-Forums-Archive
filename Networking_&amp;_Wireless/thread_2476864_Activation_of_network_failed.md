---
title: "Activation of network failed"
date: 2022-07-09
forum: Networking &amp; Wireless
---

### Post by jgw on 2022-07-09
activation of network failed

I got this error when trying to connect to my wifi.  The signal strength of my wifi was excellent.  I have a dongle to access for my computer.  Normally I just hook an antenna and there is something in my computer that deals with getting the sign from the antenna.  This time whatever that was is no longer there I guess.(I have no idea)  Its been working well for years and , now, who knows.

Any help would be appreciated

Thank you.............

---

### Post by praseodym on 2022-07-11
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by jgw on 2022-07-11
Thanks for the reply!

I don't know where, or what, the wireless script from the sticky thread is.

I am using a Ralink Technology, Corp. MT7601U Wireless Adapter (attached with usb)

```
greg@movies:~$ sudo lshw -C network
[sudo] password for greg: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 40:8d:5c:4d:8d:8e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.13.0-52-generic duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:26 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlx1cbfce9cac48
       serial: 1c:bf:ce:9c:ac:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=5.13.0-52-generic firmware=N/A ip=192.168.0.21 link=yes multicast=yes wireless=IEEE 802.11
greg@movies:~$ 

Here is what the computer sees:
greg@movies:~$ lspci -nn | grep -i ethernet
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)

```

reg@movies:~$  inxi -Nxz
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Gigabyte driver: r8169 v: kernel port: e000 bus ID: 01:00.0 
  Device-2: Ralink MT7601U Wireless Adapter type: USB driver: mt7601u 
  bus ID: 1-4:13 
greg@movies:~$ 


I did the above just after I turned on my wifi.  Works fine here but not where it needs to be.  Using the same dongle it won't connect.  The problem is the source, I think.  Here its from tp-link and when its in place the source is from the router itself.  (tp-link is down here and the router is upstairs)  So, if I goto the router network, in settings/wifi, and see what's going on I am told that the signal strength is excellent but it just won't connect.  There is no error, no notice, nothing!  Its like the wifi adapter isn't even there. I suspect I need a special driver for my dongle and have no idea where to find one or how to install it.

---

### Post by #&amp;thj^% on 2022-07-11
> **jgw said:**
> Thanks for the reply!

I don't know where, or what, the wireless script from the sticky thread is.


You'll find it here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
with instructions

---

### Post by jgw on 2022-07-11
Thanks for the reply!

This whole thing is strange.  It used to be that the machine in question simply loaded up the internet without the wifi dongles.  Then that stopped and now I am trying to figure what's going on.  My problem is getting the right dongle.  I have ordered a couple and they should get here next week.  I have no idea if they are going to work but ......

I will do all that stuff tomorrow as I have to move the system so I can plug it in to the internet.  Then I can do it!

---

### Post by praseodym on 2022-07-12
Check the outputs of
```

lsmod
rfkill list
iwconfig
dmesg | grep mt7
```

---

