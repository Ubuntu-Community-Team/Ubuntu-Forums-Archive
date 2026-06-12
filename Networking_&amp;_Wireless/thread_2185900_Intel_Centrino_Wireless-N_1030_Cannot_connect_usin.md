---
title: "Intel Centrino Wireless-N 1030: Cannot connect using wifi after upgrading to 13.10"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by eshrauy on 2013-11-04
I see my network available, but I try to connect and it fails.

My wifi network controller is the following:
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)

It worked fine with Ubuntu 13.04. ¿Any idea?

---

### Post by varunendra on 2013-11-06
Welcome to the forums eshrauy !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by eshrauy on 2013-11-29
```

*************** info trace ***************

***** uname -a *****

Linux rodrigo-QA-UY 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
	Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04c5]
	Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1bcf:2b81 Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

iwldvm                237440  0 
mac80211              596969  1 iwldvm
iwlwifi               165398  1 iwldvm
cfg80211              479757  3 iwlwifi,mac80211,iwldvm

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        14:FE:B5:C2:55:1B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.59.20.25
    Prefix:          24 (255.255.255.0)
    Gateway:         10.59.20.254

    DNS:             10.59.130.1
    DNS:             10.59.130.2


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        AC:72:89:46:58:57

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Despegar:        Infra, 20:BB:C0:64:97:70, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA Enterprise
    Despegar-Mobile: Infra, 20:BB:C0:64:97:72, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    Despegar-Guest:  Infra, 20:BB:C0:64:97:71, Freq 2412 MHz, Rate 54 Mb/s, Strength 79
    Despegar:        Infra, 20:BB:C0:64:96:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA Enterprise
    Despegar-Mobile: Infra, 20:BB:C0:64:96:52, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2
    Despegar-Guest:  Infra, 20:BB:C0:64:96:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    Despegar-Desa:   Infra, 20:BB:C0:64:96:54, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA2
    portthru:        Ad-Hoc, 32:73:93:9B:39:B5, Freq 2457 MHz, Rate 54 Mb/s, Strength 100
    Despegar-Desa:   Infra, 20:BB:C0:64:97:74, Freq 2462 MHz, Rate 54 Mb/s, Strength 79 WPA2



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: 20:BB:C0:64:97:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Despegar-Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8ac202abe
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000F44657370656761722D4D6F62696C65
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051400318D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E0F008F000F00FF03590055595A412D41502D30342D456469660014000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 02 - Address: 32:73:93:9B:39:B5
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"portthru"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000013c42cfdcb
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0008706F727474687275
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020000010000
          Cell 03 - Address: 20:BB:C0:64:97:71
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"Despegar-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8ac1fd563
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000E44657370656761722D4775657374
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051400318D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E0F008F000F00FF03590055595A412D41502D30342D456469660014000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 04 - Address: 20:BB:C0:64:97:70
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Despegar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8ac207e9b
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00084465737065676172
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051400318D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E0F008F000F00FF03590055595A412D41502D30342D456469660014000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 05 - Address: 20:BB:C0:64:96:50
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Despegar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014db9c21d4
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00084465737065676172
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051900338D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000D00000000000000000000000000000000000000
                    IE: Unknown: 851E14008F000F00FF03590055595A412D41502D30352D456469660019000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 06 - Address: 20:BB:C0:64:96:51
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"Despegar-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014db9d0ecc
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000E44657370656761722D4775657374
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051900338D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000D00000000000000000000000000000000000000
                    IE: Unknown: 851E14008F000F00FF03590055595A412D41502D30352D456469660019000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 07 - Address: 20:BB:C0:64:97:73
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8ac20e178
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051400318D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E0F008F000F00FF03590055595A412D41502D30342D456469660014000036
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400
          Cell 08 - Address: 20:BB:C0:64:97:74
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8ac227978
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051400318D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 851E0F008F000F00FF03590055595A412D41502D30342D456469660014000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 09 - Address: 20:BB:C0:64:96:52
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Despegar-Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014db9d6439
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000F44657370656761722D4D6F62696C65
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051900338D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000D00000000000000000000000000000000000000
                    IE: Unknown: 851E14008F000F00FF03590055595A412D41502D30352D456469660019000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 10 - Address: 20:BB:C0:64:96:54
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014db9dd978
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706415220010B1E
                    IE: Unknown: 0B051900338D5B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000D00000000000000000000000000000000000000
                    IE: Unknown: 851E14008F000F00FF03590055595A412D41502D30352D456469660019000036
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401


***** resolv.conf *****

search despexds.net despegar.it
nameserver 10.254.130.1
nameserver 10.1.1.68

***** blacklist *****
```

---

### Post by eshrauy on 2013-11-30
Well, finally I found a way to fix my wifi.

I downloaded the firmware from [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) ([iwlwifi-6000g2b-ucode-17.168.5.2.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000g2b-ucode-17.168.5.2.tgz")).
Then I extracted the driver and I copied the file .ucode to /lib/firmware. Finally, I deactivate, and reactivate the network, and no problem to get connected and browse internet.

I don't know if it will be ok in my work with the enterprise connection, but at least I can get connected at home.
I hope it helps others with the same problem.

---

