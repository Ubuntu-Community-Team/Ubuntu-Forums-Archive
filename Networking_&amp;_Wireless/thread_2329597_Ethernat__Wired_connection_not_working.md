---
title: "Ethernat / Wired connection not working"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by dhuffer on 2016-07-03
Hello all it has been a long time since I have been here or done anything with Ubuntu / Linux so bare with me I recently installed Ubuntu 16.04 LTS On a HP Pavilion and can only achieve an Internet connection via wireless.....  I have searched and searched the net and none of the answers I have tried seem to work for me...  My network card is a:                                                                          

Qualcomm Atheros AR8161 PCI-E Gigabit Ethernet Controller

Oh and I am running a dual boot system along side windows 10 windows is able to use the wired connection with out any issues... And Ubuntu sees that it is connected however I can not get Internet.... Any help would be greatly appreciated.

Dan

---

### Post by jeremy31 on 2016-07-03
Post ```
lspci -nnk | grep -iA2 net; lshw -c net
```

welcome to the forums

---

### Post by dhuffer on 2016-07-04
> **jeremy31 said:**
> Post ```
lspci -nnk | grep -iA2 net; lshw -c net
```

welcome to the forums

Info


```
:~$ lspci -nnk | grep -iA2 net; lshw -c net
03:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:f051]
    Kernel driver in use: rt2800pci
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
    Subsystem: Hewlett-Packard Company AR8161 Gigabit Ethernet [103c:2ad5]
    Kernel driver in use: alx
    Kernel modules: alx
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 20:16:d8:04:98:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.4.0-28-generic firmware=0.34 ip=192.168.1.85 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7d00000-f7d0ffff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 08
       serial: 70:54:d2:1c:ce:2c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:32 memory:f7c00000-f7c3ffff ioport:d000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```



** And thank you for the welcome to forum!
Dan

---

### Post by jeremy31 on 2016-07-04
First, open Network Manager and set the MTU for the wired connection to 8192.  Reboot and see if it works correctly

I do have patched source code that will fix but it won't work if secure boot is enabled and I still have to figure out how to get dkms to work when using the 4.4 kernel since dkms can't see any difference between my module and the one in the kernel

---

### Post by dhuffer on 2016-07-04
> **jeremy31 said:**
> First, open Network Manager and set the MTU for the wired connection to 8192.  Reboot and see if it works correctlyI do have patched source code that will fix but it won't work if secure boot is enabled and I still have to figure out how to get dkms to work when using the 4.4 kernel since dkms can't see any difference between my module and the one in the kernelATM this seems to have fixed it Thanks!   I am dumb when it comes to some things Ubuntu... Can you or anyone explain why this fixed this issue??  Very interestingDan

---

### Post by jeremy31 on 2016-07-04
It is a bug in the module that was [fixed with this patch](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/ethernet/atheros/alx?id=c406700cdf882b89cb036117414fcd8b0cc2656d) but it was released after 4.4.  It could be added to the Ubuntu kernel but a bug report would have to be filed

---

### Post by dhuffer on 2016-07-04
Ok thank you!

---

### Post by jwaiwit on 2016-07-07
fantastic, really fixed my problem.

---

