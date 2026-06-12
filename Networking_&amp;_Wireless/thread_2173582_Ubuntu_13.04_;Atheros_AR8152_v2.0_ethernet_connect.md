---
title: "Ubuntu 13.04 ;Atheros AR8152 v2.0 ethernet connected, no web access"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by d-lhoest-y on 2013-09-10
Hello, 

My wireless works fine, my ethernet connects but later, no internet connection. 
I have tried to change ipv6 to link-local then ignore, no luck
I have tried to play the MTU card, no luck
I reinstalled the network drivers from source, ditto
...

Here are some terminal outputs that I hope will help 
```
ifconfigeth0      Link encap:Ethernet  HWaddr 84:8f:69:ba:9e:32  
          inet6 addr: fe80::868f:69ff:feba:9e32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78638 errors:0 dropped:20387 overruns:20387 frame:20387
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:5991942 (5.9 MB)  TX bytes:37808 (37.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:66553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7276565 (7.2 MB)  TX bytes:7276565 (7.2 MB)


wlan0     Link encap:Ethernet  HWaddr 4c:80:93:3b:2f:36  
          inet addr:172.20.11.30  Bcast:172.20.11.255  Mask:255.255.252.0
          inet6 addr: fe80::4e80:93ff:fe3b:2f36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:215767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113272679 (113.2 MB)  TX bytes:191564513 (191.5 MB)



```

```
sudo lshw -C network  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 4c:80:93:3b:2f:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-30-generic firmware=18.168.6.1 ip=172.20.11.30 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:f0600000-f0601fff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: 84:8f:69:ba:9e:32
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:50 memory:f0400000-f043ffff ioport:2000(size=128)



```

```
lspci00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)



```

```
traceroute6 www.google.betraceroute: unknown host www.google.be



```

Something that might be interesting, on Wifi : 

```
ping 172.16.150.1PING 172.16.150.1 (172.16.150.1) 56(84) bytes of data.
64 bytes from 172.16.150.1: icmp_req=1 ttl=254 time=28.8 ms
64 bytes from 172.16.150.1: icmp_req=2 ttl=254 time=11.0 ms
64 bytes from 172.16.150.1: icmp_req=3 ttl=254 time=27.0 ms
64 bytes from 172.16.150.1: icmp_req=4 ttl=254 time=2.96 ms
64 bytes from 172.16.150.1: icmp_req=5 ttl=254 time=5.12 ms
64 bytes from 172.16.150.1: icmp_req=6 ttl=254 time=10.7 ms
64 bytes from 172.16.150.1: icmp_req=7 ttl=254 time=11.9 ms
64 bytes from 172.16.150.1: icmp_req=8 ttl=254 time=14.9 ms
64 bytes from 172.16.150.1: icmp_req=9 ttl=254 time=4.97 ms
64 bytes from 172.16.150.1: icmp_req=10 ttl=254 time=8.46 ms
64 bytes from 172.16.150.1: icmp_req=11 ttl=254 time=10.4 ms
64 bytes from 172.16.150.1: icmp_req=12 ttl=254 time=1.82 ms
64 bytes from 172.16.150.1: icmp_req=13 ttl=254 time=4.44 ms
64 bytes from 172.16.150.1: icmp_req=14 ttl=254 time=1.92 ms
64 bytes from 172.16.150.1: icmp_req=15 ttl=254 time=5.49 ms
64 bytes from 172.16.150.1: icmp_req=16 ttl=254 time=9.88 ms
64 bytes from 172.16.150.1: icmp_req=17 ttl=254 time=6.31 ms
^C
--- 172.16.150.1 ping statistics ---
17 packets transmitted, 17 received, 0% packet loss, time 16023ms
rtt min/avg/max/mdev = 1.820/9.783/28.852/7.560 ms



```

On cable : 

```
ping 172.16.150.1PING 172.16.150.1 (172.16.150.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 172.16.150.1 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 6999ms



```

---

### Post by d-lhoest-y on 2013-09-10
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.150.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.16.150.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
172.20.8.0      0.0.0.0         255.255.252.0   U     9      0        0 wlan0



```

EDIT : bad typo

---

### Post by chili555 on 2013-09-10
With the wireless switched off, what is the result of:```
sudo ufw status
```If it is enabled, temporarily do:```
sudo ufw disable
```See if you can click the Network Manager icon and connect with ethernet. If so, does it ping?```
ping -c3 www.google.com
```Reference for chili: [http://ubuntuforums.org/showthread.php?t=1801151](http://ubuntuforums.org/showthread.php?t=1801151)

---

### Post by d-lhoest-y on 2013-09-10
Master (yes, I believe I've followed all the post on the question, and basically, you were in every single one. Hence, the title), here are the outputs : 

```
sudo ufw status
Status: inactive
```

```
ping -c3 www.google.com
ping: unknown host www.google.com
```

Basically, ethernet is connected, no problem there...

---

### Post by chili555 on 2013-09-10
Thank for your kind words.> Basically, ethernet is connected,Still with wireless switched off, let me see:```
ifconfig
nm-tool
dmesg | grep -e atl1 -e eth0
```In Network Manager, I suggest IPv6 be set to ignore as you are not getting an IPv6 address. I assume either the ISP or the equipment isn't yet ready.> inet6 addr: fe80::868f:69ff:feba:9e32/64fe80 is a dummy placeholder address.

My favorite kind of problem; everything looks perfect but it doesn't work!

---

### Post by d-lhoest-y on 2013-09-10
I'm afraid ipv6 is already set on Ignore :D

Here's the output requested, 
Yeah, I love them usually but for now, that's a bit annoying :D


```
dlhoest@Dell:~$ ifconfigeth0      Link encap:Ethernet  HWaddr 84:8f:69:ba:9e:32  
          inet addr:172.16.150.180  Bcast:172.16.150.255  Mask:255.255.255.0
          inet6 addr: fe80::868f:69ff:feba:9e32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:225463 errors:0 dropped:20387 overruns:20387 frame:20387
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:16983394 (16.9 MB)  TX bytes:104210 (104.2 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:99243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10648520 (10.6 MB)  TX bytes:10648520 (10.6 MB)


wlan0     Link encap:Ethernet  HWaddr 4c:80:93:3b:2f:36  
          inet6 addr: fe80::4e80:93ff:fe3b:2f36/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:379599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254014585 (254.0 MB)  TX bytes:230085985 (230.0 MB)


dlhoest@Dell:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        84:8F:69:BA:9E:32


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         172.16.150.180
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.150.1


    DNS:             172.16.1.15
    DNS:             172.16.1.60




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        4C:80:93:3B:2F:36


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    IIMC-FACULTY:    Infra, 00:3A:99:34:93:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    IIMC-FACULTY:    Infra, 00:3A:99:34:A2:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    IIMC-GUEST:      Infra, 00:3A:99:34:93:D4, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    IIMC-GUEST:      Infra, 00:3A:99:34:A2:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    IIMC-STUDENT:    Infra, 00:3A:99:34:A2:83, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    IIMC-STUDENT:    Infra, 00:3A:99:34:93:D3, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2




dlhoest@Dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 84:8f:69:ba:9e:32  
          inet addr:172.16.150.180  Bcast:172.16.150.255  Mask:255.255.255.0
          inet6 addr: fe80::868f:69ff:feba:9e32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226212 errors:0 dropped:20387 overruns:20387 frame:20387
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:17030435 (17.0 MB)  TX bytes:104554 (104.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:99387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10657412 (10.6 MB)  TX bytes:10657412 (10.6 MB)


dlhoest@Dell:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        84:8F:69:BA:9E:32


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         172.16.150.180
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.150.1


    DNS:             172.16.1.15
    DNS:             172.16.1.60




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        4C:80:93:3B:2F:36


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




dlhoest@Dell:~$ dmesg | grep -e atl1 -e eth0
[35689.871454] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:b9:bf:0a:88:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=128 ID=12281 PROTO=UDP SPT=68 DPT=67 LEN=312 
[36263.746595] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=17818 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36333.896850] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=18156 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36361.410657] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=18462 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36384.617765] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=18723 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36424.357238] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=19072 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36437.988475] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=19328 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36500.351411] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=19515 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36625.620287] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:1c:75:08:72:c5:1a:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=1 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36627.615706] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:1c:75:08:72:c5:1a:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=64 ID=2 PROTO=UDP SPT=68 DPT=67 LEN=310 
[36666.854737] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:30:f9:ed:d4:07:a2:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=347 TOS=0x00 PREC=0x00 TTL=128 ID=7992 PROTO=UDP SPT=68 DPT=67 LEN=327 
[36771.803370] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:3c:97:0e:a7:0b:78:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=64 ID=31179 PROTO=UDP SPT=68 DPT=67 LEN=311 
[36895.170022] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:c8:60:00:35:e0:1f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=25650 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36898.822811] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:c8:60:00:35:e0:1f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=25652 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36906.764609] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:c8:60:00:35:e0:1f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=25654 PROTO=UDP SPT=68 DPT=67 LEN=308 
[36906.770392] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:c8:60:00:35:e0:1f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=335 TOS=0x00 PREC=0x00 TTL=128 ID=25655 PROTO=UDP SPT=68 DPT=67 LEN=315 
[37060.679561] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:77:21:cc:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308 
[37062.677211] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:77:21:cc:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=344 TOS=0x00 PREC=0x00 TTL=128 ID=1 PROTO=UDP SPT=68 DPT=67 LEN=324 
[37510.440419] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:3c:97:0e:a7:0b:78:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=331 TOS=0x00 PREC=0x00 TTL=64 ID=31218 PROTO=UDP SPT=68 DPT=67 LEN=311 
[37680.683384] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:60:eb:69:e4:41:6f:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=11583 PROTO=UDP SPT=68 DPT=67 LEN=308 
[37809.437943] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:b9:bf:0a:88:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=128 ID=32425 PROTO=UDP SPT=68 DPT=67 LEN=312 
[37850.141001] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:b9:bf:0a:88:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=128 ID=150 PROTO=UDP SPT=68 DPT=67 LEN=312 
[37865.329484] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:b9:bf:0a:88:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=128 ID=157 PROTO=UDP SPT=68 DPT=67 LEN=312 
[37937.840519] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17884 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.203377] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17918 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.206315] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17919 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.206345] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17920 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.207127] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17921 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.397005] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22919 DPT=53 LEN=31 
[37938.397016] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22919 DPT=53 LEN=31 
[37938.397371] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29122 DPT=53 LEN=31 
[37938.397393] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29122 DPT=53 LEN=31 
[37938.492856] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63483 DPT=53 LEN=42 
[37938.492865] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63483 DPT=53 LEN=42 
[37938.492905] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39667 DPT=53 LEN=42 
[37938.492911] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39667 DPT=53 LEN=42 
[37938.492960] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35581 DPT=53 LEN=42 
[37938.492966] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35581 DPT=53 LEN=42 
[37938.492998] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3313 DPT=53 LEN=42 
[37938.493003] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3313 DPT=53 LEN=42 
[37938.493063] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7730 DPT=53 LEN=42 
[37938.493069] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7730 DPT=53 LEN=42 
[37938.493100] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52154 DPT=53 LEN=42 
[37938.493106] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52154 DPT=53 LEN=42 
[37938.493150] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32664 DPT=53 LEN=42 
[37938.493156] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32664 DPT=53 LEN=42 
[37938.493186] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5098 DPT=53 LEN=42 
[37938.493192] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5098 DPT=53 LEN=42 
[37938.513146] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60103 DPT=53 LEN=31 
[37938.513160] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60103 DPT=53 LEN=31 
[37938.513313] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55721 DPT=53 LEN=31 
[37938.513322] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55721 DPT=53 LEN=31 
[37938.525246] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64642 DPT=53 LEN=40 
[37938.525260] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64642 DPT=53 LEN=40 
[37938.525405] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8644 DPT=53 LEN=40 
[37938.525416] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8644 DPT=53 LEN=40 
[37938.525498] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23628 DPT=53 LEN=40 
[37938.525508] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23628 DPT=53 LEN=40 
[37938.525562] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56797 DPT=53 LEN=40 
[37938.525572] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56797 DPT=53 LEN=40 
[37938.525659] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53478 DPT=53 LEN=40 
[37938.525669] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53478 DPT=53 LEN=40 
[37938.525716] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65369 DPT=53 LEN=40 
[37938.525723] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65369 DPT=53 LEN=40 
[37938.525772] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21456 DPT=53 LEN=40 
[37938.525781] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21456 DPT=53 LEN=40 
[37938.525825] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52948 DPT=53 LEN=40 
[37938.525833] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52948 DPT=53 LEN=40 
[37938.891442] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17964 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.904817] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30166 DPT=53 LEN=42 
[37938.904860] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30166 DPT=53 LEN=42 
[37938.905034] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14256 DPT=53 LEN=42 
[37938.905074] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14256 DPT=53 LEN=42 
[37938.905301] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40614 DPT=53 LEN=42 
[37938.905339] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40614 DPT=53 LEN=42 
[37938.905465] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46155 DPT=53 LEN=42 
[37938.905486] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46155 DPT=53 LEN=42 
[37938.905707] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64370 DPT=53 LEN=42 
[37938.905728] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64370 DPT=53 LEN=42 
[37938.905835] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14759 DPT=53 LEN=42 
[37938.905854] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14759 DPT=53 LEN=42 
[37938.906011] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31252 DPT=53 LEN=42 
[37938.906031] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31252 DPT=53 LEN=42 
[37938.906135] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50519 DPT=53 LEN=42 
[37938.906154] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50519 DPT=53 LEN=42 
[37938.907781] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30798 DPT=53 LEN=40 
[37938.907813] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30798 DPT=53 LEN=40 
[37938.908068] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57151 DPT=53 LEN=40 
[37938.908100] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57151 DPT=53 LEN=40 
[37938.908355] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=26947 DPT=53 LEN=40 
[37938.908384] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=26947 DPT=53 LEN=40 
[37938.908663] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11551 DPT=53 LEN=40 
[37938.908691] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11551 DPT=53 LEN=40 
[37938.951823] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17965 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.954867] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17966 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.954902] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17967 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37938.955680] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17968 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37939.639780] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17989 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37939.700725] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17990 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37939.703902] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17991 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37939.703934] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17992 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37939.704595] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17993 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37939.904316] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12575 DPT=53 LEN=36 
[37939.904363] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12575 DPT=53 LEN=36 
[37939.904493] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24086 DPT=53 LEN=36 
[37939.904514] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24086 DPT=53 LEN=36 
[37939.904629] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51523 DPT=53 LEN=36 
[37939.904662] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51523 DPT=53 LEN=36 
[37939.904783] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20453 DPT=53 LEN=36 
[37939.904815] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20453 DPT=53 LEN=36 
[37939.904962] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40156 DPT=53 LEN=36 
[37939.905012] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40156 DPT=53 LEN=36 
[37939.905302] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12224 DPT=53 LEN=36 
[37939.905334] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12224 DPT=53 LEN=36 
[37939.989995] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35338 DPT=53 LEN=42 
[37939.990025] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35338 DPT=53 LEN=42 
[37939.990148] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37106 DPT=53 LEN=42 
[37939.990167] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37106 DPT=53 LEN=42 
[37939.990339] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20179 DPT=53 LEN=42 
[37939.990359] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20179 DPT=53 LEN=42 
[37939.990443] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12662 DPT=53 LEN=42 
[37939.990462] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12662 DPT=53 LEN=42 
[37939.990680] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41495 DPT=53 LEN=42 
[37939.990703] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41495 DPT=53 LEN=42 
[37939.990790] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46441 DPT=53 LEN=42 
[37939.990809] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46441 DPT=53 LEN=42 
[37939.990978] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45268 DPT=53 LEN=42 
[37939.991001] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45268 DPT=53 LEN=42 
[37939.991102] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13119 DPT=53 LEN=42 
[37939.991121] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13119 DPT=53 LEN=42 
[37940.388675] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17994 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37940.677370] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:19:ee:19:be:08:00 SRC=172.16.150.129 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=19369 PROTO=UDP SPT=68 DPT=67 LEN=308 
[37940.762893] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18001 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37940.764982] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18003 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37940.765413] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18002 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37940.902770] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37563 DPT=53 LEN=41 
[37940.902800] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37563 DPT=53 LEN=41 
[37940.903062] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1993 DPT=53 LEN=41 
[37940.903090] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1993 DPT=53 LEN=41 
[37940.903303] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38695 DPT=53 LEN=41 
[37940.903323] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38695 DPT=53 LEN=41 
[37940.903515] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55036 DPT=53 LEN=41 
[37940.903557] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55036 DPT=53 LEN=41 
[37940.904536] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47754 DPT=53 LEN=41 
[37940.904564] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47754 DPT=53 LEN=41 
[37940.904778] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18253 DPT=53 LEN=41 
[37940.904801] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18253 DPT=53 LEN=41 
[37940.904960] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39612 DPT=53 LEN=41 
[37940.904979] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39612 DPT=53 LEN=41 
[37940.905180] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9522 DPT=53 LEN=41 
[37940.905199] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9522 DPT=53 LEN=41 
[37940.906407] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=28029 DPT=53 LEN=44 
[37940.906429] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=28029 DPT=53 LEN=44 
[37940.906592] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15872 DPT=53 LEN=44 
[37940.906612] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15872 DPT=53 LEN=44 
[37940.906765] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63873 DPT=53 LEN=44 
[37940.906784] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63873 DPT=53 LEN=44 
[37940.906922] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1957 DPT=53 LEN=44 
[37940.906941] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1957 DPT=53 LEN=44 
[37940.907946] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65191 DPT=53 LEN=44 
[37940.907979] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65191 DPT=53 LEN=44 
[37940.908053] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8876 DPT=53 LEN=44 
[37940.908059] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8876 DPT=53 LEN=44 
[37940.908296] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=62948 DPT=53 LEN=44 
[37940.908324] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=62948 DPT=53 LEN=44 
[37940.908523] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=53 LEN=44 
[37940.908548] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20691 DPT=53 LEN=44 
[37940.989317] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:19:ee:19:be:08:00 SRC=172.16.150.129 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=19372 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37941.401026] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:38:ea:a7:ea:7a:72:08:00 SRC=172.16.150.25 DST=172.16.150.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=914 PROTO=UDP SPT=138 DPT=138 LEN=209 
[37941.511181] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18017 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37941.514097] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18018 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37941.514123] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18019 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37941.737498] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:19:ee:19:be:08:00 SRC=172.16.150.129 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=19373 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37942.260056] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18020 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37942.262900] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18021 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37942.262936] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18022 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37942.486480] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:22:19:ee:19:be:08:00 SRC=172.16.150.129 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=19374 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37942.850848] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23246 DPT=53 LEN=42 
[37942.850892] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23246 DPT=53 LEN=42 
[37942.851174] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35948 DPT=53 LEN=42 
[37942.851211] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35948 DPT=53 LEN=42 
[37942.851480] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39985 DPT=53 LEN=42 
[37942.851513] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39985 DPT=53 LEN=42 
[37942.851755] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31082 DPT=53 LEN=42 
[37942.851788] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31082 DPT=53 LEN=42 
[37943.313195] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18036 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37943.319176] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18037 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37943.320599] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18038 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37943.846006] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38980 DPT=53 LEN=42 
[37943.846046] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38980 DPT=53 LEN=42 
[37943.846279] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53338 DPT=53 LEN=42 
[37943.846300] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53338 DPT=53 LEN=42 
[37943.846538] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21858 DPT=53 LEN=42 
[37943.846570] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21858 DPT=53 LEN=42 
[37943.846783] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45030 DPT=53 LEN=42 
[37943.846804] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45030 DPT=53 LEN=42 
[37944.061633] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18046 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37944.067333] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18047 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37944.069410] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18048 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37944.810342] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18050 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37944.816328] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18051 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37944.818228] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18052 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37944.904445] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35208 DPT=53 LEN=41 
[37944.904476] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35208 DPT=53 LEN=41 
[37944.904792] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30048 DPT=53 LEN=41 
[37944.904816] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30048 DPT=53 LEN=41 
[37944.905119] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31358 DPT=53 LEN=41 
[37944.905143] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31358 DPT=53 LEN=41 
[37944.905327] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1152 DPT=53 LEN=41 
[37944.905346] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1152 DPT=53 LEN=41 
[37944.906980] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11941 DPT=53 LEN=41 
[37944.907003] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11941 DPT=53 LEN=41 
[37944.907203] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22810 DPT=53 LEN=41 
[37944.907222] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22810 DPT=53 LEN=41 
[37944.907514] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24387 DPT=53 LEN=41 
[37944.907545] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24387 DPT=53 LEN=41 
[37944.907725] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50956 DPT=53 LEN=41 
[37944.907744] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50956 DPT=53 LEN=41 
[37944.908854] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36311 DPT=53 LEN=44 
[37944.908876] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36311 DPT=53 LEN=44 
[37944.909064] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36712 DPT=53 LEN=44 
[37944.909082] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36712 DPT=53 LEN=44 
[37944.909238] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17818 DPT=53 LEN=44 
[37944.909257] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17818 DPT=53 LEN=44 
[37944.909393] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36203 DPT=53 LEN=44 
[37944.909411] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36203 DPT=53 LEN=44 
[37944.910752] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58443 DPT=53 LEN=44 
[37944.910780] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58443 DPT=53 LEN=44 
[37944.911088] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21236 DPT=53 LEN=44 
[37944.911116] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21236 DPT=53 LEN=44 
[37944.911334] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=25257 DPT=53 LEN=44 
[37944.911357] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=25257 DPT=53 LEN=44 
[37944.911535] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27627 DPT=53 LEN=44 
[37944.911558] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27627 DPT=53 LEN=44 
[37946.197896] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18056 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37946.946166] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18057 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37947.323801] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15728 DPT=53 LEN=42 
[37947.323832] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15728 DPT=53 LEN=42 
[37947.324069] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45544 DPT=53 LEN=42 
[37947.324089] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45544 DPT=53 LEN=42 
[37947.324258] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37153 DPT=53 LEN=42 
[37947.324278] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37153 DPT=53 LEN=42 
[37947.324523] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6398 DPT=53 LEN=42 
[37947.324551] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6398 DPT=53 LEN=42 
[37947.695063] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:68:7c:86:dc:08:00 SRC=172.16.150.144 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=18058 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37948.467737] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23332 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37949.216381] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23333 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37949.965560] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23334 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37950.314215] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:14:fe:b5:ad:17:d9:08:00 SRC=172.16.150.139 DST=255.255.255.255 LEN=162 TOS=0x00 PREC=0x00 TTL=128 ID=13593 PROTO=UDP SPT=17500 DPT=17500 LEN=142 
[37950.319593] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:14:fe:b5:ad:17:d9:08:00 SRC=172.16.150.139 DST=255.255.255.255 LEN=162 TOS=0x00 PREC=0x00 TTL=128 ID=13594 PROTO=UDP SPT=17500 DPT=17500 LEN=142 
[37950.319626] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:14:fe:b5:ad:17:d9:08:00 SRC=172.16.150.139 DST=255.255.255.255 LEN=162 TOS=0x00 PREC=0x00 TTL=128 ID=13595 PROTO=UDP SPT=17500 DPT=17500 LEN=142 
[37950.319878] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:14:fe:b5:ad:17:d9:08:00 SRC=172.16.150.139 DST=255.255.255.255 LEN=162 TOS=0x00 PREC=0x00 TTL=128 ID=13596 PROTO=UDP SPT=17500 DPT=17500 LEN=142 
[37950.320286] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:14:fe:b5:ad:17:d9:08:00 SRC=172.16.150.139 DST=172.16.150.255 LEN=162 TOS=0x00 PREC=0x00 TTL=128 ID=13597 PROTO=UDP SPT=17500 DPT=17500 LEN=142 
[37950.976342] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4235 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37950.981245] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4236 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37950.993234] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4237 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.019488] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4240 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.088413] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23345 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.724619] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4249 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.729542] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4250 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.741487] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4251 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.767475] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4252 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37951.836811] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23346 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37952.473549] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4256 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37952.478415] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4257 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37952.490360] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4258 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37952.516410] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:18:03:73:a6:ec:3e:08:00 SRC=172.16.150.166 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=4259 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37952.585654] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23347 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37952.901827] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51672 DPT=53 LEN=41 
[37952.901858] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51672 DPT=53 LEN=41 
[37952.902125] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60050 DPT=53 LEN=41 
[37952.902165] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60050 DPT=53 LEN=41 
[37952.902444] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24909 DPT=53 LEN=41 
[37952.902478] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24909 DPT=53 LEN=41 
[37952.902786] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16487 DPT=53 LEN=41 
[37952.902814] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16487 DPT=53 LEN=41 
[37952.904117] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43241 DPT=53 LEN=41 
[37952.904140] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43241 DPT=53 LEN=41 
[37952.904371] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9055 DPT=53 LEN=41 
[37952.904392] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9055 DPT=53 LEN=41 
[37952.904604] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32858 DPT=53 LEN=41 
[37952.904624] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32858 DPT=53 LEN=41 
[37952.904833] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51283 DPT=53 LEN=41 
[37952.904855] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51283 DPT=53 LEN=41 
[37952.906193] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35637 DPT=53 LEN=44 
[37952.906232] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35637 DPT=53 LEN=44 
[37952.906464] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55625 DPT=53 LEN=44 
[37952.906486] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55625 DPT=53 LEN=44 
[37952.906691] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31840 DPT=53 LEN=44 
[37952.906712] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31840 DPT=53 LEN=44 
[37952.906895] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27289 DPT=53 LEN=44 
[37952.906915] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27289 DPT=53 LEN=44 
[37952.908120] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3351 DPT=53 LEN=44 
[37952.908141] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3351 DPT=53 LEN=44 
[37952.908358] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=28101 DPT=53 LEN=44 
[37952.908384] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=28101 DPT=53 LEN=44 
[37952.908609] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46021 DPT=53 LEN=44 
[37952.908630] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46021 DPT=53 LEN=44 
[37952.908786] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22960 DPT=53 LEN=44 
[37952.908805] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22960 DPT=53 LEN=44 
[37953.179093] Unknown InputIN=eth0 OUT= MAC=84:8f:69:ba:9e:32:e8:03:9a:92:36:d0:08:00 SRC=172.16.150.194 DST=172.16.150.180 LEN=29 TOS=0x00 PREC=0x00 TTL=128 ID=8958 PROTO=UDP SPT=62443 DPT=7 LEN=9 
[37953.645472] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23350 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37953.832267] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7698 DPT=53 LEN=42 
[37953.832338] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7698 DPT=53 LEN=42 
[37953.832649] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61137 DPT=53 LEN=42 
[37953.832685] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61137 DPT=53 LEN=42 
[37953.832980] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23731 DPT=53 LEN=42 
[37953.833014] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23731 DPT=53 LEN=42 
[37953.833259] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56828 DPT=53 LEN=42 
[37953.833289] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56828 DPT=53 LEN=42 
[37954.393977] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23352 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37954.709230] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14107 DPT=53 LEN=42 
[37954.709274] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14107 DPT=53 LEN=42 
[37954.709432] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8707 DPT=53 LEN=42 
[37954.709465] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8707 DPT=53 LEN=42 
[37954.709891] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29463 DPT=53 LEN=42 
[37954.709926] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29463 DPT=53 LEN=42 
[37954.710074] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10712 DPT=53 LEN=42 
[37954.710106] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10712 DPT=53 LEN=42 
[37954.710415] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10600 DPT=53 LEN=42 
[37954.710449] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10600 DPT=53 LEN=42 
[37954.710583] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1996 DPT=53 LEN=42 
[37954.710614] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1996 DPT=53 LEN=42 
[37954.710861] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57098 DPT=53 LEN=42 
[37954.710892] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57098 DPT=53 LEN=42 
[37954.711049] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32049 DPT=53 LEN=42 
[37954.711084] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32049 DPT=53 LEN=42 
[37954.717631] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50697 DPT=53 LEN=40 
[37954.717641] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50697 DPT=53 LEN=40 
[37954.717723] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36858 DPT=53 LEN=40 
[37954.717732] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36858 DPT=53 LEN=40 
[37954.717812] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55827 DPT=53 LEN=40 
[37954.717821] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55827 DPT=53 LEN=40 
[37954.717896] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53113 DPT=53 LEN=40 
[37954.717906] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53113 DPT=53 LEN=40 
[37955.143077] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:a0:b3:cc:83:c5:08:08:00 SRC=172.16.150.158 DST=172.16.150.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=23360 PROTO=UDP SPT=137 DPT=137 LEN=58 
[37955.249666] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:70:88:eb:31:08:00 SRC=172.16.150.163 DST=255.255.255.255 LEN=140 TOS=0x00 PREC=0x00 TTL=64 ID=23856 PROTO=UDP SPT=17500 DPT=17500 LEN=120 
[37955.254032] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:70:88:eb:31:08:00 SRC=172.16.150.163 DST=255.255.255.255 LEN=140 TOS=0x00 PREC=0x00 TTL=64 ID=23857 PROTO=UDP SPT=17500 DPT=17500 LEN=120 
[37955.254070] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:70:88:eb:31:08:00 SRC=172.16.150.163 DST=172.16.150.255 LEN=140 TOS=0x00 PREC=0x00 TTL=64 ID=23858 PROTO=UDP SPT=17500 DPT=17500 LEN=120 
[37955.708666] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47624 DPT=53 LEN=42 
[37955.708697] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47624 DPT=53 LEN=42 
[37955.708852] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55530 DPT=53 LEN=42 
[37955.708874] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55530 DPT=53 LEN=42 
[37955.709108] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16571 DPT=53 LEN=42 
[37955.709141] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16571 DPT=53 LEN=42 
[37955.709254] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19283 DPT=53 LEN=42 
[37955.709273] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19283 DPT=53 LEN=42 
[37955.709515] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52689 DPT=53 LEN=42 
[37955.709584] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52689 DPT=53 LEN=42 
[37955.709731] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12310 DPT=53 LEN=42 
[37955.709763] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12310 DPT=53 LEN=42 
[37955.709883] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63424 DPT=53 LEN=36 
[37955.709915] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63424 DPT=53 LEN=36 
[37955.710054] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13311 DPT=53 LEN=36 
[37955.710090] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13311 DPT=53 LEN=36 
[37955.710234] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46360 DPT=53 LEN=36 
[37955.710268] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46360 DPT=53 LEN=36 
[37955.710411] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33060 DPT=53 LEN=36 
[37955.710445] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33060 DPT=53 LEN=36 
[37955.710715] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20621 DPT=53 LEN=42 
[37955.710749] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20621 DPT=53 LEN=42 
[37955.710885] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61051 DPT=53 LEN=42 
[37955.710918] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61051 DPT=53 LEN=42 
[37955.711040] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16289 DPT=53 LEN=36 
[37955.711072] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16289 DPT=53 LEN=36 
[37955.711364] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14104 DPT=53 LEN=36 
[37955.711392] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=56 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14104 DPT=53 LEN=36 
[37955.724348] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=255.255.255.255 LEN=227 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=207 
[37955.726812] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.150.255 LEN=227 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=207 
[37956.706932] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18006 DPT=53 LEN=41 
[37956.706962] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18006 DPT=53 LEN=41 
[37956.707261] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30036 DPT=53 LEN=41 
[37956.707285] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30036 DPT=53 LEN=41 
[37956.707540] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34221 DPT=53 LEN=41 
[37956.707569] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34221 DPT=53 LEN=41 
[37956.707781] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9660 DPT=53 LEN=41 
[37956.707805] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9660 DPT=53 LEN=41 
[37956.709218] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23272 DPT=53 LEN=41 
[37956.709246] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23272 DPT=53 LEN=41 
[37956.709620] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35988 DPT=53 LEN=41 
[37956.709647] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35988 DPT=53 LEN=41 
[37956.710028] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12294 DPT=53 LEN=41 
[37956.710056] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12294 DPT=53 LEN=41 
[37956.710430] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10740 DPT=53 LEN=41 
[37956.710458] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10740 DPT=53 LEN=41 
[37956.711795] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23165 DPT=53 LEN=44 
[37956.711823] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23165 DPT=53 LEN=44 
[37956.712004] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64273 DPT=53 LEN=44 
[37956.712024] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64273 DPT=53 LEN=44 
[37956.712338] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1131 DPT=53 LEN=44 
[37956.712365] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1131 DPT=53 LEN=44 
[37956.712586] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40094 DPT=53 LEN=44 
[37956.712608] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40094 DPT=53 LEN=44 
[37956.713838] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=25594 DPT=53 LEN=44 
[37956.713866] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=25594 DPT=53 LEN=44 
[37956.714168] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64825 DPT=53 LEN=44 
[37956.714196] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64825 DPT=53 LEN=44 
[37956.714413] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17613 DPT=53 LEN=44 
[37956.714436] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17613 DPT=53 LEN=44 
[37956.714615] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37025 DPT=53 LEN=44 
[37956.714639] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37025 DPT=53 LEN=44 
[37957.827416] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39721 DPT=53 LEN=45 
[37957.827447] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39721 DPT=53 LEN=45 
[37957.827698] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11022 DPT=53 LEN=45 
[37957.827727] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11022 DPT=53 LEN=45 
[37957.827956] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58616 DPT=53 LEN=45 
[37957.827979] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58616 DPT=53 LEN=45 
[37957.828189] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51140 DPT=53 LEN=45 
[37957.828210] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51140 DPT=53 LEN=45 
[37960.667934] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:30:f9:ed:fd:57:dd:08:00 SRC=172.16.150.176 DST=255.255.255.255 LEN=171 TOS=0x00 PREC=0x00 TTL=128 ID=23367 PROTO=UDP SPT=17500 DPT=17500 LEN=151 
[37960.673118] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:30:f9:ed:fd:57:dd:08:00 SRC=172.16.150.176 DST=172.16.150.255 LEN=171 TOS=0x00 PREC=0x00 TTL=128 ID=23368 PROTO=UDP SPT=17500 DPT=17500 LEN=151 
[37960.673506] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:30:f9:ed:fd:57:dd:08:00 SRC=172.16.150.176 DST=255.255.255.255 LEN=171 TOS=0x00 PREC=0x00 TTL=128 ID=23369 PROTO=UDP SPT=17500 DPT=17500 LEN=151 
[37960.710737] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31753 DPT=53 LEN=41 
[37960.710774] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31753 DPT=53 LEN=41 
[37960.711059] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24584 DPT=53 LEN=41 
[37960.711083] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24584 DPT=53 LEN=41 
[37960.711331] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41679 DPT=53 LEN=41 
[37960.711364] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41679 DPT=53 LEN=41 
[37960.711589] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55751 DPT=53 LEN=41 
[37960.711610] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55751 DPT=53 LEN=41 
[37960.713319] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47412 DPT=53 LEN=41 
[37960.713348] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47412 DPT=53 LEN=41 
[37960.713597] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45334 DPT=53 LEN=41 
[37960.713632] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45334 DPT=53 LEN=41 
[37960.713915] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65478 DPT=53 LEN=41 
[37960.713937] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65478 DPT=53 LEN=41 
[37960.714182] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34064 DPT=53 LEN=41 
[37960.714233] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34064 DPT=53 LEN=41 
[37960.719729] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59521 DPT=53 LEN=44 
[37960.719768] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59521 DPT=53 LEN=44 
[37960.720030] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48549 DPT=53 LEN=44 
[37960.720065] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48549 DPT=53 LEN=44 
[37960.720310] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42474 DPT=53 LEN=44 
[37960.720343] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42474 DPT=53 LEN=44 
[37960.720591] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23616 DPT=53 LEN=44 
[37960.720625] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23616 DPT=53 LEN=44 
[37960.722566] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13982 DPT=53 LEN=44 
[37960.722606] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13982 DPT=53 LEN=44 
[37960.722878] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5261 DPT=53 LEN=44 
[37960.722914] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5261 DPT=53 LEN=44 
[37960.723187] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6958 DPT=53 LEN=44 
[37960.723219] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6958 DPT=53 LEN=44 
[37960.723444] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=49902 DPT=53 LEN=44 
[37960.723475] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=49902 DPT=53 LEN=44 
[37961.818524] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32850 DPT=53 LEN=45 
[37961.818554] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32850 DPT=53 LEN=45 
[37961.818829] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24533 DPT=53 LEN=45 
[37961.818852] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24533 DPT=53 LEN=45 
[37961.819098] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29974 DPT=53 LEN=45 
[37961.819122] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29974 DPT=53 LEN=45 
[37961.819298] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.15 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59953 DPT=53 LEN=45 
[37961.819316] Unknown OutputIN= OUT=eth0 SRC=172.16.150.180 DST=172.16.1.60 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59953 DPT=53 LEN=45 



```

---

### Post by chili555 on 2013-09-10
> DNS:             172.16.1.15
DNS:             172.16.1.60Old Chili doesn't like this one bit! Stil with the wireless disconnected, please try:```
ping -c3 8.8.8.8
ping -c3 74.125.131.99
```If you get ping returns here, then we suspect (no, confirm) DNS problems. Then try:```
firefox 74.125.131.99
```Depending on your report, we'll fix it pretty easily.

---

### Post by d-lhoest-y on 2013-09-11
There you go, 

```
dlhoest@Dell:~$ ping -c3 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms


dlhoest@Dell:~$ ping -c3 74.125.131.99
PING 74.125.131.99 (74.125.131.99) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 74.125.131.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2017ms


dlhoest@Dell:~$ 



```

```
dlhoest@Dell:~$ firefox 74.125.131.99

(process:27056): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed



```

Firefox is "connecting" for a while, then times out.

---

### Post by chili555 on 2013-09-11
When wireless is connected, is everything working as expected? May we see this when wireless is working?```
nm-tool
```Are your IP address, DNS, etc. settings provided by the DHCP server at the router or switch? Or are they manually set in Network Manager? What does this tell us?```
cat /etc/network/interfaces
```Please disguise any passwords, etc. Ideally, Network Manager will do all the heavy lifting and the interfaces file will contain only loopback entries. 

And this is weird:> Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:26:b9:bf:0a:88:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=128 ID=12281 PROTO=UDP SPT=68 DPT=67 LEN=312 

---

### Post by d-lhoest-y on 2013-09-11
```
dlhoest@Dell:~$ nm-tool

NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             disconnected
  Default:           no
  HW Address:        84:8F:69:BA:9E:32


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0  [IIMC-STUDENT] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        4C:80:93:3B:2F:36


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    IIMC-FACULTY:    Infra, 00:3A:99:34:93:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    IIMC-GUEST:      Infra, 00:3A:99:34:93:D4, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    IIMC-GUEST:      Infra, 00:3A:99:34:A2:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    *IIMC-STUDENT:   Infra, 00:3A:99:34:A2:83, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    IIMC-STUDENT:    Infra, 00:3A:99:34:93:D3, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    IIMC-FACULTY:    Infra, 00:3A:99:34:A2:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    IIMC-GUEST:      Infra, 00:3A:99:33:F3:34, Freq 2412 MHz, Rate 54 Mb/s, Strength 34


  IPv4 Settings:
    Address:         172.20.11.30
    Prefix:          22 (255.255.252.0)
    Gateway:         172.20.8.1


    DNS:             172.16.1.15
    DNS:             172.16.1.60
```

```
cat /etc/network/interfacesauto lo
iface lo inet loopback
wireless-power on



```

Can't really help you on the DNS settings, basically, I'm exchange student in a uni in India, but the problem was already present in my home.

When Wireless is connected, everything works as expected, I can ping, browse, ...

---

### Post by chili555 on 2013-09-11
> Can't really help you on the DNS settings,Surely you know whether you put any extra settings in Network Manager.  Please right-click the Network Manager icon and Edit Connections. Under Wired, it should be blank except for MTU which should be Automatic. Under IPv4, it should say Automatic (DHCP): [http://i.stack.imgur.com/L7j9v.png](http://i.stack.imgur.com/L7j9v.png) and IPv6 should be set to ignore. All other settings should be blank. Save and close NM. Now switch off the wireless, reboot and tell us if things are improved.> cat /etc/network/interfacesauto lo
iface lo inet loopback
[COLOR="#FF0000"]wireless-power on[/COLOR]What is that for? It is undoubtedly doing nothing here.

---

### Post by d-lhoest-y on 2013-09-11
I had an address as Device mac address, removed it, rebooted, still not working.

Shall I remove the wifi-power on then?

---

### Post by d-lhoest-y on 2013-09-11
No wait! 

It works.

Ok, but there's something strange. When I boot up my computer, my connection tab on the menu bar, only has this : 

Enable Networking
Enable Wifi
Information
Edit

When I turn Wifi on, I get the full connection menu, 
Ethernet network
- wired connection
- Disconnect
Wifi network, 
- connected network
- disconnected
List of available wifi networks
Connect to hidden network, ... Well, you see what I mean.

Funny thing is, if I now try to turn wifi off, ethernet behaves the same way as before, ie : doesn't work, ping gives an "operation not permitted" message

---

### Post by chili555 on 2013-09-11
We are getting closer! Lets' have a look at:```
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/modules
cat /etc/rc.local
```When you boot up, is the ethernet driver already loaded?```
lsmod | grep ath
```> Shall I remove the wifi-power on then? I would.

---

### Post by d-lhoest-y on 2013-09-12
```
dlhoest@Dell:~$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=84:8F:69:BA:9E:32,


[ifupdown]
managed=false

```

```
dlhoest@Dell:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc

```

```
dlhoest@Dell:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0

```
For the last one, this is all I have : 


```
dlhoest@Dell:~$ lsmod | grep ath
dlhoest@Dell:~$ lsmod | grep ath
dlhoest@Dell:~$ 

```

Line (wifi-power) removed :)

---

### Post by chili555 on 2013-09-12
Let's make a manual change here:```
gksudo gedit /etc/NetworkManager/NetworkManager.conf 
```Remove this line:```

no-auto-default=84:8F:69:BA:9E:32,
```Proofread carefully, save and close gedit. Reboot with the wireless switched off and the ethernet plugged in and let us have your report.

---

### Post by d-lhoest-y on 2013-09-12
Well, 

I've removed the line, saved, closed everything and rebooted with wifi turned off.

Once logged in, ethernet was working perfectly fine, until I tried adding Wifi. At that point, ethernet was dead. Turning wifi off does not help, nor does disconnecting - reconnecting the cable.

Seriously, does it make any sense to you? :D

---

### Post by chili555 on 2013-09-12
> Once logged in, ethernet was working perfectly fine, until I tried adding Wifi. At that point, ethernet was dead. That's what the system is designed to do, although it usually works in reverse; that is, the connection of an ethernet cable usually disables wireless!

I am glad to hear that the ethernet is working as expected. Are you able to just use one or the other and not switch back and forth? Surely, at least at home, if you have ethernet, you can simply use ethernet and be happy. No?

---

### Post by d-lhoest-y on 2013-09-12
Yes, you are right, I'm able to use one or the other but only once. I mean, as soon as I switch the Wireless on, Ethernet would stop working.

I am happy indeed, and basically, it is only thanks to you for which, any beers, any time. I however wanted to be able and to set a hotspot from my computer to my smartphone but that is only a bonus. 

I will in any case fresh install Ubuntu 13.10 (my version has been upgraded twice already and definitely has some glitches) so I believe everything will be back to normal...

Thank you again so much :)

---

### Post by chili555 on 2013-09-12
I was very happy to have been able to help. I am sorry that I couldn't completely solve it. Thanks for your kind words!

---

