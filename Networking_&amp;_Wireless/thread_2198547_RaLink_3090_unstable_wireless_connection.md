---
title: "RaLink 3090 unstable wireless connection"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by tgntrr on 2014-01-09
Recently I moved from Windows, and since I installed a Linux distro(I'm using Xubuntu 13.10) my wireless connection is uncommonly slow (~50kb/s from ~2mb/s). I got no problems using wired Internet from the same router. I've read about alot of possible issues around the web the past couple of days, i tried disabling ipv6 and n connection, wicd, edited nsswitch.conf, did wlan0 power off, got rt2800 firmware pack(i think that here is the problem, no fix found tho), checked blacklist, modified channel and dns and etc.
What i got is, that every time i connect to my wireless network my internet is good for the first 1-2 minutes, then it drops. I think that this would explain the problem to a person, that is into network and wireless.
Thanks!

---

### Post by tfrue on 2014-01-09
Would you be so kind to post the output of:
```
sudo lshw -C network
lspci | grep Network
and 
sudo nm-tool
```

Thanks,
Chris

---

### Post by tgntrr on 2014-01-09
here it is
```
sudo lshow -C network     *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:5e:b6:cf
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:44 memory:d0500000-d053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 94:39:e5:87:68:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.12.0-031200-generic firmware=0.34 ip=172.16.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0400000-d040ffff
```

```
[COLOR=#000000][FONT=Ubuntu Mono]lspci | grep Network
[/FONT][/COLOR]02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
```

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo nm-tool[/FONT][/COLOR]
State: connected (global)


- Device: wlan0  [Tugg] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        94:39:E5:87:68:7E


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    varbanov701012:  Infra, 64:70:02:EB:CF:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2
    Sladko i Soleno: Infra, 90:F6:52:E8:A4:68, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    IVO:             Infra, 00:25:86:CF:79:C6, Freq 2427 MHz, Rate 54 Mb/s, Strength 55 WPA
    ivanov:          Infra, C8:D3:A3:4F:13:44, Freq 2472 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Richi:           Infra, 64:66:B3:D3:2E:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    10lv/mesec:      Infra, 00:26:5A:B2:18:42, Freq 2457 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    zuzka:           Infra, F8:D1:11:64:E0:E8, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    *Tugg:           Infra, 64:66:B3:F7:7D:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    BDK WIFI:        Infra, 64:70:02:3D:31:2C, Freq 2442 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    www.networx-bg.com: Infra, 62:66:B3:F7:7D:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    www.networx-bg.com: Infra, 62:70:02:EB:CF:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 65
    www.networx-bg.com: Infra, 00:18:39:D4:2E:3D, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    www.networx-bg.com: Infra, 62:66:B3:D3:2E:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    MITAKA:          Infra, 64:68:0C:26:74:F7, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA
    tneuf:           Infra, F8:1A:67:3F:53:32, Freq 2442 MHz, Rate 54 Mb/s, Strength 62 WPA2
    www.networx-bg.com: Infra, FA:1A:67:3F:53:32, Freq 2442 MHz, Rate 54 Mb/s, Strength 69
    sintra-home:     Infra, B0:48:7A:CE:74:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    www.networx-bg.com: Infra, 00:12:0E:B5:B3:A6, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    www.networx-bg.com-05: Infra, B6:48:7A:CE:83:7A, Freq 2457 MHz, Rate 54 Mb/s, Strength 42
    hpsetup:         Ad-Hoc, AA:25:B3:92:3D:C5, Freq 2437 MHz, Rate 54 Mb/s, Strength 32


  IPv4 Settings:
    Address:         172.16.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.1.1


    DNS:             212.25.58.2
    DNS:             212.25.58.8




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        DC:0E:A1:5E:B6:CF


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off
```

---

### Post by varunendra on 2014-01-13
Hello tgntrr,

Please follow the advice in this thread : [http://ubuntuforums.org/showthread.php?t=2195144](http://ubuntuforums.org/showthread.php?t=2195144)

If it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions in the linked post, and post back the report it generates.

---

