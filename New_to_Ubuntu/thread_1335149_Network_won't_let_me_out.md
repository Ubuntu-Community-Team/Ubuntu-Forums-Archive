---
title: "Network won't let me out"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by texpat on 2009-11-23
I'm trying to test Ubuntu on my office PC, which means I'm running it off a live CD to see whether it'll behave as expected.

I'm having trouble getting into the Internet. I edit the network settings and set the following:

Manual IP
IP-address
Network mask
Gateway
DNS server(s)

It confirms that it can connect to the network, and I can ping the gateway. But that's it. It won't let me 'out'. What am I missing?

The machine normally runs XP and connects to the net without so much as a hiccup.

I appreciate any hints.

Tex

---

### Post by ukripper on 2009-11-23
post your ifconfig:
```
ifconfig
```

---

### Post by Cheesemill on 2009-11-23
If you're in a corporate environment then chances are that your company blocks all direct internet traffic and has XP set up to use a proxy server so that they can control what you can access.

Either check your proxy server settings in XP and apply them to Ubuntu or check with your IT department.

PS - Everywhere I have worked in IT support it has been against company policy to run any software not specifically allowed by the IT department. It's worth checking if they will let you use Ubuntu as failure to ask could result in losing your job.

---

### Post by texpat on 2009-11-23
Hi all and thanks for picking up this thread so quickly.

ukripper:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:7d:9d:d9:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:50:70:44:0b:fe  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:70ff:fe44:bfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6466 (6.4 KB)  TX bytes:6587 (6.5 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:940 (940.0 B)  TX bytes:940 (940.0 B)

Cheesemill:

I'm not in that kind of corporate environment. This is basically a 3-5 wo/man show, depending on who you count in as employees. IT-support? Whats that??? ;-)

---

### Post by ukripper on 2009-11-23
Can you try disabling ipv6 in firefox, this is temperory only:

1. Type about:config in your address entry bar (in firefox)
2. Type "ipv6" in the filter
3. Change the value of "network.dns.disableIPv6" to true

Now see if you can surf with firefox. We will go from there.

---

### Post by texpat on 2009-11-23
Tried the Firefox settings. Still no fun.

Please bear in mind that I have to boot Ubuntu from CD, do whatever is needed, and then boot back into XP to report the outcome. This means im _slow_ (...sorry).

Btw: It says I'm using Karmic under my avatar pic, but that's at home. I'm using a Jaunty live CD for the problem at hand (just in case it makes a difference).

Tex

---

### Post by ukripper on 2009-11-23
in that case can you post output of following:
```
sudo lshw -C network
```

```
cat /etc/network/interfaces
```

```
ping -c 10 ubuntu.com
```

---

### Post by texpat on 2009-11-24
OK..

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:e0:7d:9d:d9:f8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:16 ioport:d000(size=256) memory:ea000000-ea0000ff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 74
       serial: 00:50:70:44:0b:fe
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.6 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:e800(size=256) memory:ea002000-ea0020ff

```

```
ubuntu@ubuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

```
ubuntu@ubuntu:~$ ping -c 10 ubuntu.com
ping: unknown host ubuntu.com

```

Tex

---

### Post by The Cog on 2009-11-24
This tells us that your ethernet is working fine and has been allocated an IP address. Good so far:
> eth1 Link encap:Ethernet HWaddr 00:50:70:44:0b:fe
inet addr:192.168.0.6 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::250:70ff:fe44:bfe/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:73 errors:0 dropped:0 overruns:0 frame:0
TX packets:45 errors:0 dropped:0 overruns:0 carrier:0

Firstly, lets see if the default route is there: Can you post the output of **route -n**
You should see a route to 0.0.0.0 via your default gateway.

Secondly, lets see if you can get out to the internet by IP address. Try:
**ping 91.189.94.186**
If this works then your default gateway and al the routing is OK.

Next lets see if name lookups work as well. Try:
**ping ubuntuforums.com**
If this fails then you have a name resolution problem. Double-check the file /etc/resolv.conf - it should have at least one line like
**nameserver 1.2.3.4**
but of course givig the address of your name server instead of 1.2.3.4.

Lets see how far you get with that lot. Post results if any step doesn't work. Don't bother trying to disable IPv6 - that's a red herring.

---

### Post by texpat on 2009-11-25
@The Cog:

Cheers! It turned out to be a name server problem. Had the wrong addresses. And yes, I know what I deserve for that. *OUCH* See, kicking myself already ;)

Thanks to everyone who helped!

Tex

---

