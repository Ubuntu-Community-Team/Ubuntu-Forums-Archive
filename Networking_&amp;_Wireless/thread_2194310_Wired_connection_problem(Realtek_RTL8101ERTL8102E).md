---
title: "Wired connection problem(Realtek RTL8101E/RTL8102E)"
date: 2013-12-17
forum: Networking &amp; Wireless
---

### Post by milos.dumonic on 2013-12-17
Hello,

This first time for me to use linux(newbie). I bought 2 days ago Dell Inspiron 15 3521 which has ubuntu 12.04 LTS.
When I use wireless card i have no problem, but when I want to use my cable modem connection failed.
At the same time when I use same modem with my desktop computer (Windows 7) he work without issues.
I've tried to solve my problem using this thread :[http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200) 
but without succsess.
This is some information about my computer:

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 74:86:7a:33:a8:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43568 (43.5 KB)  TX bytes:18567 (18.5 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27203 (27.2 KB)  TX bytes:27203 (27.2 KB)

wlan0     Link encap:Ethernet  HWaddr bc:85:56:9e:bd:ed  
          inet addr:192.168.43.235  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::be85:56ff:fe9e:bded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43115 (43.1 KB)  TX bytes:73069 (73.0 KB)


```

sudo lshw -C network -numeric

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10EC:8136]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: 74:86:7a:33:a8:31
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.024.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network
       description: Wireless interface
       product: Atheros Communications Inc. [168C:36]
       vendor: Atheros Communications Inc. [168C]
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: bc:85:56:9e:bd:ed
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-39-generic firmware=N/A ip=192.168.43.235 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c1500000-c157ffff memory:9fb00000-9fb0ffff


```
nm-tool

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [AndroidAP] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        BC:85:56:9E:BD:ED

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TP-LINK_ACD2C3:  Infra, 74:EA:3A:AC:D2:C3, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    HG520c:          Infra, E8:39:DF:5B:25:64, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    Tweety:          Infra, 00:30:4F:76:76:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    *AndroidAP:      Infra, 94:71:AC:98:F0:42, Freq 2437 MHz, Rate 54 Mb/s, Strength 85
    MarkoItanVuk:    Infra, 54:BE:F7:0F:35:4F, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    HG530:           Infra, 20:2B:C1:D7:93:4E, Freq 2417 MHz, Rate 54 Mb/s, Strength 25
    Cuka:            Infra, 7C:05:07:58:76:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2

  IPv4 Settings:
    Address:         192.168.43.235
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8101
  State:             unavailable
  Default:           no
  HW Address:        74:86:7A:33:A8:31

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

```

cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

```

cat /etc/resolv.conf

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```

cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=74:86:7A:33:A8:31,42:1E:31:8E:39:F9,

[ifupdown]
managed=false

```

cat /var/lib/NetworkManager/NetworkManager.state

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

Thank you in advance

---

### Post by varunendra on 2013-12-20
Welcome to the forums milos.dumonic !

While being connected to internet, please install ethtool -
```
sudo apt-get install ethtool
```
..and run -
```
sudo ethtool -s eth0 speed 100 duplex half autoneg off
```
Then check if you can connect. If not, try resetting the BIOS and retry the above last command. If still no joy, please post back the output of -
```
sudo ethtool eth0
```

---

