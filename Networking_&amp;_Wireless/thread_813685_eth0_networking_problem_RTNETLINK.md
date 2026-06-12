---
title: "eth0 networking problem RTNETLINK"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by crashovaride on 2008-05-31
All,

I've just recently ran into this issue while running an nmap scan and my network bogging down on me. After multiple tries to get the network card back up. I've tested the card directly connected to my DMZ, Firewall and switch and nothing is working. 

After a reboot the network card knows my IP address as 192.168.0.1 and nothing further happens. I can ping local host lo, yet i cannot ping the router home (192.168.1.1 / 192.168.0.1) nor any other machines on the network. 

After performing an /etc/init.d/networking restart it goes through the process of connecting my wifi card, however not my eth0 device. And, with an ifup eth0 i receive:

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120

I've removed the /var/run/dhclient.eth0 file, chmodded it, and still the same problem. On top of that, my /var/log/messages file reports the following: 

May 31 01:18:53 HOST kernel: [16976.696000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 31 01:19:05 HOST dhcdbd: Started up.
May 31 01:19:16 HOST kernel: [16999.320000] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 31 01:19:19 HOST kernel: [17002.320000] b44: eth0: Link is up at 100 Mbps, full duplex.
May 31 01:19:19 HOST kernel: [17002.320000] b44: eth0: Flow control is off for TX and off for RX.
May 31 01:19:19 HOST kernel: [17002.324000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 31 01:28:42 HOST kernel: [17564.984000] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 31 01:28:45 HOST kernel: [17567.984000] b44: eth0: Link is up at 100 Mbps, full duplex.
May 31 01:28:45 HOST kernel: [17567.984000] b44: eth0: Flow control is off for TX and off for RX.
May 31 01:28:45 HOST kernel: [17567.988000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


I have searched the internet high and low, for 4 hours and cannot find anything. Ontop of which i get the error sometimes i get the following error: RTNETLINK: answers no such process

I even attempted to do a dist-upgrade from ubuntu 7.10 and it babbles about an error in checking the package size. 

I've tried to restart networking, modify the udev rules and everything else. my udev rules are as follows:

[70-persistent-net.rules]

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:14:22:f2:5e:e4", NAME="eth0"

# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:18:de:c1:f9:34", NAME="eth1"

This is an lspci dump

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Any suggestions? (dell inspiron 9400). 

Thanks In Advanced.

---

