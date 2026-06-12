---
title: "wireless discrepancy iwl3945"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by idoisler on 2008-05-10
my wireless doesn't work , i tried all everything i saw here 

when i type lshw -C network 
it tells me my interference is   logical name: wmaster0
and my driver is  iwl3945

when i type ifconfig

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:85:51:24  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30824385 (29.3 MB)  TX bytes:33006487 (31.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7590 (7.4 KB)  TX bytes:7590 (7.4 KB)


and when i type iwconfig

i get :

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


so what is going on is my interference wmaster0 or eth1 ?
how can i get my wireless to work ???

---

### Post by chili555 on 2008-05-10
First, you can ignore wmaster0. It's an additional interface created by iwl3945 that we needn't worry about for now.

Network Manager, which is installed by default, will not allow a wireless connection if you have a good, working IP address with an ethernet connection, which you do:> eth0 Link encap:Ethernet HWaddr 00:a0:d1:85:51:24
inet addr:192.168.1.2So, please detach the wire and reboot. Can you now configure wireless?

---

### Post by idoisler on 2008-05-10
No it's not working 
I'm using Wicd , under preferences the wpa supplicant driver is wext
and the wireless interface is eth1 
i dont know if that is the way it should be or not 

i tried disconnecting the wire and booting but it keeps saying 
no wireless network found

---

