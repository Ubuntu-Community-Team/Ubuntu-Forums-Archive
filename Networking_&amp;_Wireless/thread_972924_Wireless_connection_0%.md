---
title: "Wireless connection 0%"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by lado on 2008-11-06
Please help me! 

I have the exactly same problem as described here by another user.. 
Hardy heron, Intel Corp PRO/wireless 2200BG Network. 
Someone have any ideas?

"When I click on the network icon in the upper right, I can see the network that I want to connect to and a bar that I assume is the broadcast signal strength. I click on it and it prompts me for the WEP hex. I enter it and it says "Wireless connection to '[my network's name]' 0%" when I hover over the bar signal icon which looks empty. It acts the same if I enter a bunch of random letters and numbers in the WEP hex field. Point is, I can't get any signal from this network. I'm not even sure if it is even trying to connect. In the drop down under the network icon, it shows my wired connection and the wireless connection with the little select bubble filled in indicating that it is connected. Still, when I unplug my ethernet, no internet."

here is my info from the terminal:

lado@lado-laptop2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2304 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lado@lado-laptop2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:a0:da:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171916 (167.8 KB)  TX bytes:171916 (167.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:35:9d:5d:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Memory:d0202000-d0203000 

lado@lado-laptop2:~$

---

### Post by superprash2003 on 2008-11-06
is the wifi router really far off.. could be a simple signal problem..

---

### Post by lado on 2008-11-07
I have good signal from my router befor i hit connect... and anyway it works fine in XP. 
I bet the problem is somewhere else... 
I now got wicd manager. When i hit connect, he try to connect for a few second, then it just says disconnected.. 

Someone had a similar problem?? please help!

---

