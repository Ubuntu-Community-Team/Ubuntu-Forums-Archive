---
title: "Wireless Networking Problems on a Fresh Install of 7.10"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Infinitas on 2008-02-21
I'm having some interesting problems with my wireless card. I just got a new Lenovo Thinkpad T61 laptop with an Intel 3945 a/b/g wireless card. The card works on unsecure networks, but is having problems with wireless security. I can get a connection no problem with unsecure networks, but can't connect to my network.

Here are the outputs of some helpful commands.

--------------------------------------------------

```
 sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:86:21:a4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiat
ion
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0
.3-0 ip=192.168.0.178 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:bf:ba:dd:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no
 module=ipw3945 multicast=yes wireless=unassociated
```

----------------------------------------------------------------

 ```
ifconfig


eth0      Link encap:Ethernet  HWaddr 00:1E:37:86:21:A4  
          inet addr:192.168.0.178  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fe86:21a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1836273 (1.7 MB)  TX bytes:149102 (145.6 KB)
          Base address:0x1840 Memory:fe200000-fe220000 

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:BA:DD:F2  
          inet6 addr: fe80::21c:bfff:feba:ddf2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:6357 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57722 (56.3 KB)  TX bytes:98310 (96.0 KB)
          Interrupt:17 Base address:0x8000 Memory:df2ff000-df2fffff 

eth1:avah Link encap:Ethernet  HWaddr 00:1C:BF:BA:DD:F2  
          inet addr:169.254.11.247  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x8000 Memory:df2ff000-df2fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4448 (4.3 KB)  TX bytes:4448 (4.3 KB)

```

----------------------------------------------------------------

```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Infinitas"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:EE:A8:51   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6448   Missed beacon:0
```

---

### Post by Hightide on 2008-02-22
Hi

are you using WEP(not recommended) or WPA?

If its WPA have a look at Weiman's[ tutorial]("http://ubuntuforums.org/showthread.php?t=318539")

regards

:)

---

### Post by Infinitas on 2008-02-22
I followed the HOWTO and I still get the same results. Here are some more of the recommended outputs from the HOWTO. This is very frustrating. I've never had networking problems under Ubuntu before.

```

sudo dhclient eth1


Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1c:bf:ba:dd:f2
Sending on   LPF/eth1/00:1c:bf:ba:dd:f2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

```

 sudo cat /etc/network/interfaces


auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid Infinitas
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 91d36fcb2c0e0b145399180f31e964241be239229eca50287fb6da91f386707b


```

```

sudo route


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1


```

---

### Post by Infinitas on 2008-02-23
I am beginning to wonder if for some reason I have a bad install of Gutsy. I had a problem with my CPU frequency monitor program. I had to chmod the program to get it to work. I didn't have this issue the last time I installed Gutsy on an almost identical Thinkpad laptop. Furthermore, the keys that control the brightness of the screen are not working. This too worked fine on the last install of Gutsy on the similar laptop. These along with the wireless problems I am having make me wonder if there was a problem with installation that would merit a "quick fix" of reinstalling. These are minor problems, but I am having troubles getting them resolved. Any thoughts? Thanks.

Infinitas

---

### Post by Infinitas on 2008-02-24
After some research I found that the default nVidia driver provided by Ubuntu is out dated. Using the Envy tool mentioned on the ThinkWiki website allowed me to update to the latest nVidia driver. This fixed my brightness buttons problem. However, I discovered a new problem. If i press the Fn+F5 button combination, I am supposed to be able to switch on my wireless and bluetooth antennas. This doesn't work either. I had to make a script that would turn bluetooth on and off. I wonder if this has something to do with the wireless card.

Any help is appreciated. Thanks!

Infinitas

---

### Post by Infinitas on 2008-02-26
I have resolved all problems with this install besides my wireless network. I REALLY need to get this resolved. The wireless works just fine in Windows with my WPA settings. Why doesn't it work in Linux?!

Infinitas

---

### Post by arunsub on 2008-02-29
I have the same Intel 3945 card. My wireless was fine until I moved to Gutsy. The problem with Gutsy is, my wireless works fine if I'm close to my wireless router. If I'm little farther away, it won't connect. Windows connects fine anywhere in my house. I didn't have this problem before Gutsy.

---

### Post by Infinitas on 2008-03-03
Well, I'm in the same room as my wireless router. I'm not more than 10 feet away. I'm pretty sure that isn't the problem.

Infinitas

---

### Post by arunsub on 2008-03-03
75% it connects fine if I'm in the same room, but 25% it won't connect even if i'm in the same room. If I move out of the room, then 100% of the time it won't connect.

---

### Post by Infinitas on 2008-06-02
I never did get the problem resolved. After several months of waiting I was finally able to do a fresh install of 8.04. This solved the problem.

Infinitas

---

