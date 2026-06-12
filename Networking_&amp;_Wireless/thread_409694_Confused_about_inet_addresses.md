---
title: "Confused about inet addresses"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2007-04-14
Why is the inet address on eth0 different from the local one?
As far as I can tell, 192.168.0.4 is my modem.
What is the 127.0.0.1 being returned below?
I'm using 6.10, FF2.0.0.3, connected by ethernet to a Netgear DG834G modem/router on ADSL.
Cheers

dexter@home-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:FD:04:B3  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17392133 (16.5 MiB)  TX bytes:399423 (390.0 KiB)
          Interrupt:217 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

---

### Post by dbott67 on 2007-04-14
127.0.0.1 is the local loopback address.

> **WikiPedia]A loopback interface has several uses. It may be used by network client software on a computer to communicate with server software on the same computer&#8211 said:**
> web server[/URL], pointing a [web browser]("http://en.wikipedia.org/wiki/Web_browser") at the [URL]("http://en.wikipedia.org/wiki/URL") [http://127.0.0.1/](http://127.0.0.1/) will access that computer's own web site. This can be done without the computer being connected to any network&#8211;so it is useful for testing services without exposing them to remote network access. Likewise, to [ping]("http://en.wikipedia.org/wiki/Ping") the loopback interface is a basic test that one's IP stack is working properly.

All sorts of gory details here:
[http://en.wikipedia.org/wiki/Loopback](http://en.wikipedia.org/wiki/Loopback)


-Dave

---

### Post by BoneKracker on 2007-04-14
The 127.0.0.1 address is an additional ethernet interface that your system uses for programs on your computer to talk to each other.  It's referred to as "local" or "loopback".

Programs that are modular often talk to each other using sockets or other messaging strategies primarily designed for communication on a single computer.  But a lot of modular programs are designed to be "client/server" applications where part of the program might be on another machine.  

Many of those programs have been designed to go ahead and use TCP as a single means of communication, even though it might be talking to the same computer.  To enable this, along with your "eth0" and/or "eth1" interface (or whatever), you also have the "local" interface. 

Just like 192.168.blah.blah is one of several groups of IP addresses that are reserved for "private" networks, 127.blah.blah.blah is reserved for "local" (i.e. intra-system) networking.

So it's basically a way for programs on your computer to talk to each other using internet-style communications without actually sending the messages out over the network.

---

### Post by BoneKracker on 2007-04-14
[Edit] duplicate post

---

### Post by Buster95 on 2007-04-15
Thanks guys

---

