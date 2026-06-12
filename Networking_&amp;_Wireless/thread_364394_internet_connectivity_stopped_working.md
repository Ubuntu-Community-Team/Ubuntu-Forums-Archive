---
title: "internet connectivity stopped working"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by ctokar on 2007-02-18
Hello,
This is my situation. My ISP recently gave me a static ip address. Previously, both my xp and kubuntu partitions were able to connect and browse the internet. Now, only XP is able to, not kubuntu.

on XP, which works fine when I ipconfig /all:
-----------------------------------------------------------------------------------------
Windows IP Configuration

Host Name . . . . . . . . . . . . : chris-e92d23733
Primary Dns Suffix . . . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No
DNS Suffix Search List. . . . . . : classcom.pl

Ethernet adapter Wireless Network Connection:

Media State . . . . . . . . . . . : Media disconnected
Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network
Connection
Physical Address. . . . . . . . . : 00-13-CE-C3-EE-F6

Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix . : classcom.pl
Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
Physical Address. . . . . . . . . : 00-14-22-E4-78-57
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 195.150.76.36
Subnet Mask . . . . . . . . . . . : 255.255.255.255
Default Gateway . . . . . . . . . : 172.27.45.1
DHCP Server . . . . . . . . . . . : 192.168.240.254
DNS Servers . . . . . . . . . . . : 172.27.45.1
195.150.77.18
Lease Obtained. . . . . . . . . . : Sunday, February 18, 2007 9:08:12 AM

Lease Expires . . . . . . . . . . : Sunday, February 18, 2007 3:08:12 PM

-----------------------------------------------------------------------------------------

I went into the kubuntu network gui and and tried every possible configuration if manual/dhcp, netmask, gateway to no avail. I cannot ping, but somehow my dns servers are being populated in the gui.

Is there an obvious problem I am missing? Why did windows work right away when my isp flipped the switch to give me the static ip and kubuntu didn't?

ifconfig in kubuntu says:

-------------------------------------------------------------------------------------------

eth0 Link encap:Ethernet HWaddr 00:14:22:E4:78:57
inet addr:195.150.76.36 Bcast:195.150.76.255 Mask:255.255.255.255
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:153 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:20307 (19.8 KiB) TX bytes:0 (0.0 b)
Interrupt:209

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0

---

### Post by lloyd_b on 2007-02-18
Could you run the "route" command in a terminal and post the results?  Also, if you "ping" an address from in a terminal, what error does it display (I'm guessing "network unreachable").

The "ifconfig" output shows that your machine is getting the same IP address in both Linux and XP.  What looks a bit weird is the fact that the IP you're getting is in the 195.150.x.x range, but your default gateway is set to 172.27.45.1.

So what I *think* is happening is that when you try to send a packet (ping, for example), the computer knows that it needs to send it via a gateway at 172.27.45.1, but it doesn't know how to reach the gateway.

Most likely, you just need to add a static route so that Linux knows that the gateway at 172.27.45.1 is reachable via the interface eth0.  In a terminal window, try running the following:
```
sudo route add -net 172.27.45.0 netmask 255.255.255.0 dev eth0
```
and then see if you can ping an internet host.

Lloyd B.

---

### Post by ctokar on 2007-02-18
ok I ran 
sudo route add -net 172.27.45.0 netmask 255.255.255.0 dev eth0
successfully

when i "ping google.com" I get "network unreachable"

when I run "route"
I get this:

Destination    Gateway    Genmask               Flags    Metric   Ref   Use    Iface
172.27.45.0   *               255.255.255.0        U         0          0      0       eth0

any ideas?

---

### Post by lloyd_b on 2007-02-18
> ok I ran
sudo route add -net 172.27.45.0 netmask 255.255.255.0 dev eth0
successfully

when i "ping google.com" I get "network unreachable"

when I run "route"
I get this:

Destination Gateway Genmask Flags Metric Ref Use Iface
172.27.45.0 * 255.255.255.0 U 0 0 0 eth0

There's no default route (i.e. it hasn't been told where the default gateway is:
```
sudo route add default gw 172.27.45.1
```
should take care of it.

Note: you may or may not need that other route.  I was *assuming* that it was correctly setting a default route (which it wasn't), and just needed an extra route.   So try adding the default route in without the other route, and see if it works.  If not, then try adding that other route again.

Lloyd B.

---

### Post by ctokar on 2007-02-18
that works thanks a lot!

---

### Post by nixcraft on 2007-02-18
A better way is to add default route 172.27.45.1 to file /etc/network/interfaces or use GUI network admin. If you are using DHCP iggy this post :)

---

