---
title: "LAN internet problems"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by JasonCYH on 2008-01-15
I have a v3015AU,and on my laptop  I have vista and Ubuntu 7.10,dual boot.
I have problems using my hostel's internet services(its through LAN,using the ethernet adapter)
in vista,all i do to get online is type in my PC's IP address(given by the administrator)and I'm on the net.
How do I connect to the net in ubuntu in the same manner?

i think,Ubuntu senses my network is present,as in I can see computers attached to the network,my network status icon has no red crossmark on it.

What could be my problem?

asides from that internet issue,I find ubuntu better than vista...everything's just....fast!

---

### Post by carverj on 2008-01-15
> in vista,all i do to get online is type in my PC's IP address(given by the administrator)and I'm on the net.

You manually configure in Vista with ipconfig from the command line?
the equivalent command to find out your ip address in linux is ifconfig
This will give you information on which interfaces are present, and whether
or not an IP address has been automatically assigned.

---

### Post by JasonCYH on 2008-01-16
No ,in vista i just open mange network connections,select my adapter,right click IPv4
and key in my IP address(which the administrator/hostel internet provider gave)press OK and I'm connected to the net.

in Ubuntu,I clicked Network,chose Static IP address and I typed in my IP address:192.168.1.180.this should allow me to get on the net right?or is there anymore steps?

anyhow,when i used ifconfig:
jason@jason:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:A8:15:81  
          inet addr:192.168.1.180  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fea8:1581/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25049 (24.4 KB)  TX bytes:3369 (3.2 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

what should I do now?

---

