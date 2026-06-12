---
title: "Wired Network Device not managed"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by rajibhasan11 on 2011-05-08
Hello all,

I have installed Ubuntu 11.04 in a separate drive with my Windows XP. It installed perfectly but whenever I run the Ubuntu, the wired network showed disconnected. Then I manually configured my IP address and proxy settings. But the problem remains. The network icon shows 'device not managed'. I should mention I am a novice at Linux. I have searched for solutions in the internet but couldn't really help me. 
If i type **ifconfig** in the terminal the following message appears

ifconfig
eth0      Link encap:Ethernet  HWaddr 70:71:bc:62:ad:fd  
          inet6 addr: fe80::7271:bcff:fe62:adfd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2446 (2.4 KB)  TX bytes:10827 (10.8 KB)
          Interrupt:43 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 70:71:bc:62:ad:fd  
          inet addr:169.254.11.181  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1998 (1.9 KB)  TX bytes:1998 (1.9 KB)

And when I run firefox, a message appears

The proxy server is refusing connections
       
          Firefox is configured to use a proxy server that is refusing connections.
     
Check the proxy settings to make sure that they are correct.
Contact your network administrator to make sure the proxy server is
working.


Without internet connection, I cant really move further. Your help will be highly appreciated.

Thank you.

---

