---
title: "Problem with Network on Ubuntu 15.10"
date: 2016-07-08
forum: Networking &amp; Wireless
---

### Post by atlarep on 2016-07-08
[LEFT][COLOR=#242729][FONT=Arial]I  recently deployed a VM with Ubuntu 15.10 and I am having trouble  configuring the network properly. Note: When the OS was installed, it  picked up an IP (from DHCP I guess), because it didn't ask me to set up  the network. After installation I could access the server via that IP.  However, I keep trying to add another IP (10.100.144.115) to the server  and the server does not pick it up.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]This is what I have on /etc/network/interfaces:[/FONT][/COLOR][/LEFT]```
root@blah20:/etc/network# cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo ens33
iface lo inet loopback

# The primary network interface – use DHCP to find our address
auto ens33
iface ens33 inet static
address 10.100.144.142
netmask 255.255.255.0
broadcast 10.100.144.255
gateway 10.100.144.1
dns-nameserver 8.8.8.8

# The secondary IP – This one is very important as it hosts the Portal.
auto ens33
iface ens33:0 inet static
address 10.100.144.115
netmask 255.255.255.0
gateway 10.100.144.1
root@blah20:/etc/network#

```

[LEFT][COLOR=#242729][FONT=Arial]When I restart the network, I only get the first IP.[/FONT][/COLOR][/LEFT]```
root@blah20:/etc/network# ifconfig
ens33     Link encap:Ethernet  HWaddr 00:50:56:a4:5e:35
          inet addr:10.100.144.142  Bcast:10.100.144.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fea4:5e35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:482877 errors:2 dropped:2 overruns:0 frame:0
          TX packets:44446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:108341017 (108.3 MB)  TX bytes:14661830 (14.6 MB)
          Interrupt:19 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:170653 (170.6 KB)  TX bytes:170653 (170.6 KB)

root@blah20:/etc/network#

```

[LEFT][COLOR=#242729][FONT=Arial]I  have tried different things but nothing seems to work. Can somebody  tell me what I am doing wrong? I never had this issue with Ubuntu  before.
[/FONT][/COLOR][/LEFT]

---

### Post by mörgæs on 2016-07-09
Hi, welcome to the fora.
Are you sure that you would want to troubleshoot 15.10 which is out of support by end of this month?

---

### Post by Bucky Ball on 2016-07-09
> **mörgæs said:**
> Hi, welcome to the fora.
Are you sure that you would want to troubleshoot 15.10 which is out of support by end of this month?

Welcome. I'll second that. Try 16.04. 15.10 is dead.

Incidentally, 16.04 LTS is an LTS release (long term support) which gives five years support. The interim releases, like 15.10, are supported for nine months.

---

### Post by atlarep on 2016-07-11
> **Bucky Ball said:**
> Welcome. I'll second that. Try 16.04. 15.10 is dead.

Incidentally, 16.04 LTS is an LTS release (long term support) which gives five years support. The interim releases, like 15.10, are supported for nine months.

Thank you guys, but I tried that and I seem to be having the same issue on 16.04 LTS. Can you please help me solve this?

Thanks in advance.

---

