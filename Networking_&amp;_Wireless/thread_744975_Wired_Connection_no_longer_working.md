---
title: "Wired Connection no longer working"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by shortiedragon on 2008-04-04
Hello, I installed Linux about a week ago and my internet was working fine.  I recently tried to access some stuff on my external but it wouldn't mount because it was "still in use" and I had to safely remove it in windows.  That didn't work out  well.  So I restarted my computer and then my wired connection stopped working.  I rebooted again an nd this time I got an error message after logging in.  I can't remember exactly what it said, but it was something along the lines of "GNOME Daemon settings were lost and will try to load them again on next start up" or something like that.  Using a Dell Inspiron 1520, not sure what the ethernet card I'm using is, but my wireless is working just fine.  Any ideas?

---

### Post by superprash2003 on 2008-04-04
go to the terminal, type ifconfig and post results here

---

### Post by shortiedragon on 2008-04-04
predrag@Predrag:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:95:25:2B  
          inet6 addr: fe80::21c:23ff:fe95:252b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:586303 (572.5 KB)  TX bytes:26565 (25.9 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1C:26:91:C9:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2580 errors:0 dropped:2032 overruns:0 frame:0
          TX packets:1692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1940169 (1.8 MB)  TX bytes:176932 (172.7 KB)
          Interrupt:10 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1C:23:95:25:2B  
          inet addr:169.254.3.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by superprash2003 on 2008-04-04
read this [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html) .. i think its got to do with ROAMING MODE..

---

