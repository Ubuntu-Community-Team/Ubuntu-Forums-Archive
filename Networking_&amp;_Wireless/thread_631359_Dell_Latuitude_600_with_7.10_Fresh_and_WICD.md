---
title: "Dell Latuitude 600 with 7.10 Fresh and WICD"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by caricc on 2007-12-04
I have a Dell Latitude that I just received to set for a friend with Ubuntu. I have it loaded with 7.10, this is a fresh install since it didn't have an OS when he received it. I was wanting to get WICD setup as the network manager. 

He has 2 different wireless networks that he uses. One at his home and the other at his office. I have setup both networks so I am familiar with the setup at both locations. 

My main question is What is the best way to configure WICD so that both locations can be accessed via wireless. 

Thanks in advance for your assistance and help.

---

### Post by redhatoscar on 2007-12-04
Try this link : setup to locations 

[http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubnet_m/ub_wirless]("http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubnet_m/ub_wirless")

---

### Post by caricc on 2007-12-06
Hey, thanks,,,,,My biggest problem was not having all the updates after loading 7.10, But, I fixed it. Now it shoud be working per you link for nidswrapper. 

Thanks again.

---

### Post by caricc on 2007-12-09
Still not connecting via wireless. here is a showing of my listings:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:c9:0f:c2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5705-v3.16 ip=192.168.1.64 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:4e:fd:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
david@david-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         home            0.0.0.0         UG    100    0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1
david@david-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:C9:0F:C2  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fec9:fc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:378 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:467306 (456.3 KB)  TX bytes:40744 (39.7 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:4E:FD:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000 Memory:fafef000-fafeffff 

eth1:avah Link encap:Ethernet  HWaddr 00:0C:F1:4E:FD:4E  
          inet addr:169.254.8.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x8000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

david@david-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1A:04:F6:68:91
                    ESSID:"CARICK"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:96  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12ms ago
          Cell 02 - Address: 00:19:E4:14:63:41
                    ESSID:"2WIRE569"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:48  Signal level:0  Noise level:0
                    Extra: Last beacon: 892ms ago

any help.

Thanks in advance.

---

