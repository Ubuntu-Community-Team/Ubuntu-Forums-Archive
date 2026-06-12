---
title: "Wired Network Connection Dropping out"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by mark_catalystic on 2007-10-29
Hi Everyone,

I have an issue with my Ubuntu installation. I had this problem with 7.04 and now with 7.10.

Basically I have Ubuntu 7.10 installed on my machine that has a Asus P5W DH Deluxe motherboard with onboard networking.

I mainly use the machine as a host server to run Virtual machines. in All of my virtual machines the network connection keeps on dropping out and comes back a few seconds later.

I have another pc on the network and the internet doesn't drop out, so its not a internet issue. I switched to Fedora after the network dropping out on Ubuntu 7.04 caused me too much distress, and there were no network issues with Fedora... So that means that there is no hard ware issue.

So that leaves me with 2 possible break down points... Ubuntu or VMware.

I am using a Static Network Configuration, so it should not have anything to do with DHCP but stranger things have happened

Now I want to be methodical, but don't really know what logs to look at... or which tools to run... On Ubuntu to prove or disprove that its the issue.

So could someone point me to some tools  I could run over time  or log locations to see if its my Ubuntu installation?

My gut feeling is that its the drivers of the ubuntu... But I want to be sure... 

Any help would be appreciated

Regards

Mark

---

### Post by mark_catalystic on 2007-10-30
Hi Everyone,

I got some details about my hardware from running some commands listed here...

[http://ubuntuforums.org/showthread.php?t=588648]("http://ubuntuforums.org/showthread.php?t=588648")


lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82975X Memory Controller Hub [8086:277c] (rev c0)
00:01.0 PCI bridge [0604]: Intel Corporation 82975X PCI Express Root Port [8086:277d] (rev c0)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 02)
02:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 02)
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 20)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 20)
06:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GS] [10de:0392] (rev a1)
mark@mark-desktop-ubuntu:~$ 
mark@mark-desktop-ubuntu:~$ sudo lshw -C network
[sudo] password for mark:
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 20
       serial: 00:18:f3:c5:57:e3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 20
       serial: 00:18:f3:c5:3c:ab
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0b:e4:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by mark_catalystic on 2007-10-30
Some more information about the set up...

 ethtool -i eth0
driver: sky2
version: 1.18
firmware-version: N/A
bus-info: 0000:04:00.0
mark@mark-desktop-ubuntu:~$ 
mark@mark-desktop-ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes

---

### Post by portlandbob on 2008-02-02
I have the exact same issue with 7.10. I didn't realize it was a problem until my pidgin kept dropping and reconnecting with my different chat accounts.

My onboard card is almost the same as yours and after switching to a static IP I still have the issue. Here's my cards info:

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)

Just curious if you found a fix.

---

### Post by jmandawg on 2008-04-09
I'm having the same problem and it's making my virtual machines lose their bridged connection.

I'm actually getting this error in my log file:

```
Apr  9 10:38:31 e6400 kernel: [52474.823469] sky2 eth0: receiver hang detected¬
Apr  9 10:38:31 e6400 kernel: [52474.823475] sky2 eth0: disabling interface¬
Apr  9 10:38:31 e6400 kernel: [52474.823857] sky2 eth0: enabling interface¬
Apr  9 10:38:31 e6400 kernel: [52474.869953] br0: port 1(eth0) entering disabled state¬
Apr  9 10:38:34 e6400 kernel: [52477.784832] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow contr
Apr  9 10:38:34 e6400 kernel: [52477.791295] br0: port 1(eth0) entering learning state¬
Apr  9 10:38:49 e6400 kernel: [52492.746117] br0: topology change detected, propagating¬
Apr  9 10:38:49 e6400 kernel: [52492.746122] br0: port 1(eth0) entering forwarding state¬
```

And i think that once eth0 is disabled and enabled that kills the bridge.

I think it is an issue with the ethernet driver in the kernel.
I'm using ubuntu 2.6.22-14-server kernel.

And my ethernet hardware is:
         ```
  *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 22
                serial: 00:16:e6:85:bb:29
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=1GB/s
```

Any solutions?  Get a new network card?  Upgrade to Hardy?

---

### Post by jmandawg on 2008-04-12
I think i got mine fixed.  The problem was the sky2 driver is messed up.  You need to install the linux driver off of the marvell website.

I hope this helps someone, it took me a long time to get it fixed.

---

