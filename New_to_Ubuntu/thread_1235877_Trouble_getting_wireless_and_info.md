---
title: "Trouble getting wireless and info"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Icielost on 2009-08-09
When I did my first post I couldn't get the wireless option.Then i learned that I had to enable the Broadcom STA driver. The wireless option was restored on Network Manager options.Now its just a matter of getting it to connect to the internet. I want to reset the wireless network and such. I see many helpers here request the information and the card and the driver.I can not seem to access that info though. I got the following with common commands I found around the forum and got the following:

icie@icie:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:ca:3d:d3  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:feca:3dd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5137770 (4.8 MB)  TX bytes:759637 (741.8 KB)
          Interrupt:220 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:1e:3b:65  
          inet6 addr: fe80::223:8ff:fe1e:3b65/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:4370
          TX packets:111 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13447 (13.1 KB)  TX bytes:16095 (15.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:173948 (169.8 KB)  TX bytes:173948 (169.8 KB)

icie@icie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:195  Noise level:169
          Rx invalid nwid:0  invalid crypt:91  invalid misc:0

icie@icie:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

I have no idea what all this means. I dont want to dwnload anything else to the laptop until i know its going to help mye get wireless. Thanks in advance.

---

### Post by sam_delta on 2009-08-09
to get your nentwork card post the output of ```
 lspci | grep Network
```

also, the output of the following commands would be useful
```
iwconfig
```
```
sudo iwlist scann
```

thanks
Sam

---

