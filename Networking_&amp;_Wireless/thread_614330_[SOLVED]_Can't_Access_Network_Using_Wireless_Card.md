---
title: "[SOLVED] Can't Access Network Using Wireless Card"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by Sam Plamondon on 2007-11-15
I have Ubuntu 7.10 "Gutsy Gibbon" Desktop x86 Edition on a Dell Inspiron 1521 notebook.  My Dell wireless card is working, but I cannot connect to my LAN (which uses a Belkin Wireless G Router).  My network is encrypted with 64-bit, HEX WEP, and the ESSID is "Plamondons".  I tried connecting using the Terminal, and these were the results of my latest try (I've already tried several times using both the Terminal, and the Network application under Administration):

-----

root@sam-laptop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:41:81:75
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8c:ba:20
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.2.6 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
root@sam-laptop:~# sudo ifconfig eth1 down
root@sam-laptop:~# sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1c:26:41:81:75
Sending on   LPF/eth1/00:1c:26:41:81:75
Sending on   Socket/fallback
root@sam-laptop:~# sudo ifconfig eth1 up
root@sam-laptop:~# sudo iwconfig eth1 essid "Plamondons"
root@sam-laptop:~# sudo iwconfig eth1 mode Managed
root@sam-laptop:~# sudo iwconfig eth1 key XXXXXXXXXX (I replaced WEP code with Xs for this post)
root@sam-laptop:~# sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 18136
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1c:26:41:81:75
Sending on   LPF/eth1/00:1c:26:41:81:75
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

-----

However, when I go to my Belkin Wireless G Router's Setup Utility, and I check the DCHP Client List, I see my computer:  host name "sam-laptop", with IP address 192.168.2.6 and MAC address 00-1C-23-8C-BA-20.  I've checked all my settings, and there doesn't seem to be any problems.
I even found this in the Setup Utility's Security Log, which corresponds with the time of my most recent attempt:

-----

11/15/2007_____20:45:59_____sending OFFER to 192.168.2.6
11/15/2007_____20:45:59_____sending ACK to 192.168.2.6

-----

Why can't I access the network using my wireless card?  If anybody has any idea of how I can connect, please help me.
Thank you for reading!

---

### Post by Sam Plamondon on 2007-11-17
Well, I cleared all of my connection settings and retried using network manager, and it worked right away.

---

### Post by fireandlight27 on 2007-11-17
I am having the same problem after an upgrade to Gutsy.  Could you elaborate on how you cleared what settings?

---

### Post by Sam Plamondon on 2007-11-17
> **fireandlight27 said:**
> I am having the same problem after an upgrade to Gutsy.  Could you elaborate on how you cleared what settings?
Well, first of all, I simply typed "sudo dhclient -r eth1" into the Terminal.
After that, I went to Network under System/Administration on the top taskbar, clicked on "Properties" for the wireless connection, and erased everything.  Then, I went to the "DNS" tab and cleared out both DNS Servers and Search Domains.
Next, I single-clicked on "nm-applet" (the two little monitors overlapping each other on the top taskbar) and then clicked on my network.  I then typed in the WEP key and entered it, and my wireless was working.
Hope that helps!

---

