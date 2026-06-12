---
title: "WiFi USB is not recognised on boot, only after I plug it again"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by ecarlevaro on 2018-02-17
I have a USB wireless device TPLINK TLWN7200ND (compatible with Linux). It was working fine after package upgrade.


Now, it works fine AFTER logging and if and only if I unplug the USB cable and I plug it in again.


How can I do to have wireless from boot without unplugging? 


Before I unplug, there is no trace of the USB wireless on commands iwconfig, lshw, nm-tool, rfkill or lsmod. It appears just like it doesn't exist at all.
The only command that shows me that it exists is lsusb:

********lsusb********
```
    Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
    Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

If I unplug and plug it again, all works fine, it connects to WiFi and all those commands reports.

****Lsmod** (showing only the difference between before and after)**

```
rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              53248  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              741376  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              552960  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib

```

********lshw********
```
*-network
descripción: Interfaz inalámbrica
id físico: 1
información del bus: usb@1:4
nombre lógico: wlan2
serie: f8:1a:67:25:2f:96
capacidades: ethernet physical wireless
configuración: broadcast=yes driver=rt2800usb driverversion=4.2.0-42-generic firmware=0.29 ip=192.168.10.199 link=yes multicast=yes wireless=IEEE 802.11bgn

``` 

****nm-tool****
```
NetworkManager Tool


State: connected (global)


- Device: wlan2  [redCarlevaro] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        F8:1A:67:25:2F:96


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    redCarlevaro2:   Infra, EE:08:6B:AC:F6:01, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA2
    OpenWrt:         Infra, B0:48:7A:C9:C8:0E, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    RED GARCIA:      Infra, F4:F2:6D:61:19:78, Freq 2427 MHz, Rate 54 Mb/s, Strength 35 WPA2
    cielo_azul:      Infra, 90:F6:52:FA:21:FC, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA
    redCarlevaro:    Infra, D8:5D:4C:9E:53:84, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    BM 5G:           Infra, 98:DE:D0:EE:80:5A, Freq 2422 MHz, Rate 54 Mb/s, Strength 12 WPA2
    *redCarlevaro:   Infra, EC:08:6B:AF:F6:01, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA2
    Fibertel WiFi318 2.4GHz.: Infra, C8:3D:D4:21:3B:50, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2


  IPv4 Settings:
    Address:         192.168.10.199
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1


    DNS:             192.168.10.1
    DNS:             192.168.100.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:30:67:1E:5F:81


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```
[B]
**[/B]**rfkill********
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by ecarlevaro on 2018-02-18
It was nicely solved after a:
```
sudo aptitude safe-upgrade
```
Apparently the rebuilt of the kernel image that was followed by the upgrade, solved the problem.

---

