---
title: "Wifi No DHCPOFFERS received"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by jesterthejedi on 2008-08-11
Hello,

I searched and tried a few tricks, but can't get it to connect to my wireless network. Here are some facts:

I had trouble getting my old lappy online, but after I was successful, I attempted to recreate the exact procedure but it wont work :(

A few things to mention, the drivers are installed, and my router is able to connect with my old lapptop(DHCP). Also my wifi is set up as unsecure. I run DD-WRT and prefer to only allow my specific MAC addresses connect. I turned that off for testing. Here is the data I have:

$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:7e:6f:68:20
Sending on   LPF/wlan0/00:19:7e:6f:68:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"echobase"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:12:17:26:31:C8   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth0 inet dhcp
iface wlan0 inet dhcp
wireless-essid echobase
auto wlan0

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:44:1c:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:6f:68:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by jesterthejedi on 2008-08-11
got it working by using the toolbox and then rebooting the pc. its using the b43 driver. It will connect when you first start up the computer, but then it stops giving any response.

---

### Post by jesterthejedi on 2008-08-11
I spoke too soon. It worked for like 2 minutes and now is just frozen.[IMG]http://i35.tinypic.com/2q1yl2a.png[/IMG]

---

