---
title: "Cannot connect to internet"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by d525sn on 2008-04-25
I recently dumped Windows and am now using Ubuntu however cannot connect to the internet - it's driving me mad
I'm at university so using a wired internet connection (ethernet) and have tried to adjust all the settings that i can, but to no avail. If anyone has any ideas that would be awesome.
I'm not amazing on computers so if you could explain any tecnical jargon as well that would help...
cheers

---

### Post by schmildo on 2008-04-25
Try opening up a terminal window and typing the command:
. /etc/init.d/networking restart

(remember to include the dot & space at the start)

---

### Post by d525sn on 2008-04-25
Tried it and it just went away (presume it did what it was supposed to do)... but it still doesn't do anything

I've played around with settings and things so will what i just did reset that??

if not is there another way to reset all my medelling??

if not what other settings could i adjust to make it work

cheers

---

### Post by jimny85 on 2008-04-25
Can you open a terminal and run: ifconfig

Then copy and paste the results back here, might make it easier to help.

---

### Post by d525sn on 2008-04-25
Hi, i hope this help, cuz it certainly doesn't mean a whole lot to me...

robin@dermot-reincarnated:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D0:BC:A1  
          inet addr:129.234.180.52  Bcast:129.234.180.255  Mask:255.255.255.0 
          inet6 addr: fe80::212:3fff:fed0:bca1/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:313 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:39533 (38.6 KB)  TX bytes:2272 (2.2 KB) 
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:61:E8:1F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:17 Base address:0x6000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

robin@dermot-reincarnated:~$ 


thanks for your help

---

