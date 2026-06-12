---
title: "Ubuntu 14.04 LTS &amp; WPA2 connections"
date: 2014-10-21
forum: Networking &amp; Wireless
---

### Post by RichardET on 2014-10-21
I have a secondary computer, a Lenovo B590, which I like to use quite often and in general it works very well with Ubuntu, but there are times when trying to connect to a WPA2 connection is impossible;  this never happens with a WEP connection.  What is the deal with WPA2?  I am almost entirely certain the fault lies with Ubuntu;  My Win. 8.1 laptop never has wirteless connection issues with any router.  To be fair, I cannot try the B590 as a Windows box, so we will never know for sure, but it is my suspicion.

---

### Post by jeremy31 on 2014-10-21
Does ```
nm-tool
``` reveal anything about WPA2 under Wireless Properties?

---

### Post by grahammechanical on 2014-10-21
What exactly is the problem? WPA2 is really only a better method of encryption than WEP. A security protocol in fact. I doubt very much if the problem is with Ubuntu. It may be that the wireless adapter in the laptop is not capable of WPA2 security. Or there may be a setting in the BIOS that enables it. Guessing is the best that I can give.

Regards.

---

### Post by RichardET on 2014-10-21
> **jeremy31 said:**
> Does ```
nm-tool
``` reveal anything about WPA2 under Wireless Properties?

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        3C:97:0E:88:66:07

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [5DYL5] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        1C:3E:84:06:63:C9

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Amped_WiFi_2.4:  Infra, F8:7B:8C:18:D6:87, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    tangled:         Infra, 58:6D:8F:97:BB:9D, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    chilang:         Infra, C0:C1:C0:67:07:02, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Andy-Home:       Infra, 8C:04:FF:3B:74:F3, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Prasad_Guest1:   Infra, 30:85:A9:E7:7E:E1, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Guest Network:   Infra, 8A:12:3A:35:A1:10, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    NSEALM52:        Infra, 88:1F:A1:35:3A:12, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Amped_2.4GHz_Guest_1: Infra, F8:7B:8C:18:D6:88, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    linksys:         Infra, 00:1E:E5:3D:46:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    *5DYL5:          Infra, 00:1F:90:B3:F1:EC, Freq 2412 MHz, Rate 54 Mb/s, Strength 61 WEP
    Prasad_Guest3:   Infra, 30:85:A9:E7:7E:E3, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Prasad_Guest2:   Infra, 30:85:A9:E7:7E:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Q4CXK:           Infra, 00:26:B8:AB:AD:25, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WEP
    PS_Home-guest:   Infra, 58:6D:8F:3E:1D:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    8KMA4:           Infra, 00:1F:90:D6:00:54, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
    Ambre:           Infra, 00:1F:90:B7:19:E8, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WEP

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

---

### Post by RichardET on 2014-11-13
I updated to Ubuntu 14.10 and wireless issues vanished.

---

### Post by Bucky Ball on 2014-11-13
Please mark the thread as solved, even though it was more a case of 'resolved' by the upgrade. Thanks.

---

