---
title: "Cannot connect to the internet"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by max_max_mir on 2007-12-27
Hi,

I am a newbie to Ubuntu. I'll get right down to the problem and not waste people's time.

1. I opened Firefox and typed [www.cnn.com](www.cnn.com) (after Ubuntu's installation), but it couldn't connect.
2. I typed ifconfig and here's what I got

eth0

Link encap:Ethernet HWaddr 00:0E:A6:27:55:58
inet6 addr: fe80::20e:a6ff:etc. etc. Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2806 errors:0 dropped:0 overruns:0 frame:0
TX packets: 148 errors etc. all 0
collisions:0 txqueuelen:1000

eth0:avah 

Link encap:Ethernet HWaddr 00:0E:......
inet addr:169.254.4.220 Bcast:169.254.255.255 Mast:255.255.0.0
UP BROADCAST RUNNING MUTICAST MTU:1500 Metric:1
Interrupt:17 Base address:0xa400

My /etc/network/interfaces file has

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

The way I am connected to the internet is as follows

Ubuntu Desktop (ver 7.10) ---> DLink WBR 1310 Router ---> Motorola Cable Modem

on typing ipconfig in windows, this is what I get

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : xxx_domain
   Link-local IPv6 Address . . . . . : fe80::1439:5e26:43c1:ad58%9
   IPv4 Address. . . . . . . . . . . : 192.168.1.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.2

the DHCP server on the router is on and I am connected to the router directly through an ethernet cable (cat5 cable).

What should I do? Any help is appreciated.

---

### Post by Dark Hornet on 2007-12-27
If you will notice...your NIC is not picking up an IP address (the inet addr:169.254.4.220 is not a valid IP address, you want to see a 192.168.x.x address)--are you connecting through a wireless connection?

---

### Post by carverj on 2007-12-28
Perhaps make sure that eth0 is configured for DHCP. not sure what 
eth0:avah means!?

---

### Post by max_max_mir on 2007-12-28
> **Dark Hornet said:**
> If you will notice...your NIC is not picking up an IP address (the inet addr:169.254.4.220 is not a valid IP address, you want to see a 192.168.x.x address)--are you connecting through a wireless connection?


Thanks for replying. I am connecting through a wired connection. Linux Box ----> Router ----> Cable Model - all wired. How do I get my NIC to pick up the IP address? When I check my router, it isn't assigning an IP address to my computer either.

---

### Post by max_max_mir on 2007-12-28
> **carverj said:**
> Perhaps make sure that eth0 is configured for DHCP. not sure what 
eth0:avah means!?

Thanks for the reply. I made sure that the network setting is set to use DHCP (not static IP). Still no success.

---

### Post by Dark Hornet on 2007-12-28
> **max_max_mir said:**
> Thanks for replying. I am connecting through a wired connection. Linux Box ----> Router ----> Cable Model - all wired. How do I get my NIC to pick up the IP address? When I check my router, it isn't assigning an IP address to my computer either.

on your Ubuntu box, try setting your network connections to "roaming"...then reboot your computer, router, and modem.

---

### Post by carverj on 2007-12-28
Yes, roaming, I should look into that one myself. Similar to DHCP is it?

> Thanks for replying. I am connecting through a wired connection. Linux Box ----> Router ----> Cable Model - all wired. How do I get my NIC to pick up the IP address? When I check my router, it isn't assigning an IP address to my computer either.

You said before that it worked in Windows! Is that still happening?

---

