---
title: "Gateway not being automatically detected"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by mwcinc on 2006-09-18
Hi,
I have a Suse Linux 10.1 Server running Samba and DHCP.  My Windows XP workstations all connect to the server and receive their IP addresses and the Gateway address, allowing them to connect to the Internet.
My laptop computer which uses Ubuntu 6.06 and connects to the same DHCP server, needs the following commands to be typed each time I reboot;

route add 192.168.1.1 dev eth0
route add default gw 192.168.1.1 dev eth0

My question is why do I need to type this in Ubuntu when the Windows workstations automatically get it from the same DHCP server?  When I travel and need roaming (e.g. Wifi access at the airport) I will not know what the Gateway IP address of the WiFi hotspot will be, and this will be a major problem.  How do I get around this?

Any help is appreciated.

Regards,

M.W.

---

### Post by tbonius on 2006-09-18
Does the interface have a static router already configured?

/etc/network/interfaces

What does this show ?

Also.. check netstat -rn

The gateway doesnt show up here.  Try clearing the leases file and reboot.

T

---

### Post by mwcinc on 2006-09-18
/etc/network/interfaces shows :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid MWCINC

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


netstat -rn shows:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH        0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.15.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet1
172.16.170.0    0.0.0.0         255.255.255.0   U         0 0          0 vmnet8
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

The vmnet1 and vmnet8 are VMware adapters.  There is a wireless adapter at eth1 and a wired adapter at eth0.

The leases were renewed after rebooting, but it still required typing the route commands.

Thanks for your prompt reply.

---

