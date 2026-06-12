---
title: "wifi is connecting but internet is not working"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by nav1729 on 2014-04-21
I have used Ubuntu 12.04 for 2 yrs on my laptop Lenovo G570. Now after new LTS release(14.04), I have made a fresh installation of the same.

Before installation I checked if the things or working using USB based booting. Wifi and other applications worked properly. 

After installation, computer is showing that wifi is connected but internet is not working. I have checked with my phone and friend's PC that internet is working.

My Laptop model - Lenovo G570
Operating system - Ubuntu 14.04

I know above details are not enough, please let me know what all other details are needed and how to get them.

---

### Post by Ubi_one_2014 on 2014-04-21
could be a DNS issue on your pc

are you aware of a manually dns change on your system?

---

### Post by The Cog on 2014-04-21
Let's start getting some basic info. Please can you open a command prompt and enter these 4 commands, and post the result:
```
ifconfig -a
route -n
ping -c3 91.189.94.12
ping -c3 ubuntuforums.org
```

---

### Post by nav1729 on 2014-04-21
> **Ubi_one_2014 said:**
> could be a DNS issue on your pc

are you aware of a manually dns change on your system?

there is no manual dns on the network.

I have tried to ping google dns 8.8.8.8, which is not working
I tried to ping router which is not working.


> **The Cog said:**
> Let's start getting some basic info. Please can you open a command prompt and enter these 4 commands, and post the result:
```
ifconfig -a
route -n
ping -c3 91.189.94.12
ping -c3 ubuntuforums.org
```

outputs are as follows
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:6c:9a:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:311873 (311.8 KB)  TX bytes:311873 (311.8 KB)

usb0      Link encap:Ethernet  HWaddr 7a:85:22:ac:24:ca  
          inet6 addr: fe80::7885:22ff:feac:24ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9380 errors:1 dropped:0 overruns:0 frame:1
          TX packets:7387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9132722 (9.1 MB)  TX bytes:1565209 (1.5 MB)

wlan0     Link encap:Ethernet  HWaddr e4:d5:3d:5c:10:ba  
          inet addr:192.168.2.16  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fe5c:10ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:834 errors:0 dropped:0 overruns:0 frame:102021
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75759 (75.7 KB)  TX bytes:100681 (100.6 KB)
          Interrupt:17 
```


```
route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```


```
ping -c3 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
From 192.168.2.16 icmp_seq=1 Destination Host Unreachable
From 192.168.2.16 icmp_seq=2 Destination Host Unreachable
From 192.168.2.16 icmp_seq=3 Destination Host Unreachable

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2009ms
pipe 2
```

```
ping -c3 ubuntuforums.org
ping: unknown host ubuntuforums.org
```

---

### Post by nav1729 on 2014-04-21
I came across this [script]("http://ubuntuforums.org/showthread.php?p=12350385#post12350385")

result of this script is 

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux naveen-Lenovo-G570 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: wl

##### lsusb #####

Bus 002 Device 003: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 013: ID 0fce:8172 Sony Ericsson Mobile Communications AB 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11abg  ESSID:"laila_teri_le_legi"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search Belkin

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

- Device: wlan0  [laila_teri_le_legi] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Bms220:          Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    MD2.4G:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Alfred14:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    parmar:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    MGMNT:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 54 WEP
    jyothi:          Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 52 WEP
    PrasadPurni:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    DIRECT-mH-BRAVIA:Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 82 WPA2
    Namek:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    c:\virus.exe:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    Bajaj:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    RamPriya:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    AKW5400:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WEP
    TVISHASHREE:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Rohitroy:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 25 WPA
    D-link:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WEP
    ruma:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    aravind:         Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 24 WPA2
    nagaraj:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2
    Our Home:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WEP
    KUMAR:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WEP
    saritha_auti:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WEP
    neesingh:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    pradeep:         Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    JD-INagar:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA
    vijay:           Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 12 WPA2
    r2d2:            Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 14 WPA2
    RAFAT:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WEP
    Krishna:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WEP
    *laila_teri_le_legi: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1
    DNS:             8.8.8.8

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"laila_teri_le_legi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00126C61696C615F746572695F6C655F6C656769
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010630412531019200612280000000000001021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-mH-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00104449524543542D6D482D425241564941
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C011BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1605000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD8B0050F204104A0001101044000102103B0001031047001000000000000010108000D8D43CA7893810210010536F6E7920436F72706F726174696F6E1023000B536F6E7920425241564941102400013010420001301054000800070050F204000110110012425241564941204B444C2D34325738353041100800020000103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"jyothi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00066A796F746869
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"parmar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 2352ms ago
                    IE: Unknown: 00067061726D6172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Namek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 2352ms ago
                    IE: Unknown: 00054E616D656B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B00010310470010FB5D4480BE35D086E4AEF07D6845366610210006442D4C696E6B102300074449522D363030102400074449522D3630301042000830303030303030301054000800060050F2040001101100074449522D363030100800020086
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MD2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 2352ms ago
                    IE: Unknown: 00064D44322E3447
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180205F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"RamPriya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000852616D5072697961
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160300190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340300010000000F000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B000103104700105DCF361A63B33829A79F8FE183BAB5C11021000E442D4C696E6B2053797374656D73102300074449522D363535102400024134104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F7574657210080002008C
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"nagaraj"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00076E61676172616A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010060FF7F
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 09 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706494E00010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 10 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"PrasadPurni"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000B5072617361645075726E69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"aravind"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000761726176696E64
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160C070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706494E00010D10
          Cell 13 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MGMNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00054D474D4E54
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706494E00010D10

##### iwlist channel #####

wlan0     26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.432 GHz (Channel 5)

##### lsmod #####

rndis_wlan             50281  0 
rndis_host             14503  1 rndis_wlan
usbnet                 43877  3 rndis_host,rndis_wlan,cdc_ether
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  2 wl,rndis_wlan

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.484541] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.487016] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   10.538530] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   10.672812] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  467.318835] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 5414.336231] ERROR @wl_dev_intvar_get : error (-1)
[ 5414.336237] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############
```

---

### Post by varunendra on 2014-04-22
> **nav1729 said:**
> ```

02:00.0 Network controller [0280]: Broadcom Corporation **BCM4313 802.11bgn Wireless Network Adapter [14e4:4727]** (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: **[COLOR="#FF0000"]wl[/COLOR]**
```

Please try this -
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot after this, and check the connectivity. If this helps, remember NOT to install the proprietary driver again suggested by "Additional Drivers" option.

The above alone should be enough to give you a working connection, but I would suggest to additionally do these as well -

**1)** Change the encryption type in your router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP which should be avoided.

**2)** Try changing the channel in the router to 1 or 11 and see if it improves the speed or signal quality. These channels usually offer better signal quality unless they are already too crowded.

---

### Post by nav1729 on 2014-04-22
thank a lot guys...

right on mark varunendra ji

your style of script to troubleshoot, i really like it being  a software engineer myself.

If you don't mind, can you explain how you concluded the issue from log

---

### Post by varunendra on 2014-04-22
> **nav1729 said:**
> If you don't mind, can you explain how you concluded the issue from log

Actually, it is not just the script report. The suggestion was based on mostly our (wireless troubleshooters here) collective experience with this card.

The device ID [14e4:4727] uniquely identifies this card. **[This table]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices")** tells us that it is supported by both the proprietary driver "wl" and the native driver "brcmsmac".

But most of us wireless troubleshooters here have had so much fun with this card that we don't need to look it up in that table. This card's ID and related problems/solution have been deeply imprinted in our memories. It used to work nicely with the "wl" driver in kernel 3.2 and older. But then the native driver "brcmsmac" became better and better with every kernel upgrade (some problems occurred in kernel 3.11 again, but they were fixed in newer ones), while the "wl" got worse (with this particular card).

Now as soon as we see kernel version 3.8 or higher + driver "wl" with this card (14e4:4727), our immediate reaction is the suggestion that I gave you. :)

**PS:**
By the way, I am so far only a user of the wireless_script. It's original developer is forum moderator Wild Man, and its current coding is mostly a generous contribution by forum member Krytarik. I am working on a newer version of the script, but first - I am way too lazy, and second - I'm not nearly as good as required to quickly and efficiently do what I want to do with it. Despite that, it is almost finished and I may propose it to Wild Man / Krytarik any day now. :)

---

### Post by nav1729 on 2014-04-22
thank you very much for quick explanation...

---

