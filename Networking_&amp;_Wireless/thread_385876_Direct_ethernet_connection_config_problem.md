---
title: "Direct ethernet connection config problem"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by jeff_p on 2007-03-16
Hello,

I have just replaced an old Win2K fileserver with a brand new Ubuntu box.  It is connected to the internet through my wireless router, and connected to my desktop computer using an ethernet cable (not a crossover).

In Win2k, this setup worked flawlessly.  I had it working under Ubuntu for about five hours, until I restarted the machine.

Here is the command I used to get it working: 
~$ ifconfig eth0 169.254.228.172

After doing that, I was able to ping the machine from my desktop, access files and various servers that I run on there.

After the restart, however, I can't even ping the machine, without accessing it via the wireless connection.  The only thing that works through the direct ethernet connection is SAMBA.  I can guess that this works because SAMBA uses UDP, but things like VNC or Apache use TCP.  

In any case, I can't find out what is going on.  Here is some info:

~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:19:D1:3E:0A:FC  
          inet addr:169.254.228.172  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:d1ff:fe3e:afc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:11732 (11.4 KiB)
          Base address:0x20e0 Memory:50300000-50320000 

Can anyone help me find the problem?

---

### Post by jeff_p on 2007-03-16
Some more info...  The ubuntu machine can ping itself.  Also, SAMBA is running very slowly, but I think that might be an unrelated problem.

---

### Post by admiralawesome on 2007-03-19
I don't exactly have the solution to your problem, but I have a couple of suggestions.

First, you should be using a cross-over ethernet cable (as opposed to a straight-through ethernet cable) to connect two alike devices (computers, in this situation) directly to each other.

Second, the 169.254.x.x address range is used by Windows machines on interfaces that are looking to recieve their IP addresses from a DHCP server, but fail to do so.  By doing so, all the Windows machines that couldn't pull DHCP addresses will, hopefully, be able to connect to each other.  I would try setting a static address on each end of that direct ethernet connection in an address range other than 169.254.x.x.  I don't know what range of addresses your wireless router is giving out, but try 10.0.0.1 on one end, and 10.0.0.2 on the other.  Use a subnet mask of 255.0.0.0 for both.

Again, probably not the solution, but give those a try.

---

