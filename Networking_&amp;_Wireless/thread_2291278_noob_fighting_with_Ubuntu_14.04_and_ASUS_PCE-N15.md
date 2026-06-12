---
title: "noob fighting with Ubuntu 14.04 and ASUS PCE-N15"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by thadeus1867 on 2015-08-19
Hello all,

I'm hoping you can forgive my total cluelessness and help me with my Ubuntu install.

Installed Ubuntu 14.04 on a desktop computer that's three or four years old. The computer is in a different room than my home office and connects to the internet via an ASUS PCE-N15 wireless adapter. 

When I was running Windows on the same box, the card worked just like it was supposed to. But after installing Ubuntu, it's gotten flaky. Sometimes it works for a relatively long time (over an hour) and other times, it only works for a few minutes. Whenever it stops, I need to restart the computer to get it working again. After a restart, I'm able to go online but only for a period of time. It quits again and I'm back to a restart.

I found the ASUS driver on ASUS' website but I'm so dumb with Linux/Ubuntu I don't know what do with it now that I've got it. I don't even know if installing a driver is the correct first step. I'm pretty much troubleshooting like I would a Windows machine and I don't know if that's wise or not.

Thanks in advance for your help.

---

### Post by coldraven on 2015-08-19
Check your router wi-fi settings. From a quick internet search you may need to use WPA-PSK or WPA2-PSK. I just checked my own router, WPA-PSK/WPA2-PSK is what the drop-down menu is set to.

---

### Post by Bucky Ball on 2015-08-19
Per coldraven's suggestion. After that change, throw us the output of this:

```
sudo lshw -C network
```

Please use code tags for the output (see last link in my signature for how). Cheers.

---

### Post by thadeus1867 on 2015-08-19
RE: WPA-PSK/WPA2-PSK

Thanks for your reply. That's currently what I'm using.

---

### Post by thadeus1867 on 2015-08-19
> **Bucky Ball said:**
> Per coldraven's suggestion. After that change, throw us the output of this:

```
sudo lshw -C network
```

Please use code tags for the output (see last link in my signature for how). Cheers.

```
 *-network               
       description: Wireless interface
       product: RTL8192CE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: f0:79:59:ea:5a:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.19.0-25-generic firmware=N/A ip=192.168.1.176 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:e000(size=256) memory:f7c00000-f7c03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:b2:df:38
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:24 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff



```

---

### Post by thadeus1867 on 2015-08-22
Ignore - May have figured it out.

---

### Post by Bucky Ball on 2015-08-22
Convention on the forums is to share with the community how you figured it out then mark the thread as solved (see the first link in my signature). Thanks.

---

### Post by thadeus1867 on 2015-08-22
> **Bucky Ball said:**
> Convention on the forums is to share with the community how you figured it out then mark the thread as solved (see the first link in my signature). Thanks.

Unfortunately, what I thought worked didn't so now I'm back to square one. I'm at a dead end and if you're able to help, I'd really appreciate it.

---

### Post by Bucky Ball on 2015-08-23
What did you do that worked, if only briefly?

---

