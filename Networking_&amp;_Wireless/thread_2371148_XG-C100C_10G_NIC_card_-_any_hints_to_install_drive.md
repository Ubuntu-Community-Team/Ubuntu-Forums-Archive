---
title: "XG-C100C 10G NIC card - any hints to install driver?"
date: 2017-09-11
forum: Networking &amp; Wireless
---

### Post by madumi on 2017-09-11
I'm new to linux, so I'm struggling even more installing the driver for the XG-C100C from the Terminal (ubuntu 16.04 server edition - Webmin is my only GUI).

As far as I know, Ubuntu 16.04 server installation failed to install the driver for the XG-C100C. It did however install the driver for the onboard 1G NIC, so I'm able to access through Webmin.

If it's useful, output for lshw -class network is as follows:
[HTML]  *-network UNCLAIMED
       description: Ethernet controller
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm msix msi vpd bus_master cap_list
       configuration: latency=0
       resources: memory:df440000-df44ffff memory:df450000-df450fff memory:df000000-df3fffff memory:df400000-df43ffff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 50:9a:4c:59:ed:1f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.11.131 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:126 memory:df700000-df71ffff[/HTML]

Attempting the install the current XG-C100C driver (Atlantic1.5.348.0.tar.bz2) through Webmin (Webmin-->System-->software packages-->install from uploaded file, informs me that the file is not a valid Debian DPKG.

Attempting to install from Terminal & a Makefile like so:
```
(unpack directory)
./configure
make
sudo make install
```
fails at the ./configure command

I gather that the driver would be easier to install if I could use the APT-repository, but I couldn't locate a package there...

Any hints?
thanks!

---

### Post by praseodym on 2017-09-11
Please show
```

lspci -nnk
```

---

### Post by madumi on 2017-09-11
> **praseodym said:**
> Please show
```

lspci -nnk
```

here it is:

```
00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers [8086:1918] (rev 07)
    Subsystem: Dell Skylake Host Bridge/DRAM Registers [1028:07c5]
    Kernel driver in use: ie31200_edac
    Kernel modules: ie31200_edac
00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:191d] (rev 06)
    DeviceName: Intel HD Graphics
    Subsystem: Dell Device [1028:07c5]
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller [8086:a12f] (rev 31)
    Subsystem: Dell Sunrise Point-H USB 3.0 xHCI Controller [1028:07c5]
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-H Thermal subsystem [8086:a131] (rev 31)
    Subsystem: Dell Sunrise Point-H Thermal subsystem [1028:07c5]
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    Subsystem: Dell Sunrise Point-H CSME HECI [1028:07c5]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:16.3 Serial controller [0700]: Intel Corporation Sunrise Point-H KT Redirection [8086:a13d] (rev 31)
    Subsystem: Dell Sunrise Point-H KT Redirection [1028:07c5]
    Kernel driver in use: serial
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] [8086:a102] (rev 31)
    Subsystem: Dell Sunrise Point-H SATA controller [AHCI mode] [1028:07c5]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #1 [8086:a110] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #5 [8086:a114] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #9 [8086:a118] (rev f1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a149] (rev 31)
    Subsystem: Dell Sunrise Point-H LPC Controller [1028:07c5]
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    DeviceName: Onboard SATA #1
    Subsystem: Dell Sunrise Point-H PMC [1028:07c5]
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
    Subsystem: Dell Sunrise Point-H SMBus [1028:07c5]
    Kernel modules: i2c_i801
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-LM [8086:15b7] (rev 31)
    Subsystem: Dell Ethernet Connection (2) I219-LM [1028:06b7]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
01:00.0 Ethernet controller [0200]: Device [1d6a:d107] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8741]
02:00.0 PCI bridge [0604]: Texas Instruments XIO2001 PCI Express-to-PCI Bridge [104c:8240]
    Kernel modules: shpchp
04:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
    Subsystem: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:1060]
    Kernel driver in use: ahci
    Kernel modules: ahci
05:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
    Subsystem: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:1060]
    Kernel driver in use: ahci
    Kernel modules: ahci
```

---

### Post by chili555 on 2017-09-11
> Attempting the install the current XG-C100C driver (Atlantic1.5.348.0.tar.bz2) Where did you find this? May we see a link? Maybe we can help compile it.

---------

Note to chili: aquantia.ko ??

---

### Post by madumi on 2017-09-11
> **chili555 said:**
> Where did you find this? May we see a link? Maybe we can help compile it.

---------

Note to chili: aquantia.ko ??

Thanks chili... The driver was included on a CD, but it's the same version as on Asus's website:
[https://www.asus.com/us/Networking/XG-C100C/HelpDesk_Download/](https://www.asus.com/us/Networking/XG-C100C/HelpDesk_Download/)

---

### Post by chili555 on 2017-09-11
> **madumi said:**
> Thanks chili... The driver was included on a CD, but it's the same version as on Asus's website:
[https://www.asus.com/us/Networking/XG-C100C/HelpDesk_Download/](https://www.asus.com/us/Networking/XG-C100C/HelpDesk_Download/)Hmmmm. Is it necessary to register? I selected OS - Linux and then ... nothing.

---

### Post by madumi on 2017-09-11
> **chili555 said:**
> Hmmmm. Is it necessary to register? I selected OS - Linux and then ... nothing.

you shouldn't have to register. I'm accessing with win10, so I'm not sure what mechanism triggers the download...
The zip file I downloaded is here:
<snip>

---

### Post by QIII on 2017-09-11
Hello.

Please do not use shortened URLs, particularly ones that immediately initiate unknown downloads.

Thanks.

---

### Post by chili555 on 2017-09-11
I was able to download the file by ... don't even ask!

The correct procedure is:```
cd  ~/Desktop/Forum/DR_XG_C100C_5005_Linux/Atlantic
```...or wherever you downloaded the file and extracted it, if not Desktop > Forum.```
make
sudo make install
sudo modprobe atlantic
```This is your device:> Ethernet controller [0200]: Device [[COLOR="#FF0000"]1d6a:d107[/COLOR]] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8741]Checking modinfo shows:```
filename:       /home/chili/Desktop/Forum/DR_XG_C100C_5005_Linux/Atlantic/atlantic.ko
description:    aQuantia Corporation(R) Network Driver
author:         aQuantia
version:        1.5.348.0
license:        GPL v2
srcversion:     2823960AD5D456D76885444
alias:          pci:v00001D6Ad0000D109sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad0000D108sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="#FF0000"]1D6A[/COLOR]d0000[COLOR="#FF0000"]D107[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad0000D100sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad00000001sv*sd*bc*sc*i*
depends:        
vermagic:       4.10.0-33-generic SMP mod_unload 

```Let us know how it goes; we will have another step.

---

### Post by madumi on 2017-09-11
Thanks so much Chili555

I installed make with apt-get build-essential, the make command went well, but sudo make install failed--I'll paste the terminal session below:

```

[me@nas Atlantic]# make
make -j4 CC=gcc -C /lib/modules/4.4.0-93-generic/build M=/home/me/Atlantic modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-93-generic'
  CC [M]  /home/me/Atlantic/aq_main.o
  CC [M]  /home/me/Atlantic/aq_nic.o
  CC [M]  /home/me/Atlantic/aq_pci_func.o
  CC [M]  /home/me/Atlantic/aq_vec.o
  CC [M]  /home/me/Atlantic/aq_ring.o
  CC [M]  /home/me/Atlantic/aq_hw_utils.o
  CC [M]  /home/me/Atlantic/aq_ethtool.o
  CC [M]  /home/me/Atlantic/hw_atl/hw_atl_a0.o
  CC [M]  /home/me/Atlantic/hw_atl/hw_atl_b0.o
  CC [M]  /home/me/Atlantic/hw_atl/hw_atl_utils.o
  CC [M]  /home/me/Atlantic/hw_atl/hw_atl_llh.o
  LD [M]  /home/me/Atlantic/atlantic.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/me/Atlantic/atlantic.mod.o
  LD [M]  /home/me/Atlantic/atlantic.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-93-generic'
[me@nas Atlantic]# sudo make install
make: *** No rule to make target 'install'.  Stop.

```

Sorry I'm so ignorant, but any hints where I'm going wrong?

---

### Post by chili555 on 2017-09-12
What's going wrong is not you; it is the author of the driver, who, in the Makefile, gives no way to permanently install the driver. And me; because I don't have the hardware and don't need to install it, I never, as I should, tested 'sudo make install'.

Try this instead:```
cd ~/Atlantic
sudo insmod atlantic.ko
```Does your ethernet device spring to life? If so, we'll automate the 'insmod' and if not, we'll troubleshoot:```
dmesg | grep -i atl
```

---

### Post by madumi on 2017-09-12
Thanks again chili555

There's a bit of progress, not quite sure how much though. output of dmesg | grep -i atl

```
[41620.461798] atlantic: module verification failed: signature and/or required key missing - tainting kernel
```

and output of lshw -class network   seems to show the card with more info now available (logical name, serial, etc), but it also shows the wrong capacity info (it's a 10G card).

```
*-network DISABLED
       description: Ethernet interface
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 02
       serial: 10:7b:44:e8:d9:85
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm msix msi vpd bus_master cap_list rom ethernet physical 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=aquantia driverversion=1.5.348.0 duplex=full firmware=1.5.44 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:df440000-df44ffff memory:df450000-df450fff memory:df000000-df3fffff memory:df400000-df43ffff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 50:9a:4c:59:ed:1f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.11.131 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:126 memory:df700000-df71ffff
```

Is there anything else worth trying?

---

### Post by chili555 on 2017-09-12
I am interested in the notation DISABLED. Disabled by what, we wonder. I am also interested that the driver now calls itself aquantia. Let's check the log for more clues:```
grep -e aquantia -e enp1s0 /var/log/syslog
```Was the ethernet cable attached to the XG-C100C at the time? Let's be sure to conduct all future tests with it connected to your 10 Gbps capable router or switch.

By the way, the release notes for the driver reports that the aq_cfg.h file is a configuration file. Currently, all the parameters, I assume, are commented out. Here it is:

```
/*
 * aQuantia Corporation Network Driver
 * Copyright (C) 2014-2017 aQuantia Corporation. All rights reserved
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms and conditions of the GNU General Public License,
 * version 2, as published by the Free Software Foundation.
 */

/* File aq_cfg.h: Definition of configuration parameters and constants. */

#ifndef AQ_CFG_H
#define AQ_CFG_H

#define AQ_CFG_VECS_DEF   4U
#define AQ_CFG_TCS_DEF    1U

#define AQ_CFG_TXDS_DEF    4096U
#define AQ_CFG_RXDS_DEF    1024U

#define AQ_CFG_IS_POLLING_DEF 0U

#define AQ_CFG_FORCE_LEGACY_INT 0U

#define AQ_CFG_IS_INTERRUPT_MODERATION_DEF   1U
#define AQ_CFG_INTERRUPT_MODERATION_RATE_DEF 0xFFFFU
#define AQ_CFG_IRQ_MASK                      0x1FFU

#define AQ_CFG_VECS_MAX   8U
#define AQ_CFG_TCS_MAX    8U

#define AQ_CFG_TX_FRAME_MAX  (16U * 1024U)
#define AQ_CFG_RX_FRAME_MAX  (5U * 1024U)

/* LRO */
#define AQ_CFG_IS_LRO_DEF           1U

/* RSS */
#define AQ_CFG_RSS_INDIRECTION_TABLE_MAX  128U
#define AQ_CFG_RSS_HASHKEY_SIZE           320U

#define AQ_CFG_IS_RSS_DEF           1U
#define AQ_CFG_NUM_RSS_QUEUES_DEF   AQ_CFG_VECS_DEF
#define AQ_CFG_RSS_BASE_CPU_NUM_DEF 0U

#define AQ_CFG_PCI_FUNC_MSIX_IRQS   9U
#define AQ_CFG_PCI_FUNC_PORTS       2U

#define AQ_CFG_SERVICE_TIMER_INTERVAL    (2 * HZ)
#define AQ_CFG_POLLING_TIMER_INTERVAL   ((unsigned int)(2 * HZ))

#define AQ_CFG_SKB_FRAGS_MAX   32U

#define AQ_CFG_NAPI_WEIGHT     64U

#define AQ_CFG_MULTICAST_ADDRESS_MAX     32U

/*#define AQ_CFG_MAC_ADDR_PERMANENT {0x30, 0x0E, 0xE3, 0x12, 0x34, 0x56}*/

#define AQ_CFG_FC_MODE 3U

#define AQ_CFG_SPEED_MSK  0xFFFFU	/* 0xFFFFU==auto_neg */

#define AQ_CFG_IS_AUTONEG_DEF       1U
#define AQ_CFG_MTU_DEF              1514U

#define AQ_CFG_LOCK_TRYS   100U

#define AQ_CFG_DRV_AUTHOR      "aQuantia"
#define AQ_CFG_DRV_DESC        "aQuantia Corporation(R) Network Driver"
#define AQ_CFG_DRV_NAME        "aquantia"
#define AQ_CFG_DRV_VERSION	__stringify(NIC_MAJOR_DRIVER_VERSION)"."\
				__stringify(NIC_MINOR_DRIVER_VERSION)"."\
				__stringify(NIC_BUILD_DRIVER_VERSION)"."\
				__stringify(NIC_REVISION_DRIVER_VERSION)

#endif /* AQ_CFG_H */
```I am not at all familiar with the driver and its use, but if you see anything useful here, we can try to un-comment the parameter and re-compile.

---

### Post by madumi on 2017-09-12
Thanks again...

Hmm, yes, I can't exactly plug the card in normally as I don't have a 10G switch/router. I'm planning to connect it directly with my other XG-C100C in my win10 computer. The closest I could try was to plug the XG-C100C card into my current home network, but it did not seem to want to auto negotiate IP addresses (I logged into the router interface & deleted the DHCP lease, then also executed sudo dhclient -r enp1s0 ). I figured that was a sign enough that the card wasn't working...

output for grep -e aquantia -e enp1s0 /var/log/syslog
```
Sep 12 09:49:07 nas kernel: [41620.480386] aquantia 0000:01:00.0 enp1s0: renamed from eth0
```

I looked over the config file & couldn't see anything that stood out as out of place...

The odd thing is that when I plug the 10G card into my home network, the lights on the NIC won't turn on, but when I plug it directly into my other 10G card (no static IP set on this other card yet), the lights turn green. lshw -class network  still shows it as DISABLED, but if I check win10-->ipconfig, my win10 machine seems to have auto assigned 169.254.246.10 to itself.

I couldn't figure out a way to ping this address from the ubuntu server as I think the win10 firewall rules might drop pings.

output however of ifconfig only shows entries from enp0s31f6 and lo (not enp1s0).

Any clues?

---

### Post by chili555 on 2017-09-12
> my win10 machine seems to have auto assigned 169.254.246.10 to itself.Ahhh! The old 169.254.x.y address! [https://www.techrepublic.com/forums/discussions/where-did-ip-16925451183-come-from/](https://www.techrepublic.com/forums/discussions/where-did-ip-16925451183-come-from/)    > The 169.254.x.x range of IP addresses is reserved by Microsoft for private network addressing. If you have a pc set to automatically obtain an IP and you recieve one of these addresses, windows has assigned this because it cannot find a DHCP server within the network subnet.> The odd thing is that when I plug the 10G card into my home network, the lights on the NIC won't turn on,Is there any change if you plug in to your home router and then do:```
sudo ifconfig enp1s0 up
```Are there any clues at the terminal when you do? In the log?```
dmesg | grep enp1s0
```

I'm running low on talent. I figured out the driver but I know anything about your device or 10 Gbps service.

---

### Post by madumi on 2017-09-12
yup, I'm feeling at an end of ideas... but then I was there before I posted the question :)

```
sudo ifconfig enp1s0 up
```
brings the interface up with an inet6 address. This disappears if the cable is unplugged. I don't know if that's just a reflection of the mac address. But there's no ipv4 address. Here's how it reads:
```
enp1s0    Link encap:Ethernet  HWaddr 10:7b:44:e8:d9:85  
          inet6 addr: fe80::127b:44ff:fee8:d985/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:8 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:508 (508.0 B)
```

```
dmesg | grep enp1s0
```
reads:
```
[41620.480386] aquantia 000:01:00.0 enp1s0: renamed from eth0
[83537.935168] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[83543.945619] IPV6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
```

Thanks so much for your help so far. Let me know when it's the end of the road :)

---

### Post by chili555 on 2017-09-13
> brings the interface up with an inet6 address.However...> inet6 addr: fe80::127b:44ff:fee8:d985/64 fe80:: is a link-local address. Just like 169.254.x.y, it means that a valid IPv6 address was sought but not given. 

The one last thing I can think of it to hook the two 10 Gbps devices together and then Edit Connections in Network Manager and, under IPv4 settings, select 'Share to other computers.' Perhaps the two will begin to work as expected.

You could also try setting static IP addresses, in the same place, such as 10.0.0.10 for one of them and 10.0.0.20 for the other. If that sticks, see if you can ping them.

I am now officially out of knowledge and even guesses!

---

### Post by madumi on 2017-09-13
Thanks so much again for your input! So far no success, I'll post back when I find an answer :)

---

### Post by madumi on 2017-09-13
Hmmm, so, after checking around, I found this comment on anandtech by someone under their review of the XG-C100C
[HTML]For anyone curious, the Linux drivers were upstreamed in 4.11.
Unfortunately this means that it won't work out of the box on most  current non-rolling distributions.
Ubuntu 17.04 and Fedora 25 are both  on 4.10, latest Debian stable is 4.9.[/HTML]
So... I installed Kernel 4.12 using this tutorial ([http://ubuntuhandbook.org/index.php/2017/07/install-linux-kernel-4-12-in-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2017/07/install-linux-kernel-4-12-in-ubuntu-linux-mint/))

Everything seemed to install fine... output of uname -r
[HTML]4.12.0-041200-generic[/HTML]

Then i updated packages within Webmin & tried to execute make again from within the Atlantic directory

Sadly that failed as follows:
[HTML]make -j4 CC=gcc -C /lib/modules/4.12.0-041200-generic/build M=/home/me/Atlantic modules
make[1]: Entering directory '/usr/src/linux-headers-4.12.0-041200-generic'
  CC [M]  /home/me/Atlantic/aq_pci_func.o
  CC [M]  /home/me/Atlantic/aq_ring.o
  CC [M]  /home/me/Atlantic/aq_ethtool.o
  CC [M]  /home/me/Atlantic/aq_hw_utils.o
/home/me/Atlantic/aq_pci_func.c: In function 'aq_pci_func_init':
/home/me/Atlantic/aq_pci_func.c:157:8: error: implicit declaration of function 'pci_enable_msix' [-Werror=implicit-function-declaration]
  err = pci_enable_msix(self->pdev, self->msix_entry,
        ^
  CC [M]  /home/me/Atlantic/hw_atl/hw_atl_a0.o
  CC [M]  /home/me/Atlantic/hw_atl/hw_atl_b0.o
cc1: some warnings being treated as errors
scripts/Makefile.build:302: recipe for target '/home/me/Atlantic/aq_pci_func.o' failed
make[2]: *** [/home/me/Atlantic/aq_pci_func.o] Error 1
make[2]: *** Waiting for unfinished jobs....
Makefile:1512: recipe for target '_module_/home/me/Atlantic' failed
make[1]: *** [_module_/home/me/Atlantic] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.12.0-041200-generic'
Makefile:60: recipe for target 'all' failed
make: *** [all] Error 2[/HTML]

Any ideas whether upgrading to a Kernel >= 4.11 could help? Or why make would fail now that I have Kernel 4.12?

---

### Post by madumi on 2017-09-13
Hmmm, so I found this
[https://www.spinics.net/lists/netdev/msg421033.html](https://www.spinics.net/lists/netdev/msg421033.html)
which requested:
[HTML]pci_enable_msix has been long deprecated, but this driver adds a new
instance.  Convert it to pci_alloc_irq_vectors so that no new instance
of the deprecated function reaches mainline.[/HTML]

If I'm reading that right, the vendor didn't convert it, but allowed pci_enable_msix to go into the current Atlantic1.5.348.0 driver... So I guess an official fix is needed... at least before it's 4.12 compliant (Asus website says compliant only up to kernel 4.4)

---

### Post by chili555 on 2017-09-13
> For anyone curious, the Linux drivers were upstreamed in 4.11.I interpret this to mean that the needed driver is already installed in 4.11 et seq.

What do these tell us while booted into kernel version 4.12.0-xx?```
modinfo aquantia | grep D107
modinfo atlantic | grep D107
```Before we hack the driver, let's see if we really need to first.

---

### Post by madumi on 2017-09-13
Thanks! In the meanwhile, I did a clean install of Ubuntu server 16.04. Should I maybe try installing Kernel 4.11 & go from there?

---

### Post by chili555 on 2017-09-13
> Should I maybe try installing Kernel 4.11 & go from there?Yes, please. But why not 4.12?

Why did you feel that you needed to reinstall?

---

### Post by madumi on 2017-09-13
I did a clean install because I wasn't convinced I needed Kernel 4.12 (the Asus driver as stated on the site is said to be compatible with 3.2, 3.6, 4.2, 4.4) and I didn't know how to roll back to 4.4
Anyways, I re-installed Kernel 4.12...

> **chili555 said:**
> What do these tell us while booted into kernel version 4.12.0-xx?```
modinfo aquantia | grep D107
modinfo atlantic | grep D107
```

```
modinfo aquantia | grep D107
```
gives nothing

```
modinfo atlantic | grep D107
```
after a reboot, it gave "alias:          pci:v00001D6Ad0000D107sv*sd*bc*sc*i*"

------------------------------------------------------------------------------------

additionally, after executing ```
sudo ifconfig enp1s0 up
```
```
lshw -class network
```
gives
[HTML]  *-network
       description: Ethernet interface
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 02
       serial: 10:7b:44:e8:d9:85
       size: 10Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm msix msi vpd bus_master cap_list rom ethernet physical tp 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atlantic driverversion=1.5.345.0 duplex=full firmware=1.5.44 latency=0 link=yes multicast=yes port=twisted pair speed=10Gbit/s
       resources: irq:16 memory:df440000-df44ffff memory:df450000-df450fff memory:df000000-df3fffff memory:df400000-df43ffff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 50:9a:4c:59:ed:1f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.11.131 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:130 memory:df700000-df71ffff[/HTML]

(enp1s0 is no longer listed as DISABLED).

I tried setting 10.10.10.10 as the static IP for the Win10 machine side of the two NIC cards & sharing the network connection through this, but it didn't seem to trigger anything. I found the file for setting static IP's by executing ```
sudo nano /etc/network/interfaces
```but I didn't dare enter info for the enp1s0 card as it didn't have any entries to begin in the file...

---

### Post by chili555 on 2017-09-14
You shouldn't need to, on an experimental basis, edit the interfaces file; you can merely do:```
sudo ifconfig enp1s0 10.10.10.20 up
```Do the lights come on? Can you then ping the Windows machine?```
ping -c3 10.10.10.10
```

If this works, you can edit the interfaces file to read:```
auto lo
iface lo inet loopback

auto enp1s0
iface enp1s0 inet static
address 10.10.10.20
netmask 255.255.255.0
```Your usual ethernet interface, connecting to the internet, should still be controlled by Network Manager.

---

### Post by madumi on 2017-09-14
Looking pretty good here now.

I tried
```
sudo ifconfig enp1s0 10.10.10.20 up
```

and then pinged from my win10 machine side, all packets returned successfully

So I added:
[HTML]auto enp1s0
iface enp1s0 inet static
address 10.10.10.20
netmask 255.255.255.0[/HTML]

below the other interfaces listed & rebooted.

It took me a while to set up Samba file sharing to test transfers, and a ramdrive. I only had 8G ram in the ubuntu machine, so I only set up 3G for the ramdrive... Not really enough for a sustained test, but this was what I saw for the 1 or 2 seconds the file transfer interface was visible:
[IMG]http://www.bertpohl.com/links/2017ramdisk.jpg[/IMG]

I would say that is fairly successful.
Thanks so much for your help and persistence!

---

### Post by chili555 on 2017-09-14
Awesome! Glad it's working.

---

### Post by madumi on 2017-09-16
Hi again,

I have seen two of what look look like Kernel panic states while trying to execute sustained transfers @ about 150Mb/s... (crashed the server)

Any idea whether something like that would be more likely caused by hardware, or software (I can wait for software updates, but if it's more likely hardware-related, I can still return the card).

Or maybe it's because I'm using the 4.12 Kernel...(?)

thanks!

---

### Post by madumi on 2017-09-17
On the off chance that the server crashes were caused by a bug in the 4.12 Kernel, I did a clean install of Ubuntu server 16.04 & then upgraded the kernel to 4.13.2 (the latest one listed as "stable").

After setting a static IP & Samba shares, I initiated a file transfer over the network. Sadly, this again crashed the server (after about 150GB).

To check whether this might be unrelated to the XG-C100C, I did the same transfer to the same Samba shares only using the onboard 1G NIC. The system didn't crash, so I'm thinking it must be due to the card (?)
I also did a separate test with a 80mm fan blowing on the NIC to see if the crashes were related to heat. It crashed just as quickly, so I'm guessing heat doesn't play a role...

Does anyone know how I can check which version of the driver the card is presently using from the Kernel (I didn't install it separately... it installed from the 4.13.2 Kernel)? If it's an old driver & Asus could release an updated version, then I might wait for a fix... After all, Asus states that the Atlantic1.5.348.0 driver (= Asus driver version 5.0.0.5), is compatible only with kernels 3.2, 3.6, 4.2, & 4.4...

After all this however, I'm strongly tempted simply to return the card & find something else more stable... thoughts?

---

### Post by madumi on 2017-09-18
Sorry this has been so tedious, but I think I'm getting closer to a solution.

After using Kernel 4.13.2 failed, I got to thinking that I should try installing under the (supported) 4.4 kernel. Previously, I didn't think the installation took, but I tried again.

-------------------------
STEPS:
1) clean install of Ubuntu 16.04. Then installed webmin so I could work a bit from a GUI.
2) install the build-essential package from apt
3) download the Asus 5.0.0.5 driver for the XG-C100C to /home/madumi, unzipped the file to reveal the Atlantic1.5.348.0.tar.bz2 archive, which I then unpacked: tar -xvjf /home/madumi/Atlantic1.5.348.0.tar.bz2
4) using the terminal (webmin has a different interface), after navigating to the new /home/madumi/Atlantic directory, ran: make which then generated a "atlantic.ko" file.
5) I then edited the network interfaces file: sudo nano /etc/network/interfaces and set the static IP for my card (occupying the enp1s0 slot):
   auto enp1s0
   iface enp1s0 inet static
   address 10.10.10.20
   netmask 255.255.255.0
6) finally, I ran: sudo insmod /home/madumi/Atlantic/atlantic.ko
   at which point, everything seemed functional & I mounted drives & set up Samba shares

-------------------------
TESTING:
I'm still testing, but at this point, I haven't seen any kernel panic states & the server hasn't crashed.
Previous crashes took place after ~150GB, transferred from a single HDD at a rate of about 640Mb/s (80MB/s).
So far I've transferred close to 1TB from 3 HDD's at a rate averaging 1760Mb/s (220MB/s) & as fast as 2720Mb/s (340MB/s) & it's going fine. Ethernet cable is about 150 feet.

-------------------------
PERMANENT INSTALLATION?
Which leaves me with the question, how can I make this a permanent installation? I'm new to linux, so I'm just feeling my way, but I understand ```
sudo insmod /home/madumi/Atlantic/atlantic.ko
``` only installs the driver till the next reboot. Do I need to automate this command at boot time, or is there a better way to make this a permanent installation?

---

### Post by madumi on 2017-09-20
FURTHER TESTING - perfectly stable

I have been able to transfer approximately 6TB (read/write) without any problems.
I haven't been able to test the max speed because I've been using HDD's, but while transferring at about 250MB/s (3 HDD's at once), the card handled heat dissipation competently (it was never scorching to the touch).

So, I'd say it's been successful... I'm inclined to keep the cards.

PERMANENT INSTALLATION?

Can anyone comment on a good way to use the sudo insmod atlantic.ko command to install the driver after a reboot? thanks!

---

### Post by praseodym on 2017-09-20
Run
```

echo atlantic | sudo tee -a /etc/modules
```

---

### Post by chili555 on 2017-09-21
Sorry for the delays in my reply. I am away from home for a few weeks.> PERMANENT INSTALLATION?
Which leaves me with the question, how can I make this a permanent installation? I'm new to linux, so I'm just feeling my way, but I understand
Code:
sudo insmod /home/madumi/Atlantic/atlantic.ko
only installs the driver till the next reboot. Do I need to automate this command at boot time, or is there a better way to make this a permanent installation?I suggest that you do:```
sudo nano /etc/rc.local
```Amend the file to read:```
#!/bin/sh -e

insmod /home/madumi/Atlantic/atlantic.ko

exit 0

```Save and close the text editor.

---

### Post by madumi on 2017-09-21
> **chili555 said:**
> I suggest that you do:```
sudo nano /etc/rc.local
```Amend the file to read:```
#!/bin/sh -e

insmod /home/madumi/Atlantic/atlantic.ko

exit 0

```Save and close the text editor.

That's perfect! It works nicely after reboot.

Out of interest, the #!/bin/sh -e on the first line of the script is commented out by the # right? Or does it accomplish something the way it's written?

haha, and I owe you big time for all the help you've given me... I don't know how to say thanks enough!

---

### Post by chili555 on 2017-09-21
> Or does it accomplish something the way it's written?It does. The well-known #! also known as crunch bang, is part of shell scripting, about which I am almost ignorant. 

Glad it's working!

---

### Post by jxd on 2018-01-13
This has all been extremely helpful, as I was attempting exactly the same thing. I managed to get everything working on 4.12 kernel, and then the kernel panic came. I don't have a video card, so I could only be sure the computer was freezing. 

I downgraded the kernel to 4.4, updated grub, removed the other kernels, rebooted
For some reason, I kept trying to insmod atlantic.o instead of atlantic.ko .... wasted quite a bit of time.

Finally it is all up and running again, and now hopefully, no more kernel panic =) If I don't post again, then all is beautiful. Thanks again.

---

### Post by madumi on 2018-01-13
> **jxd said:**
> Finally it is all up and running again, and now hopefully, no more kernel panic =) If I don't post again, then all is beautiful. Thanks again.

Once I had it up and running on kernel 4.4, it's been rock solid ever since--no issues at all. Hope you get the same mileage :-)

---

