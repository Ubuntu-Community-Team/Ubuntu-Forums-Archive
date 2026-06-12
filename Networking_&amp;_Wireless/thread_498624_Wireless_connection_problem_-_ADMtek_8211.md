---
title: "Wireless connection problem - ADMtek 8211"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by radmod90 on 2007-07-11
Sorry to ask the same question asked by many before me but I have only installed and been using Ubuntu for about a week.  I have gone through every tutorial, guide I can find and still am unable to setup wireless intenet connection.  I have been trying on both my desktop and laptop systems, which use different wifi adapters and neither work.  It must be something stupid I am or am not doing. I'm currently using Ubuntu Fesity 7.04 on my laptop.  I have installed ndiswrapper and the driver for my wifi pcmia card.  It is a ADMtek 802.11b wireless card.  The card has a power light but no signal is being received.  I am trying to connect to a Dynamode R-ADSL-C4W-G wireless router

 with 64 bit WEP encryption enabled.



Results of some terminal commands are shown below.



```
ndiswrapper -l



Installed ndis drivers:

netadm11	driver present, hardware present.
```




```
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11b  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11b  ESSID:"HILTON_9M"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1162 (1.1 KiB)  TX bytes:1162 (1.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:03:6D:FF:1A:B7  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:6dff:feff:1ab7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:5773 (5.6 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-03-6D-FF-1A-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
route -n:

Kernel IP routeing table
Destination     Gateway         Genmask         Flags   Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U             0      0        0      wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U            1000   0        0      wlan0   --- PROBLEM ??
0.0.0.0           192.168.1.1     0.0.0.0         UG              0      0        0      wlan0

```


Any help will be GREATLY appreciated.  Any more info needed i will be happy to provide.

I dont have the abiltity to connect via an ethernet cable so i can only access internet from my windows machine.


Thanks,
David

---

