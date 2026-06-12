---
title: "ADSL pppoeconf problems doesn't find any AC"
date: 2005-08-19
forum: Networking &amp; Wireless
---

### Post by itatabitovski on 2005-08-19
I can't configure my ADSL connection

I have Ubuntu horay installed, and when i do pppoeconf eth1(this is my nic eth0 is my wireless) i get a message that no Access Concentrator was found.

any ideas?
thanks

---

### Post by eywu on 2005-08-30
I recently installed Ubuntu Horay too and encounter the same problem.

I am have experience with Linux and networking. Could someone explain to me what's Access Concentrator? How do I setup ADSL in Linux?

---

### Post by eywu on 2005-08-30
I have been looking around on the forums. There is little I could understand.

So far I have tried the Networking tool under the Administration folder and pppeoconf, but they didn't give me much information on what went wrong or what's not working.

Can someone give me some suggestions on what configurations I need to look at to find out what went wrong?

The best I can do is using ifconfig which prints out the following:

eth0      Link encap:Ethernet  HWaddr 00:11:43:7A:57:2E  
          inet addr:192.168.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe7a:572e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15027 (14.6 KiB)  TX bytes:12954 (12.6 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 Base address:0xa000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141790 (138.4 KiB)  TX bytes:141790 (138.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Any help is much appreciated

---

### Post by dean79 on 2005-09-08
hi,
   i had the same problem. it ended up being the modems fault, it was set for a static web address rather than dhcp.

   check your user guide for your modem and look for something about establishing communication or configure manually.

   i'm using a zoom x4 model 5551 modem, this is what it told me to do...

   open your web browser (even though it's not connected to the internet), and enter [http://10.0.0.2](http://10.0.0.2) into the address bar.
   this will take you to a screen where it will ask for your user name and password (these are supplied in the modems manual and are not the ones for your isp).

e.g. username:admin
       password:zoomadsl

   this then took me to a screen where i could change the mode from static to automatic, after saving the changes it automaticly searched for my isp and asked me for my username and password (for my isp) after entering them i was connected. i didn't have to use pppoeconf after that.

   i hope this helps as it's took me a week to get mine working and i was getting very frustrated with my lack of linux knowhow (first os since xp). anyway sorry for waffling on, good luck.

---

