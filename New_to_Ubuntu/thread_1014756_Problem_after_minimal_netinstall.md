---
title: "Problem after minimal netinstall"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Asem on 2008-12-18
Hello  everyone 

I installed ubuntu 8.10 netinstall through unetbootin and everything went fine when i was in the step of selecting packages i didnt choose any thing because i got a backup of apt cache so i continue with the minimal installation then after reboot i put the cach on its place and installed the meta package ubuntu-desktop 
so the problem is that after rebooting i noticed 2 things the volume muted ( not an issue ) and the networking applet show a network disabled  so i right clicked it and choosed edit connections and added a wired connection with automatic connecting checked but still ther is no networking 
i noticed that if i start firefox from the terminal i can connect normally so i dont know where is the problem 

can you guide me please to solve this  so i dont have to start everything from terminal?

by the way the output of the ifconfig command is this

eth0      Link encap:Ethernet  HWaddr 00:15:f2:78:dd:56  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe78:dd56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2319879 (2.3 MB)  TX bytes:177118 (177.1 KB)
          Interrupt:19 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

Have a nice day

---

