---
title: "help, my rt25xx cant connect, no local ip, and hangs"
date: 2005-08-22
forum: Networking &amp; Wireless
---

### Post by mutejute on 2005-08-22
i was able to make my rt25xx driver work now. ive been trying to configure using the rt2500 driver not knowing my wifi is rt2570. i installed the rt2570 and its ok now. i can see the wireless driver now in the networking applet and was able to configure it. but most of the time, if i activate it under networking applet or thru the bash prompt (sudo ifup rausb0), my system locks up and have to power it off thru the mains. btw, my system detects/reports it as "rausb0" and not wlan0 or ra0.

i added "auto rausb0" in my /etc/network/interfaces and it activated my wifi on startup. it seems the driver is working, if i look at kwifimanager, heres the info it shows:

searching for network: 000d0b3bc0a0
access point 00:00:00:00:00:00
local ip: unavailable
frequency channel: 2.412 [1]

if i click "scan networks...", i can see the SSID of my buffalo airstation wireless router (which is 000d0b3bc0a0).

as you can see, local ip is not set. if i run "dhclient rausb0" (with rt2570 activated), i cant get an IP from the dhcp server (my router). if i run "ifdown rausb0" and then "dhclient rausb0", my system locks up.

here's my /etc/network/interfaces:

auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp

auto eth0

iface rausb0 inet dhcp
wireless-essid 000d0b3bc0a0
wireless-key mypasswordkey

auto rausb0


and here's my /etc/modules:

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
ndiswrapper

please help cause i really want to make it work because my setup is, my router is in the first floor and my pc (this pc) is in my room at the second floor. im connecting my windows XP thru wifi. right now im sitting on the floor next to my router and connected via eth0 so I can configure my wifi in ubuntu (hoary). i brought it down so i can connect my ubuntu linux to the internet via eth0.

btw, my kernel version is 2.6.10-5-386 (thats what it says when i run "uname -r").  many many thanks.

EDIT:

additional info: (ifconfig -a)

eth0      Link encap:Ethernet  HWaddr 00:11:09:BB:11:E9
          inet addr:192.168.11.3  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:febb:11e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:68885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100167068 (95.5 MiB)  TX bytes:2733604 (2.6 MiB)
          Interrupt:18 Base address:0xd300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1179143 (1.1 MiB)  TX bytes:1179143 (1.1 MiB)

rausb0    Link encap:Ethernet  HWaddr 00:11:09:51:4B:AD
          inet6 addr: fe80::211:9ff:fe51:4bad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31310 (30.5 KiB)  TX bytes:342888 (334.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

the last line in rausb0 changes everytime i run ifconfig -a. so that means my rausb0 is working?

thanks again in advance.

---

