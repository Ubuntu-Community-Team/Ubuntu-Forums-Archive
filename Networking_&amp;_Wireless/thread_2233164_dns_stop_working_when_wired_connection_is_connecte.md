---
title: "dns stop working when wired connection is connected"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by frohfroh on 2014-07-06
I have a wireless connection that gives me access to the internet that works fine.
I want to connect to a router(that is not connected to the internet) through the wired connection. However, when the wired connection is connected, ping to any url gives no answer. If I try to ping an IP it does work fine.
I tried to check the box "Require IPv4 addressing for this connection to complete" and "Use this connection only for resources in its network" as suggested in multiple threads , but it does not help.
I tried also to uncomment the prepend domain-name-servers 127.0.0.1 on /etc/dhcp/dhclient.conf but it did not help either.
The wired connection Method is Manual and the wireless is Automatic(DHCP)
Can anyone help me?

---

### Post by varunendra on 2014-07-07
Please post the outputs of -
```
route -n
nm-tool
```
..from both states. That is - with and without the wired connection.

---

### Post by frohfroh on 2014-07-07
Thanks for answering.
Without the wired connection:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [NOTERITA2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        94:39:E5:5A:AC:9E

  Capabilities:
    Speed:           57 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CALDER:          Infra, B0:48:7A:B4:E2:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    TIM Wi-Fi SIM:   Infra, DC:A5:F4:05:DB:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    ProcopioHome:    Infra, 00:22:3F:67:B0:B2, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WEP
    #NET-GUEST:      Infra, 0C:85:25:35:5E:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    *NOTERITA2:      Infra, 34:8A:AE:11:AD:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    CLARO-WIFI2:     Infra, 0C:85:25:35:5E:E3, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    NET-VIRTUA-WIFI: Infra, 0C:85:25:35:5E:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    TIM Wi-Fi:       Infra, DC:A5:F4:05:DB:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    CLARO-WIFI:      Infra, 0C:85:25:35:5E:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    A&E:             Infra, 7C:D1:C3:C9:59:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Australia:       Infra, FC:B0:C4:99:8A:AE, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Rede Vida:       Infra, 00:24:36:A7:6D:53, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ProcopioHome:    Infra, 1C:7E:E5:BE:42:B2, Freq 2442 MHz, Rate 54 Mb/s, Strength 25 WEP

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             127.0.0.1
    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        2C:41:38:62:F7:35

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```


With the wired connection:
```
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [NOTERITA2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        94:39:E5:5A:AC:9E

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CALDER:          Infra, B0:48:7A:B4:E2:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    TIM Wi-Fi SIM:   Infra, DC:A5:F4:05:DB:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    ProcopioHome:    Infra, 00:22:3F:67:B0:B2, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WEP
    #NET-GUEST:      Infra, 0C:85:25:35:5E:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    *NOTERITA2:      Infra, 34:8A:AE:11:AD:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    CLARO-WIFI2:     Infra, 0C:85:25:35:5E:E3, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    NET-VIRTUA-WIFI: Infra, 0C:85:25:35:5E:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    TIM Wi-Fi:       Infra, DC:A5:F4:05:DB:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    CLARO-WIFI:      Infra, 0C:85:25:35:5E:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    A&E:             Infra, 7C:D1:C3:C9:59:2A, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Australia:       Infra, FC:B0:C4:99:8A:AE, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Rede Vida:       Infra, 00:24:36:A7:6D:53, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ProcopioHome:    Infra, 1C:7E:E5:BE:42:B2, Freq 2442 MHz, Rate 54 Mb/s, Strength 25 WEP
    maxhaus Vl Olimpia: Infra, 64:70:02:93:70:26, Freq 2452 MHz, Rate 48 Mb/s, Strength 22 WPA2
    CLARO-WIFI2:     Infra, 0C:85:25:34:DB:63, Freq 2437 MHz, Rate 54 Mb/s, Strength 22

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             127.0.0.1
    DNS:             192.168.1.1


- Device: eth0  [RoteadorOpenwrt] ----------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           no
  HW Address:        2C:41:38:62:F7:35

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         255.255.255.0


```

---

### Post by Iowan on 2014-07-07
Must the wired router use the 192.168.1.X subnet?
Having two interfaces (eth0 and wlan0) in the same subnet may not work well.

---

### Post by frohfroh on 2014-07-07
Thanks a lot!
Problem solved now

---

### Post by Iowan on 2014-07-07
What fixed it?

---

### Post by frohfroh on 2014-07-08
your advice (changed router ip to 192.168.2.1). Thanks once again

---

