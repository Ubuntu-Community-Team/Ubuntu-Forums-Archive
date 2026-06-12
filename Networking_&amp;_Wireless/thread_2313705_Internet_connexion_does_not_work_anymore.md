---
title: "Internet connexion does not work anymore"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by clement.analogue on 2016-02-15
Hello,

I don't have Internet connexion since this morning. However, I have access to local network and my other devices does not have issue to access Internet.
I tried to reboot, I even shutdown the laptop for a while, same thing on both network interfaces (eth0 and wlan0). I even tried with another Internet connexion.

Thank you in advance for your help.


Tracepath:
```
% tracepath 192.168.1.1         
 1?: [LOCALHOST]                                         pmtu 1500
 1:  forumanalogue.fr                                      1.592ms reached
 1:  forumanalogue.fr                                      1.359ms reached
     Resume: pmtu 1500 hops 1 back 1 

```

```
% tracepath 8.8.8.8             
 1?: [LOCALHOST]                                         pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 
```

More informations:
```
% sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 68:5b:35:96:f6:e1
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=57765-v1.37 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Wireless interface
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: a8:86:dd:93:41:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:a0600000-a0603fff

```

```
 % sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 68:5b:35:96:f6:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1602881 (1.6 MB)  TX bytes:1602881 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr a8:86:dd:93:41:6c  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aa86:ddff:fe93:416c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23639 errors:0 dropped:0 overruns:0 frame:1319
          TX packets:20794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28913966 (28.9 MB)  TX bytes:2315442 (2.3 MB)
          Interrupt:17 

```

```
% cat  /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
Odd? Where's wlan0? Though I have access to local network.

```
% sudo nm-tool

NetworkManager Tool

State: connected (global)

- Device: 30:76:6F:0A:8D:02 ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:


- Device: wlan0  [Bbox-A7B38DFF-5GHz] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        A8:86:DD:93:41:6C

  Capabilities:
    Speed:           300 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Bbox-A7B38DFF:   Infra, 5C:A3:9D:85:40:98, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Bbox-0A2E264B-5GHz: Infra, 64:7C:34:33:4C:30, Freq 5180 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Bbox-0A2E264B:   Infra, 64:7C:34:33:4C:2C, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    SFR-0313:        Infra, FC:B4:E6:3B:0A:C1, Freq 5240 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    SFR-0313:        Infra, 00:37:B7:51:03:19, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Bbox-233A6BC7:   Infra, E8:BE:81:AF:55:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    freebox_PVAGJE:  Infra, 00:24:D4:6B:77:C4, Freq 2432 MHz, Rate 54 Mb/s, Strength 27 WPA
    SFR_80A0:        Infra, 24:95:04:C9:80:A4, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    SFR WiFi Mobile: Infra, D2:95:04:C9:80:A7, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    FreeWifi_secure: Infra, 00:24:D4:E6:E2:96, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    Bouygues Telecom Wi-Fi: Infra, 64:7C:34:33:4C:2D, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    SFR WiFi FON:    Infra, D2:95:04:C9:80:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    LG-E460_6416:    Infra, 9A:D6:F7:ED:AA:63, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA2
    Bbox-233A6BC7-5GHz: Infra, E8:BE:81:AF:55:44, Freq 5200 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    FreeWifi_secure: Infra, 00:24:D4:6B:77:C6, Freq 2432 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    FreeWifi:        Infra, 00:24:D4:6B:77:C5, Freq 2432 MHz, Rate 54 Mb/s, Strength 27
    FreeWifi:        Infra, 00:24:D4:E6:E2:95, Freq 2447 MHz, Rate 54 Mb/s, Strength 22
    Freebox-AF55C5:  Infra, 00:24:D4:E6:E2:94, Freq 2447 MHz, Rate 54 Mb/s, Strength 19 WPA
    DOC:             Infra, F4:CA:E5:87:F7:3C, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    Bbox-AA1A1FAE:   Infra, A0:1B:29:B1:59:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    PIERREBRUN:      Infra, 80:EA:96:F3:60:9A, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    *Bbox-A7B38DFF-5GHz: Infra, 5C:A3:9D:85:40:90, Freq 5180 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             127.0.0.1
    DNS:             192.168.1.8


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        68:5B:35:96:F6:E1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

---

### Post by lensman3 on 2016-02-15
Can you ping-> "ping -I wlan0 192.168.1.254" ?  This is your gateway IPv4 network address from ifconfig (ifconfig doesn't need to be sudo). The -I sends the ping out the wifi port.  The -I is dash-eye (capital eye) for interface.

ipconfig shows you that you have a wlan0 wifi access..

Also try:
1) arping 192.168.1.254               for several seconds and then do
2) arp                                            and see what else "might" be on your network.

What does "netstat -nr" show?  Do you have a gateway?

---

### Post by clement.analogue on 2016-02-16
Ethernet interface:
```
% ping -c 5 -I eth0 192.168.1.254
PING 192.168.1.254 (192.168.1.254) from 192.168.1.4 eth0: 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=0.557 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=0.655 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=0.785 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=0.664 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=0.614 ms

--- 192.168.1.254 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.557/0.655/0.785/0.075 ms
```

```
 % arping 192.168.1.254 -I eth0 -c 5 
ARPING 192.168.1.254 from 192.168.1.4 eth0
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  1.013ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  0.937ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  0.962ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  0.941ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  0.920ms
Sent 5 probes (1 broadcast(s))
Received 5 response(s)
```

Wifi interface:
```
% ping -c 5 -I wlan0 192.168.1.254
PING 192.168.1.254 (192.168.1.254) from 192.168.1.5 wlan0: 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=1.41 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1.40 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=1.38 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=1.42 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=1.45 ms

--- 192.168.1.254 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 1.385/1.417/1.454/0.040 ms
```

```
% arping 192.168.1.254 -I wlan0 -c 5
ARPING 192.168.1.254 from 192.168.1.5 wlan0
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  2.480ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  2.794ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  1.699ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  1.846ms
Unicast reply from 192.168.1.254 [80:18:A7:B3:8D:00]  1.677ms
Sent 5 probes (1 broadcast(s))
Received 5 response(s)
```

Network scan:
```
% arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.254            ether   80:18:a7:b3:8d:00   C                     eth0
192.168.1.254            ether   80:18:a7:b3:8d:00   C                     wlan0
calendar.forumanalogue.  ether   00:16:3e:31:2a:6e   C                     eth0
forumanalogue.fr         ether   30:5a:3a:7f:84:3f   C                     eth0
ns.forumanalogue.fr      ether   00:16:3e:9e:4f:a6   C                     wlan0
ns.forumanalogue.fr      ether   00:16:3e:9e:4f:a6   C                     eth0
calendar.forumanalogue.  ether   00:16:3e:31:2a:6e   C                     wlan0
```

Routing table:
```
% netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
```

---

### Post by clement.analogue on 2016-02-16
After an odd return of the command iptables -L, I figured out that the  file /etc/iptables/rules.v4 was corrupted, so I flush the rules iptables -F and add the correct ones.

---

