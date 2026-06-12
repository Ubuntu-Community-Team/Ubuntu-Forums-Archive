---
title: "[SOLVED] messed up connection to my cable ISP, please help."
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by brjoon1021 on 2008-11-14
Ubuntu 8.04
I have a buffalo wireless router and I use Linux based "dd-wrt" firmware in it. I upgraded to a newer firmware recently and on the very next reboot of my PC, some strange problems started, Since then:
 
 
A. **My desktop**:
 
1. [COLOR=red]Wired[/COLOR]- very, very, slow with Ubuntu or PClinuxOS directly wired to the router.
2. I can't access the router's web based administration page from my desktop at all.
3. **** With both Linux distros I deleted the network connection to the cable ISP, rebooted the modem and router, then re-established the network connection and had ....blazing fast internet UNTIL I rebooted, then it was back to the same broken / slow connection again with both distros ?!?!?!?. So, the NIC is not broken. It has something to do with Linux / the NIC talking to the router... beyond me, though....
 
B. **My laptop**:
 
1. [COLOR=red]Wireless[/COLOR]- works great with both windows XP and PCLinuxOS
2. [COLOR=red]Wired[/COLOR] to the router- works great with both XP and PCLinuxOS
3. I have to use my laptop, either wired or wireless to access the router's web based admin page.
 
 
 
I posted at the dd-wrt forum and pretty much got no help. Even though the firmware is essentially Linux, no one could help, and anyway, the problem does not seem to be the router/firmware as the laptop works beautifully. I have rebooted the computer, cable modem, router, dozens of times, by the way so that is not the problem.
 
Please help, I am frustrated and stumped.
 
B.

---

### Post by jonobr on 2008-11-14
hello

from a termina could you post your ifconfig on the wired connection?

from your terminal could you also do w3m google.com
see how long that takes (hit q to quit)

how quick was the info back from google vs doing a regular browser?

---

### Post by brjoon1021 on 2008-11-17
here is the ifconfig:

	 	 th0      Link encap:Ethernet  HWaddr 00:19:66:59:44:7c   
           inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::219:66ff:fe59:447c/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:922 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:416 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:203107 (198.3 KB)  TX bytes:49758 (48.5 KB)  
           Interrupt:20 Base address:0x6800  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:2472 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:2472 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:123600 (120.7 KB)  TX bytes:123600 (120.7 KB)

---

### Post by brjoon1021 on 2008-11-17
still not solved.

---

