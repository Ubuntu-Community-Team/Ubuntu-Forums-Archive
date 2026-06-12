---
title: "Problem with ip configuration"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by mowvich on 2008-10-15
Hi everyone,

I'm new here, i have several problems with my ip & just did a deep search into the forum but couldn't find an answer.

I'm running Ubuntu server 8.04 (x86 64bit) on Macbook pro through VM fusion, i configured with the instructions at [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

**Problem 1:**

I'm trying to change my dhcp to static ip but everytime my internet connection drops.

- My /etc/network/interfaces output is:

```
auto eth0
iface eth0 inet dhcp
address 192.168.1.34
netmask 255.255.255.0
gateway 192.168.1.1

```

-My ifconfig output (on dhcp) is:

```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:e2:f4:eb  
          inet addr:172.16.138.137  Bcast:172.16.138.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee2:f4eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2384556 (2.2 MB)  TX bytes:349712 (341.5 KB)
          Base address:0x2040 Memory:e8920000-e8940000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55657 (54.3 KB)  TX bytes:55657 (54.3 KB)

```

-My ifconfig output (on static) is:

```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:e2:f4:eb  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee2:f4eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3318573 (3.1 MB)  TX bytes:486887 (475.4 KB)
          Base address:0x2040 Memory:e8920000-e8940000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64936 (63.4 KB)  TX bytes:64936 (63.4 KB)

```

**2nd problem:**

i tried to change my ip to static on the router (Zyxel) web config page but i totally lost connection, now i can't even access the router config page neither by 192.168.1.1 nor by my web ip .

**3rd problem:**

As you can see from my /etc/network/interfaces the ip is 192.168.1.34 but i can't access my domain through this but through 172.16.138.137, what i'm missing here??

**4th problem**

I can access my server via 172.16.138.137 from firefox on ubuntu & all browsers on Os x on my computer but my friends can't access it from other location, they say page doesn't load!!

i would appreciate any help

---

### Post by superprash2003 on 2008-10-15
what connection are you running?? cable or DSL??

---

### Post by Iowan on 2008-10-15
**Problem 1:**> **mowvich said:**
> auto eth0
iface eth0 inet [COLOR="Red"]dhcp[/COLOR]
address 192.168.1.34
netmask 255.255.255.0
gateway 192.168.1.1
 For static configuration, this should be "static" [B]
Problem 2:[/B] Did you change your client address - or the router's address? 
**Problem 3:** See Problem 2 - dhclient may be overwriting your assigned values.
**Problem 4:** Your router will need to port-forward to your server - gotta get addressing issues fixed, first.

---

### Post by Viruk on 2008-10-16
Make sure you set appropriate values for your addresses, I have taken a guess based on the addresses you list. The main problem I can see is that you have stated that the interface will be dhcp then you have tried to assign a static IP.

Your interfaces file should look something like the following. 

auto eth0
iface eth0 inet static
	address		192.168.1.34
	netmask		255.255.255.0
	network		192.168.1.0
	broadcast	192.168.1.255
	gateway		192.168.1.1

---

