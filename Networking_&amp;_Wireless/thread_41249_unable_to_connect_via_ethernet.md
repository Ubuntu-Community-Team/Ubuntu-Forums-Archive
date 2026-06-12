---
title: "unable to connect via ethernet"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by geofff on 2005-06-12
I am upgrading to broadband -  via a wired ethernet connection to a cable modem. 

The new connection was first set up with a windows machine (that I'm on now!) and then the ethernet cable swapped to the linux. This machine doesn't connect.

I have deleted all dial up connections from network settings, and now just have eth0. 

I was unable to activate eth0 via dhcp and had to do it manually. When tested the IP address, 192.168.1.2 pings, the gateway 192.168.1.1 doesn't. (interestingly for me at least when the two are reversed the IP still pings and the gateway doesn't - I don't know whether this is significant?)

When I originally set up the dial-up I had a lot of trouble with slow speeds and tried all sorts to speed it up - eventually succeeding with modem lights. I wonder whether something I've done is now conflicting with the ethernet connection. 

I've looked for inspiration on the forum and have done ifconfigs etc. I can post these if they would be any use. However I'm still very new so please keep any advice simple!

TIA 
Geoff

---

### Post by defkewl on 2005-06-12
Yes I think you need to show us your ifconfig here

---

### Post by geofff on 2005-06-13
My ifconfig (typed out)

eth0   Link encap:Ethernet HWaddr 00:11:2F:11:E5:08
          inet addr:192:168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fell:e508/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1386 (1.3 KiB)
          Interrupt:169 Base address:0xe800


lo        Link encap:Local  Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:1699 errors:0 dropped:0 overruns:0 frame:0
           TX packets:1699 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
           RX bytes:236898 (231.3 KiB)  TX bytes:236898 (231.3 KiB)

Thanks for the help. I've been waiting two months for a hoary cd to upgrade but its not arrived so I was intending to do it once I was on broadband. Now I'm on nothing! Help therefore very very welcome!

Geoff

---

### Post by geofff on 2005-06-13
Problem now resolved! I have just fitted a router to join our three machines. When I first attached the linux box it failed to connect to the web as expected. I then changed properties within network settings to dhcp and expected it to fail to activate as happened before. However the box remained ticked and I am now connected!

It would be interesting to know why it works now and wouldn't before but it's no longer critical.  

defkewl - thanks for your support. Appreciated

Geoff

---

