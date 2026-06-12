---
title: "Wireless Network Problems"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-04-04
I switched over from Ubuntu to Kubuntu. I had my wireless working until I tried to set the static IP....and now I seemed to have screwed up something. I can get the wired to work (I am writing this via the wired) but I cannot seem to get the wireless to work any more....any suggestions would be appreciated - also, I could not seem to set the static IP in the Network Manager (I was able to do it very easily in Ubuntu)



eth0      Link encap:Ethernet  HWaddr 00:12:3f:10:d2:75  
          inet addr:10.1.1.5  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe10:d275/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:272646 errors:40 dropped:0 overruns:0 frame:40
          TX packets:154514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:397936720 (397.9 MB)  TX bytes:11665954 (11.6 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:95:49:5b  
          inet6 addr: fe80::212:f0ff:fe95:495b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:3687 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84 (84.0 B)
          Interrupt:17 Base address:0xc000 Memory:dfbff000-dfbfffff 

eth1:avahi Link encap:Ethernet  HWaddr 00:12:f0:95:49:5b  
          inet addr:169.254.6.157  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xc000 Memory:dfbff000-dfbfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12634005 (12.6 MB)  TX bytes:12634005 (12.6 MB)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by hyper_ch on 2009-04-05
I never liked the network managers as they never really worked as I wanted so I use now WICD for managing my network. If you're not in need of roaming then you might have a look at it.

---

### Post by dunbrokin on 2009-04-05
Solved.....user error :(

---

