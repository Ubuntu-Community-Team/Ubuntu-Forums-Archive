---
title: "Ubuntu 14 wifi not connecting (using TP-Link TL-WN822N)"
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by joanna5 on 2014-07-23
Hello all, 

I am new to Ubuntu and I am hoping you can help me with a problem I am facing. Last week I did a clean installation of the latest version of Ubuntu and though initially everything was going ok, today I can longer seem to be able to connect to the internet. 

The desktop running Ubuntu is in an area where a wired connection is not possible, so I bought a TP-Link TL-WN822N and connected the computer wirelessly. Upon plugging in the TP-Link TL-WN822N I connected to the internet just fine without being asked to install anything. 

This morning when I turned on the computer I could no longer see the wifi connection icon on the bar, and I could not connect to the internet. In the settings I can see that I am connected to the network, but I can not load any pages. 

Yesterday before I shut off the computer I was asked to install some updates (don't know if this is related). 

When typing nm-applet on command I get the following: 
```
nm-applet-Message: using fallback from indicator to GtkStatusIcon 
(nm-applet:3443): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
```

I tried looking in the forums and tested a couple of things, but I can't find a solution. I also run the commands in the Sticky thread of this subforum, but it did not change something.

 I hope someone has more ideas I can try :) Running a clean installation is a solution I would like to avoid. 


```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux dev-desktop 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169


##### lsusb #####


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi


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


wlan3     IEEE 802.11bgn  ESSID:"WOS05058788"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan3
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan3


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan3  [WOS05058788 3] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
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
    DIRECT-AkC460 Series: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2
    NLR Guest Network: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 64 WPA2
    NLR:             Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 54 WPA2
    OLVG_DATA:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    OLVG_DATA4:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    OLVG_DATA3:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    NLR:             Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 4 WPA2
    OLVG_DATA4:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    OLVG_DATA3:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2
    HP-Print-df-LaserJet 200: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84
    KPN:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44
    KPN:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4
    KPN:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4
    KPN:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46
    OLVG_DATA4:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    OLVG_DATA:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    OLVG_DATA4:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    OLVG_DATA3:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2
    OLVG_DATA:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    NLR Guest Network: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 4 WPA2
    OLVG_DATA:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    OLVG_DATA3:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2
    *WOS05058788:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             178.217.80.81
    DNS:             178.217.81.80


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


wlan3     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"KPN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000102a1bbf46
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00034B504E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050900300000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300191A953A9D004CBFC33FFF408E9E26E860D354FC86AEF7E9FBA1B6D5C9B1EDF4A5A80E4DEB21985B76
                    IE: Unknown: DD0E000B0E0602263EB3B9000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C4113FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"KPN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001027f35c4b
                    Extra: Last beacon: 1628ms ago
                    IE: Unknown: 00034B504E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050500300000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300175EC4139E004676643DACEF19D9D591345BDBD54AE86671AC2B94E6555793A74E51A0400EB001AFFD
                    IE: Unknown: DD0E000B0E0602263E6A53000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C4113FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"OLVG_DATA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001027f3627d
                    Extra: Last beacon: 1628ms ago
                    IE: Unknown: 00094F4C56475F44415441
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050500300000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300175EC4139E004676653DACEF19D9D591345BDBD54AE86671ACF94BAE71BD8B952696C5D483FE50ACD9
                    IE: Unknown: DD0E000B0E0602263E6A53000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-df-LaserJet 200"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002c6ed7502
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001848502D5072696E742D64662D4C617365724A657420323030
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810027A4000003A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NLR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000031e84102
                    Extra: Last beacon: 1312ms ago
                    IE: Unknown: 00034E4C52
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404080800000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DDA10050F204104A0001101044000102103B0001031047001000000000000010000000649EF387480710210014436973636F20536D616C6C20427573696E65737310230008574150343431304E10240007322E302E342E321042000C3132333435363738393031321054000800060050F204000110110008574150343431304E100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 06 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NLR Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000031e85d66
                    Extra: Last beacon: 1308ms ago
                    IE: Unknown: 00114E4C52204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404080800000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WOS05058788"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002c87de1a7
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 000B574F533035303538373838
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000B427A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000500000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000101103B00010310470010BC329E001DD811B28601001DAA82A72C1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000100
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"OLVG_DATA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000102a1bc578
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 00094F4C56475F44415441
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050900330000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300191A953A9D004CBFC43FFF408E9E26E860D354FC86AEF7E9FB618E9CF2008C1DE085A4B8A2CBF6ABB7
                    IE: Unknown: DD0E000B0E0602263EB3B9000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"OLVG_DATA4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000102a1bcc4e
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000A4F4C56475F4441544134
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050900330000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300191A953A9D004CBFC53FFF408E9E26E860D354FC86AEF7E9FB8285F697B9DAFA2B3438ACC436B1C664
                    IE: Unknown: DD0E000B0E0602263EB3B9000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-AkC460 Series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7999cc349
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00144449524543542D416B4334363020536572696573
                    IE: Unknown: 01088C1218243048606C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD09001018020000040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001016A65700007C1000BB490215991097721021000842726F6164636F6D10230006536F66744150102400013010420001301054000800060050F20400011011000B4334363020536572696573100800020088103C0001011049000E00372A0001200106FFFFFFFFFFFF
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001028766e10
                    Extra: Last beacon: 27632ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01069824B04860EC
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050900350000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD05000B0E0400
                    IE: Unknown: DD16000B0E02000000000A0618A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300191A953A9D0EED9CF13FFF408E9E26E860D354FC86AEF7E9FB59B184D81C92732C4B4A6BB8E0892E44
                    IE: Unknown: DD0E000B0E0602263EB3B9000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
          Cell 12 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001027f32c40
                    Extra: Last beacon: 1728ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01069824B04860EC
                    IE: Unknown: 030101
                    IE: Unknown: 050400010100
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050500300000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD05000B0E0400
                    IE: Unknown: DD16000B0E02000000000A0618A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300175EC4139E0EEDA5843DACEF19D9D591345BDBD54AE86671AC42AAA15CA6C6BA0AF6916FD624C7A8F1
                    IE: Unknown: DD0E000B0E0602263E6A53000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
          Cell 13 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"OLVG_DATA4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001027f37de1
                    Extra: Last beacon: 1708ms ago
                    IE: Unknown: 000A4F4C56475F4441544134
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050500300000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300175EC4139E004676663DACEF19D9D591345BDBD54AE86671ACE8DAFD822F760EB28A17B13AE20F8411
                    IE: Unknown: DD0E000B0E0602263E6A53000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
          Cell 14 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"OLVG_DATA3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001027f38488
                    Extra: Last beacon: 1704ms ago
                    IE: Unknown: 000A4F4C56475F4441544133
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 07064E4C20010D0D
                    IE: Unknown: 0B050500300000
                    IE: Unknown: 43020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD22000B0E02000000000A0C02A204A40BA60CA612A716AB18A824AA30AD48B160B66CB8
                    IE: Unknown: DD2E000B0E0300175EC4139E004676673DACEF19D9D591345BDBD54AE86671AC642A152507579BAA38911CE198CFCD3A
                    IE: Unknown: DD0E000B0E0602263E6A53000A0A020A
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C411BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"OLVG_DATA3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master


##### iwlist channel #####


wlan3     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     7B1675B5BB89B5DD8E7EBAC
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846pF001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


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


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:0x0601 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"


##### dmesg #####


[   12.877566] rtl8192cu: Chip version 0x11
[   12.954016] rtl8192cu: MAC address: <MAC address removed>
[   12.954019] rtl8192cu: Board Type 0
[   12.954271] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   12.954339] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   13.530296] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.530681] rtlwifi: wireless switch is on
[   13.548197] systemd-udevd[482]: renamed network interface wlan0 to wlan3
[   16.857454] rtl8192cu: MAC auto ON okay!
[   16.890193] rtl8192cu: Tx queue select: 0x05
[   17.260729] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[   17.261066] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[   18.551197] wlan3: authenticate with <MAC address removed>
[   18.567364] wlan3: direct probe to <MAC address removed> (try 1/3)
[   18.771039] wlan3: direct probe to <MAC address removed> (try 2/3)
[   18.975021] wlan3: direct probe to <MAC address removed> (try 3/3)
[   19.179445] wlan3: authentication with <MAC address removed> timed out
[   19.467464] wlan3: authenticate with <MAC address removed>
[   19.490917] wlan3: send auth to <MAC address removed> (try 1/3)
[   19.501755] wlan3: authenticated
[   19.502897] wlan3: associate with <MAC address removed> (try 1/3)
[   19.522500] wlan3: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=2)
[   19.522536] wlan3: associated
[   19.522544] IPv6: ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
[  143.079435] wlan3: deauthenticating from <MAC address removed> by local choice (reason=3)
[  144.047791] wlan3: authenticate with <MAC address removed>
[  144.059960] wlan3: send auth to <MAC address removed> (try 1/3)
[  144.068878] wlan3: authenticated
[  144.070179] wlan3: associate with <MAC address removed> (try 1/3)
[  144.080848] wlan3: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[  144.080920] wlan3: associated
[  150.395556] wlan3: deauthenticated from <MAC address removed> (Reason: 15)
[  151.218235] wlan3: authenticate with <MAC address removed>
[  151.241219] wlan3: send auth to <MAC address removed> (try 1/3)
[  151.252739] wlan3: authenticated
[  151.256741] wlan3: associate with <MAC address removed> (try 1/3)
[  151.286353] wlan3: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[  151.286461] wlan3: associated


########## wireless info END ############

```

---

### Post by praseodym on 2014-07-23
Change the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf  
```
Reboot.

---

### Post by joanna5 on 2014-07-28
Thanks and sorry for the late reply! 

I tried reinstalling the driver. It looks like I can connect to the internet now though I still cant see the wifi icon.

---

