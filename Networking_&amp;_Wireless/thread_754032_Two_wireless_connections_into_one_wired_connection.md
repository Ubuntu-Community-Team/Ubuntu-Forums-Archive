---
title: "Two wireless connections into one wired connection?"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by ksmustng on 2008-04-13
Has anyone been able to pull this off.  I've been trying to make it work for the last couple weeks and have been unsuccessful.  Granted I haven't done anything with linux in many years.  I have tried using bonding to achieve this load balance if you will and can't seem to get it to grab the wireless networks.  Both wireless cards are attached to their respective wireless routers.  I will post my ifconfig and iwconfig here in a minute since I'm not on my Ubuntu machine.

---

### Post by ksmustng on 2008-04-13
ifconfig:
bond0     Link encap:Ethernet  HWaddr 00:03:B3:48:50:2C  
          UP BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

bond0:ava Link encap:Ethernet  HWaddr 00:03:B3:48:50:2C  
          inet addr:169.254.4.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MASTER MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:11:43:20:90:BD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:11:43:20:90:BD  
          inet addr:169.254.6.233  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:3B:0A:1D:4B  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3bff:fe0a:1d4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:563 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2580456 (2.4 MB)  TX bytes:51882 (50.6 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0E:3B:0A:1D:23  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:3bff:fe0a:1d23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71390 errors:0 dropped:30 overruns:30 frame:30
          TX packets:3934 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8631626 (8.2 MB)  TX bytes:561122 (547.9 KB)
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     RT73 WLAN  ESSID:"linksys"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1D:7E:66:C7:92   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=41/100  Signal level:-80 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     RT73 WLAN  ESSID:"belkin54"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:50:F2:B5:EC   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=32/100  Signal level:-86 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bond0     no wireless extensions.

---

### Post by ksmustng on 2008-04-13
Come on now.  Surely there's someone with some insight on this?  :guitar:

---

### Post by Rizla on 2008-05-16
I'm looking for more info on this as well.  I've been doing a lot of searching online, but nothing thats been too definitive.   I wanted to take it a step further and do it with three, but proof of concept on two would help.

---

### Post by ksmustng on 2008-05-16
That's what I want to do as well.  But I would settle for being able to do two.  I was going to try and pull it off with a virtual machine but I haven't had the time to do any testing.  So far all the things I have found out on the web haven't worked.  So I think using ifenslave in a virtual machine might do it.

---

