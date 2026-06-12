---
title: "two connections and ip's"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by ayu on 2007-10-14
Hello,

What I would like to do is to do a remote connect to my windows machine via a direct ethernet connection (eth0).  I have successfully done this in the past, with my wireless (eth1) off, by remembering the ip that windows always assigns to my machine when there is no dhcp server (as in the case with just two machines hooked up to each other).
However, now that I am connected to my router through my wireless, I can't seem to establish a connection to my windows machine via eth0. Any suggestions?  Thanks!

ifconfig (with eth0 plugged in):

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX    
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
 
route -n:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

---

### Post by tgalati4 on 2007-10-14
It helps to have both machines on the same subnet:  192.168.1.XX.  Your wireless router may have a built-in firewall that treats all wireless connections as "Outside" the LAN.  You may need to port-forward port 80,22, and a few others to get decent connectivity.

You may have to use:

>sudo ifconfig eth0 down

This forces the on-board, wired ethernet port to go down so that the wireless port becomes the primary connection.

---

### Post by ayu on 2007-10-17
Hi, 

Thanks for the suggestions.  I know it helps for both machines to be on the same subnet, however this is not possible, as far as I know, because the router supplies 192.168.x.x while direct connections in windows default to 169.x.x.x.
I should clarify what I want to do:  I am looking to start a direct connection to my windows machine (100mbps) while maintaining my wireless connection (in practice only 1mbps) to the internet.  Because of the difference in connection speeds I want eth0 to see the windows machine, and keep eth1 so I can remain online.

Thanks!

---

### Post by Synflux on 2007-10-17
Hello,

The 169.254.x.x address is a 'link local' or APIPA address which is an automatic private address Windows assigns when it can't find DHCP. Ubuntu also has a mechanism called Avahi that will hand out one of these addresses which is probably how it used to work before you got involved with the wireless.

It looks like Avahi is either not working or is getting confused. I've never used it myself. So you have two choices:

1) Re-install Avahi. I wouldn't recommend this at all, it's more of a last resort than something that should be relied on.

2) Assign static IPs to both your Windows and Ubuntu boxes for their ethernet connections. This is what I'd recommend.

There are plenty of guides on here for how to set a static IP for your network card. The only thing to watch out for here is to put your wired connections into a separate subnet from your wireless (unless you're going to bridge them but lets keep it simple!).

So your wireless is handing out 192.168.1.0/24 addresses, I'd suggest setting your ubuntu eth0 to 192.168.2.1 and your windows Local Area Connection to 192.168.2.2   and use a subnet mask of 255.255.255.0 on both, don't worry about setting gateways or dns, you don't need them for your scenario.

Hope this helps you. :)

---

### Post by ayu on 2007-10-19
Hi,
Thanks for the tips, especially about Avahi, never knew what it was called.  I've think I've tried setting static ip's before, and it didn't seem to work, but I can always try again.  The thing is, is that my windows machine is currently headless, so I can't risk setting a static ip that is unreachable and then I can never connect again to it.  
Also, when I tried setting a static for eth0 in the past, it seems to kill off my internet connection (eth1).  What should I do to tell Ubuntu to reach the internet via eth1 and not eth0?
Many thanks!

---

### Post by Synflux on 2007-10-20
Hi, you should find that if you just don't set a default gateway for the connection to your Windows box then Ubuntu will realise it's got to go through the wireless to get to the internet.

:)

---

### Post by VHans on 2007-10-20
Hello Ayu,

I have a similar problem: I want to use both my wireless (for Internet) and my Ethernet (for printing large files) at the same time.

But it seems like Network Manager doesn't want me to use both network connections together. It makes a connection to only one of them and not both at the same time.

How can we make NM open both connections together (I suppose that is your question too?). I am curious to know if this is possible at all.

---

