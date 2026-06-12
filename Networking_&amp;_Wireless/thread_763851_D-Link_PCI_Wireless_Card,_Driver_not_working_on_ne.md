---
title: "D-Link PCI Wireless Card, Driver not working on new install"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by curbsidesteak on 2008-04-23
I have just installed Ubuntu 7.10. All seems well except i have a wireless card, and the driver is giving me trouble. I currently have an ethernet cord connected from the wireless router which is why the eth0 is showing connectivity. I tried disconnecting and restarting the network, but this seems to be a waste of time as the driver is not working properly to begin with. 

It is a d-link Xtreme N DWA-522 wireless PCI card

I followed completely the instructions on

[https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

and have found myself stuck on 3.5

after entering "tail /var/log/messages" my response was no errors but then after entering "ifconfig" and "iwconfig" here was the response

eth0 Link encap:Ethernet HWaddr 00:11:11:17:51:A7
inet addr:71.56.48.198 Bcast:255.255.255.255 Mask:255.255.255.0
inet6 addr: fe80::211:11ff:fe17:51a7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8240 errors:0 dropped:0 overruns:0 frame:0
TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2684353 (2.5 MB) TX bytes:309210 (301.9 KB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)



lo no wireless extensions.

eth0 no wireless extensions.

No wireless "wlan0" appears.
At this point the instructions assume that a wireless network will appear in the drop-down list from the Network Manager Icon on my desktop, but this is not the case. All that shows is the wired and modem.

I looked further into troubleshooting and found a help section suggesting to check to make sure the wireless card was "turned on"

You'll see below what I entered and what was the response.

joel@joel:~$ sudo lshw -C network
*-network:0 UNCLAIMED
description: Network controller
product: AR5416 802.11a/b/g/n Wireless PCI Adapter
vendor: Atheros Communications, Inc.
physical id: 2
bus info: pci@0000:02:02.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: latency=64
*-network:1
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 02
serial: 00:11:11:17:51:a7
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.0.160 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

This is where I am stuck. Don't know what to try from here as there was nothing in the forums I could find about how to actually turn on the card if it is not on. I do not think this is the problem however, but am not sure as I am fairly new to this.

Tried restarting the network "sudo /etc/init.d/networking restart"
didn't bring the wlan0 out from hiding. 
Any ideas?

---

### Post by dstew on 2008-04-23
What is the output of **ndiswrapper -l**? If ndiswrapper is having a hard time, the madwifi driver seems to work with this chipset in Gutsy. See [_this thread_]("http://ubuntuforums.org/showthread.php?t=668272"). But, you should pick one or the other to work on.

---

### Post by curbsidesteak on 2008-04-24
I was just reading on that, thanks for the help. I'll post if I am able to make it work.

---

