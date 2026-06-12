---
title: "Difficulty connecting to wireless network consistantly"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by fishfreek on 2008-07-16
I have a wifi network with WPA2 personal encryption.  I can connect to the wireless network on a perodic basis only.  Sometimes when I boot up the system it will connect within a few seconds and other times I will need to try to connect multiple times before I eventually get a connection.  Sometimes I even have to go to the network manager and disable the wireless and then enable the wireless before it will connect.  Im using nm-applet 0.6.6 in the GUI to connect to the wifi.

Is there a better application to use for managing wifi/network connections?  I can connect to unsecured connections with no trouble but clearly I don't want to open my home wifi up just to get consistant connections with the laptop.  I know its not my router because I have tried connecting this system to other wpa secured networks and experence the same level of difficulty.

Just incase you want this is the output of ifconfig

wlan1     Link encap:Ethernet  HWaddr 00:90:4b:7d:d8:01  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe7d:d801/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2259332 (2.1 MB)  TX bytes:545785 (532.9 KB)
          Interrupt:5 Memory:fafee000-faff0000 

iwconfig 

wlan1     IEEE 802.11g  ESSID:"Home"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1D:7E:1D:70:0D   
          Bit Rate=48 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by moore.bryan on 2008-07-16
many people find [wicd]("http://wicd.sourceforge.net/") solves their problems; i did.

---

### Post by fishfreek on 2008-07-17
Thanks Ill give that a try tonight.

---

### Post by moore.bryan on 2008-07-17
good luck.

---

