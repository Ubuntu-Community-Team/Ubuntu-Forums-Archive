---
title: "bittorrent doesn't work with wireless card"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by gpap on 2007-06-29
I am using feisty and I recently got an ndiswrapper-compatible usb wireless card. After some irrelevant problems I got it to work. Now everything works fine except for bittorrent. I prefer the BitTornado client but also have Azureus. They both have the same behaviour; they find the peers and seeds but they don't connect to them(and it's not that I'm impatient - they really DON'T connect). Needless to say I have manually disabled the firewall of my router and forwarded the corresponding ports. I have tried reinstalling BitTornado which temporarily half-fixed the problem (I got u/dload speeds ~ 5 Kb/s). Then the problem reappeared. I tried changing the ports but that didn't fix it. Whenever I use the wired LAN connection it all works fine so it can't be the ISP blocking the ports and apart from BT everything else works well (if I download from a friend's ftp server from some random port I download with ~ 600Kb/s). I am with talktalk in the uk , which is not the best provider and I had to change the router's setting for MTU to 1400. I tried setting the MTU value of wlan0 in /etc/network/interfaces to the same value and it didn't make a difference. I don't really know what else to do, any help appreciated. The output of ifconfig is:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:DE:E3:59  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fede:e359/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:7257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4881125 (4.6 MiB)  TX bytes:1231422 (1.1 MiB)

and my router model is Belkin 54g(F5D7230-4).

---

### Post by t4thfavor on 2007-06-29
Borrow a router from someone else that is a bit beefier, and see if it still gives you problems.
I have heard that the wireless on some routers will go down if there is multiple tcp sessions from one nic on the lan due to the router running out of memory, or available sockets.

This was a big problem with the wrt54g a while back.

Note: The same router will work fine wired since there is far less overhead on a wired connection.

---

### Post by stchman on 2007-06-29
> **gpap said:**
> I am using feisty and I recently got an ndiswrapper-compatible usb wireless card. After some irrelevant problems I got it to work. Now everything works fine except for bittorrent. I prefer the BitTornado client but also have Azureus. They both have the same behaviour; they find the peers and seeds but they don't connect to them(and it's not that I'm impatient - they really DON'T connect). Needless to say I have manually disabled the firewall of my router and forwarded the corresponding ports. I have tried reinstalling BitTornado which temporarily half-fixed the problem (I got u/dload speeds ~ 5 Kb/s). Then the problem reappeared. I tried changing the ports but that didn't fix it. Whenever I use the wired LAN connection it all works fine so it can't be the ISP blocking the ports and apart from BT everything else works well (if I download from a friend's ftp server from some random port I download with ~ 600Kb/s). I am with talktalk in the uk , which is not the best provider and I had to change the router's setting for MTU to 1400. I tried setting the MTU value of wlan0 in /etc/network/interfaces to the same value and it didn't make a difference. I don't really know what else to do, any help appreciated. The output of ifconfig is:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:DE:E3:59  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fede:e359/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:7257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4881125 (4.6 MiB)  TX bytes:1231422 (1.1 MiB)

and my router model is Belkin 54g(F5D7230-4).

You need to open up certain port on your router using port forwarding.

[http://www.portforward.com/english/routers/port_forwarding/Belkin/F5D7230-4/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/Belkin/F5D7230-4/Azureus.htm)

This should help.

---

### Post by gpap on 2007-06-29
> **t4thfavor said:**
> Borrow a router from someone else that is a bit beefier, and see if it still gives you problems.
I have heard that the wireless on some routers will go down if there is multiple tcp sessions from one nic on the lan due to the router running out of memory, or available sockets.

This was a big problem with the wrt54g a while back.

Note: The same router will work fine wired since there is far less overhead on a wired connection.

I think that's not the problem. There's some conflict that I don't understand going on between the wireless and the ethernet interface. After system shutdown BitTornado is working properly and "sudo route" gives the following output:

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         .               0.0.0.0         UG    0      0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 eth0

when there's no etheret cable attached. Then after some point it falls to 5-6 Kb/s and if I switch eth0 off ("sudo ifdown eth0") it goes back to not u/dloading (I repeat: NO ETHERNET CABLE attached).

> **stchman said:**
> You need to open up certain port on your router using port forwarding.

[http://www.portforward.com/english/routers/port_forwarding/Belkin/F5D7230-4/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/Belkin/F5D7230-4/Azureus.htm)

This should help.

That's not the problem either. As I said
> **gpap said:**
> I have manually disabled the firewall of my router and forwarded the corresponding ports
I have the correct ports forwarded to my IP and BitTornado is listening to those ports.

If it helps at all, I had to reinstall ndiswrapper using this
[http://ubuntuforums.org/showthread.php?t=483548]("http://ubuntuforums.org/showthread.php?t=483548")
set of instructons. I manually had to enter the mac address of my card in /etc/network/interfaces and that's about all I had to do for it to work fine(-ish).

---

### Post by alejandro.mc on 2007-07-23
GPAP, at last someone shares my pain. Sorry for yours but I was feeling kind of lonely in the world. I live in Buenos Aires, Argentina, and have the exact same problem you have. I have lots of torrents with lots of seeds just waiting for me to connect and because my connection is wireless it wont connect. 

Did you find out how to solve it? Please if you find out anything let me know.

Well good luck to you and to us, lets hope someone comes to us with good news..

---

### Post by gpap on 2007-07-27
> **alejandro.mc said:**
> GPAP, at last someone shares my pain. Sorry for yours but I was feeling kind of lonely in the world. I live in Buenos Aires, Argentina, and have the exact same problem you have. I have lots of torrents with lots of seeds just waiting for me to connect and because my connection is wireless it wont connect. 

Did you find out how to solve it? Please if you find out anything let me know.

Well good luck to you and to us, lets hope someone comes to us with good news..

What I can only say to help is that I switched to a friends more modern router and the problem persisted so I am more inclined to believe it was a software issue. I can no longer play with my machine as I bought a new one and have lent the one with the problem to a friend. I'll post here if he manages to find a workaround.

---

