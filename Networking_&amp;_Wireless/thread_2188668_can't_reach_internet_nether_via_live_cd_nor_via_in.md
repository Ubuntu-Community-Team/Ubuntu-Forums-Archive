---
title: "can't reach internet nether via live cd nor via installation"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by ksuourgos on 2013-11-18
Hello everybody ):P. First of all I have very little experience with computers and none with ubuntu. I have an old machine and my problem is what I have written in the title of this thread.My connection is wired. I am not trying to establish a wireless connection. It must be a hardware issue of **_my_** pc because using the same connection and the same live cd but with a borrowed laptop I **_can_** reach the internet. The live cd contains lubuntu 13.04 I searched for help at the absolute's beginner's forum but was adviced to start a new thread in this forum.

if I open the terminal and type **ifconfig** I get this:

eth0 Link encap:Ethernet HWaddr 00:30:05:62:68:6f 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::230:5ff:fe62:686f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:34 errors:0 dropped:0 overruns:0 frame:0
TX packets:42 errors:6 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:4528 (4.5 KB) TX bytes:3972 (3.9 KB)

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:300 errors:0 dropped:0 overruns:0 frame:0
TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:24082 (24.0 KB) TX bytes:24082 (24.0 KB)

if I type **lspci -v** I get this:

00:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
Subsystem: Fujitsu Technology Solutions Scenic N300 ADMtek AN983 10/100 Mbps PCI Adapter
Flags: bus master, medium devsel, latency 64, IRQ 19
I/O ports at 1800 [size=256]
Memory at d4005000 (32-bit, non-prefetchable) [size=1K]
[virtual] Expansion ROM at 20020000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: tulip

I copypasted only the paragraph about the network adapter. Does anyone have any ideas about what I should do in order to be able to reach the web via **_my_** machine? Thank you in advance.

---

### Post by TheFu on 2013-11-18
You've provided almost everything we need to determine the root cause already. THANK YOU!  I think it is a network configuration issue, NOT drivers or hardware, at this point.

Lets do just a little more troubleshooting to determine the exact issue. If you can please [run the commands]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking") in this blog post.  I suspect it is really just a DNS issue. Those commands will nail that down.

---

### Post by ksuourgos on 2013-11-19
Hello @TheFu ):P Thank you very much for your reply and for your willingness to help me. Credits go to @The Cog who instructed me what to include in my first post. He was helping me out at the absolute beginner's forum for this same problem and adviced me to continue searching for help here.

[B]ping the router
[/B]I am not sure I know what my router's IP address is. Is it perhaps 192.168.1.1? If I type ping 192.168.1.1 this is what I get:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
...

it doesn't stop here. icmp_seq can reach to 1000 before I stop it.

[B]ping 8.8.8.8
[/B]( I get the same resuts as before)

I aso tried this, in case this is my router's IP
[B]ping 192.168.1.2
[/B](First 10 lines,again it does not stop)
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_req=1 ttl=64 time=0.041 ms
64 bytes from 192.168.1.2: icmp_req=2 ttl=64 time=0.044 ms
64 bytes from 192.168.1.2: icmp_req=3 ttl=64 time=0.082 ms
64 bytes from 192.168.1.2: icmp_req=4 ttl=64 time=0.074 ms
64 bytes from 192.168.1.2: icmp_req=5 ttl=64 time=0.040 ms
64 bytes from 192.168.1.2: icmp_req=6 ttl=64 time=0.043 ms
64 bytes from 192.168.1.2: icmp_req=7 ttl=64 time=0.044 ms
64 bytes from 192.168.1.2: icmp_req=8 ttl=64 time=0.042 ms
64 bytes from 192.168.1.2: icmp_req=9 ttl=64 time=0.042 ms
64 bytes from 192.168.1.2: icmp_req=10 ttl=64 time=0.023 ms
....

[B]ping google.com
[/B]ping: unknown host google.com

[B]dmesg |grep eth[0-9]
[/B][ 1.434661] net eth0: ADMtek Comet rev 17 at Port 0x1800, 00:30:05:62:68:6f, IRQ 19
[ 10.495217] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 17.633715] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[ 17.633729] net eth0: Setting full-duplex based on MII#1 link partner capability of 41e1
[ 34.816035] NETDEV WATCHDOG: eth0 (tulip): transmit queue 0 timed out
[ 34.817594] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 42.817388] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 50.817391] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 58.817391] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 66.817390] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 74.817401] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 82.817396] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 90.817393] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 98.817390] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 106.817390] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 114.817393] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 122.817389] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 130.817389] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 138.817395] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 146.817395] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 154.817395] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 162.817393] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 170.817393] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 178.817390] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 186.817389] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 194.817392] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 202.817386] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 210.817389] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 218.817390] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 226.817396] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 234.817389] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 242.817389] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 250.817393] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 258.817392] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)
[ 266.817390] tulip 0000:00:06.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc07c057 CSR6 0xff970111)

[B]sudo lshw -C network
[/B]*-network 
description: Ethernet interface
product: NC100 Network Everywhere Fast Ethernet 10/100
vendor: ADMtek
physical id: 6
bus info: pci@0000:00:06.0
logical name: eth0
version: 11
serial: 00:30:05:62:68:6f
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.2 latency=64 maxlatency=128 mingnt=64 multicast=yes
resources: irq:19 ioport:1800(size=256) memory:d4005000-d40053ff memory:20020000-2003ffff

[B]ifconfig -a
[/B]eth0 Link encap:Ethernet HWaddr 00:30:05:62:68:6f 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::230:5ff:fe62:686f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:25 errors:0 dropped:315 overruns:0 frame:0
TX packets:32 errors:224 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:3718 (3.7 KB) TX bytes:3092 (3.0 KB)
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:2027 errors:0 dropped:0 overruns:0 frame:0
TX packets:2027 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:199161 (199.1 KB) TX bytes:199161 (199.1 KB)

[B]more /etc/resolv.conf
[/B]# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
# DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search zte.com.cn

[B]route
[/B]Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
192.168.1.0 * 255.255.255.0 U 1 0 0 eth0

---

### Post by TheFu on 2013-11-19
Does your network have a router or not?  
Is the machine directly connected to the internet?

From what I see above, it appears there is a break in the connection between your PC (192.168.1.2) and the router (192.168.1.1).

That could be a bad router port, bad cable, or misconfigured router. I am not seeing anything "funny" on the ubuntu side of the configuration. This assumes that 192.168.1.2 is a valid IP on the subnet provided by the router. If it isn't, then all bets are off.

Is the PC network DHCP or static?  Any idea where the 192.168.1.2 came from?

To simplify things, disabling ipv6 might be helpful too. Do that by adding "blacklist ipv6" to the /etc/modprobe.d/blacklist.conf file. Just follow the other examples and reboot after.

---

### Post by sioxs on 2013-11-19
Hi saw your post and wanted to throw in a suggestion.
I've run into this many times usually when setting up or running different computers through the same router with different MAC addresses.
The lease time for DHCP is one possability to eliminate.
Try rebooting the router and connecting again - ensuring the dhcp cashe is cleared to allow new assignments of ip addresses
From your output this could very well be all there is to your problems.
If this fix works and you run into it again perhaps you might want to assign a fixed ip address to your machine from the router.

BTW: to stop ping from going on just issue the -c switch and a numeric value (for the number of pings you want)
eg: ```
ping  -c3 some-ip-address or some-hostname
```
peace!
sioxs

---

### Post by ksuourgos on 2013-11-19
My network has a router and the machine is connected to the router. I am using the same router with another machine succesfully. I have tried other ports for my machine but nothing changes. Other cable as well. Still nothing changes. I rebooted the router and I see that now my machine is 192.168.1.3 Does this gives us any information?
When I give the command **gksudo gedit /etc/modprobe.d/blackist.conf** a window pops up asking for my password in order to perform administrative tasks, I give my password but nothing happens. Isn't this the right command to give in order to add "blacklist ipv6" ?
I cannot find gedit in Synaptic Package Manager. Should'n it be there? If I run lubuntu from live-cd in the borrowed machine I can find gedit in Synaptic Pachage Manager,install it from there and it opens when I give the command **gksudo gedit /etc/modprobe.d/blackist.conf**  
From the borrowed machine which has windows xp as an operating system, if I reach **advanced Internet Protocol (TCP/IP) Properties** and select **IP Settings** what I see is **Acivated DHCP**. Does this clarify anything?

---

### Post by ksuourgos on 2013-11-21
[COLOR=#000000]This problem was finally solved by installing an ethernet pci card and using [/COLOR]**it **&#8203;instead of the on board card my machine had. I followed advice given to me by @The Cog. I have some other problems now however. No sound and trouble when visiting youtube. Will start a new thread. I hope I can find a way to solve these as well.

---

