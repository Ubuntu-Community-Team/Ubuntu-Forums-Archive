---
title: "Ethernet disconnected Ubuntu"
date: 2015-12-10
forum: Networking &amp; Wireless
---

### Post by joanalpinto on 2015-12-10
The ethernet network does not work.

I already try this:

lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)

modinfo e1000e | grep 15B8
alias:          pci:v00008086d000015B8sv*sd*bc*sc*i*

dmesg | grep e100
[ 1168.361605] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[ 1168.361608] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.

What should I do?

Thanks,
Joana

---

### Post by ian-weisser on 2015-12-10
What have you tried?
Have you ruled out the network? The cable?

---

### Post by joanalpinto on 2015-12-10
> **ian-weisser said:**
> What have you tried?
Have you ruled out the network? The cable?

Yes, I tried... Let me know what you want to know. I tried the commands I mentioned in the first post, because I found a similiar post on the forum.

[http://ubuntuforums.org/showthread.php?t=2305909](http://ubuntuforums.org/showthread.php?t=2305909)

---

### Post by joanalpinto on 2015-12-14
I really need to work with ethernet, can anyone help me please?

---

### Post by Skaperen on 2015-12-14
define "does not work".   does the light not come on?  does it not show up as *eth0*?  does *ifconfig* show it as down?  what are *you expecting* to happen that does not happen?

---

### Post by joanalpinto on 2015-12-14
> **Skaperen said:**
> define "does not work".   does the light not come on?  does it not show up as *eth0*?  does *ifconfig* show it as down?  what are *you expecting* to happen that does not happen?

Ethernet is not even detected.

ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:546156 (546.1 KB)  TX bytes:546156 (546.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2f:5e:83  
          inet addr:194.210.220.208  Bcast:194.210.223.255  Mask:255.255.252.0
          inet6 addr: 2001:690:2100:1016:226:5eff:fe2f:5e83/64 Scope:Global
          inet6 addr: fe80::226:5eff:fe2f:5e83/64 Scope:Link
          inet6 addr: 2001:690:2100:1016:2da8:a471:d3ff:b7ac/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177293 errors:0 dropped:1 overruns:0 frame:1180362
          TX packets:115236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56624508 (56.6 MB)  TX bytes:23306530 (23.3 MB)
          Interrupt:16

---

### Post by joanalpinto on 2015-12-14
When I connect the cable the light turns on, but it does not show up as eth0. As you can see in ifconfig eth0 does not appear.

---

### Post by coffeecat on 2015-12-14
@joanalpinto, the ethernet device you mention in this bit of your post:

> **joanalpinto said:**
> 

lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)

... is a Realtek, not Intel and doesn't use the e1000e driver. See this from my system - the same Realtek ethernet device:

```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 0c
       serial: 00:8c:fa:74:66:68
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:26 ioport:2000(size=256) memory:c8600000-c8600fff memory:c8400000-c8403fff

```

I've highlighted the in-use driver in bold.

Which means that the thread you link in post #3 may not be relevant. 

That being said, your dmesg output does mention the e1000e driver, which is for Intel devices, so I wonder if you have more than one ethernet device attached to your system. Please post the unedited output of:

```
lspci
```

And the unedited output of:

```
sudo lshw -C network
```

Also, which version of Ubuntu are you using? The latest, 15.10, doesn't use the "eth0" terminology, although your output of ifconfig does suggest you are using a pre-15.10 release. Nevertheless, it would be useful to clarify this point.

---

### Post by joanalpinto on 2015-12-14
@coffeecat I am using Ubuntu 14.04.3 LTS

```


[COLOR=#000000][FONT=Ubuntu Mono]lspci

[/FONT][/COLOR]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

```

sudo lshw -C network

*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:5e:2f:5e:83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=194.210.220.208 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:d9000000-d9003fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:31 ioport:5000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d8000000-d800ffff


```


> **coffeecat said:**
> @joanalpinto, the ethernet device you mention in this bit of your post:



... is a Realtek, not Intel and doesn't use the e1000e driver. See this from my system - the same Realtek ethernet device:

```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 0c
       serial: 00:8c:fa:74:66:68
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:26 ioport:2000(size=256) memory:c8600000-c8600fff memory:c8400000-c8403fff

```

I've highlighted the in-use driver in bold.

Which means that the thread you link in post #3 may not be relevant. 

That being said, your dmesg output does mention the e1000e driver, which is for Intel devices, so I wonder if you have more than one ethernet device attached to your system. Please post the unedited output of:

```
lspci
```

And the unedited output of:

```
sudo lshw -C network
```

Also, which version of Ubuntu are you using? The latest, 15.10, doesn't use the "eth0" terminology, although your output of ifconfig does suggest you are using a pre-15.10 release. Nevertheless, it would be useful to clarify this point.

---

### Post by joanalpinto on 2015-12-15
Anyone? I really need to solve the problem because wifi is not so good at my work.

Thanks

---

### Post by coffeecat on 2015-12-15
There is this in your lshw output:

> **joanalpinto said:**
> 
```

  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.


```

Your ethernet interface is disabled, which would explain why you can't get it to work. What is not obvious is why.

Click on the network manager icon and make sure "Enable Networking" is ticked. Try this in a terminal:

```
sudo ifconfig eth0 up
```

I'm assuming your ethernet device is eth0.

Apart from that, is there anything you have done with the system which might explain why the ethernet card is disabled? I have never had any problems with that Realtek ethernet device, which is in several of the systems that I have used.

---

### Post by joanalpinto on 2015-12-15
I installed a clean version of Ubuntu this week and ethernet never worked.
Enable networking is enabled

 This is what I got:

```

sudo ifconfig eth0 up
SIOCSIFFLAGS: Cannot assign requested address

```

> **coffeecat said:**
> There is this in your lshw output:



Your ethernet interface is disabled, which would explain why you can't get it to work. What is not obvious is why.

Click on the network manager icon and make sure "Enable Networking" is ticked. Try this in a terminal:

```
sudo ifconfig eth0 up
```

I'm assuming your ethernet device is eth0.

Apart from that, is there anything you have done with the system which might explain why the ethernet card is disabled? I have never had any problems with that Realtek ethernet device, which is in several of the systems that I have used.

---

