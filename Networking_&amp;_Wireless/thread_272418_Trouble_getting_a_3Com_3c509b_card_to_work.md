---
title: "Trouble getting a 3Com 3c509b card to work"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by hillrunr on 2006-10-06
I'm having some trouble getting my 3Com network card to work with Ubuntu.

I found on the Wiki to add the following line to /etc/modules and did so:
3c509

I found elsewhere to add the following to /etc/network/interfaces and did so:
auto eth0
iface eth0 inet dhcp

I also found elsewhere to run the following commands but it didn't say what to do based on the output:
**sudo dhclient**
(Result: a bunch of "send_packet: Network is down" errors followed by "No DHCPOFFERS received." and "No working leases in persistent database - sleeping."

**sudo ifconfig -a**
(Result: I see the following for eth0)
Link encap:Ethernet  HWaddr 00:10:5A:25:99:45
BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Interrupt:10 Base address:0x230

Rebooted and nothing. ](*,) 

Anyone have any thoughts?

---

### Post by Iowan on 2006-10-06
The  "No DHCPOFFERS received" sounds like no DHCP server is available.
The "send_packet: Network is down" error sounds like nothing is available.

To what is the NIC connected, and with what kind of cable (crossover or straight)?
One other thought: the 3c509b may need to be configured.  There's a (windows/DOS-based) program on 3Com's site to configure the cards.  I have a copy at home somewhere.

---

### Post by hillrunr on 2006-10-06
I did double check that the connection was live. It's connected to a DSL router with a straight cable to the router. I actually booted up my laptop with the Live CD and had no trouble when I simply unplugged from the desktop and into the laptop. My connection was automatically set up and established. Given this, I think (correct me if I'm wrong) that it has to be something about this card and how it's communicating with the PC/OS.

Unfortunately, my PC was so fried with Windows that I actually removed all signs of Windows and DOS even before looking into Ubuntu. Is there any way to configure the card with no signs of Windows/DOS on the machine? Actually, I can try to browse around for configuration utilities for this card and answer my own question.

---

### Post by Iowan on 2006-10-10
IIRC, the file is a **.exe** that extracts onto a bootable floppy - but that means a DOS environment (or WINE?) [http://support.3com.com/infodeli/tools/nic/3c509b.htm]("http://support.3com.com/infodeli/tools/nic/3c509b.htm")
Here's a starting point.

---

### Post by mips on 2006-10-10
tried booting with  acpi=off  ?

---

