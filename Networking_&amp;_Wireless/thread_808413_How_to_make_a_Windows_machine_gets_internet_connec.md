---
title: "How to make a Windows machine gets internet connection from an ubuntu one"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by tsonev on 2008-05-26
Hello, 
 Sorry if there are posts about this problem, but I am very tired of it.I have Ubuntu 7.10 on my PC, which is connected to the internet with static ip address and my home made has a laptop with Windows XP. So the problemis that the laptop can not connect to internet. this are the results of if config command on my computer: 

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:0F:4F:42  
          inet addr:87.120.229.215  Bcast:87.120.231.255  Mask:255.255.252.0
          inet6 addr: fe80::20a:e6ff:fe0f:4f42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4021042 (3.8 MB)  TX bytes:1102352 (1.0 MB)
          Interrupt:20 Base address:0xee00 

eth1      Link encap:Ethernet  HWaddr 00:08:A1:37:A2:A2  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe37:a2a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:609450 (595.1 KB)  TX bytes:95768 (93.5 KB)
          Interrupt:19 Base address:0xcf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



 So I see the laptop at mshome and still it has no connection to the internet. Please help me! Thank you in advance.

---

### Post by superprash2003 on 2008-05-26
have you already configured the internet connection sharing part?

---

### Post by hariprs on 2008-05-26
1) Enable forwarding in Ubuntu
2) Assign a IP for your windows PC in same subnet as your eth1 in Ubuntu.
3) Give ubuntu's eth1 IP as windows PCs default gateway.
4) Now try ping Ubuntu's eth1 IP.
5) If it works then you should be able to browse the internet in Windows.

---

### Post by tsonev on 2008-05-27
Well, I don't know how to make the forwarding. I saw some examples in the forums, but they were for DHCP and i have static ip address. I will be very thankful if someone could send me link with an example.

---

### Post by superprash2003 on 2008-05-27
read this [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by tsonev on 2008-05-27
Thank you hariprs and superprash the link was very helpful. It took me some time to realise how to save the changes, but now it's alright and it works after reboot.
 Thanx again!

---

