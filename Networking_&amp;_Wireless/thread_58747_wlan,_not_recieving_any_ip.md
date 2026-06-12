---
title: "wlan, not recieving any ip??"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by hamil on 2005-08-21
Hello, I have tried to solve my problem the last days, without finding any solution. Hope that someone here can help me?? 

The Problem:
I bought a NetGear WG311 Wireless PCI adapter, that I belived would work on the wireless network in my appartment.
After installing it in my computer, and booting it up, it shows in "Networking" as wlan0. Without me doing anything with it.
I tried to configure it in the console with this commands:
```
sudo ifconfig wlan0 up
```

```
sudo iwconfig wlan0 channel 6 (wich is the right channel)
sudo iwlist scan
My network now showed up with all the information about essid (Etasje 3) 
and the acess point (00:0F:3D:DF:EB:AA) 
```

I then issued these commands:
```
sudo iwconfig wlan0 essid "Etasje 3"
sudo iwconfig wlan0 ap 00:0F:3D:DF:EB:AA
sudo iwconfig key 1234567890
sudo dhclient wlan0 
```

This last command, only issues this error code:
lars@kullen:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:80:b6:d9
Sending on   LPF/wlan0/00:0f:b5:80:b6:d9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

From other forum threads, and from searching th solution on the net, I am told that I should try this for many minutes, but after 3 days, I still can not get it to work.
My level of experience is not able to connect me to internet in Ubuntu, so I sure hope that someone else is able to inform/educate me in this area..??

I have also tried to issue the key code in this format:
```
sudo iwconfig wlan0 key restricted 1234567890 
```

Without any luck....

Some information about my computer:
Its an AMD 64, running on Ubuntu 5.04 i386 (For time being on a dual doot...)
The Wireless card is an: NetGear WG311, Wireless PCI adapter, recognised in Ubuntu as an "Texas Instruments ACX111 54Mbps Wireless"
My ethernet card is disabled, left unconfigured
My ifconfig gives this output:

```
lars@kullen:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:342322 (334.2 KiB)  TX bytes:342322 (334.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:80:B6:D9
          inet6 addr: fe80::20f:b5ff:fe80:b6d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:14094 (13.7 KiB)
          Interrupt:10
 
```


Looking forward to hear from you all!
Brgds
Lasse

---

### Post by xfs on 2005-08-22
Having exacly the same problem with my DWL-G520+, it's the same chip: ACX111.
Having tryed ndiswrapper too, but it also dont work...

---

