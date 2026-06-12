---
title: "Can't get wired connection going"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by fountain_ou on 2008-05-04
I'm a newbie and I just installed 7.1.

I'm using a DHCP network via a router.  I'm not able to get my wired connection going.  

Here's what I get when I ping my router:
"PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
From 192.168.1.3 icmp_seq=1 Destination Host unreachable"

I tried dhclient and I get the following response:
"Listening on LPF /eth0/00:1b:24:a1:2b:f8
sending on LPF /eth0/00:1b:24:a1:2b:f8
sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCP offers received
Trying recorded lease 192.168.1.3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
100% packet loss
No Working leases in persistent database - sleeping"


I don't think it's a connection or cable problem because I'm able to ping the router from windows & in recovery mode.  I have the wired connection set to "DHCP" and it looks like an IP address is assigned during boot-up but for whatever reason I can't connect when the OS completely comes up.  It must be some config file..

Can somebody advise?

Thanks!

---

### Post by superprash2003 on 2008-05-05
could you post your ifconfig output

---

### Post by Iowan on 2008-05-05
I'm not near my Ubuntu machine, so I don't have exact verbage, but...
Do you have the "Roaming" box checked (on manual configuration page) - my machine works better without it.

---

### Post by fountain_ou on 2008-05-05
Here's what I get when I type ifconfig:

eth0     
Liink encap:Ethernet HWaddr 00:1B:24:A1:2B:F8
inet6 addr: fe80::21b:24ff:feal:2bf8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:608 (608.0 b) TX bytes:342 (342.0 b)
Interrupt:16 Base address:0xcc00

eth0:avah
Link encap:Ethernet HWaddr 00:1B:24:A1:2B:F8
inet addr:169.254.7.203 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interupt:16 Base address:0xcc00

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0  txqueuelen:0
RX bytes:704 (704.0 b) TX bytes:704 (704.0 b)

BTW, I do have roaming disabled.  I have it set for manual config, DHCP.

I'm using an ACER 5050, dual booted with Vista.

THanks!!!

---

### Post by superprash2003 on 2008-05-06
you havent setup your eth0 properly.. your ifconfig shows that eth0 isnt getting an ip.. go to system->administration->network.. and go to eth0 properties.. and enter ip address manually.. 192.168.1.3.. and then try

---

### Post by fountain_ou on 2008-05-08
Tried the manual address.  I even updated the windows drivers.

still no luck.  Any new ideas?
Thanks!

---

