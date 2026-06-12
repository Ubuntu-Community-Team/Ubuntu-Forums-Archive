---
title: "Download speed drops to zero"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by Ruan_Costa on 2014-10-25
Hi there.
Whenever I try to download anything, a few minutes later (3 or sometimes more), the download speed starts to drop very fast until it hits zero, and the download is killed. This happens on chrome, firefox, apt-get, etc. When I'm on windows this doesn't happen. So its a ubuntu problem. I was using ubuntu 14.04 and I installed 14.10, but the problem persists.

I tried to follow a solution posted here [http://ubuntuforums.org/showthread.php?t=1416987](http://ubuntuforums.org/showthread.php?t=1416987) , but no luck.
Below is the output of some tools.

Cheers, 
Ruan

[B]nm-tool

[/B]NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        40:61:86:FD:27:05


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off




- Device: wlan0  [JTCD] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        40:61:86:A6:D1:FA


  Capabilities:
    Speed:           45 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    CasaDB:          Infra, 20:AA:4B:42:69:22, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    CasaDB:          Infra, 9C:A9:E4:17:25:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Matheus Wifi:    Infra, 00:1A:3F:96:23:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    *JTCD:           Infra, 90:F6:52:F0:B0:40, Freq 2472 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1

[B]ifconfig

[/B]eth0      Link encap:Ethernet  HWaddr 40:61:86:fd:27:05  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:64702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86175840 (86.1 MB)  TX bytes:4354423 (4.3 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3001473 (3.0 MB)  TX bytes:3001473 (3.0 MB)


wlan0     Link encap:Ethernet  HWaddr 40:61:86:a6:d1:fa  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fea6:d1fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:423159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:484309511 (484.3 MB)  TX bytes:35869274 (35.8 MB)

---

