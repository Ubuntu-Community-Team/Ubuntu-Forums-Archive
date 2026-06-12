---
title: "cold boot, no network, reboot, it comes back"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by saberworks on 2010-11-15
I recently built a new computer (specs follow).  I installed Ubuntu 10.10 on a fresh hard drive (well, ssd).  Everything seemed to work for a few days, but now when I start the computer from "off" it starts with no network.  The network icon in the top right shows two computers with a small X between them.  When I click it, it shows no "eth0" or similar, it just has the "VPN" menu item.  When I then use the menu to reboot the computer, when it comes back, the network card is shown and works perfectly.  This happens every time I cold boot: no network, reboot, network works.  Does anyone have any idea what is going on or how I should approach troubleshooting this issue?  The network card is an integrated 10/100/1000.  Specs:

Core i-5 760
Intel motherboard with integrated sound & network
Corsair 128GB SSD
Some generic dvd/cd burner
Nvidia GTX 460 with the restricted drivers installed using the packager

The only other "weird" thing is that I installed a CISCO vpn client 4.8.02 (0030), which required some patch to make it work, I followed the information here: [http://www.shuvoovuhs.com/linux/install-cisco-vpn-client-on-ubuntu-10-10-maverick-meerkat/](http://www.shuvoovuhs.com/linux/install-cisco-vpn-client-on-ubuntu-10-10-maverick-meerkat/)

Thanks in advance for any help!

---

### Post by Hippytaff on 2010-11-16
Is it wireless or ethernet?
 
If it's wireless it might either not be enabled on first startup or blocked. You can check if its blocked by typing
```

rfkill list

```
in a terminal. If there are any block (will say sof block yes for example)
```

rfkill unblock all

```
:-)

---

### Post by theozzlives on 2010-11-16
An onboard card is normally ethernet. If it's not to much trouble try taking the Cisco stuff off and see if that works.

---

### Post by saberworks on 2010-11-16
It's a wired card.  I removed the cisco vpn software and the problems persist.  Immediately after removing them, I rebooted and the network was up.  I shut down, left the computer off for a few seconds, then booted it.  No network till I reboot.  If I run lshw -C network when the networking isn't running, I get this:

>   *-network UNCLAIMED
       description: Ethernet controller
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:de200000-de21ffff memory:de224000-de224fff ioport:2020(size=32)
After rebooting, when the network is running, the same command outputs this:
>   *-network
       description: Ethernet interface
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:1c:c0:fe:37:01
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.10-5 ip=192.168.0.108 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:49 memory:de200000-de21ffff memory:de224000-de224fff ioport:2020(size=32)
/etc/network/interfaces looks like this in either case:
> auto lo
iface lo inet loopback
I suppose I would have expected to have an entry for eth0 in there but maybe not.

Is there something else I should be looking at?

---

### Post by theozzlives on 2010-11-16
what do you get if your network is up?

---

### Post by saberworks on 2010-11-16
> **theozzlives said:**
> what do you get if your network is up?

It's in the second quoted section above.

---

### Post by Hippytaff on 2010-11-16
> 
what do you get if your network is up?

 
```

*-network
description: Ethernet interface
product: 82578DC Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 05
serial: 00:1c:c0:fe:37:01
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.10-5 ip=192.168.0.108 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:49 memory:de200000-de21ffff memory:de224000-de224fff ioport:2020(size=32) 
```
:-)

---

### Post by dj.bettega on 2010-11-22
Hi there,

Exactly the same behavior experienced

Ubuntu-10.10-server-amd64 edition (with full ubuntu-desktop installed)

Motherboard: DFP LP MI P55-T35 MINI-ITX (integrated 82578DC Gigabit Network card)
ATI graphics card: 512MB SAPPHIRE HD4350 DDR2
CPU: Intel Core i5 760 2.8G s1156
HDD: 300G WD3000BLFS Velociraptor
RAM: Corsair Memory XMS3 8GB DDR3 1333 Mhz

Almost identical outputs from  lshw -C network command

Any hints/ solutions much appreciated

D

---

### Post by dj.bettega on 2010-11-24
UPDATE

Thought this might be done to a driver problem. Found this post

[http://wwww.ubuntuforums.org/showthread.php?t=1390410&page=2](http://wwww.ubuntuforums.org/showthread.php?t=1390410&page=2)

it deals with a different problem, but, explains how to install new versions. Unfortunately, this has not solved the problem.

As an update to my previous post - I have listed the output of the both lshw & lspci commands below

WHEN WORKING (after reboot)

lshw -C Network

<Output>

  *-network               
       description: Ethernet interface
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 00:01:29:01:61:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.10-5 ip=192.168.1.23 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:41 memory:fbec0000-fbedffff memory:fbefc000-fbefcfff ioport:dc00(size=32)



========================================================
lspci -nn

<Output>

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV710 [Radeon HD 4350] [1002:954f]
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]

WHEN NOT WORKING (after cold boot)

sudo lshw -C Network

<Output>

  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:fbec0000-fbedffff memory:fbefc000-fbefcfff ioport:dc00(size=32)


===============================================


sudo lspci -nn

<Output>

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV710 [Radeon HD 4350] [1002:954f]
01:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]

And finally, the driver versions used

OLD DRIVER

sudo ethtool -i eth0
<output>

driver: e1000e
version: 1.0.2-k4
firmware-version: 0.10-5
bus-info: 0000:00:19.0


=============================

NEW DRIVER

sudo ethtool -i eth0
<output>

driver: e1000e
version: 1.2.20-NAPI
firmware-version: 0.10-5
bus-info: 0000:00:19.0


============================

---

### Post by grant937 on 2010-11-25
Just FYI I have the same problem when booting up.  My computer specs are different and I run 10.04 but no solution yet.

---

### Post by dj.bettega on 2010-11-25
ANOTHER UPDATE

Sorry for the hijacking of the thread saberworks... hopefully, some of my posts will prove useful in tracking down the issue.

The output of 

```
sudo lspci -v
```WHEN WORKING

0:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
    Subsystem: Intel Corporation Device 0000
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fbec0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fbefc000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at dc00 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e

============================================================
WHEN NOT WORKING

00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
    Subsystem: Intel Corporation Device 0000
    Flags: fast devsel, IRQ 20
    Memory at fbec0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fbefc000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at dc00 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel modules: e1000e

Looked into the kernel messages surrounding the reason why the "e1000e" driver loads in some instances and not in others. The output of

```
dmesg | grep e1000e
```WHEN NOT WORKING

administrator@server1:~$ dmesg | grep e1000e
[    1.975246] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.975248] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.975278] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.975285] e1000e 0000:00:19.0: setting latency timer to 64
[    1.975371] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    3.041468] e1000e 0000:00:19.0: PCI INT A disabled
[    3.041475] e1000e: probe of 0000:00:19.0 failed with error -3


====================================================
WHEN WORKING

administrator@server1:~$ dmesg | grep e1000e
[    1.987511] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.987513] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.987544] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.987551] e1000e 0000:00:19.0: setting latency timer to 64
[    1.987736] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    2.209460] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:01:29:01:61:7a
[    2.209462] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.209512] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 9, PBA No: ffffff-0ff
[    8.661036] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    8.720955] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   10.260448] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   10.260451] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO

Looking into why the following happens

```
e1000e: probe of 0000:00:19.0 failed with error -3
```led me to the posts here - which points to a problem with how the BIOS interacts with the system

[http://kerneltrap.org/mailarchive/linux-kernel/2010/6/10/4581663/thread#mid-4581663](http://kerneltrap.org/mailarchive/linux-kernel/2010/6/10/4581663/thread#mid-4581663)

and subsequently to the bug reports here

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/591707](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/591707)

Am a newbie - so please view with a critical eye

D

---

### Post by Hippytaff on 2010-11-25
dudes - please can you put any terminal output in code tags...easier to read :-)

having a look :-)

---

### Post by Hippytaff on 2010-11-25
I've got a feeling it is a bug...either that or for some reason the module is not loading the first time around. There must be a difference beyond my knowledge between booting and re-booting...others here might understand this better, and that might point to the problem/solution :-)

---

### Post by saberworks on 2010-11-25
No worries about thread-jacking, the more people looking at this the better.  Here's my dmesg | grep e1000 output (looks like yours):

```
[    0.795165] pci 0000:05:03.0: reg 14: [mem 0xde100000-0xde103fff]
[    0.795277] pci 0000:00:1e.0:   bridge window [mem 0xde100000-0xde1fffff]
[    0.839580] pci 0000:00:1e.0:   bridge window [mem 0xde100000-0xde1fffff]
[    0.839736] pci_bus 0000:05: resource 1 [mem 0xde100000-0xde1fffff]
[    1.947060] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.947062] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.947097] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.947104] e1000e 0000:00:19.0: setting latency timer to 64
[    1.947290] e1000e 0000:00:19.0: irq 49 for MSI/MSI-X
[    3.007306] e1000e 0000:00:19.0: PCI INT A disabled
[    3.007318] e1000e: probe of 0000:00:19.0 failed with error -3
```

---

### Post by saberworks on 2010-11-27
I think I got this fixed.  I bought my motherboard from Newegg.com a few weeks ago, it turns out it ships with a really old version of the BIOS.  I downloaded the latest version from intel's web site, flashed my BIOS, and 2 cold boots in a row I have network.  I'll post again if I run into it again, but I'm considering it fixed for now.  FYI, the BIOS versions:

> 
WBIBX10J.86A.0122.2009.0802.2219 # Original
WBIBX10J.86A.0310.2010.0728.2257 # New


My motherboard is: Intel® Desktop Board DP55WB

I went line-by-line through their release notes/changelogs and didn't see anything directly addressing the issue I was having, but I noticed after the first version (which is my original above), their "lan" firmware revision went from 1.0 to 1.2.  Not sure if it's related.

---

### Post by logan_five on 2010-11-28
Confirmed, works for me as well. My mainboard is an Intel DP55WG. Updated to the latest BIOS from the Intel website and everything is running fine.

Thanks for the suggestion, saberworks. This problem didn't show up for me until 10.10, and I was on the verge of rolling back to 10.04.

---

### Post by parisv on 2011-08-07
I'm having the same issue with an Intel DH67BL v3 motherboard. I've updated to the BIOS and Intel LAN drivers but still having the same issue.

This is the output when it's working:

```
cat dmesgworking | grep e1000e
[    1.445780] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.445782] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.445812] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.445821] e1000e 0000:00:19.0: setting latency timer to 64
[    1.445921] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    2.834014] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) e0:restofmacadd:00
[    2.834016] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.834049] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[   16.443734] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   16.503584] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
```


and this is dmesg when it's not working:

```
 cat dmesgnotwoking | grep e1000e
[    1.458940] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.458942] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.458973] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.458982] e1000e 0000:00:19.0: setting latency timer to 64
[    1.459081] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    2.523612] e1000e 0000:00:19.0: PCI INT A disabled
[    2.523618] e1000e: probe of 0000:00:19.0 failed with error -3
```

Odd thing is I've enabled WOL and can boot it up via that so the nic is working!

---

### Post by parisv on 2011-08-08
I've found this

[http://downloadmirror.intel.com/15817/eng/README.txt]("http://downloadmirror.intel.com/15817/eng/README.txt")

It says:

```
Configuring the Driver on Different Distributions
  -------------------------------------------------
  Configuring a network driver to load properly when the system is started
  is distribution dependent.  Typically, the configuration process involves
  adding an alias line to /etc/modules.conf or /etc/modprobe.conf as well
  as editing other system startup scripts and/or configuration files.  Many
  popular Linux distributions ship with tools to make these changes for you.
  To learn the proper way to configure a network device for your system,
  refer to your distribution documentation.  If during this process you are
  asked for the driver or module name, the name for the Linux Base Driver
  for the Gigabit Family of Adapters is e1000e.

  As an example, if you install the e1000e driver for two Gigabit adapters 
  (eth0 and eth1) and want to set the interrupt mode to MSI-X and MSI 
  respectively, add the following to modules.conf or /etc/modprobe.conf:

       alias eth0 e1000e
       alias eth1 e1000e
       options e1000e IntMode=2,1

```

I've made a file in /etc/modprobe.d/ called e1000e.conf with:

alias eth0 e1000e
       alias eth1 e1000e
       options e1000e IntMode=2,1

inside it. I've tried IntMode=2,1 as well as just 2,1 and 0 on their own.

It doesn't actually seem like it's making a difference. When I grep dmesg it's the same when eth0 doesn't work and when it does.

---

### Post by mendhak on 2011-11-01
Did any of you guys find a solution for this?  Please post back if you did.

---

### Post by parisv on 2011-11-01
nope. upgraded to 11.10 still no joy. I'm going to have to disable the onboard nic and buy a pci e one.

---

### Post by saberworks on 2011-11-01
As I mentioned, updating to the latest bios and also the latest integrated network card firmware (not drivers!) solved my problem.  I haven't had a problem since I posted above.

---

### Post by parisv on 2011-11-01
> **mendhak said:**
> Did any of you guys find a solution for this?  Please post back if you did.

which motherboard are you using I'm using intel DH67BL version 3. I've updated the firmware also but looks like intel hasn't fixed the issue with my MB.

---

### Post by saberworks on 2011-11-01
Please note they ship their integrated network card firmware in separate files than their bios files.  It's a separate step, not the same as the bios.

---

### Post by parisv on 2011-11-01
> **saberworks said:**
> Please note they ship their integrated network card firmware in separate files than their bios files.  It's a separate step, not the same as the bios.

Ah ok thanks for the heads up. According to [here]("http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh67bl.html") my motherboard uses an 82579V Gigabit Ethernet Controller.

I can only find drivers for this no firmware updates [here]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller")

---

### Post by saberworks on 2011-11-01
I looked at the pages you linked, yeah it looks like on yours they're putting the network card firmware in the bios package.  Their readme says:

LAN Option ROM: v1365 PXE 2.1 Build 089

So that would be the latest I guess.  If you have the latest bios already (which includes the latest network card firmware) maybe you're running into a different problem with the same symptoms.  In my case, the network card would always work under my dual-booted windows 7, but the network performance was sporadic.  Once I did the firmware update, it fixed the linux and the windows problem.  Sorry I can't be of more help.  I was taking shots in the dark trying to fix my problem and I guess I just got lucky.

---

