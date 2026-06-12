---
title: "Wired connection suddenly stopped working"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Sylar_7 on 2008-06-05
I've been using 8.04 since it came out with no problem.  About 2 days ago my internet connection stopped working.  It works in Windows, but not in Ubuntu or the liveCD.

I've tried manualy configuring, uninstalling the network manager and reinstalling it, reinstalling ubuntu, disabling ipv6, and just about anything I could find in posts with simmilar problems.  

Any ideas on what could be causing this?  I dont think it's hardware/mac because it works fine in windows, but I don't see how it could be software since I reinstalled the os and it still doesn't work...

Thanks

---

### Post by superprash2003 on 2008-06-05
could you post ifconfig output from terminal

---

### Post by Kinnza on 2008-06-05
did you try disabling roaming mode ? that one worked for me

---

### Post by Sylar_7 on 2008-06-05
I've tried turning off roaming and that didn't work.

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:13:d3:02:ec:30  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21 Base address:0xdf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:460 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:24408 (23.8 KB)  TX bytes:24408 (23.8 KB)

---

### Post by Farull on 2008-06-05
My wired connection also stopped working after installing updates on June-03. Luckily, my wireless connection still works.

The interface is up, but it has trouble getting a DHCP address. Once it does, it can communicate somewhat but with about 90% packet-loss.

These packages was installed that day:

gnome-about_1%3a2.22.2-0ubuntu3_i386.deb
gnome-desktop-data_1%3a2.22.2-0ubuntu3_all.deb
libgnome-desktop-2_1%3a2.22.2-0ubuntu3_i386.deb
linux-libc-dev_2.6.24-18.32_i386.deb
linux-restricted-modules-common_2.6.24.13-18.41_all.deb
linux-source-2.6.24_2.6.24-18.32_all.deb
pm-utils_0.99.2-3ubuntu10_all.deb
xulrunner-1.9-gnome-support_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb

xulrunner-1.9_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb

My uneducated guess is that there could be a regression in linux-restriced-modules-common. But it wasn't fixed in the following update installed today (2.6.24.13-19.42).

Strange...

---

### Post by superprash2003 on 2008-06-05
have you tried static or dhcp mode?

---

### Post by Sylar_7 on 2008-06-05
> **superprash2003 said:**
> have you tried static or dhcp mode?

yes, both

---

