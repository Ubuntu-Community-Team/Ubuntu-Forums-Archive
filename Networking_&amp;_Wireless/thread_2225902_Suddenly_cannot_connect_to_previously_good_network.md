---
title: "Suddenly cannot connect to previously good network, no updates, Ubuntu 12.04"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by loganetherton on 2014-05-24
OK, so, I've been using my home connection for about 2 weeks now in a new place. Everything worked fine until tonight. In the middle of work, the wireless disconnected, and refused to reconnect. The connection shows up as available, and when I attempt to connect, the connection animation shows for about 10 seconds, after which I'm asking for a password. After giving the password, the same process repeats.

I am able to connect without a problem to my phone as a wifi hotspot. I find it particularly puzzling, as this happened not after an update, not after something changed on the network, but just suddenly.

Things I've done:
1) Since I'm using ath9k, I disabled hwcrpyt, as follows:
```

sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
No luck.
2) Used modprobe to disabled 11n, as follows:
```

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```
No luck.
3) Looked into altering power settings. Rather than do this blindly, I opted to ask for advice.
4) Looked into getting backports drivers. Again, this is beyond the scope of my experience, and as I've messed things up before this way, I left it alone until I had a better idea of what I'm doing.

So, before spending any more time blindly Googling, I thought I'd ask for some help from those who may know better than I.

The output of the wireless script as recommended in the sticky is below. Thanks in advance.
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux logan-N56VZ 3.8.0-39-generic #58~precise1-Ubuntu SMP Fri May 2 21:33:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
    Subsystem: ASUSTeK Computer Inc. N56VZ [1043:1477]
    Kernel driver in use: alx

##### lsusb #####

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:0a37 Logitech, Inc. 
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 003: ID 0bc2:2320 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 13d3:3362 IMC Networks 
Bus 001 Device 004: ID 064e:d213 Suyin Corp. 

##### PCMCIA Card Info #####

##### rfkill #####

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
4: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"AndroidTether"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:19  Invalid misc:79   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [AndroidTether 1] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Howieuga:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Router, I Hardly Know Her: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    lysaght:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    mark-wifi:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA
    Silver Fern:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    cocobutter:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    lemmon:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    WhachuTalkinBoutWireless?: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    *AndroidTether:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    True Colors :    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    bcf2222222:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    NETGEAR03:       Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Silverspoon:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Lilypad:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    #201:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    SallyL1:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2

  IPv4 Settings:
    Address:         192.168.2.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.254

    DNS:             192.168.2.254

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
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
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"AndroidTether"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000007edf51e8
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000D416E64726F6964546574686572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23020E00
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A20101AFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F202010184000364000027A4000041435E0061322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"lemmon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000757eb6195
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 00066C656D6D6F6E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Router, I Hardly Know Her"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010bbdccdb5
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 0019526F757465722C204920486172646C79204B6E6F7720486572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"lemmon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000757b6759d
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00066C656D6D6F6E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1ABD1817FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010512043CFCEBC03AD624DFFCF6ACAC41B102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"cocobutter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ed1de21ac4
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000A636F636F627574746572
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502002C127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545700010B10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DDB80050F204104A0001101044000102103B00010310470010BC329E001DD811B2860108863B25BF621021001442656C6B696E20496E7465726E6174696F6E616C1023001D42656C6B696E204E373530444220576972656C65737320526F757465721024000A46394B313130332076311042000E31323131313847473130373231301054000800060050F20400011011001D42656C6B696E204E373530444220576972656C65737320526F75746572100800020084103C000101
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"lysaght"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fa45e40207
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00076C797361676874
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010B9C0451DC20E713098C6E5DC3D5B81441021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180205F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"True Colors "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000109f47f4183
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 000C5472756520436F6C6F727320
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Silver Fern"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004faaeb1f8f9
                    Extra: Last beacon: 660ms ago
                    IE: Unknown: 000B53696C766572204665726E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706545700010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860108863BD698C0103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030021127A
                    IE: Unknown: DD07000C4307000000
          Cell 09 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"MiaJoey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000423747b4db4
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00074D69614A6F6579
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD890050F204104A0001101044000102103B00010310470010CFBF598FC448DB55BE2E1EEB57AE62711021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010bbb2a6a3
                    Extra: Last beacon: 3016ms ago
                    IE: Unknown: 00200000000000000000000000000000000000000000000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Silverspoon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002abf150545f
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000B53696C76657273706F6F6E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020010127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880F8EDA522EFD010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 12 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR03"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001267d2eeb74
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00094E4554474541523033
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD890050F204104A0001101044000102103B00010310470010D5A9A403F8401399D935BF6480AF3D521021000D4E4554474541522C20496E632E1023000A574E44523334303076331024000A574E44523334303076331042000230311054000800060050F20400011011000A574E4452333430307633100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Howieuga"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d0e272421
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0008486F776965756761
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD680050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100045562656510230004556265651024000631323334353610420007303030303030311054000800060050F204000110110006556265654150100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WhachuTalkinBoutWireless?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005b76f006186
                    Extra: Last beacon: 1096ms ago
                    IE: Unknown: 001957686163687554616C6B696E426F7574576972656C6573733F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD0E0017F20700010106B88D126355ED
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c8d559a009
                    Extra: Last beacon: 1064ms ago
                    IE: Unknown: 00200000000000000000000000000000000000000000000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"mark-wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c8d559a613
                    Extra: Last beacon: 1064ms ago
                    IE: Unknown: 00096D61726B2D77696669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### lsmod #####

ath9k                 152312  0 
mac80211              631446  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              422615  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
iwlwifi               187941  0 
ath3k                  12968  0 
bluetooth             247324  15 bnep,rfcomm,ath3k,btusb
cfg80211              526422  4 ath9k,mac80211,ath,iwlwifi

##### modinfo #####

filename:       /lib/modules/3.8.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E312829772C1F7035ACC133
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-39-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

filename:       /lib/modules/3.8.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-39-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     CCE4DE0B5B797FACEF3BB03
depends:        ath
intree:         Y
vermagic:       3.8.0-39-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-39-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
srcversion:     5A113A7294F746786C0EDF7
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-39-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)

filename:       /lib/modules/3.8.0-39-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     5C844657111492DE4FF295C
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.8.0-39-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

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

[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331
blacklist nvidia-334
blacklist nvidia-334-updates
blacklist nvidia-experimental-334
blacklist nvidia-337
blacklist nvidia-337-updates
blacklist nvidia-experimental-337

##### udev rules #####

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    9.013599] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[    9.096105] ath: EEPROM regdomain: 0x60
[    9.096107] ath: EEPROM indicates we should expect a direct regpair map
[    9.096108] ath: Country alpha2 being used: 00
[    9.096109] ath: Regpair used: 0x60
[   21.210788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.213757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.937212] wlan0: authenticate with <MAC address removed>
[   24.947064] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.148145] wlan0: send auth to <MAC address removed> (try 2/3)
[   25.352018] wlan0: send auth to <MAC address removed> (try 3/3)
[   25.555893] wlan0: authentication with <MAC address removed> timed out
[   25.700110] wlan0: authenticate with <MAC address removed>
[   25.713520] wlan0: direct probe to <MAC address removed> (try 1/3)
[   25.915753] wlan0: direct probe to <MAC address removed> (try 2/3)
[   26.119644] wlan0: direct probe to <MAC address removed> (try 3/3)
[   26.323495] wlan0: authentication with <MAC address removed> timed out
[   29.947089] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   88.532113] wlan0: authenticate with <MAC address removed>
[   88.542400] wlan0: send auth to <MAC address removed> (try 1/3)
[   88.743485] wlan0: send auth to <MAC address removed> (try 2/3)
[   88.947391] wlan0: send auth to <MAC address removed> (try 3/3)
[   89.151268] wlan0: authentication with <MAC address removed> timed out
[   90.259167] wlan0: authenticate with <MAC address removed>
[   90.269494] wlan0: direct probe to <MAC address removed> (try 1/3)
[   90.470568] wlan0: direct probe to <MAC address removed> (try 2/3)
[   90.674461] wlan0: direct probe to <MAC address removed> (try 3/3)
[   90.878357] wlan0: authentication with <MAC address removed> timed out
[   93.541275] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  112.655816] wlan0: authenticate with <MAC address removed>
[  112.666313] wlan0: send auth to <MAC address removed> (try 1/3)
[  112.867100] wlan0: send auth to <MAC address removed> (try 2/3)
[  113.070992] wlan0: send auth to <MAC address removed> (try 3/3)
[  113.274888] wlan0: authentication with <MAC address removed> timed out
[  114.387127] wlan0: authenticate with <MAC address removed>
[  114.397320] wlan0: direct probe to <MAC address removed> (try 1/3)
[  114.598224] wlan0: direct probe to <MAC address removed> (try 2/3)
[  114.802090] wlan0: direct probe to <MAC address removed> (try 3/3)
[  115.005972] wlan0: authentication with <MAC address removed> timed out
[  117.666429] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  183.247463] wlan0: authenticate with <MAC address removed>
[  183.257931] wlan0: send auth to <MAC address removed> (try 1/3)
[  183.458853] wlan0: send auth to <MAC address removed> (try 2/3)
[  183.662775] wlan0: send auth to <MAC address removed> (try 3/3)
[  183.866656] wlan0: authentication with <MAC address removed> timed out
[  184.975505] wlan0: authenticate with <MAC address removed>
[  184.985150] wlan0: direct probe to <MAC address removed> (try 1/3)
[  185.185969] wlan0: direct probe to <MAC address removed> (try 2/3)
[  185.389894] wlan0: direct probe to <MAC address removed> (try 3/3)
[  185.593761] wlan0: authentication with <MAC address removed> timed out
[  188.257988] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  229.635769] wlan0: authenticate with <MAC address removed>
[  229.646053] wlan0: send auth to <MAC address removed> (try 1/3)
[  229.648305] wlan0: authenticated
[  229.651147] wlan0: associate with <MAC address removed> (try 1/3)
[  229.662611] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  229.662672] wlan0: associated
[  229.662686] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  229.704906] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  522.876711] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  523.043373] wlan0: Trigger new scan to find an IBSS to join
[  526.086079] wlan0: Trigger new scan to find an IBSS to join
[  529.112566] wlan0: Trigger new scan to find an IBSS to join
[  535.550180] wlan0: authenticate with <MAC address removed>
[  535.566671] wlan0: send auth to <MAC address removed> (try 1/3)
[  535.568676] wlan0: authenticated
[  535.569875] wlan0: associate with <MAC address removed> (try 1/3)
[  535.581612] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  535.581676] wlan0: associated
[  535.621135] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  622.923640] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  623.030301] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  623.122718] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  623.122850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  625.926743] wlan0: authenticate with <MAC address removed>
[  625.935779] wlan0: send auth to <MAC address removed> (try 1/3)
[  625.937741] wlan0: authenticated
[  625.940676] wlan0: associate with <MAC address removed> (try 1/3)
[  625.952092] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  625.952141] wlan0: associated
[  625.952165] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  625.993826] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  632.368758] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  633.493401] wlan0: authenticate with <MAC address removed>
[  633.503653] wlan0: direct probe to <MAC address removed> (try 1/3)
[  633.704605] wlan0: direct probe to <MAC address removed> (try 2/3)
[  633.908604] wlan0: direct probe to <MAC address removed> (try 3/3)
[  634.112597] wlan0: authentication with <MAC address removed> timed out
[  638.505964] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  704.550189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  710.535916] wlan0: authenticate with <MAC address removed>
[  710.546595] wlan0: send auth to <MAC address removed> (try 1/3)
[  710.548613] wlan0: authenticated
[  710.551582] wlan0: associate with <MAC address removed> (try 1/3)
[  710.563107] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  710.563174] wlan0: associated
[  710.563190] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  710.653681] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  715.430906] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  716.556901] wlan0: authenticate with <MAC address removed>
[  716.566564] wlan0: send auth to <MAC address removed> (try 1/3)
[  716.767520] wlan0: send auth to <MAC address removed> (try 2/3)
[  716.971555] wlan0: send auth to <MAC address removed> (try 3/3)
[  717.175511] wlan0: authentication with <MAC address removed> timed out
[  717.318864] wlan0: authenticate with <MAC address removed>
[  717.335665] wlan0: direct probe to <MAC address removed> (try 1/3)
[  717.539508] wlan0: direct probe to <MAC address removed> (try 2/3)
[  717.743489] wlan0: direct probe to <MAC address removed> (try 3/3)
[  717.947499] wlan0: authentication with <MAC address removed> timed out
[  721.567527] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  739.435644] wlan0: authenticate with <MAC address removed>
[  739.446036] wlan0: send auth to <MAC address removed> (try 1/3)
[  739.448024] wlan0: authenticated
[  739.451194] wlan0: associate with <MAC address removed> (try 1/3)
[  739.462691] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  739.462735] wlan0: associated
[  739.497054] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[  744.195889] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  749.464243] wlan0: authenticate with <MAC address removed>
[  749.474115] wlan0: direct probe to <MAC address removed> (try 1/3)
[  749.675088] wlan0: direct probe to <MAC address removed> (try 2/3)
[  749.879060] wlan0: direct probe to <MAC address removed> (try 3/3)
[  750.083045] wlan0: authentication with <MAC address removed> timed out
[  754.475453] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  782.715247] wlan0: authenticate with <MAC address removed>
[  782.725685] wlan0: send auth to <MAC address removed> (try 1/3)
[  782.727657] wlan0: authenticated
[  782.730632] wlan0: associate with <MAC address removed> (try 1/3)
[  782.742022] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  782.742082] wlan0: associated
[  782.789938] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 1115.527447] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1115.636051] ath9k: ath9k: Driver unloaded
[ 1122.146553] ath: EEPROM regdomain: 0x60
[ 1122.146554] ath: EEPROM indicates we should expect a direct regpair map
[ 1122.146556] ath: Country alpha2 being used: 00
[ 1122.146557] ath: Regpair used: 0x60
[ 1122.171613] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1122.175364] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1124.967734] wlan0: authenticate with <MAC address removed>
[ 1124.977466] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1124.980863] wlan0: authenticated
[ 1124.982358] wlan0: associate with <MAC address removed> (try 1/3)
[ 1125.002790] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1125.002872] wlan0: associated
[ 1125.002925] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1125.039535] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 1131.569486] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1132.699348] wlan0: authenticate with <MAC address removed>
[ 1132.709410] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1132.910310] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1133.114180] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1133.318105] wlan0: authentication with <MAC address removed> timed out
[ 1137.709406] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1166.250373] wlan0: authenticate with <MAC address removed>
[ 1166.261213] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1166.263187] wlan0: authenticated
[ 1166.266048] wlan0: associate with <MAC address removed> (try 1/3)
[ 1166.277456] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1166.277520] wlan0: associated
[ 1166.285994] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 1934.145267] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1949.311450] wlan0: authenticate with <MAC address removed>
[ 1949.321848] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1949.522688] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1949.726620] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1949.930485] wlan0: authentication with <MAC address removed> timed out
[ 1950.075146] wlan0: authenticate with <MAC address removed>
[ 1950.091986] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1950.294313] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1950.498226] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1950.702103] wlan0: authentication with <MAC address removed> timed out
[ 1954.320305] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1969.317241] wlan0: authenticate with <MAC address removed>
[ 1969.327440] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1969.329907] wlan0: authenticated
[ 1969.332516] wlan0: associate with <MAC address removed> (try 1/3)
[ 1969.346665] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1969.346712] wlan0: associated
[ 1969.406541] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 3175.277763] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3180.419770] wlan0: authenticate with <MAC address removed>
[ 3180.430152] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3180.631175] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3180.835071] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3181.038991] wlan0: authentication with <MAC address removed> timed out
[ 3181.183711] wlan0: authenticate with <MAC address removed>
[ 3181.200530] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3181.402786] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3181.606688] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3181.810579] wlan0: authentication with <MAC address removed> timed out
[ 3185.430200] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3216.549804] wlan0: authenticate with <MAC address removed>
[ 3216.559897] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3216.561853] wlan0: authenticated
[ 3216.564717] wlan0: associate with <MAC address removed> (try 1/3)
[ 3216.576088] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3216.576137] wlan0: associated
[ 3216.609831] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 3362.487251] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3362.576959] ath9k: ath9k: Driver unloaded
[ 3369.394595] ath: EEPROM regdomain: 0x60
[ 3369.394597] ath: EEPROM indicates we should expect a direct regpair map
[ 3369.394599] ath: Country alpha2 being used: 00
[ 3369.394600] ath: Regpair used: 0x60
[ 3369.411750] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3369.415493] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3372.220866] wlan0: authenticate with <MAC address removed>
[ 3372.230365] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3372.232340] wlan0: authenticated
[ 3372.235267] wlan0: associate with <MAC address removed> (try 1/3)
[ 3372.246667] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3372.246725] wlan0: associated
[ 3372.246753] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3372.280074] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 3377.128747] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3378.256775] wlan0: authenticate with <MAC address removed>
[ 3378.267231] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3378.468069] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3378.671972] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3378.875859] wlan0: authentication with <MAC address removed> timed out
[ 3383.268336] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3432.284142] wlan0: authenticate with <MAC address removed>
[ 3432.294611] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3432.296581] wlan0: authenticated
[ 3432.299438] wlan0: associate with <MAC address removed> (try 1/3)
[ 3432.310873] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3432.310932] wlan0: associated
[ 3432.358046] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 3673.870054] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3674.991649] wlan0: authenticate with <MAC address removed>
[ 3675.002199] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3675.203031] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3675.406926] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3675.610840] wlan0: authentication with <MAC address removed> timed out
[ 3675.755336] wlan0: authenticate with <MAC address removed>
[ 3675.772109] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3675.974644] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3676.178551] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3676.382441] wlan0: authentication with <MAC address removed> timed out
[ 3680.000291] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3740.466099] wlan0: authenticate with <MAC address removed>
[ 3740.476576] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3740.677457] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3740.881319] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3741.085240] wlan0: authentication with <MAC address removed> timed out
[ 3742.193115] wlan0: authenticate with <MAC address removed>
[ 3742.203671] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3742.404537] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3742.608436] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3742.812352] wlan0: authentication with <MAC address removed> timed out
[ 3745.476653] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3792.231990] wlan0: authenticate with <MAC address removed>
[ 3792.242056] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3792.244014] wlan0: authenticated
[ 3792.246937] wlan0: associate with <MAC address removed> (try 1/3)
[ 3792.258331] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3792.258390] wlan0: associated
[ 3792.313610] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>
[ 5092.264148] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5100.528824] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5103.332627] wlan0: authenticate with <MAC address removed>
[ 5103.342499] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5103.543335] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5103.747239] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5103.951125] wlan0: authentication with <MAC address removed> timed out
[ 5108.340935] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5193.150301] wlan0: authenticate with <MAC address removed>
[ 5193.160406] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5193.361240] wlan0: send auth to <MAC address removed> (try 2/3)
[ 5193.565132] wlan0: send auth to <MAC address removed> (try 3/3)
[ 5193.769001] wlan0: authentication with <MAC address removed> timed out
[ 5194.877386] wlan0: authenticate with <MAC address removed>
[ 5194.887632] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5195.088352] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5195.292263] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5195.496119] wlan0: authentication with <MAC address removed> timed out
[ 5198.160476] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5257.349005] wlan0: authenticate with <MAC address removed>
[ 5257.359422] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5257.560287] wlan0: send auth to <MAC address removed> (try 2/3)
[ 5257.764153] wlan0: send auth to <MAC address removed> (try 3/3)
[ 5257.968073] wlan0: authentication with <MAC address removed> timed out
[ 5262.357848] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5262.498369] wlan0: authenticate with <MAC address removed>
[ 5262.515167] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5262.717611] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5262.921534] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5263.125426] wlan0: authentication with <MAC address removed> timed out
[ 5267.513909] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 8679.924417] wlan0: authenticate with <MAC address removed>
[ 8679.934511] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8679.938511] wlan0: authenticated
[ 8679.939495] wlan0: associate with <MAC address removed> (try 1/3)
[ 8679.950935] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 8679.950993] wlan0: associated
[ 8679.951007] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8679.985407] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC address removed>

########## wireless info END ############

```

---

### Post by loganetherton on 2014-05-24
Anyone have any suggestions?

---

### Post by wildmanne39 on 2014-05-25
This > Trigger new scan to find an IBSS to joinmeans you are trying to connect to an ad-hoc connection. Make sure in network manager the setting is infrastructure.

It could be because there are many networks near yours and almost all of them are using channel 1 or 11 so you are getting a lot of interference or your computer is roaming from one network to another, please try changing the channel.

You have iwlwifi driver loaded and ath9k, why is the first one loaded?
Thanks

---

### Post by loganetherton on 2014-05-26
Thank you for your help, Wild Man. I was unaware that I had multiple drivers loaded, and I've corrected that. It was probably back from when I was just messing around in Ubuntu trying to figure it out.

As for the solution, it actually had nothing to do with my system. What was affecting my ability to connect to wifi was that there were several other wifis in the area that were also operating on the same channel. Simply going into the router and changing the channel allowed me to connect once again.

---

