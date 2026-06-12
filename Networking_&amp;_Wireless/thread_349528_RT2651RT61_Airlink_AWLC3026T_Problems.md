---
title: "RT2651/RT61 Airlink AWLC3026T Problems"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by pbureau on 2007-01-30
ntro:

I have configured my system with Dd-link pcmcia dwl-630 using ndiswrapper
drivers with WPA connectivity and everything works.

I am curious to get this other card I have on hand working, and to some 
extend I am getting somewhere,but it seems I have reached a dead end with it.
The Gnome-NetworkManager, seems intent on reconizing it as a 
"wired network (RaLink RT2561/RT61 802.11g PCI) " (ETH1) connection, 
I have tried Linux and Ndiswrapper drivers to no avail, anyone 
ever encounter this issue ? or know how to resolv it ?

This is a project not critical, please find the information about my configs 
and pc details below for review and suggestions.


I have an Airlink 101 Model # AWLC3026T 802.11g pcmcia card.


Packages Installed:
=======================================================================
wpa_supplicant 0.5.4-5
NetworkManager Applet 0.6.4
Network Monitor 2.12
linux-restricted-modules-2.6.17-10-modules
linux-restricted-modules-common
linux-restricted-modules-386
linux-restricted-modules-generic
ndiswrapper 1.1.8-1ubuntu-2
-----------------------------------------------------------------------

lspci:
=======================================================================
0b:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
-----------------------------------------------------------------------

sudo lshw -C network:
=======================================================================
*-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0b:00.0
       logical name: wmaster0
       version: 00
       serial: 00:14:a5:53:a5:89
       width: 32 bits
       clock: 33MHz
capabilities: bus_master cap_list logical wireless ethernet physical
configuration: broadcast=yes driver=rt61pci driverversion=CVS 
firmware=.bin ip=169.254.202.228 link=yes multicast=yes wireless=IEEE 
802.11g resources: iomemory:2c000000-2c007fff irq:11
-----------------------------------------------------------------------

cat /etc/network/interfaces:
=======================================================================
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
----------------------------------------------------------------------

cat /etc/wpa_supplicant.conf
======================================================================
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant
ENABLED=0
----------------------------------------------------------------------

ifconfig:
======================================================================
ath0      Link encap:Ethernet  HWaddr 00:11:95:4A:02:E8  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe4a:2e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:371 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:279064 (272.5 KiB)  TX bytes:37116 (36.2 KiB)

eth0      Link encap:Ethernet  HWaddr 00:00:39:4F:2B:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:24:28:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd100 


-----------------------------------------------------------------------

iwconfig:
=======================================================================
ath0      IEEE 802.11g  ESSID:"PRIVATE-ESSID"  Nickname:"PRIVATE-ESSID"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:D5:E8:70   
          Bit Rate:24 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/94  Signal level=-30 dBm  Noise level=-95 dBm
          Rx invalid nwid:1406  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.447 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:53:A5:89  
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:108 (108.0 b)
          Base address:0x3000 

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-53-A5-89-00-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x3000 
--------------------------------------------------------------------------------

---

### Post by crys on 2007-01-31
Try the driver at [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

---

