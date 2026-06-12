---
title: "TCP port is unavailable.. How can I fix?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by hopelessone on 2009-11-09
Hi,

I'm testing my ports on a default 9.10 using amule from repo's my Internet has no modem as it plugs into the wall socket directly..

[http://www.amule.org/testport.php?tcpport=54662](http://www.amule.org/testport.php?tcpport=54662)

Error: TCP port 54662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).

Detailed Error Message
TCP Error 111 Connection refused

Explanation
The port is available for connections but a connection was refused meaning there is nothing listening on that port. This most likely means you can use ED2K but your client is not currently running. Try running this test again with an ED2K client running to make sure you can really establish a connection. No info available; this TCP error probably indicates a problem with the networking on your system (i.e. the TCP/IP stack). 

How can i make them available?

Thanks

---

### Post by lavinog on 2009-11-10
Since you are pluging directly into the wall, it sounds like you don't have control over what ports get forwarded.  Is this a school.  It may be that the provider is blocking that port...can you switch port numbers?

---

### Post by XCan on 2009-11-10
+1 We need to know what kind of connection you have. Most likely you're sharing a fiber connection with some other folks, thus you will have to ask the administrator about ports.

---

### Post by hopelessone on 2009-11-10
Hi,

No School, and not sharing any other computers..(house)

Thanks,

---

### Post by hopelessone on 2009-11-10
Hi,

Nevermind, it's something else stuffing it up...i went to [http://swiss.ubuntuforums.org/showthread.php?t=1151456](http://swiss.ubuntuforums.org/showthread.php?t=1151456)

> go to system>Admin> network tools > Port scan tab

type the IP of the computer whose port you are trying to forward (check the ip by right clicking the network manager applet and go to Connection information), make some popcorn and grab a beer, and watch the show.

A list of open ports related to that IP should come up

and it was open...it's a software glitch...i read before something...somewhere...servers...

anyways..

---

### Post by hopelessone on 2009-11-10
Nope...

its happening now across Deluge and Amule...what could be the problem? 

ISP Provider?

---

### Post by lavinog on 2009-11-10
Are you familiar with ip addresses?
Is your ip address a public or a private address?
Private addresses tend to start with 192.168.###.### or 10.0.###.###

---

### Post by mikewhatever on 2009-11-10
Can you post the output of ifconfig. Also, elaborate a bit on you networking setup.

---

### Post by hopelessone on 2009-11-11
Hi Thanks for helping,

Ip Address -> 192.168.20.3

```
some@one:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:be:ff:a4  
          inet addr:192.168.20.3  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:febe:ffa4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22539277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22460804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26285490542 (26.2 GB)  TX bytes:14819384340 (14.8 GB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2248802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2248802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:444752529 (444.7 MB)  TX bytes:444752529 (444.7 MB)

```

---

### Post by mikewhatever on 2009-11-11
Well. 192.168.x.x means you are on an internal network of some kind, and to forward a port, you'd need access to the configuration utility of that network.

---

### Post by lavinog on 2009-11-11
The problem is called Network Address Translation, or NAT
Even though the port is open, the packets are not directed to go to your machine.
What you need is port forwarding, but only the administrator of the network can do this.

I thought some of the p2p clients had a feature to get around needing a port open.

---

