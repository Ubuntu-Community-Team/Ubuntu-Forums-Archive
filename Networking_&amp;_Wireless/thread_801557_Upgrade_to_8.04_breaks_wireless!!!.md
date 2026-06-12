---
title: "Upgrade to 8.04 breaks wireless!!!"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Killer Bee on 2008-05-20
After system restart following an internet upgrade from dapper (6.06) to Hardy (8.04), wireless network connection to internet no longer existed. Here are some console logs that may help (kernel version is 2.6.24):

myhome@mycomputer:~$ sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 8355
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:29:9e:82:5d
Sending on   LPF/eth0/00:e0:29:9e:82:5d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.11.99 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFFLAGS: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; No such device.


myhome@mycomputer:~$ sudo lspci | grep -i Network
05:06.0 Network controller: Standard Microsystems Corp [SMC] SMC2602W EZConnect / Addtron AWA-100 / Eumitcom PCI WL11000 (rev 02)


iwlist scan reports “no scan results” for both wifi0 and eth0


after using lspci -v | less in the console, the results for the network controller where thus:
05:06.0 Network controller: Standard Microsystems Corp [SMC] SMC2602W EZConnect / Addtron AWA-100 / Eumitcom PCI WL11000 (rev 02)
Subsystem: Standard Microsystems Corp [SMC] SMC2602W EZConnect / Addtron AWA-100 / Eumitcom PCI WL11000
Flags: medium devsel, IRQ 20
I/O ports at a000 [size=128]
Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
I/O ports at a400 [size=64]

again, here are more results of tests:
myhome@mycomputer:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: SMC2602W EZConnect / Addtron AWA-100 / Eumitcom PCI WL11000
       vendor: Standard Microsystems Corp [SMC]
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wifi0
       version: 02
       serial: 00:e0:29:9e:82:5d
       width: 32 bits
       clock: 33MHz
       capabilities: logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=0.7.6 latency=0 module=hostap_plx multicast=yes wireless=IEEE 802.11-DS


When i click on the configure button inside the network monitor tool on my desktop panel, i receive this error message when it is set to eth0:

The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system.

As i ran these tests, the wireless network monitor reported eth0 as disconnected.

Please feel free to instruct me as to how to gather more relevant information.

---

### Post by chili555 on 2008-05-20
Isn't eth0 your wired ethernet interface? Your wireless appears to be wifi0. Can you click and configure wifi0? Also scan needs to be run as sudo.

---

### Post by Killer Bee on 2008-05-20
After another reboot, an interesting thing happened. eth0 was recorded as sending in the screen of the network monitor applet, but not receiving. After i typed in wifi0 into the field of the applet, it showed me that wifi0 was receiving but not sending. Is this important?

I ran sudo iwlist scan, but again it returned no results for eth0 and wifi0.
I cannot configure wifi0.

---

### Post by chili555 on 2008-05-21
Let's take a look at the terminal command *ifconfig* and *lspci*. Thanks.

---

