---
title: "Wifi problem with ASUS x401a with Ralink 5390 and RT2860 driver"
date: 2016-06-21
forum: Networking &amp; Wireless
---

### Post by jon115 on 2016-06-21
I just upgraded my daughters ASUS x401a with Ubuntu 14.04 with the hope of getting more involve with linux operations.  However my wireless seems to have issues which it seems is pretty common when I looked at other threads.  Following the previous thread on this subject I documented the three commands iwconfig, nm-tool and rfkill list all with the hope someone can direct my on what to do next. I'm rather new/old and rather stay. Thanks!!! Jon  BTW the Ethernet wire works fine. :confused:

iwconfig: 

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=42/100  Signal level:-88 dBm  Noise level:-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.



nm-tool:
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:BF:48:6A:79:30

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off


- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        E0:06:E6:68:75:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR:         Infra, C0:3F:0E:57:1D:86, Freq 2462 MHz, Rate 54 Mb/s, Stre
ngth 22 WPA2
    HOME-6BC2:       Infra, 94:87:7C:41:6B:C0, Freq 2437 MHz, Rate 44 Mb/s, Stre
ngth 22 WPA WPA2
    xfinitywifi:     Infra, 96:87:7C:41:6B:C0, Freq 2437 MHz, Rate 44 Mb/s, Stre
ngth 22



NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        10:BF:48:6A:79:30

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             unavailable
  Default:           no
  HW Address:        E0:06:E6:68:75:E6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

rfkill list all

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
0: asus-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by jon115 on 2016-06-23
Can someone help me out. I'm learning that I don't have RT2860 and most likely reading other threads need RT2800 but having issues installing this. Please Help!!!

---

### Post by X-RED_Tech on 2016-06-23
> **jon115 said:**
> Can someone help me out. I'm learning that I don't have RT2860 and most likely reading other threads need RT2800 but having issues installing this. Please Help!!!


Apparently you do have it:
```
[COLOR=#000000]Type: 802.11 WiFi[/COLOR]
[COLOR=#000000]Driver: rt2860[/COLOR]
```

What issues are you having?

---

