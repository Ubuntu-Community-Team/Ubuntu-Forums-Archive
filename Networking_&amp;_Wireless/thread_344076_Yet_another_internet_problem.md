---
title: "Yet another internet problem"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by old fogie on 2007-01-22
Hi
I'm another Ubuntu (6.06) newbie with the "unable to connect" woes. I've been watching the threads and trying each suggestion given, but so far have been unsuccessful.

I have an Acer Aspire with an Athlon 64+, 51Mb RAM, 160 Mb HD. The machine is running Windows XP.  I connect to a D-Link DI-624 Air Plus Xtreme router (DI firmware: 4.00). The router is connected by an ethernet cable to a wireless receiver on a post outside. I get my feed from about 5k away. (I'm in the country and cannot get any other highspeed connection other than satellite.)I'm not sure what to call the connection - cable? DSL? 

Win XP has no trouble with this connection, and I've had good service.

I've included the results of my  investigations so far:

pinging: I can't ping the router, let alone anything past that:

ping 192.168.0.1 connect: Network is unavailable

ifconfig
eth0 
Link encap:Ethernet HWaddr 00:15:58:39:EB:CF
inet6 addr: fe80::215:58ff:fe39:ebcf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:16436 Metric:1
RX packets:563 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:25836 (25.24 KiB) TX bytes:0 (0 KiB)
Interrupt:209 Base address:0xc2000

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:21 errors:0 dropped:0 overruns:0 frame:0
TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:6432 (6.2 KiB) TX bytes:6432 (6.2 KiB


lspci | grep controller
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (r a2)
0000:00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (r. a2)

dhclient eth0
Internet Systems Consortium DHCP client V 3.0.3
can't create/var/lib/dhcp3/dhclient. Leases  Permission denied
can't create/var/run/dh client.pid: Permission denied
drop-priveleges: could not set groupid: operation not permitted

pppoeconf
command not found

ifconfig eth0 up
SIOCSIFFLAGS: Prermission denied

dhcpcd eth0 up
dhcpcd eth0 up command not found

lwlist scan
lo   Interface doesn't support scanning
eth0   Interface doesn't support scanning
sit0    Interface doesn't support scanning

I'm not sure what to do about the permissions problems. Any ideas?

---

### Post by spd106 on 2007-01-22
Linux requires root privileges for some tasks, similar to the administrator account on windows. 

On Ubuntu the root account is disabled, instead you prefix the command you want to run with "sudo", then you are asked to enter your password.

It looks like your eth0 interface has not grabbed an IP address, are you sure that the router has a dhcp server? 
If so try **sudo dhclient eth0**.

---

