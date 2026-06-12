---
title: "Problem with Internal Network Card"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by kiyoshigawa on 2006-08-30
Well, I was hoping it wouldn't have to come to this, but after two days of searching these forums and the internet in general for a solution, I guess I'll have to post something.

This is a frech install of dapper from the live CD. My setup is as follows: I am attempting to make a server box that will basically act as a firewall and share the internet to the 4 other computers in my home. In my current setup, the internet comes from my cable modem to eth1. eth1 is configured automatically by DHCP and I am now able to connect to the internet. I also have eth0 configured to the IP address 192.168.0.1 and hooked into the switch that the other 4 computers are currently connected to. I have followed the instructions in [here]("http://www.ubuntuforums.org/showthread.php?t=74925") and [here]("http://www.ubuntuforums.org/showthread.php?t=74925") to no avail, both several times. Currently the computer is unable to ping any internal network IP address, and none of the network computers are able to ping 192.168.0.1. This is the case with firestarter on and off, so I don't think the firewall is preventing communication.

my ifconfig is as follows:
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:E0:C6:07
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:80:AD:40:46:66
          inet addr:67.164.195.58  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::280:adff:fe40:4666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7626871 (7.2 MiB)  TX bytes:484490 (473.1 KiB)
          Interrupt:9 Base address:0xf400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6556 (6.4 KiB)  TX bytes:6556 (6.4 KiB)

and my /etc/network/interfaces looks like this:

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth1 inet dhcp

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1

auto eth0

Any help you can offer would be greatly appreciated. Thanks in advance.

---

