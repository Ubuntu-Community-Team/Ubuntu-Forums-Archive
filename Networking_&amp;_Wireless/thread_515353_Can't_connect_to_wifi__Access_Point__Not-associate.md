---
title: "Can't connect to wifi:  Access Point:  Not-associated"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by spaceywilly on 2007-08-01
Hi, first post.  Just getting started with linux...

I can't seem to connect to my wireless network.  I'm using WEP encryption and I'm trying to connect with my motherboard's integrated wifi, which is a rtl8187 chip and has native drivers.  The router is a linksys wrt54g with dd-wrt firmware.  I've checked and all the settings look right, but it won't associate with my access point.

Here are the outputs of iwconfig and ifconfig.

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"willards"  
          Mode:Managed  Channel=6  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:C12E-CCBE-8C67-5635-94BE-F63E-AE   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F3:00:AC:62  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe00:ac62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:701152 (684.7 KiB)  TX bytes:146336 (142.9 KiB)
          Interrupt:225 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:04:63:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1046 errors:6 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177205 (173.0 KiB)  TX bytes:0 (0.0 b)


Note: eth0 is connected to my windows laptop with internet connection sharing

Here's what I get from iwlist

 iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:27:E0:4F
                    ESSID:"willards"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:15  Signal level:0  Noise level:10
                    Extra: Last beacon: 10ms ago

I tried using ndiswrapper but I couldn't get it to work.  I got it installed but it said to run

rmmod rtl8187

to disable the native driver and I couldn't get that command to work.  Any help with either getting the native driver to work or getting ndiswrapper working is greatly appreciated.

---

### Post by spaceywilly on 2007-08-01
I got this working.  I had to blacklist r8187, not rtl8187.  Once I figure that out I just rebooted and not it's connected :)

---

