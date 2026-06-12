---
title: "iwlwifi for intel 7260 is very slow"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by Moheeb_Aljaroudi on 2014-04-20
Hi , i notices slow download speed after installing ubuntu 14.04 i even tried the previous version but i still have the same problem because of my wifi device
i use laptop which has intel 7260 drive . in windows my download speed is about 1-2 mb but when i go to linux the speed drop into 200 kb 
its not from the site i am sure , after working so long the speed become worse that before . 
the firmware i have is [iwlwifi-7260-ucode-22.24.8.0]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.24.8.0.tgz")

---

### Post by varunendra on 2014-04-20
Welcome to the forums Moheeb_Aljaroudi !

Can you try an older firmware suggested here : [http://ubuntuforums.org/showpost.php?p=12924319](http://ubuntuforums.org/showpost.php?p=12924319) ?

Of course backup the current one first -
```
tar czf /lib/firmware/iwlwifi-7260* Desktop/fw-7260.tar.gz
```
This will backup the current firmware on your Desktop in an archive file named "fw-7260.tar.gz".

But before testing the older firmware, please make sure the current driver can recognize and accept it. To check that, please run the following command -
```
modinfo iwlwifi | grep 7260
```
If it shows -
```
firmware:       iwlwifi-7260-7.ucode
```
..go ahead. If it is "..7260-8.." or anything different than above, it won't be accepted (unless the firmware at the suggested link has also been updated).

---

### Post by Moheeb_Aljaroudi on 2014-04-25
Hi , thanks for your reply . i am sorry for taking so long to answer . 
your idea to downgrade worked little bit , but it still cannot get the same speed as windows maybe its the half now 
i think what i need is a new upgrade for it

---

### Post by Moheeb_Aljaroudi on 2014-04-27
i hope they make a new firmware , it still need some fixes

---

### Post by varunendra on 2014-04-28
I have no way to test it myself, but yes, from what I have found so far, it certainly isn't perfect yet. But as per some posts, some kernel+firmware combinations do get upto 300 Mb/s speed. What are the connection (link) and actual (e.g., download) speeds you are getting? Can we see a wireless_script report please? You can find it in the "Wireless Script" link in my signature below, with instructions on how to get and run it, and how to post back its report.

---

### Post by Moheeb_Aljaroudi on 2014-04-28
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux user-Lenovo-IdeaPad-Y510P 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

08:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Lenovo Device [17aa:3800]
    Kernel driver in use: alx
09:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
    Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
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

wlan0     IEEE 802.11bgn  ESSID:"Hawks wifi bldg 4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5615   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.1    0.0.0.0         UG    0      0        0 wlan0
192.168.42.0    0.0.0.0         255.255.254.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Hawks wifi bldg 4] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HP-Print-58-Officejet Pro 8600: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    belkin.889:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2
    HP-Print-8D-Deskjet 3510 series: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 64 WPA2
    HP-Print-D7-Deskjet 3510 series: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2
    belkin.37a:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    SETUP:           Ad-Hoc, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 57
    benzovirus:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    F4DE TO BL4CK:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    TMHYC:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    CiscoD5720-guest:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    NETGEAR97:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 62 WPA2
    Hawks wifi bldg 4: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66
    Hawks wifi bldg 4: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    *Hawks wifi bldg 4: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74
    Hawks wifi bldg 2: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    Hawks wifi bldg 4: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24

  IPv4 Settings:
    Address:         192.168.42.87
    Prefix:          23 (255.255.254.0)
    Gateway:         192.168.42.1

    DNS:             38.108.152.10
    DNS:             216.135.118.250

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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000021674468
                    Extra: Last beacon: 7604ms ago
                    IE: Unknown: 00114861776B73207769666920626C64672034
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001F00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5320012
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"benzovirus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000044c9497617
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000A62656E7A6F7669727573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD0022750707B21021000642656C6B696E1023000F463544373233342D342D763130303010240007575053303030311042000E32303833363732333430383935371054000800060050F204000110110020463544373233342D34000000000000000000000000000000000000000000000010080002008C
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000212a3106
                    Extra: Last beacon: 7604ms ago
                    IE: Unknown: 00114861776B73207769666920626C64672034
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001F00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5320012
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"CiscoD5720-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d21e60d747
                    Extra: Last beacon: 8304ms ago
                    IE: Unknown: 0010436973636F44353732302D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR97"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000050fdeab73
                    Extra: Last beacon: 7604ms ago
                    IE: Unknown: 00094E4554474541523937
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010000000000000100000004C60DEE22A6A102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 06 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-8D-Deskjet 3510 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000082a1512dcff
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 001F48502D5072696E742D38442D4465736B6A6574203335313020736572696573
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1604080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD740800090004000000030102010002017803134465736B6A6574203335313020736572696573040F33353132000000000000000F434E320510434E32414B314E484A4830355237000006101C852A4DB8001F08ABCD10604BEB738D070400000000080200C4090200080A04000000010B0400000000
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001cdbb217f
                    Extra: Last beacon: 8120ms ago
                    IE: Unknown: 00114861776B73207769666920626C64672034
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001D00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001D00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0C00156D0001000000E5320012
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"belkin.889"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ca1426a0c
                    Extra: Last beacon: 7604ms ago
                    IE: Unknown: 000A62656C6B696E2E383839
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200100C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B0001031047001000000000000000010003EC1A5908C8891021001242656C6B696E20436F72706F726174696F6E1023000946394B31303032763410240007342E30302E30371042000E31323132323447433430393033331054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020080
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"SETUP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000008ca4516a970
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00055345545550
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020000010000
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a137bc8c
                    Extra: Last beacon: 7604ms ago
                    IE: Unknown: 00114861776B73207769666920626C64672034
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001F00000000000000000000000000000000000000
                    IE: Unknown: DD0C00156D0001000000E5320012
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"belkin.37a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f686d5bf09
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000A62656C6B696E2E333761
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050200CB127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545700010B10
                    IE: Unknown: DDB50050F204104A0001101044000102103B00010310470010BC329E001DD811B2860108863BFD137A1021001442656C6B696E20496E7465726E6174696F6E616C1023001D42656C6B696E204E373530444220576972656C65737320526F757465721024000746394B313130331042000E31323334353647383930313233341054000800060050F20400011011001D42656C6B696E204E373530444220576972656C65737320526F75746572100800020084103C000101
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005868d205
                    Extra: Last beacon: 7868ms ago
                    IE: Unknown: 00114861776B73207769666920626C64672032
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 05050001000010
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001F00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0C00156D0001000000E5320012
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-D7-Deskjet 3510 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000111c7c2d5
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 001F48502D5072696E742D44372D4465736B6A6574203335313020736572696573
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-58-Officejet Pro 8600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f0dd25055
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 001E48502D5072696E742D35382D4F66666963656A65742050726F2038363030
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 3A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006882b180
                    Extra: Last beacon: 680ms ago
                    IE: Unknown: 00124861776B73207769666920626C6467203341
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010480
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001F00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0C00156D0001000000E5320012
          Cell 16 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"Hawks wifi bldg 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000009bdc3af
                    Extra: Last beacon: 676ms ago
                    IE: Unknown: 00114861776B73207769666920626C64672034
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001F00000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010102000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001F00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0C00156D0001000000E5320012

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### lsmod #####

iwlmvm                189774  0 
mac80211              626489  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
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
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
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
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
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
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

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

# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    9.991531] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   10.083886] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   10.274535] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f01)
[   10.851490] iwlwifi 0000:09:00.0: irq 48 for MSI/MSI-X
[   11.029500] iwlwifi 0000:09:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   11.738488] iwlwifi 0000:09:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[   11.738542] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   11.738770] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   11.974533] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   19.283639] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   19.283866] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[   19.296100] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.296389] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.031889] wlan0: authenticate with <MAC address removed>
[   21.033813] wlan0: send auth to <MAC address removed> (try 1/3)
[   21.041782] wlan0: authenticated
[   21.041904] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[   21.045625] wlan0: associate with <MAC address removed> (try 1/3)
[   21.049271] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=7)
[   21.050366] wlan0: associated
[   21.050383] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  101.476516] wlan0: authenticate with <MAC address removed>
[  101.478621] wlan0: send auth to <MAC address removed> (try 1/3)
[  101.515104] wlan0: authenticated
[  101.515511] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  101.519458] wlan0: associate with <MAC address removed> (try 1/3)
[  101.787012] iwlwifi 0000:09:00.0: No association and the time event is over already...
[  101.787052] wlan0: Connection to AP <MAC address removed> lost
[  102.916619] wlan0: associate with <MAC address removed> (try 2/3)
[  103.041744] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=15)
[  103.045796] wlan0: associated
[  104.841517] wlan0: authenticate with <MAC address removed>
[  104.843139] wlan0: send auth to <MAC address removed> (try 1/3)
[  104.853147] wlan0: authenticated
[  104.853265] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  104.854060] wlan0: associate with <MAC address removed> (try 1/3)
[  104.870977] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=13)
[  104.874800] wlan0: associated
[  113.828507] wlan0: authenticate with <MAC address removed>
[  113.830344] wlan0: send auth to <MAC address removed> (try 1/3)
[  113.834613] wlan0: authenticated
[  113.834895] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[  113.837395] wlan0: associate with <MAC address removed> (try 1/3)
[  113.848242] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=7)
[  113.855398] wlan0: associated

########## wireless info END ############
```
the max speed i get on windows is 5 mb/s but i can get at least 1mb/s even when using the browser 
in linux , i used both firefox and plugin and both of them cant have 400 kb 
one thing that i noticed , when i disable the wifi device then i get it back , it work fast than before.and after minutes the problem back

---

### Post by Moheeb_Aljaroudi on 2014-04-29
A new driver on the kernel site , i will check for it

---

### Post by varunendra on 2014-04-29
A few things that you may (should) try with the current or any version of drivers -
> **Moheeb_Aljaroudi said:**
> ```
##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"Hawks wifi bldg 4"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5615   Missed beacon:0
```

Most of us wireless troubleshooters are always skeptical about "Power Management" on wireless interfaces. Especially when the problem is of the nature you described - initially good, then getting worse with time until reconnected.

Try a quick fix please -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
It should show "Power Management" to be "off". But keep frequently checking it, especially when (if) the performance starts going low. I believe it may automatically turn "on" again. Whether it does or not, there is a driver parameter with the driver "iwlmvm" that makes me curious -
```
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
```
With respect to above (and some other factors), please try what is suggested in this post : [http://ubuntuforums.org/showpost.php?p=12943350](http://ubuntuforums.org/showpost.php?p=12943350)

Please post back if any of that makes any positive (or negative) difference.

---

### Post by Moheeb_Aljaroudi on 2014-04-29
nothing changed, i still have the same problem , and the power managment doesnt change from off .
i still think its a firmware problem . 
can you help me to update it because everytime i try it still on the 8 version even after updating the kernel to 3.14

---

### Post by Moheeb_Aljaroudi on 2014-04-30
yep its firmware problem , i tried pretty much everything

---

### Post by tobyS23 on 2014-05-14
I'm experiencing the same issue. Is there any way to report firmware issues?  Edit:  I just realized that there is already new firmware, but not compatible with the current 14.04 kernel. So I might try to get a newer one and see if the issue is fixed. Or did anyone already do that?

---

### Post by excetara2 on 2014-09-30
Anyone try the newer drivers? How are they working? I tried core-8 but was actually worse so I resorted back to 7. Has anyone tried the -9 with a newer kernal?

---

### Post by Metanei on 2015-04-18
> **excetara2 said:**
> Anyone try the newer drivers? How are they working? I tried core-8 but was actually worse so I resorted back to 7. Has anyone tried the -9 with a newer kernal?


Hello,

I have the kernel 3.16.0-34-generic and the -9 firmware and I was having troubles with the wireless (I'm having cuttings on the connection), but I turned off Power Management and now everything seem works fine. 

I'm using Xubuntu 14.04.2.


Best Regards!

---

### Post by novojilov-ilya on 2015-12-28
> **varunendra said:**
> A few things that you may (should) try with the current or any version of drivers -


```
sudo iwconfig wlan0 power off
```
Then check -

This one did the job for me.

---

