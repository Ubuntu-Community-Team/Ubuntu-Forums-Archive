---
title: "[SOLVED] Connection Ubuntu Studio + Orange Livebox"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by TimH1980 on 2007-11-28
Hello,

New here on the forum and since monday Ubuntu Studio installed. 

I'm quite a Linux newbee. In the past I installed Suse and Fedora but both the distro's didn't fulfill my needs. (also I don't know anything about commands, I do most of the things graphicaly). 

I'm a common user but I also do audio mixing and producing therefore I wanted to give Ubuntu Studio a chance. Right now I made a dual boot next to XP. So far I'm quite happy, if I can find satisfiable audio apps I want to switch completely. 

Now my question: 

I read many posts about problems with the livebox but I couldn't find my specific problem:

I installed NDISGTK and it can find the usb dongle I have for my wireless connection. It says hardware present. I configured my connection with hex wep key and automatic dhcp settings. 

But it doesn't connect to the internet. 

When I type ifconfig in the terminal it says (I'm at work so I can't copy and paste the exact message before the evening, sorry but maybe it's clear already) 

"Wireless access point invalid" next to some other messages. It seems next to this that it does recognize my usb dongle. 

Can somebody help me out? Thanks in advance!

---

### Post by TimH1980 on 2007-11-29
This is my message if I type iwconfig:

tim@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"livebox-df5d"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any help would be more than welcome. In the meantime I'll keep on looking. 

Thanks in advance!

By the way, this is the output for ifconfig:

tim@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:DC:03:27  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fedc:327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20289024 (19.3 MB)  TX bytes:2155310 (2.0 MB)
          Interrupt:16 Base address:0xaf80 

eth1      Link encap:Ethernet  HWaddr 00:60:B3:0D:0C:1D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:38 dropped:0 overruns:0 frame:38
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3744 (3.6 KB)

eth1:avah Link encap:Ethernet  HWaddr 00:60:B3:0D:0C:1D  
          inet addr:169.254.2.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81571 (79.6 KB)  TX bytes:81571 (79.6 KB)

tim@ubuntu:~$

---

### Post by TimH1980 on 2007-11-29
I'm sorry to bounce this thread again. Looked into many topics but I don't see a way of doing this. Can somebody PLEASE help me?

---

