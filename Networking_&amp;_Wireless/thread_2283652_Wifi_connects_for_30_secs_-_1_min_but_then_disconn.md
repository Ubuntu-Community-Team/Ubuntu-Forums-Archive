---
title: "Wifi connects for 30 secs - 1 min but then disconnects and firefox doesn't load"
date: 2015-06-23
forum: Networking &amp; Wireless
---

### Post by rob138 on 2015-06-23
I have recently formatted and reinstalled ubuntu 14.04 on my computer hoping to fix a problem I've been having with my wifi. Wifi had been working fine previously but I tried to install open office and the drivers for my printer and they seem to have messed it up. I've read lots of people's posts with a similar problem copying and pasting commands in the terminal but nothing has worked.  I would be very grateful for any help.

Here is ifconfig and iw config info

eth0      Link encap:Ethernet  HWaddr 74:d4:35:d4:77:a8  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fed4:77a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21628899 (21.6 MB)  TX bytes:4518522 (4.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:564766 (564.7 KB)  TX bytes:564766 (564.7 KB)

wlan0     Link encap:Ethernet  HWaddr 30:b5:c2:1d:3b:d1  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::32b5:c2ff:fe1d:3bd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:487379 (487.3 KB)  TX bytes:12464 (12.4 KB)


eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MOVISTAR_A290"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: B2:46:FC:77:A2:90   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0

lo        no wireless extensions.

---

### Post by Pilot6 on 2015-06-23
Please give output of

lspci -knn | grep Net -A2

---

### Post by rob138 on 2015-06-23
it doesn't give any output info: 
rob@rob-H81M-D2V:~$ lspci -knn | grep Net -A2 
rob@rob-H81M-D2V:~$ lspci -knn | grep Net -A2 
rob@rob-H81M-D2V:~$ sudo lspci -knn | grep Net -A2 
rob@rob-H81M-D2V:~$ 


I have attached the wireless-info.tar doc

---

### Post by rob138 on 2015-06-23
[ATTACH]262810[/ATTACH]

---

