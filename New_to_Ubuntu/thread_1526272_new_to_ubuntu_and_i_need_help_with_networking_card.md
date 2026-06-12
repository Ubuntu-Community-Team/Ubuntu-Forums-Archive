---
title: "new to ubuntu and i need help with networking cards"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by 562sparky562 on 2010-07-07
Hello,

I'm new to ubuntu and i'm not a very knowledgeable about pc's.

I have a acer aspire 3680 laptop that someone asked me to see if i could get working again. 

The laptop originally had windows vista installed in it. 

It would not boot up, I don't have the restore cd's for it and acer does not have restore cd's
for laptops older than 3 years.

I installed ubuntu netbook 10.04 and it looks fantastic but I can't get sound or internet access.

I would like to get the network cards working.  I dont have wired or wireless internet access working
at this time.

I would at least like to have wired internet access because that's what i have on my other computer.

Any help would be greatly appreciated.  =)

---

### Post by 562sparky562 on 2010-07-07
I got this info off my laptop to see if anyone has any suggestions as to what to change

elsa@elsa-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
elsa@elsa-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:35:83:eb  
          inet6 addr: fe80::21b:24ff:fe35:83eb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2835420 (2.8 MB)  TX bytes:16078 (16.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:56:00:80  
          inet6 addr: fe80::219:7eff:fe56:80/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6769 (6.7 KB)  TX bytes:41677 (41.6 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:19:7e:56:00:80  
          inet addr:169.254.5.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---

