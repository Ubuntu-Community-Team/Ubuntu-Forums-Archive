---
title: "[SOLVED] Rosewill RC-400LX will not obtain IP address."
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by toolfan2k4 on 2008-11-07
Hello all, I have a Rosewill RC-400LX gigabit NIC that will not obtain an IP address. This is a dual boot machine and it works in windows so I know the card is fine. Ubuntu shows it as a Realtek gigabit card. I tried using a static IP and it does not connect to the network that way as well. Is there a way for me to delete the drivers for the NIC and attempt to reinstall them? If so can someone give me the commands to do this? :) If need be I can connect the onboard NIC to use internet on it but that is on 10/100 so I want to get this NIC working. Any help is appreciated, thanks.

---

### Post by toolfan2k4 on 2008-11-09
Anyone know how to uninstall and reinstall a NIC driver via command line? Thats the only fix I can think of....even better does anyone have a better idea?

---

### Post by toolfan2k4 on 2008-11-10
Issue is resolved. I simply reloaded the ubuntu OS.:(

---

### Post by RHAnthony on 2011-08-07
Reloading the OS is not an acceptable solution.

I have the exact same card and issue.  I also see it as a Realtek card, but I think 'just because they use Realtek chips, so that's not a big deal I don't think.

The card will not reset it's IP on boot and I have to manually do it each time from the console to get it talking.
I can configure a static IP with ifconfig no problem and it will let me ping on the network:

$ ifconfig eth1 inet 192.168.1.20 netmask 255.255.255.0 up

I can't seem to use DNS though, and after a timeout (20 minutes?), it will shut it self down (sleep) and I can not re-up the interface without rebooting the machine.  I also can't kick it above 100Mbps.

/etc/network/interfaces:

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.20
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

birch# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0a:cd:1d:a5:a6
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe1d:a5a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:560351 (560.3 KB)  TX bytes:143236 (143.2 KB)
          Interrupt:17 Base address:0xeb00

birch# ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
birch# lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
01:01.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
birch#

```

So pretty much it's only setting to 100Mbps and it wont use DNS (in my resolv.conf, openDNS servers), and it also shuts itself off after a timeout and I can't re-up the interface.  The card worked fine in Windows.

---

### Post by toolfan2k4 on 2011-08-07
I agree that it is not an acceptable resolution but it was the only one I could find that worked. I was actually able to get the gigabit working as well and had no issues with DNS. Am I correct in assuming that you are using a gigabit compatible ethernet cable as well as network hardware?

---

### Post by RHAnthony on 2011-08-07
Cat6 ~3ft, cable worked on another 1000Mb/s link yesterday.

---

