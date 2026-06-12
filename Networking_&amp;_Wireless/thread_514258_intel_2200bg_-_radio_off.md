---
title: "intel 2200bg - radio off"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by mtb12 on 2007-07-31
I have problems wirh my wireless connection, using intel 2200bg

*sudo iwconfig:*
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



*sudo ifconfig*
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:57:30:B0  
          inet addr:81.191.76.10  Bcast:81.191.79.255  Mask:255.255.248.0
          inet6 addr: fe80::20a:e4ff:fe57:30b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13948440 (13.3 MiB)  TX bytes:1047679 (1023.1 KiB)
          Interrupt:10 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:48:C4:FB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000 Memory:d0202000-d0202fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

Please help, i'm a newbie!

---

### Post by t4thfavor on 2007-07-31
What kind of laptop do you have, It will possibly have a hardware killswitch. It will be the same as what it was while running windows. 

You will have to get the drivers for your specific laptop, or reboot into windows(if possible) and turn the wireless on. This usually means that the wireless was turned off when you last booted windows.

---

