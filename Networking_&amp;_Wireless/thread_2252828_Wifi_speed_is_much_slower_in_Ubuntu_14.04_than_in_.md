---
title: "Wifi speed is much slower in Ubuntu 14.04 than in Windows 8"
date: 2014-11-14
forum: Networking &amp; Wireless
---

### Post by Shiyang_Fei on 2014-11-14
Hi,

I am a new Ubuntu user. I installed Ubuntu together with Win 8 on the same machine.
So far, I like Ubuntu system but I detected the wifi speed is very slow. In the speed test, download speed test shows only 1.30 Mbps (It is 8.50 Mbps in Win 8 on the same machine). The real download speed is about 100~200KB/S. I have browsed the forum and tried a lot of methods but cannot fix it. Could you please help? All tech details are as below. Thanks.

[B][SIZE=4]iwconfig[/SIZE]
[/B]
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"E63396"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:81:D8:E6:33:9C   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1126  Invalid misc:592   Missed beacon:0

```

[SIZE=4]**ifconfig**[/SIZE]
```

eth0      Link encap:Ethernet  HWaddr 4c:72:b9:58:74:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:282425 (282.4 KB)  TX bytes:282425 (282.4 KB)


wlan0     Link encap:Ethernet  HWaddr 74:e5:43:a2:14:c9  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8352675 (8.3 MB)  TX bytes:4094277 (4.0 MB)



```

[B][SIZE=4]nm-tool[/SIZE]

```
NetworkManager Tool


State: connected (global)


- Device: wlan0  [E63396] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        74:E5:43:A2:14:C9


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    19FE10:          Infra, EC:22:80:19:FE:14, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    Ramses:          Infra, 58:6D:8F:DF:84:9D, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    RMS:             Infra, 08:60:6E:BD:AE:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    Hoboken1993:     Infra, 20:4E:7F:00:B5:41, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    CJPAGR:          Infra, 9C:D3:6D:A0:D4:FA, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    DTFWG:           Infra, F8:E4:FB:8A:F6:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    CC75AD:          Infra, 84:1B:5E:CC:75:AC, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    AOSS-4225A915683:Infra, 16:6F:3F:0C:1D:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    optimumwifi:     Infra, EE:22:80:19:FE:15, Freq 2412 MHz, Rate 54 Mb/s, Strength 72
    optimumwifi:     Infra, A2:81:D8:E6:33:9C, Freq 2437 MHz, Rate 54 Mb/s, Strength 85
    optimumwifi:     Infra, 86:1B:5E:CC:75:AD, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    optimumwifi:     Infra, A2:81:D8:ED:48:04, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    optimumwifi:     Infra, 92:81:D8:E5:A3:64, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    *E63396:         Infra, 00:81:D8:E6:33:9C, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA WPA2
    DIRECT-roku-763-8A3CA0: Infra, B8:3E:59:DB:A4:35, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    062098:          Infra, F8:E9:03:06:20:9C, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    mayathomas:      Infra, 10:6F:3F:0C:1D:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Bubba:           Infra, 6C:19:8F:14:58:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    ED47FE:          Infra, 00:81:D8:ED:48:04, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    D66D66:          Infra, 84:1B:5E:D6:6D:65, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Farco Incorporated: Infra, 00:03:D8:B1:AA:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    HHHFJ:           Infra, F8:E4:FB:9B:5B:A3, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    E5A35E:          Infra, 00:81:D8:E5:A3:64, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    BA9FB4:          Infra, 00:03:D8:BA:9F:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    1B4668 2.4G:     Infra, EC:22:80:1B:46:6C, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    69C810:          Infra, 00:03:D8:69:C8:16, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    E156D6:          Infra, 00:81:D8:E1:56:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Force:           Infra, 00:1F:90:F7:63:38, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    Ramses-guest:    Infra, 58:6D:8F:DF:84:9F, Freq 2412 MHz, Rate 48 Mb/s, Strength 69
    optimumwifi:     Infra, FA:E9:03:06:20:9D, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    optimumwifi:     Infra, 9E:D3:6D:A0:D4:FB, Freq 2437 MHz, Rate 54 Mb/s, Strength 42
    optimumwifi:     Infra, 86:1B:5E:D6:6D:66, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    optimumwifi:     Infra, EE:22:80:1B:46:6D, Freq 2452 MHz, Rate 54 Mb/s, Strength 35
    optimumwifi:     Infra, 6E:19:8F:14:58:5F, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    optimumwifi:     Infra, A2:03:D8:69:C8:16, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    optimumwifi:     Infra, 92:03:D8:BA:9F:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    optimumwifi:     Infra, 92:81:D8:E1:56:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    HP-Print-48-LaserJet M1217: Infra, 60:D8:19:8A:04:48, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    optimumwifi:     Infra, A2:03:D8:B1:AA:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    optimumwifi:     Infra, B2:C5:54:D2:B3:AD, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    T-bone's Network:Infra, 00:23:6C:BE:E9:55, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    4D9A28:          Infra, 70:62:B8:4D:9A:2C, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    CA4B62:          Infra, 84:1B:5E:CA:4B:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    141C86:          Infra, 6C:19:8F:14:1C:8A, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    optimumwifi:     Infra, 6E:19:8F:16:ED:6F, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    optimumwifi:     Infra, B2:C5:54:CD:77:C7, Freq 2462 MHz, Rate 54 Mb/s, Strength 32
    S Square:        Infra, 58:6D:8F:9F:BA:99, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Fuad Zatzukal:   Infra, B0:C5:54:D0:F3:3C, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    3JWX7:           Infra, 4C:ED:DE:25:E2:8D, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP
    Singnet:         Infra, 20:4E:7F:3A:1B:A0, Freq 2417 MHz, Rate 54 Mb/s, Strength 62 WPA2
    Springfield:     Infra, 44:D8:84:6B:BB:2F, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Clinton1Low:     Infra, E0:3F:49:02:9B:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Tadpole-24G:     Infra, 30:46:9A:15:33:C1, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    LHZ82:           Infra, 00:26:62:39:A7:AE, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WEP
    Ward law:        Infra, EC:22:80:19:60:40, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    optimumwifi:     Infra, A2:81:D8:E3:EA:34, Freq 2412 MHz, Rate 54 Mb/s, Strength 32


  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        4C:72:B9:58:74:9C


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off





```[/B]

---

### Post by praseodym on 2014-11-15
Try deactivating the hardware encryption of the driver:
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

---

