---
title: "[SOLVED] Can't connect to wireless - hardy heron"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by graememcc on 2008-05-29
Hi

Linux newbie here.

Installed hardy heron yesterday, and managed to get ndiswrapper up and running with the windows driver for my Atheros network card. nm-applet then detected our wireless network, and I was able to find and connect to the network, enter my WEP 64bit hex key, and start browsing.

Today, the next day, however I can't.

nm-applet can still see our network, and prompts me to enter the WEP key, but never connects, and just reprompts for the WEP key.

I noticed that I can always see the signal strengh in the tray, but I never see the spinning balls graphic I seen when succesfully connecting yesterday.

I tried following the manual connection instructions from the wiki, but this also did not work, (I get no dhcpoffers received). 
I persuaded my flatmate to login to his router, temporarily disable security, and followed the sticky instructions for manually connecting to an unsecured network, but again hit the no dhcpoffers error.

Can anyone help me as to why it has suddenly stopped working? I haven't added any packages that would have affected networking. I inspected the driver setup, it is still the same as yesterday.

Here's some command outputs:

**lshw -C network:**
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:56:71:49
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:b8:e9:11
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

**ndiswrapper -l:**
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:1e:68:56:71:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53869 (52.6 KB)  TX bytes:53869 (52.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:b8:e9:11  
          inet6 addr: fe80::21f:3aff:feb8:e911/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17187 (16.7 KB)  TX bytes:222266 (217.0 KB)
          Interrupt:19 Memory:f6000000-f6010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:b8:e9:11  
          inet addr:169.254.6.181  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f6000000-f6010000 


**iwconfig:**
lo        no wireless extensions

eth0      no wireless extensions

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by graememcc on 2008-05-29
Solved.

Solution in:
[http://ubuntuforums.org/showpost.php?p=4829624&postcount=345]("http://ubuntuforums.org/showpost.php?p=4829624&postcount=345")

---

