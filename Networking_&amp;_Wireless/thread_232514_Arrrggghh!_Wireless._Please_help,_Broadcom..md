---
title: "Arrrggghh! Wireless. Please help, Broadcom."
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by fraterns on 2006-08-08
I really want to switch over to Linux for my desktop and I would like to use ubuntu, but I can't deal with this anymore.

I have spent about four weeks now, on and off when I have time, going through the threads on setting up my wireless card, the wireless Wiki, other resources on the net. I have tried every method/combination I have found. Wifiradar, Networkmanager, Ndiswrapper, etc.

Can someone please just walk me through this. Here is my environment, and what I want to achieve.

My laptop is an eMachines m6805, the card is the Broadcom 4306 chipset, I am using ubuntu 6.06.

What I want/need is for the wireless card to by default connect to my home network. G only , hidden SSID, WEP-128 (I would prefer WPA but have downgraded my network to WEP specifically due to the pain wpasupplicant added to the mix. if we can get it back to WPA I would prefer it.)

I would also like to be able to scan for networks while traveling and temporary attach to them, ie hotels, cafes, etc.

I have run Free/OpenBSD, I admin AIX at work, Linux is fairly new to me but I am familar in general, its just trying to configure the wireless that is driving me nuts, because I do something and do not get the results I expect.

Can someone please talk me through this

some current info

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:0D:81:5F
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe0d:815f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:831924 (812.4 KiB)  TX bytes:184051 (179.7 KiB)
          Interrupt:177 Base address:0x1800

eth1      Link encap:Ethernet  HWaddr 00:90:96:8A:E9:88
          inet6 addr: fe80::290:96ff:fe8a:e988/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:d0000000-d0002000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16404 (16.0 KiB)  TX bytes:16404 (16.0 KiB)

cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid hiddenssid
wireless-key s:xxxxxxxxxxxxxxxxxxx

 cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
ndiswrapper

---

