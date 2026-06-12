---
title: "new user - no internet connectivity - please help!"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by rearlclay on 2007-08-26
Hello.  I just installed Ubuntu this afternoon and everything looks  good, EXCEPT I seem to have NO internet connectivity.  Please help.  I've looked through this forum but can't seem to find another post that describes quite the same problem.  Output of ifconfig looks as follows below.  I'm hoping that problem is obvious and easily fixed!  Thanks in advance for any help you can give me.
Rod Clay
-------------------------------------------------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:E0:29:82:1E:8A  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe82:1e8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5451 (5.3 KiB)  TX bytes:6405 (6.2 KiB)
          Interrupt:3 Base address:0xdf80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
----------------------------------------------------------------------------------------------------

---

### Post by jhofmann on 2007-08-26
You seem to be connected, as you have an address.  Try pinging the router;
$ ping 192.168.0.1

If that works, you are connected.  Are you sure the router is connected to something?

Jim

---

### Post by rearlclay on 2007-08-26
Jim,
I tried the ping and it worked!  Then I tried Firefox again and now it's working!  Not sure why it wasn't working before.  I tried several times.  Oh well, all's well that ends well.  Thanks for your reply.
Rod

---

