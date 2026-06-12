---
title: "can't add gateway to routes (dapper)"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by silver_shadow on 2007-04-19
so here's the background:
switched to a new ISP. they gave me a modem connected to my NIC. the NIC has a static IP 125.x.x.x/255.255.254.0, gateway 125.x.x.x.

i found i that in ubuntu (6.06 LTS - dapper drake?) i can't use the internet whereas it's fine in xp.

now i just checked using netstat: here's what i got

[B]arjun@arjun-server:~$ netstat -r
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
125.99.238.0 * 255.255.254.0 U 0 0 0 eth0[/B]

my gateway IP which i have supplied using the GUI interface is 125.99.232.1. as you can see it doesn't appear.

so i do

[B]arjun@arjun-server:~$ sudo route add default gw 125.99.232.1 eth0
SIOCADDRT: Network is unreachable[/B]

now why cannot i add the gateway? hopefully after i manage to do this, then there shouldn't be any other reason why ubuntu won't get connected.

---

### Post by spd106 on 2007-04-19
SIOCADDRT: Network is unreachable

This means the gateway address you have provided is not on the same network as the address that's bound to the interface. I suggest that you check the netmask.

---

### Post by silver_shadow on 2007-04-20
> **spd106 said:**
> SIOCADDRT: Network is unreachable

This means the gateway address you have provided is not on the same network as the address that's bound to the interface. I suggest that you check the netmask.

yep, no problem with what i've entered... same stuff the ISP entered in xp... works here. i thought the cable modem can act as a router?

---

### Post by silver_shadow on 2007-04-20
just checked this site:
[http://ip-adress.com/](http://ip-adress.com/)

i found out that this is very much a public IP (i wasn't sure despite the IP range - because i've seen at least 2 companies that were using non private IP ranges within the LAN!)

---

### Post by silver_shadow on 2007-04-21
here's ipconfig's (XP) output:

[B]C:\Documents and Settings\Arjun>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : karnik
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : DAVICOM 9102/A PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-60-6E-2E-00-F6
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 125.99.238.65
        Subnet Mask . . . . . . . . . . . : 255.255.254.0
        Default Gateway . . . . . . . . . : 125.99.232.1
        DNS Servers . . . . . . . . . . . : 202.88.156.6
                                            202.88.130.67[/B]

and ifconfig (ubuntu):


[B]arjun@arjun-server:~$ ifconfig -a

eth0  	Link encap:Ethernet  	HWaddr 00:60:6E:2E:00:F6 
inet addr:125.99.238.65  Bcast:125.99.239.255  Mask:255.255.254.0
inet6 addr: fe80::260:6eff:fe2e:f6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:14156 errors:0 dropped:0 overruns:0 frame:0
TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:857820 (837.7 KiB)  TX bytes:2484 (2.4 KiB)
Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:23 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1780 (1.7 KiB)  TX bytes:1780 (1.7 KiB)

sit0      Link encap:IPv6-in-IPv4
NOARP  MTU:1480  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/B]

---

### Post by spd106 on 2007-04-21
Try a subnet mask of 255.255.248.0 == /21

---

### Post by silver_shadow on 2007-04-22
that worked - weird considering the other netmask works in XP.

---

