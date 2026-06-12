---
title: "Can see my network but can´t connect"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Bino on 2007-09-17
I installed Ubuntu 7.04 last week and I have been tampering with it. However, one thing I failed to get fully operational was going wireless. I can see my network on the statusbar at the top and if I want to connect it asks me for the WEP key. I then see the connecting icon where the bottom green light lights up, however, at the end I don´t get a connection and I get asked again for the WEP key. I already checked on our router and the key I enter is correct. 

I also already disabled WEP encryption and SSI but still couldn´t connect. The router is running MAC filtering on my laptop but when I look at ifconfig it is the right address.

I also had a look at IWLIST SCAN
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:BF:35:D4:EA
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-68 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 2844ms ago
```

IFCONFIG
```

eth0      Link encap:Ethernet  HWaddr 00:13:A9:85:2D:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:19:D2:49:D2:0E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:354 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000 Memory:cc000000-cc000fff 

eth0:avah Link encap:Ethernet  HWaddr 00:13:A9:85:2D:65  
          inet addr:169.254.5.162  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)
```


lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:49:d2:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
       resources: iomemory:cc000000-cc000fff irq:18
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0a:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:85:2d:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:d2005000-d2005fff ioport:6000-603f irq:22
```

I also noticed I had the following driver in the restricted drivers screen:
Intel(R) PRO/Wireless 3945 Network Connection driver for linux

In windows I had a look for my driver as indicated in threads before and found the following file: BCMWL6.SYS

As you can see, I tried quite a lot however did not have any succes at getting the wireless to work.

Therefor any help is greatly appreciated.

---

### Post by skycrawler on 2007-09-17
Would be interesting to take a look at the packets.
Use ethereal to capture packets at the interface and paste them here.

---

