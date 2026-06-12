---
title: "Wifi icon lit, wireless enabled, no wireless networks detected"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by hobs on 2008-07-08
My wireless used to work before I did a clean install of Hardy.  I have a Broadcom wireless card (Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)) and I installed the firmware for it by using the Hardware Drivers Manager.  

The wifi icon on my Dell Vostro is lit and when I click on the network icon, wireless is enabled but no networks are found. I know that at least 3 should be listed and that there are no problems with these networks.

I've browsed the forums, tried [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560), but I can't find a solution to my problem.  

What am I missing?

Thanks for your help!

---

### Post by abhilashkumar on 2008-07-08
Try adding the essid and other settings manually. I had to do it once with my wifi.

---

### Post by hobs on 2008-07-08
I just tried with that two networks and I could not connect to either.

---

### Post by hobs on 2008-07-08
iwconfig spits out:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig spits out:
eth0      Link encap:Ethernet  HWaddr 00:1c:23:84:0d:c9  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe84:dc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65934408 (62.8 MB)  TX bytes:2855506 (2.7 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18300 (17.8 KB)  TX bytes:18300 (17.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:1a:15:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-26-1A-15-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

