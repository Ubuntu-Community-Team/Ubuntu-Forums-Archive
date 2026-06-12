---
title: "Driver installed but cannot connect to router"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by jackliddle on 2006-08-16
I am using the live CD, I wan't to get the wifi working before I commit.

Installed ndiswrapper-utils and ndisgtk from a usb drive.

Which seems to have worked

ifconfig gives

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27444 (26.8 KiB)  TX bytes:27444 (26.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 02:11:22:33:8D:8F  
          inet6 addr: fe80::11:22ff:fe33:8d8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2178 (2.1 KiB)
          Interrupt:3 Memory:cffb0000-cffc0000 

and iwconfig gives

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:6 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

In the network config tool, it can see my router and gives me its name, so I'm pretty sure that the card is working.

But when I run the network config tool and put in my WEP key, it thinks for about a minute and then stops, seemingly not connected.

Any ideas what I should try next?  Anything else I should post about my system etc..?

Thanks very much 

Jack Liddle

---

### Post by jackliddle on 2006-08-16
Update.  If I disable security on the router.  It works and I can connect to the internet.   (hooray!)

Any idea what I'm doing wrong regarding the WEP key.  I've been searching the forums but haven't had much luck.

---

