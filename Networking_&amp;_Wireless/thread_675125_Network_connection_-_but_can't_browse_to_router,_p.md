---
title: "Network connection - but can't browse to router, ping or connect to internet at all!"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by superbungalow on 2008-01-22
Hey, I just installed ubuntu, and on loading it it seems it connects to my network, but when I open firefox, it doesn't want to connect to the internet, instead just looking it up and then saying unable to connect. I am a ubuntu newbie, so you may have to explain things to me in a bit more detail. Thanks!

---

### Post by Dark Hornet on 2008-01-22
If you could please post the output to the following command from a terminal, that may help us to troubleshoot a little easier...

```
ifconfig
```

---

### Post by superbungalow on 2008-01-22
lo             Link encap:Local Loopback
                inet addr:127.0.0.1   Mask:255.0.0.0
                inet6 addr:  ::1/128 Scope:Host
               UP LOOPBACK RUNNING MTU:16436  Metric:1
               RX packets: 823 errors:0 dropped:0 overruns:0 frame:0
               TX packets:823 errors: 0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:0
               RX bytes:110332 (107.7 KB) TX bytes:110332 (107.7 KB)

wlan0      Link encap:Ethernet  HWaddr 00:19:5B:79:7B:6F:
                inet6 addr: fe08::219:5bff:fe79:7b6f/64 Scope:Link
               UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
               RX packets:150 errors:0 dropped:0 overruns:0 frame:0
               TX packets:68 errors: 0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RX bytes:22667 (22.1 KB) TX bytes:8033 (7.7 KB)

wlan0:ava    Link encap:Ethernet  HWaddr 00:19:5B:79:7B:6F:
                     inet addr:169.254.6.82 Bcast: 169.254.255.255 Mask: 255.255.0.0
                     UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-79-7B-6F-00-00-00-00-00-00-00-00-00-00
                   UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
                   RX packets: 823 errors:0 dropped:0 overruns:0 frame:0
               TX packets:823 errors: 0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by Dark Hornet on 2008-01-22
I don't see your eth0 or eth1 interface...how are you connecting to the web...cable, DSL, Fiber, etc?  From your output, you do not have a correctly configured interface.  Usually you will be running DHCP, where your router will assign a private IP address to you...usually a 192.168.x.x, or a 10.x.x.x address.  

For example, my output from ifconfig shows the following:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:C9:1B:EB  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fec9:1beb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28756455 (27.4 MB)  TX bytes:1796782 (1.7 MB)
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10846 (10.5 KB)  TX bytes:10846 (10.5 KB)

notice my eth0 interface has a 192.168.x.x address,,,

---

### Post by superbungalow on 2008-01-22
I'm not quite sure what you mean, but I am connecting on this computer by an ethernet cable plugged directly into the computer, how would I make the other computer run DHCP?

---

### Post by Dark Hornet on 2008-01-22
You are probably already set up to use DHCP...I know you are connecting using an Ethernet cable, but are you at home, or school (college), etc...and if you are home, who provides your internet services?

---

### Post by superbungalow on 2008-01-22
I'm at home, and it's tiscali

---

### Post by Dark Hornet on 2008-01-22
ok..so Tiscali is your ISP...it appears that they provide a modem/router to you, and you are probably receiving a DHCP address from them.  From there, your router is probably assigning...again through DHCP...a private IP address to each of your computers.  Now I use the term probably a lot because I am not familiar with your ISP, etc.  Do you have access to your router..in other words, can you log into it..does Tiscali allow this?  You might want to call them and ask if you are able to log into your router's GUI so you can take a look at things/change things.  One other thing you can try is to set your Network settings to DHCP instead of "Roaming" which is what it is set to by default.  You can find your network settings if you just click on the monitor looking icon on your toolbar, and select "manual configuration"....hope this helps.

---

### Post by superbungalow on 2008-01-23
Hey, I went to my router settings, and it turns out I have DHCP server connected, and it recognises my 2 computers, saying:

```
1  	192.168.1.4  	00:19:5b:79:7b:6f
2 	192.168.1.2 	00:17:ab:53:03:c9
```

The second one, I think is my ubuntu computer.

---

### Post by bwtranch on 2008-01-23
Well, if you can't ping it... that's usually some sort of driver problem. Or more likely, a driver config problem. Try going to System -> Administration -> Network and see what's up there. Click on the connection, that is, Wired Connection and click Properties. See what is there. Should have DCHP enabled. Also, in a terminal type lspci and post that output. Might not be much, but at least we'll know what controller the ethernet is supposed to be using. We might have to delve deeper into the driver thing, but, let's start out with that.
Edit: DHCP, my typing sucks.

---

### Post by Didad on 2008-01-23
I'm watching this thread closely because my ifconfig doesn't show an eth0 either.

---

### Post by Exefurious on 2008-01-24
Same issue here:

I'm trying to connect to an open wireless network at college.  So check this out please...

I am - yes, I am - able to connect to any other wireless network in the city with no problems.  But at college, even though I am connected, receiving an IP address etc, I cannot browse.  I always receive the message that the website cannot be found.

College is the only place this happens, but it's an open wireless network.  I am baffled.

Here is my ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:E0:B8:C5:0C:05  
          inet addr:165.234.58.147  Bcast:165.234.58.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fec5:c05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14606954 (13.9 MB)  TX bytes:1200645 (1.1 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:67:ED:31  
          inet6 addr: fe80::219:d2ff:fe67:ed31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:68 overruns:0 frame:0
          TX packets:6 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2964 (2.8 KB)  TX bytes:19747 (19.2 KB)
          Interrupt:16 Base address:0x2000 Memory:d6000000-d6000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
 

---

