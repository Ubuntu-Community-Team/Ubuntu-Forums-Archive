---
title: "wireless disonnections"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by laro on 2007-10-23
Hi

i am using ubuntu 7.10

i have wireless nic card (pci) level one 0301

i can conenct to my wirelss network (linksys) without problem, and my signal strength is very good (87%)

after few minutes, the wirelesss is disconnect and i cant connect again

(in windows i dont have problem at all)

i run iwconfig and ifconfig:

root@amit:/home/amit# iwconfig

lo  no wireless extensions.

eth0 
no wireless extensions.

wmaster0  
no wireless extensions.

wlan0 
IEEE 802.11g  ESSID:"linksys"  
  
Mode:Managed  Frequency:2.452 GHz  Access Point: 00:16:B6:E1:7F:44   
      
Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
   
Link Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  
Invalid misc:0   Missed beacon:0



root@amit:/home/amit# ifconfig

eth0  Link encap:Ethernet  HWaddr 00:1A:4D:93:24:84  

      UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

      RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
  
      inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
      
      RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
      
      collisions:0 txqueuelen:0 
          RX bytes:5094 (4.9 KB)  TX bytes:5094 (4.9 KB)

wlan0     Link encap:Ethernet
      HWaddr 00:11:6B:3C:94:3E  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
       
      inet6 addr: fe80::211:6bff:fe3c:943e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
      RX packets:4377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4193 errors:0 dropped:0 overruns:0 carrier:0
      
     collisions:0 txqueuelen:1000 
          RX bytes:2179449 (2.0 MB)  TX bytes:518706 (506.5 KB)

wmaster0  Link encap:UNSPEC
     HWaddr 00-11-6B-3C-94-3E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
        
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        
     collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@amit:/home/amit# 




when i try to ping to my router i cant reach it

i can restart the computer and connect again (automaticaly) but after few minutes - same problem again

what is the problem ?

---

### Post by Henry Rayker on 2007-10-23
The problem is with Ubuntu (or rather, their wireless drivers). I had this same issue for a while before I just quit Ubuntu altogether... I worked and worked with it, but having to start at square one after each release was just upsetting. I moved to Fedora and never had this issue again...once I got wireless up in Gentoo, it never happens there either....

What kind of card are you using? What drivers does it use? This sort of information will be helpful.

---

### Post by hcorey on 2007-10-23
I am having the same issue (with Gutsy), and it's quite frustrating. I am using a Warpstar Aterm WL11CB LAN card (Hermes). I can connect, but after a few minutes, I am disconnected. I have tried replacing network manager with WICD and commenting out IPV6 in modprobe.d/alias file (someone suggested this might be the problem), with no luck. I would appreciate any help.

---

