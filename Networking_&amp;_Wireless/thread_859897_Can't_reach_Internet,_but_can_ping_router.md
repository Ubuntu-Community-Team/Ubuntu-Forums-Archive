---
title: "Can't reach Internet, but can ping router"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by eli007 on 2008-07-15
Hi,

I am running XP, and using IE6 but can't get/open an Internet site, i.e. Google, even though I can succcessfully loopback my adapter 127.0.0.1, and can successfully ping my router (192.168.1.1).  Also from ipconfig I see the dns, ip, subnet, and gateway all look good. 

I've spent a lot of time (so far two long evenings) flushing using the "netsh" commands thinging some stack must be corrupted but that hasn't helped.  I I also checked the obvious, no ip conflicts with other pc's sharing the connection, and can acccess the internet with other pc's sharing the same connection.

Any ideas?  Thanks.  Eli

---

### Post by superprash2003 on 2008-07-15
in your terminal type ping google.com and post output..

---

### Post by Loukisgr on 2008-07-15
first of all do you have internet??? Secondly try to use staic ip's in your pc. eg 192.168.1.2 with default gateway and dns 192.168.1.1 and open your routers web interface to see if you are connected to internet. if you are with cmd write tracert [www.pathfinder.gr](www.pathfinder.gr) and see not only id the dns works but also where your packets are going.

---

### Post by eli007 on 2008-07-15
I am connected to the internet, this is the response from the ping and tracert

C:\>ping google.com
Ping request could not find host google.com. Please check the name and try again
.
C:\>ping google.com
Ping request could not find host google.com. Please check the name and try again

C:\>tracert [www.pathfinder.gr](www.pathfinder.gr)
Unable to resolve target system name [www.pathfinder.gr](www.pathfinder.gr).

The other pc in my home has no trouble reaching the internet this is the output  
C:\tracert google.com
Tracing route to google.com [64.233.167.99]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.1.1
  2     5 ms     4 ms     4 ms  98.113.142.1
  3    37 ms    36 ms    43 ms  py-in-f99.google.com [64.233.167.99]

Trace complete.

What do you think? I'm very reluctant to reinstall the OS, thanks for responding.

---

### Post by linux6994 on 2008-07-15
You should not have to reinstall the OS. Please verify your dns and gw ip settings. Sounds like the dns is not set. Point everything to your router and it will do the work.

---

### Post by eli007 on 2008-07-15
I did that earlier, pointed the DNS to the same IP as the gateway but that hasn't helped.  I ran ipconfig, but now the dns seems incomplete, what do you think?

C:\Documents and Settings\HP_Owner>ipconfig
Windows IP Configuration
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

---

### Post by superprash2003 on 2008-07-19
does your connection require any dialing??

---

### Post by chili555 on 2008-07-19
> I am running XP, and using IE6This is a forum for Ubuntu, a version of the Linux operating system. I'm not sure you can get much help here.

---

