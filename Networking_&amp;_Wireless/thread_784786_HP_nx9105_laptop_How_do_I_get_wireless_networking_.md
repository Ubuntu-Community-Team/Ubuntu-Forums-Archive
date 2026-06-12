---
title: "HP nx9105 laptop How do I get wireless networking to work?"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by nrpgeek on 2008-05-06
Just installed Hardy Heron onto this laptop.

How on earth do I get the wireless to work? How do I get it to show me the available networks? There's a button on the corner which allows me to turn wireless on and off, even that doesn't work! Whats happening here?

The installation seems otherwise flawless... flummoxed!!!

---

### Post by superprash2003 on 2008-05-06
if its a broadcom , then this should help you get started with the installation [http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html)

---

### Post by nrpgeek on 2008-05-07
Thanks superprash...

The only problem is, all the methods I've found require a network connection! Neither the wired or wireless connections work.

I had no problems with a wired connection on my desktop gutsy machine.

---

### Post by Ayuthia on 2008-05-07
What kind of wireless do you have (lspci -nn)?

---

### Post by superprash2003 on 2008-05-07
also could you post your ifconfig output

---

### Post by nrpgeek on 2008-05-07
I don't know what type of wireless connection I have.
The ifconfig output is:

> eth0      Link encap:Ethernet  HWaddr 00:0f:b0:3f:b3:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136400 (133.2 KB)  TX bytes:136400 (133.2 KB)

Another problem I have is that all the left click options have gone from the network manager except Manual configuration.

---

### Post by Ayuthia on 2008-05-07
If you go to the terminal and type lspci -nn, it will list out your pci devices.  Look for something that says Ethernet Controller or Network Controller.

---

### Post by superprash2003 on 2008-05-07
try this.. go to system->administration->network and go to wired connection(eth) properties.. then select DHCP and then see if you are getting an ip address in your ifconfig.. if not try entering ip address manually in the same place

---

### Post by nrpgeek on 2008-05-11
Thanks Guys!

Using the help posted here and elsewhere, I first of all managed to get the wired network up & running and then, once networked, got the wireless to work.

This is the forum post which solved the problem...
[Click here for link]("http://ubuntuforums.org/showthread.php?t=766560")

Thanks again guys!

---

