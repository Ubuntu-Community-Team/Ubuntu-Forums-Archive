---
title: "Connect WiFi addapter on 5Ghz band only"
date: 2015-03-31
forum: Networking &amp; Wireless
---

### Post by rigged 00 on 2015-03-31
Hi

I have an onboard 802.11bgn addapter aswell as a USB dongle for 802.11abgn. Both work 100% with no problem.

On my USB dongle I can see all the bands 2.4Ghz & 5Ghz ranges - my problem is when I connect with the USB it initially connects to my SSID on 5Ghz but it doesn't take long then it drops to 2.4Ghz and stays there.
Is there anyway I can disable the 2.4Ghz (802.11bg) to only have the 5Ghz (802.11a) bands available or even just to force the dongle to only use the 5Ghz regardless of signal strength and quality?

_Below is some general info_:

Desktop = Kubuntu with KDE Plasma Worspace

```
root@Hendrik-HP:/home/hendrik# lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

```

```
 root@Hendrik-HP:/home/hendrik# iwconfig
wwan0     no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"tcm-net-wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 9C:1C:12:0F:7D:D1   
          Bit Rate=130 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:249  Invalid misc:116   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

```
root@Hendrik-HP:/home/hendrik# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 03f0:3d1d Hewlett-Packard 
Bus 001 Device 004: ID 04f2:b372 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 003 Device 003: ID 1435:0804 Wistron NeWeb AR9170+AR9104 802.11abgn Wireless Adapter**
Bus 003 Device 002: ID 17ef:6022 Lenovo 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
root@Hendrik-HP:/home/hendrik# nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan1  [TCM-NET-WIFI WLAN1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            carl9170
  State:             connected
  Default:           yes
  HW Address:        00:20:A6:C0:C2:3A

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    tcm-grp-wireless:Infra, 9C:1C:12:0F:7D:D8, Freq 5580 MHz, Rate 54 Mb/s, Strength 100 WPA2
    tcm-net-wireless:Infra, 9C:1C:12:0F:7D:D9, Freq 5580 MHz, Rate 54 Mb/s, Strength 100 WPA2
    HCNET:           Infra, 18:64:72:73:B4:EB, Freq 5660 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:8F:58, Freq 5240 MHz, Rate 54 Mb/s, Strength 55 WPA2
    tcm-grp-wireless:Infra, 9C:1C:12:0F:7D:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA2
    tcm-net-wireless:Infra, 6C:F3:7F:DB:8F:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:8F:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    HCNET:           Infra, 18:64:72:73:B4:E3, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    HCDOC:           Infra, 18:64:72:73:B4:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    tcm-guest-wireless: Infra, 9C:1C:12:0F:7D:DA, Freq 5580 MHz, Rate 54 Mb/s, Strength 100
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:8F:59, Freq 5240 MHz, Rate 54 Mb/s, Strength 54
    tcm-guest-wireless: Infra, 9C:1C:12:0F:7D:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:8F:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
    tcm-guest-wireless: Infra, 6C:F3:7F:C6:0A:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    HCGUEST:         Infra, 18:64:72:73:B4:E4, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    tcm-net-wireless:Infra, 6C:F3:7F:C6:0A:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    tcm-grp-wireless:Infra, 6C:F3:7F:C6:0A:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2
    tcm-net-wireless:Infra, 6C:F3:7F:DB:8F:5A, Freq 5240 MHz, Rate 54 Mb/s, Strength 55 WPA2
    *tcm-net-wireless: Infra, 9C:1C:12:0F:7D:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA2
    HCDOC:           Infra, 18:64:72:73:B4:E8, Freq 5660 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    tcm-net-wireless:Infra, 6C:F3:7F:DB:88:B2, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Mustek W:        Infra, 06:19:BE:00:0F:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 34 WEP
    tcm-net-wireless:Infra, 6C:F3:7F:DB:8F:5A, Freq 5200 MHz, Rate 54 Mb/s, Strength 59 WPA2
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:09:88, Freq 5500 MHz, Rate 54 Mb/s, Strength 27 WPA2
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:09:89, Freq 5500 MHz, Rate 54 Mb/s, Strength 25
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:8C:B8, Freq 5260 MHz, Rate 54 Mb/s, Strength 29 WPA2
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:8C:B9, Freq 5260 MHz, Rate 54 Mb/s, Strength 27
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:88:B8, Freq 5260 MHz, Rate 54 Mb/s, Strength 25 WPA2
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:8E:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:88:B9, Freq 5260 MHz, Rate 54 Mb/s, Strength 29
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:8E:C1, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    tcm-net-wireless:Infra, 6C:F3:7F:DB:0B:92, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA2
    tcm-grp-wireless:Infra, 6C:F3:7F:DB:0B:90, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    HLET:           Infra, 18:64:72:73:B4:E3, Freq 2412 MHz, Rate 18 Mb/s, Strength 42 WEP
    tcm-guest-wireless: Infra, 6C:F3:7F:DB:0B:91, Freq 2462 MHz, Rate 54 Mb/s, Strength 34

  IPv4 Settings:
    Address:         172.16.0.38
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.0.8

    DNS:             41.160.0.36
    DNS:             41.160.0.37
```

---

### Post by tgalati4 on 2015-03-31
Typically you would use a parameter switch to modify the behavior of the module that runs your wifi adapter.  Unfortunately, I don't see much available:

```
modinfo carl9170
```

If you give your 2.4 GHz network a different name (SSID) then you can set up NetworkManager to log into the 5GHz but not the 2.4GHz SSID.

```
man NetworkManager.conf
```

5GHz typically has less interference than the crowded 2.4GHz band, but you get less range at the higher frequency for the same transmitter power level.  I live in an area with a crowded 2.4GHz neighborhood and I have 2 laptops that constantly start at 5GHz and then drop to 2.4GHz.  I can manually set nm to ignore the 2.4GHz, but then the 5GHz throughput drops to low speed, so it is a tradeoff.

---

### Post by rigged 00 on 2015-04-07
Hi tgalati4

THX for the advice - strange, my exact behaviour is similar where I also start at 5Ghz and then drop to 2.4Ghz (my windows clients do not have this issue - if they connect at 5 they stay on 5).

At the moment I have created a 5G only SSID, however this is not the ideal solution (less SSID's in either spectrum is better).

I also noticed a weak poor quality signal reported on the 5G portion when I initially connect to the Dual Band SSID -- however, once again, my windows and Mac clients do not report or experience this issue.

When you say you use nm to ignore your 2.4GHz  how is that done? I do not see such an option when going through my nm.
Perhaps you can point me to the nm you use -- I am using the normal KDE NM, in it's about it states the following: 
Connection Editor Version 0.9.3.3
Using NM version: 0.9.8.8

---

