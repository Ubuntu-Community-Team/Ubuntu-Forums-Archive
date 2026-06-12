---
title: "Wireless card detected... but no internet?"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by trdcelica on 2008-03-01
Hey guys,

I had to recently install the Alpha version of Henry to get my sound to work (long story there). But now my internet has stopped working. I can start the computer up, wireless card is detected, I can connect to my network, but thats all it does. I can ping servers with 100% success rate. My modem configuration screens says my laptop is currently offline. 

I am a n00b to linux so please let me know what you need and I can provide it, I have a Toshiba laptop on a Westell verizon modem/router. Everything worked perfectly internet wise before the upgrade. 

Thanks!

---

### Post by trdcelica on 2008-03-01
i ran ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:16:e3:34:97:19  
          inet addr:192.168.1.43  Bcast:255.255.255.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:e3ff:fe34:9719/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1187 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:50766 (49.5 KB)  TX bytes:23608 (23.0 KB) 

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:3f:c3:5e  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:609 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:609 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:86444 (84.4 KB)  TX bytes:86444 (84.4 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-34-97-19-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:75447 errors:0 dropped:0 overruns:0 frame:190135 
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:8508813 (8.1 MB)  TX bytes:45116 (44.0 KB) 
          Interrupt:20

---

### Post by trdcelica on 2008-03-01
my wired connection is just fine... i had to go into the network settings and enable DCHP.

when I try to enable DCHP on my wireless setting it says I do not have the privledge needed to change it?

---

### Post by kaginken on 2008-03-02
what are you using to try and get an IP via DHCP?

Command line?  Network Manager?

If command line, try using 'sudo' in front of the command?

---

### Post by trdcelica on 2008-03-02
It keeps telling me something "You are not allowed to access the system configuration." 

I need to enable DHCP for my wireless..... but how to heck can I when it says I don't have the access? Strange

Edit: Network manager

---

### Post by trdcelica on 2008-03-02
got it... had to put "gksu" infront of a bunch of settings... but it works... case closed, thanks!

---

### Post by kaginken on 2008-03-02
Try this :

[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

and let me know how it goes.  

Hope that helps!

---

### Post by kaginken on 2008-03-02
Awesome!

---

