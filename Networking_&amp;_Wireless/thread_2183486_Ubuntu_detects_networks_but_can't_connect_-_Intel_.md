---
title: "Ubuntu detects networks but can't connect - Intel Wifi Link 5100"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by nicoeoc on 2013-10-25
Hi, I have a Dell Inspiron 1750 laptop and Ubuntu 13.10 just installed. I can see various networks in the list at top right but after picking mine it seems to try to connect but after a while it stays disconnected. In previous versions of Ubuntu I've had similar problems, ended in assuming the problem, ticking "disable wireless" and stick to the wired connection, a slight difference is that before, in Ubuntu 12.10, some minutes after it failed to connect it tried again and again always asking for my password, which was correct.

Anyway I now really need to get this wifi working, I've tried messing with wireless security type and even disabling it with no success. 

Also I have a desktop computer running ubuntu 12.04 which does get wifi connection, although is very weak/unestable, but I think that may be due to router distance, although is only about 10meters. 

Apart from that I have tried various tricks, commands, etc found in ubuntuforums/askubuntu so I may have a bit of a mess in my system

Some commands:

```
sudo lshw -C network
  *-network               
       descripción: Interfaz inalámbrica
       producto: WiFi Link 5100
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:0c:00.0
       nombre lógico: wlan0
       versión: 00
       serie: 00:22:fb:9b:56:54
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=iwlwifi driverversion=3.11.0-12-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       recursos: irq:47 memoria:f6cfe000-f6cfffff
  *-network
       descripción: Ethernet interface
       producto: 88E8040 PCI-E Fast Ethernet Controller
       fabricante: Marvell Technology Group Ltd.
       id físico: 0
       información del bus: pci@0000:09:00.0
       nombre lógico: eth0
       versión: 13
       serie: 00:25:64:44:48:2b
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       recursos: irq:45 memoria:f6bfc000-f6bfffff ioport:ce00(size=256)
```

```
lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]

```

```
iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

```
sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 18:17:25:24:75:FA
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"ONO2475FA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e646017c
                    Extra: Last beacon: 2808ms ago
                    IE: Unknown: 00094F4E4F323437354641
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D070000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120


```


I really tried to fix this with the information around but I've reach some kind of critical mental blocking situation, so I have to bother you x )

Thanks for any help.

---

### Post by richardsdma on 2013-10-25
you also can try to reset the wireless router, unplug the router from power outlet for about 30 seconds, that should be enough.

---

### Post by nicoeoc on 2013-10-25
I usually do that when going to sleep, anyway as I noted before I have at home a desktop computer which connects just fine to wifi... I think that discards a router issue doesn't it?

---

### Post by nicoeoc on 2013-10-25
Hey guys any other ideas? 

I would appreciate if at least I can narrow things down with some input... thanks!

---

### Post by varunendra on 2013-10-25
First off, Welcome to the forums nicoeoc ! :)

And my first suggestion comes from seeing this -
> **nicoeoc said:**
> 
                    IE: **[COLOR="#FF0000"]WPA Version[/COLOR]** 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/**WPA2 Version** 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
[/CODE]

Please change the encryption type in the router from the above WPA/WPA2 mixed mode to pure WPA2-PSK (AES/CCMP). No mixed mode, no TKIP, they don't work well with Linux drivers besides being inefficient. Reboot the router after saving the change to make sure the new setting is effective, then retry to connect.

If that does not solve the problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by nicoeoc on 2013-10-26
Hi, thanks for welcoming, I've been around for a while though, just that didn't have the urge of posting before... x )

Changing router encryption didn't work, so here is what I've got for Wireless script:

```

*************** info trace ***************

***** uname -a *****

Linux espe-laptop 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:0406]
    Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

***** lsusb *****

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:6400 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
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

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLAN_87D6:       Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 52 WPA
    WLAN_4DAC:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 24 WPA
    WLAN_E439:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA
    Orange-E129:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    WLAN_0BE8:       Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 25 WPA
    WLAN_5564:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 20 WPA
    ONO2475FA:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    WLAN_03EB:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    Orange-ea5a:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Jazztel_6C:      Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    WLAN_4830:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_5450:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    JAZZTEL_F6AE:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    Orange-e3f2:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    JAZZTEL_13EC:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA
    VodafoneBCEC:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_82:         Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WEP
    ONO2475FA:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2



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
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"ONO2475FA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002b91217c
                    Extra: Last beacon: 7956ms ago
                    IE: Unknown: 00094F4E4F323437354641
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"WLAN_87D6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000040004a6b19a
                    Extra: Last beacon: 7836ms ago
                    IE: Unknown: 0009574C414E5F38374436
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A080000000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"vodafone606A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f7b231613a
                    Extra: Last beacon: 7948ms ago
                    IE: Unknown: 000C766F6461666F6E6536303641
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B28601726BD36E6068103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1603050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000013127A
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3403050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLAN_82"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000031ef372183
                    Extra: Last beacon: 3128ms ago
                    IE: Unknown: 0007574C414E5F3832
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD06001018020004
          Cell 05 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WLAN_0BE8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001522836815d
                    Extra: Last beacon: 2864ms ago
                    IE: Unknown: 0009574C414E5F30424538
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010C
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000A026810BE8103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160C070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000006127A
                    IE: Unknown: DD07000C4304000000
          Cell 06 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLAN_4DAC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000094c889a0a0
                    Extra: Last beacon: 7732ms ago
                    IE: Unknown: 0009574C414E5F34444143
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000A0267C4DAC103C000101
                    IE: Unknown: 05050001006201
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503000B127A
                    IE: Unknown: DD07000C4304000000
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Orange-E129"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b0f6c7001
                    Extra: Last beacon: 2964ms ago
                    IE: Unknown: 000B4F72616E67652D45313239
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400050000
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000080C00000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C332C001EFFFF000000000000000000000000000080C00000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD050009860100


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

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
blacklist bcma
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb 

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     189D6366522149BFF40DA25
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B3EF32124305F5D1F6E94A5
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
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
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


***** udev rules *****

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   11.621289] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.621423] iwlwifi 0000:0c:00.0: irq 47 for MSI/MSI-X
[   11.726723] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[   11.747096] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.747100] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.747102] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.747104] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[   11.747107] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   11.747207] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   11.776743] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.102384] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   16.105474] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[   16.211599] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   16.214671] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[   16.247358] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.247845] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.733490] wlan0: authenticate with <MAC address removed>
[   42.737800] wlan0: direct probe to <MAC address removed> (try 1/3)
[   42.940101] wlan0: direct probe to <MAC address removed> (try 2/3)
[   43.144032] wlan0: direct probe to <MAC address removed> (try 3/3)
[   43.348209] wlan0: authentication with <MAC address removed> timed out
[   46.482483] wlan0: authenticate with <MAC address removed>
[   46.485972] wlan0: direct probe to <MAC address removed> (try 1/3)
[   46.688046] wlan0: direct probe to <MAC address removed> (try 2/3)
[   46.892220] wlan0: direct probe to <MAC address removed> (try 3/3)
[   47.096215] wlan0: authentication with <MAC address removed> timed out
[   50.288938] wlan0: authenticate with <MAC address removed>
[   50.289994] wlan0: direct probe to <MAC address removed> (try 1/3)
[   50.492082] wlan0: direct probe to <MAC address removed> (try 2/3)
[   50.696048] wlan0: direct probe to <MAC address removed> (try 3/3)
[   50.900055] wlan0: authentication with <MAC address removed> timed out
[   54.168082] wlan0: authenticate with <MAC address removed>
[   54.169141] wlan0: direct probe to <MAC address removed> (try 1/3)
[   54.372050] wlan0: direct probe to <MAC address removed> (try 2/3)
[   54.576072] wlan0: direct probe to <MAC address removed> (try 3/3)
[   54.780036] wlan0: authentication with <MAC address removed> timed out
[   57.955086] wlan0: authenticate with <MAC address removed>
[   57.958390] wlan0: direct probe to <MAC address removed> (try 1/3)
[   58.160035] wlan0: direct probe to <MAC address removed> (try 2/3)
[   58.364058] wlan0: direct probe to <MAC address removed> (try 3/3)
[   58.568030] wlan0: authentication with <MAC address removed> timed out
[   61.741871] wlan0: authenticate with <MAC address removed>
[   61.743109] wlan0: direct probe to <MAC address removed> (try 1/3)
[   61.944034] wlan0: direct probe to <MAC address removed> (try 2/3)
[   62.148048] wlan0: direct probe to <MAC address removed> (try 3/3)
[   62.354133] wlan0: authentication with <MAC address removed> timed out
[ 1437.600333] wlan0: authenticate with <MAC address removed>
[ 1437.603413] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1437.804300] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1438.008328] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1438.212107] wlan0: authentication with <MAC address removed> timed out
[ 1441.378457] wlan0: authenticate with <MAC address removed>
[ 1441.379965] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1441.580083] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1441.784289] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1441.988075] wlan0: authentication with <MAC address removed> timed out
[ 1445.167671] wlan0: authenticate with <MAC address removed>
[ 1445.172792] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1445.376107] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1445.583077] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1445.784062] wlan0: authentication with <MAC address removed> timed out
[ 1448.956739] wlan0: authenticate with <MAC address removed>
[ 1448.957946] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1449.160313] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1449.364328] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1449.568319] wlan0: authentication with <MAC address removed> timed out
[ 1452.744613] wlan0: authenticate with <MAC address removed>
[ 1452.745805] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1452.948053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1453.152041] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1453.356134] wlan0: authentication with <MAC address removed> timed out
[ 1456.534784] wlan0: authenticate with <MAC address removed>
[ 1456.539910] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1456.740327] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1456.944131] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1457.148071] wlan0: authentication with <MAC address removed> timed out
[ 8113.512705] wlan0: authenticate with <MAC address removed>
[ 8113.513920] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8113.716324] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8113.920327] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8114.124240] wlan0: authentication with <MAC address removed> timed out
[ 8117.265875] wlan0: authenticate with <MAC address removed>
[ 8117.273773] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8117.476124] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8117.683800] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8117.884073] wlan0: authentication with <MAC address removed> timed out
[ 8121.055400] wlan0: authenticate with <MAC address removed>
[ 8121.057078] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8121.260327] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8121.464326] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8121.668319] wlan0: authentication with <MAC address removed> timed out
[ 8124.856393] wlan0: authenticate with <MAC address removed>
[ 8124.858079] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8125.060274] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8125.264226] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8125.468280] wlan0: authentication with <MAC address removed> timed out
[ 8128.735056] wlan0: authenticate with <MAC address removed>
[ 8128.736516] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8128.940330] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8129.144090] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8129.348085] wlan0: authentication with <MAC address removed> timed out
[ 8132.626057] wlan0: authenticate with <MAC address removed>
[ 8132.629011] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8132.832269] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8133.036164] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8133.240327] wlan0: authentication with <MAC address removed> timed out
[16953.861085] wlan0: authenticate with <MAC address removed>
[16953.864372] wlan0: direct probe to <MAC address removed> (try 1/3)
[16954.070251] wlan0: direct probe to <MAC address removed> (try 2/3)
[16954.272066] wlan0: direct probe to <MAC address removed> (try 3/3)
[16954.480083] wlan0: authentication with <MAC address removed> timed out
[16957.714235] wlan0: authenticate with <MAC address removed>
[16957.725039] wlan0: direct probe to <MAC address removed> (try 1/3)
[16957.928274] wlan0: direct probe to <MAC address removed> (try 2/3)
[16958.132352] wlan0: direct probe to <MAC address removed> (try 3/3)
[16958.336108] wlan0: authentication with <MAC address removed> timed out
[16969.709466] wlan0: authenticate with <MAC address removed>
[16969.719494] wlan0: direct probe to <MAC address removed> (try 1/3)
[16969.920281] wlan0: direct probe to <MAC address removed> (try 2/3)
[16970.124078] wlan0: direct probe to <MAC address removed> (try 3/3)
[16970.328114] wlan0: authentication with <MAC address removed> timed out
[31864.394086] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[31868.048865] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[31868.051902] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[31868.081783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32000.332261] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[32003.943484] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[32003.948179] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[32003.984726] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32469.044892] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[32472.724897] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[32472.727922] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[32472.757814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32961.225870] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[32965.095674] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[32965.099565] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[32965.132484] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33613.322999] wlan0: authenticate with <MAC address removed>
[33613.328861] wlan0: direct probe to <MAC address removed> (try 1/3)
[33613.532323] wlan0: direct probe to <MAC address removed> (try 2/3)
[33613.736025] wlan0: direct probe to <MAC address removed> (try 3/3)
[33613.940042] wlan0: authentication with <MAC address removed> timed out
[33617.213281] wlan0: authenticate with <MAC address removed>
[33617.214361] wlan0: direct probe to <MAC address removed> (try 1/3)
[33617.416100] wlan0: direct probe to <MAC address removed> (try 2/3)
[33617.620060] wlan0: direct probe to <MAC address removed> (try 3/3)
[33617.824235] wlan0: authentication with <MAC address removed> timed out
[33629.092641] wlan0: authenticate with <MAC address removed>
[33629.093956] wlan0: direct probe to <MAC address removed> (try 1/3)
[33629.296074] wlan0: direct probe to <MAC address removed> (try 2/3)
[33629.500231] wlan0: direct probe to <MAC address removed> (try 3/3)
[33629.704100] wlan0: authentication with <MAC address removed> timed out
[33632.888459] wlan0: authenticate with <MAC address removed>
[33632.890230] wlan0: direct probe to <MAC address removed> (try 1/3)
[33633.092109] wlan0: direct probe to <MAC address removed> (try 2/3)
[33633.296107] wlan0: direct probe to <MAC address removed> (try 3/3)
[33633.500063] wlan0: authentication with <MAC address removed> timed out

****************** done ******************


```

Maybe something to do with MAC address? x )

Thanks!

---

### Post by varunendra on 2013-10-26
> **nicoeoc said:**
> Hi, thanks for welcoming, I've been around for a while though, just that didn't have the urge of posting before... x )
Hehe, no need to get flattered then.., it has become more of a habit rather than any real waves of feelings here x), but don't worry, won't take it back. :P

Let's focus on the misbehaving guys now..

Even if the encryption change didn't seem to help, it is highly recommended to keep it like that unless it clearly seems to be hurting something (which it won't).

Now try these, one at a time, and in the order as suggested below -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi swcrypto=1
sudo modprobe -v iwldvm
```
Then try to connect. Does it let you? If yes, stop here, test the stability and post back the outcome. If not, try the next one -

```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi 11n_disable=1
sudo modprobe -v iwldvm
```
Does it help? Same instructions as above. In case it fails too, try -

```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi bt_coex_active=N
sudo modprobe -v iwldvm
```
If even this one doesn't help, you may try a combination of all of the above three parameters -

```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi swcrypto=1 11n_disable=1 bt_coex_active=N
sudo modprobe -v iwldvm
```

Please note that these would be temporary changes that would be lost at reboot. If any of these seems to help, stop there, test the stability and performance, and if everything is okay, we'd make it permanent.

For the kind of behaviour you are facing, the most common fix is the second option in the above. But it is a compromise with speed (disables N-channel), so I just want to test the first one first.

---

### Post by nicoeoc on 2013-10-26
I've tried the 4 command sets, being the first one the closest one to a solution. This is the output (I have saved the other 3 outputs if needed):

```
~$ sudo modprobe -rv iwldvm
rmmod iwldvm
rmmod mac80211
rmmod iwlwifi
rmmod cfg80211

~$ sudo modprobe -v iwlwifi swcrypto=1
insmod /lib/modules/3.11.0-12-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 swcrypto=1 swcrypto=1

$ sudo modprobe -v iwldvm
```

At first it happened nothing, so I continued checking the other 3 command sets. After nothing useful came out of that I disabled encryption and tried first command again, _having then for the first time a working wifi connection_. Joy didn't last much though, after a couple of minutes it went down, failing at retrying "clicking on my network", and at repeating the whole command process.

Then still with encryption disabled I went through the other 3 command sets with no success. I managed though to get connected another time by retrying first command set and enabling/disabling wifi with the f2-function button. It didn't last long again, and I believe I've got connected a third time doing this same process lasting just some seconds.

Last thing to say is that first command set would get NM to retry connection by itself a couple of minutes after connection failure, which didn't seem to happen with the other 3 sets.

I feel we are close!

---

### Post by varunendra on 2013-10-26
Hmm.. from this output line -
```
insmod /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko **11n_disable=1 [COLOR="#006400"]swcrypto=1[/COLOR] [COLOR="#FF0000"]swcrypto=1[/COLOR]**
```
..it seems you already have the two parameters (11n_disable and swcrypto) permanently applied sometime ago. Please check -
```
grep -R "iwlwifi" /etc/modprobe.d/
```
The returned output will show the files that contain the word "iwlwifi", with the lines that contain the word.

If your router/access-point supports N-channel, could you try disabling it ? Try only b/g mode for a test, reboot the router after saving the changes to make sure. If that makes no difference, you may enable it again.

The next thing to try (if the above doesn't help) would be disabling power management on the interface by creating a blank file in /etc/pm/power.d -
```
sudo touch /etc/pm/power.d/wireless
```
This will disable the default "/usr/lib/pm-utils/power.d/wireless" script that tries to enforce power management on the interface which may cause issues in some cases.

If none of these help, please run the script again, and post back the fresh report, along with the following additional outputs -
```
[s]cat /etc/pm/power.d[/s]
ls /etc/pm/power.d
grep -R "iwlwifi" /etc/modprobe.d/
grep -R [[:graph:]] /sys/module/iwlwifi/parameters
dmesg | grep 80211
```

---

### Post by nicoeoc on 2013-10-26
Yeah I may have had that applied from the bunch of things I tried before comming here asking for proper help...

```
~$ grep -R "iwlwifi" /etc/modprobe.d/
/etc/modprobe.d/iwlwifi.conf~:options iwlwifi
/etc/modprobe.d/iwlwifi.conf:options iwlwifi 11n_disable=1 swcrypto=1

```

My router does support n channel (interface type:              802.11b/g/n) but I don't seem to find a way to configure it in router menu : /

Disabling power management doesn't seem to work, there's no output from that and wifi doesn't get connected.

Apart from that I point out some information I got from the router after wifi got connected first time, information that didn't display before, not sure if it's any use:

Wifi connection profile for espe-laptop
status: Active
Type: generic dispositve
Connected to: WLAN (wireless)
Allowed in WLAN: yes

Routing
            
Adress:     00:22:FB:9B:56:54
IP assignation:     DHCP
IP Adress:     192.168.1.10
Use always same IP adress:    No
Time of DHCP concession:  0 days, 23:51:20


And here is my updated "wireless script":

```

*************** info trace ***************

***** uname -a *****

Linux espe-laptop 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:0406]
    Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

***** lsusb *****

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:6400 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

19: phy0: Wireless LAN
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

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLAN_87D6:       Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA
    WLAN_123F:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    WLAN_4DAC:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 25 WPA
    WLAN_82:         Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WEP
    WLAN_0BE8:       Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 29 WPA
    WLAN_9771:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    Vodafone9E47:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA
    Orange-e3f2:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Orange-E129:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Orange-2CF8:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    vodafone606A:    Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA
    WLAN_5F95:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    JAZZTEL_13EC:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_2188:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA
    ASCEN:           Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA
    WLAN_D9EA:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 19 WPA
    LCA:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    WLAN_A737:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    VodafoneBCEC:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_E439:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA
    JAZZTEL_576C:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    FTE-BC83:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    ONO2475FA:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    WLAN_03EB:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA


- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



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
          Cell 01 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"WLAN_4DAC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a214eea0b0
                    Extra: Last beacon: 2784ms ago
                    IE: Unknown: 0009574C414E5F34444143
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000A0267C4DAC103C000101
                    IE: Unknown: 05050001002001
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0506000E127A
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"WLAN_87D6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000040d510bb187
                    Extra: Last beacon: 2948ms ago
                    IE: Unknown: 0009574C414E5F38374436
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A080000000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"WLAN_D9EA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000250c8b2a19e
                    Extra: Last beacon: 2752ms ago
                    IE: Unknown: 0009574C414E5F44394541
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D081100000000000000000000000000000000000000


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

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
blacklist bcma
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb 

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     189D6366522149BFF40DA25
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B3EF32124305F5D1F6E94A5
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
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
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


***** udev rules *****

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[  661.388326] wlan0: direct probe to <MAC address removed> (try 3/3)
[  661.592127] wlan0: authentication with <MAC address removed> timed out
[  664.762281] wlan0: authenticate with <MAC address removed>
[  664.772581] wlan0: direct probe to <MAC address removed> (try 1/3)
[  664.976065] wlan0: direct probe to <MAC address removed> (try 2/3)
[  665.180305] wlan0: direct probe to <MAC address removed> (try 3/3)
[  665.384096] wlan0: authentication with <MAC address removed> timed out
[  668.722705] wlan0: authenticate with <MAC address removed>
[  668.724478] wlan0: direct probe to <MAC address removed> (try 1/3)
[  668.931443] wlan0: direct probe to <MAC address removed> (try 2/3)
[  669.132075] wlan0: direct probe to <MAC address removed> (try 3/3)
[  669.340056] wlan0: authentication with <MAC address removed> timed out
[  691.183349] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[  691.183504] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[  691.184582] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[  691.205337] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  691.205342] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  691.205344] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  691.205346] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[  691.205349] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[  691.205550] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[  691.227753] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  691.234238] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[  691.238340] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[  691.339647] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[  691.342837] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[  691.374332] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  691.375349] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  740.015278] wlan0: authenticate with <MAC address removed>
[  740.017023] wlan0: direct probe to <MAC address removed> (try 1/3)
[  740.220303] wlan0: direct probe to <MAC address removed> (try 2/3)
[  740.424329] wlan0: direct probe to <MAC address removed> (try 3/3)
[  740.628149] wlan0: authentication with <MAC address removed> timed out
[  743.820136] wlan0: authenticate with <MAC address removed>
[  743.821236] wlan0: direct probe to <MAC address removed> (try 1/3)
[  744.024030] wlan0: direct probe to <MAC address removed> (try 2/3)
[  744.228190] wlan0: direct probe to <MAC address removed> (try 3/3)
[  744.432055] wlan0: authentication with <MAC address removed> timed out
[  762.802660] wlan0: authenticate with <MAC address removed>
[  762.805843] wlan0: direct probe to <MAC address removed> (try 1/3)
[  763.008129] wlan0: direct probe to <MAC address removed> (try 2/3)
[  763.212324] wlan0: direct probe to <MAC address removed> (try 3/3)
[  763.416322] wlan0: authentication with <MAC address removed> timed out
[  766.565413] wlan0: authenticate with <MAC address removed>
[  766.569325] wlan0: direct probe to <MAC address removed> (try 1/3)
[  766.777371] wlan0: direct probe to <MAC address removed> (try 2/3)
[  766.980093] wlan0: direct probe to <MAC address removed> (try 3/3)
[  767.184047] wlan0: authentication with <MAC address removed> timed out
[  770.457431] wlan0: authenticate with <MAC address removed>
[  770.458881] wlan0: direct probe to <MAC address removed> (try 1/3)
[  770.660329] wlan0: direct probe to <MAC address removed> (try 2/3)
[  770.864325] wlan0: direct probe to <MAC address removed> (try 3/3)
[  771.068323] wlan0: authentication with <MAC address removed> timed out
[ 1417.620967] wlan0: authenticate with <MAC address removed>
[ 1417.622546] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1417.824325] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1418.028286] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1418.232326] wlan0: authentication with <MAC address removed> timed out
[ 1421.427743] wlan0: authenticate with <MAC address removed>
[ 1421.428988] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1421.632093] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1421.836164] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1422.040073] wlan0: authentication with <MAC address removed> timed out
[ 1433.271329] wlan0: authenticate with <MAC address removed>
[ 1433.272554] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1433.476078] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1433.680096] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1433.884309] wlan0: authentication with <MAC address removed> timed out
[ 1437.050703] wlan0: authenticate with <MAC address removed>
[ 1437.052712] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1437.256322] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1437.460123] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1437.664055] wlan0: authentication with <MAC address removed> timed out
[ 1483.891693] wlan0: authenticate with <MAC address removed>
[ 1483.900669] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1484.104039] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1484.308128] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1484.512080] wlan0: authentication with <MAC address removed> timed out
[ 1487.679865] wlan0: authenticate with <MAC address removed>
[ 1487.682026] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1487.884328] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1488.088323] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1488.292320] wlan0: authentication with <MAC address removed> timed out
[ 1491.429552] wlan0: authenticate with <MAC address removed>
[ 1491.431516] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1491.632283] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1491.836331] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1492.040284] wlan0: authentication with <MAC address removed> timed out
[ 1495.184057] wlan0: authenticate with <MAC address removed>
[ 1495.188242] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1495.396067] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1495.600266] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1495.804232] wlan0: authentication with <MAC address removed> timed out
[ 1499.046899] wlan0: authenticate with <MAC address removed>
[ 1499.048703] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1499.252284] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1499.456285] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1499.660321] wlan0: authentication with <MAC address removed> timed out
[ 1608.868553] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1608.868693] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 1608.870580] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 1608.889980] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 1608.889985] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 1608.889987] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 1608.889989] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 1608.889991] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 1608.890209] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1608.912428] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1608.918334] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1608.921585] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1609.037773] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1609.040927] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1609.073874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1609.074919] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1642.641461] wlan0: authenticate with <MAC address removed>
[ 1642.653320] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1642.655710] wlan0: authenticated
[ 1642.656028] wlan0: associate with <MAC address removed> (try 1/3)
[ 1642.670285] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 1642.672945] wlan0: associated
[ 1642.672977] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1752.255098] wlan0: authenticate with <MAC address removed>
[ 1752.259612] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1752.262026] wlan0: authenticated
[ 1752.264054] wlan0: associate with <MAC address removed> (try 1/3)
[ 1752.278345] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 1752.280244] wlan0: associated
[ 1764.030516] wlan0: authenticate with <MAC address removed>
[ 1764.031799] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1764.136151] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1764.155987] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1764.177065] wlan0: authentication with <MAC address removed> timed out
[ 1767.410150] wlan0: authenticate with <MAC address removed>
[ 1767.411366] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1767.413212] wlan0: authenticated
[ 1767.416228] wlan0: associate with <MAC address removed> (try 1/3)
[ 1767.442104] wlan0: associate with <MAC address removed> (try 2/3)
[ 1767.473912] wlan0: associate with <MAC address removed> (try 3/3)
[ 1767.507966] wlan0: association with <MAC address removed> timed out
[ 1776.309425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1817.214533] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1817.217737] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1817.244971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1823.520833] wlan0: authenticate with <MAC address removed>
[ 1823.522322] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1823.548742] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1823.571282] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1823.592237] wlan0: authentication with <MAC address removed> timed out
[ 1826.727089] wlan0: authenticate with <MAC address removed>
[ 1826.731607] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1826.932121] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1827.136169] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1827.340227] wlan0: authentication with <MAC address removed> timed out
[ 1830.489900] wlan0: authenticate with <MAC address removed>
[ 1830.491477] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1830.692308] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1830.896059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1831.100303] wlan0: authentication with <MAC address removed> timed out
[ 1842.367750] wlan0: authenticate with <MAC address removed>
[ 1842.369409] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1842.572132] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1842.776105] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1842.980076] wlan0: authentication with <MAC address removed> timed out
[ 1851.609334] wlan0: authenticate with <MAC address removed>
[ 1851.612032] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1851.816066] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1852.020067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1852.224172] wlan0: authentication with <MAC address removed> timed out
[ 1855.373091] wlan0: authenticate with <MAC address removed>
[ 1855.377802] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1855.580294] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1855.784084] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1855.988093] wlan0: authentication with <MAC address removed> timed out
[ 1859.264084] wlan0: authenticate with <MAC address removed>
[ 1859.267950] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1859.468172] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1859.672085] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1859.876059] wlan0: authentication with <MAC address removed> timed out
[ 1863.053301] wlan0: authenticate with <MAC address removed>
[ 1863.054629] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1863.260225] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1863.464059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1863.670797] wlan0: authentication with <MAC address removed> timed out
[ 1884.890997] wlan0: authenticate with <MAC address removed>
[ 1884.892852] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1885.096306] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1885.300093] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1885.504123] wlan0: authentication with <MAC address removed> timed out
[ 1888.756070] wlan0: authenticate with <MAC address removed>
[ 1888.759245] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1888.960076] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1889.164344] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1889.368292] wlan0: authentication with <MAC address removed> timed out
[ 1913.088883] wlan0: authenticate with <MAC address removed>
[ 1913.091403] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1913.292070] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1913.496053] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1913.700086] wlan0: authentication with <MAC address removed> timed out
[ 1928.266582] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1928.266739] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 1928.267222] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 1928.287667] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 1928.287672] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 1928.287674] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 1928.287676] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 1928.287679] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 1928.287882] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1928.310084] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1928.318886] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1928.326157] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1928.433649] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1928.436760] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1928.466236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1928.467256] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1958.107142] wlan0: authenticate with <MAC address removed>
[ 1958.110266] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1958.312192] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1958.516217] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1958.720191] wlan0: authentication with <MAC address removed> timed out
[ 1970.062996] wlan0: authenticate with <MAC address removed>
[ 1970.064583] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1970.268280] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1970.472325] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1970.676277] wlan0: authentication with <MAC address removed> timed out
[ 1973.852285] wlan0: authenticate with <MAC address removed>
[ 1973.853759] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1974.056129] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1974.260068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1974.464079] wlan0: authentication with <MAC address removed> timed out
[ 1977.640651] wlan0: authenticate with <MAC address removed>
[ 1977.641923] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1977.844328] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1978.048313] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1978.252256] wlan0: authentication with <MAC address removed> timed out
[ 2015.998953] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2015.999084] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 2016.002267] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 2016.022071] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2016.022076] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2016.022078] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2016.022080] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2016.022082] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2016.022186] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2016.044362] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2016.050686] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2016.055997] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2016.165711] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2016.168855] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2016.198733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2016.199745] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2026.383767] wlan0: authenticate with <MAC address removed>
[ 2026.387865] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2026.588331] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2026.792325] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2026.996343] wlan0: authentication with <MAC address removed> timed out
[ 2030.269536] wlan0: authenticate with <MAC address removed>
[ 2030.274517] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2030.476096] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2030.680290] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2030.884308] wlan0: authentication with <MAC address removed> timed out
[ 2034.167062] wlan0: authenticate with <MAC address removed>
[ 2034.170506] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2034.372127] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2034.576106] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2034.780091] wlan0: authentication with <MAC address removed> timed out
[ 2189.830383] wlan0: authenticate with <MAC address removed>
[ 2189.832323] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2190.036326] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2190.240327] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2190.444323] wlan0: authentication with <MAC address removed> timed out
[ 2193.618378] wlan0: authenticate with <MAC address removed>
[ 2193.623862] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2193.824055] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2194.028070] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2194.232035] wlan0: authentication with <MAC address removed> timed out
[ 2197.430755] wlan0: authenticate with <MAC address removed>
[ 2197.449219] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2197.652264] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2197.856268] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2198.060097] wlan0: authentication with <MAC address removed> timed out
[ 2201.196414] wlan0: authenticate with <MAC address removed>
[ 2201.199169] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2201.400284] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2201.604341] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2201.808302] wlan0: authentication with <MAC address removed> timed out
[ 2204.983721] wlan0: authenticate with <MAC address removed>
[ 2204.984677] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2205.188039] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2205.392047] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2205.596062] wlan0: authentication with <MAC address removed> timed out
[ 2230.073633] wlan0: authenticate with <MAC address removed>
[ 2230.074945] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2230.276306] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2230.480112] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2230.684084] wlan0: authentication with <MAC address removed> timed out
[ 2250.142639] wlan0: authenticate with <MAC address removed>
[ 2250.143852] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2250.344323] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2250.548329] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2250.752279] wlan0: authentication with <MAC address removed> timed out
[ 2347.043521] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2347.043691] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 2347.044291] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 2347.063116] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2347.063121] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2347.063123] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2347.063125] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2347.063127] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2347.063339] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2347.085544] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2347.094543] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2347.098067] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2347.195545] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2347.198690] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2347.230601] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2347.231623] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2457.841086] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2457.844212] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2457.872626] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2465.380592] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2465.404059] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2467.168452] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2467.170837] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2467.174516] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2467.206266] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2473.377986] wlan0: authenticate with <MAC address removed>
[ 2473.380721] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2473.584092] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2473.792068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2473.996095] wlan0: authentication with <MAC address removed> timed out
[ 2485.215238] wlan0: authenticate with <MAC address removed>
[ 2485.220513] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2485.424045] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2485.628326] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2485.832328] wlan0: authentication with <MAC address removed> timed out
[ 2509.734435] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2509.734582] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 2509.737193] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 2509.754995] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2509.754999] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2509.755001] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2509.755003] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2509.755005] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2509.755216] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2509.777457] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2509.784874] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2509.792045] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2509.895792] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2509.898903] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2509.932578] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2509.933597] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2523.325751] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2523.380088] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2525.252637] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2525.255062] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2525.258513] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2525.291543] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2531.437760] wlan0: authenticate with <MAC address removed>
[ 2531.439606] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2531.640067] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2531.659728] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2531.680935] wlan0: authentication with <MAC address removed> timed out
[ 2534.926135] wlan0: authenticate with <MAC address removed>
[ 2534.927732] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2534.930102] wlan0: authenticated
[ 2534.936445] wlan0: associate with <MAC address removed> (try 1/3)
[ 2534.951421] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 2534.954127] wlan0: associated
[ 2534.954158] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2567.274349] wlan0: authenticate with <MAC address removed>
[ 2567.275686] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2567.296988] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2567.321965] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2567.349464] wlan0: authentication with <MAC address removed> timed out
[ 2579.249718] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2590.627814] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2590.676054] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2592.414501] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2592.416958] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2592.420464] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2592.450975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2602.976538] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2603.036051] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2607.048631] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2607.051904] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2607.055145] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2607.086531] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2631.275924] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2631.328055] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2633.060903] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2633.063280] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2633.066576] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2633.098635] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2639.262326] wlan0: authenticate with <MAC address removed>
[ 2639.264680] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2639.468307] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2639.672321] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2639.876296] wlan0: authentication with <MAC address removed> timed out
[ 2651.038499] wlan0: authenticate with <MAC address removed>
[ 2651.041297] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2651.244073] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2651.448101] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2651.652095] wlan0: authentication with <MAC address removed> timed out
[ 2654.827638] wlan0: authenticate with <MAC address removed>
[ 2654.831058] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2655.032311] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2655.236317] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2655.440322] wlan0: authentication with <MAC address removed> timed out
[ 2658.614896] wlan0: authenticate with <MAC address removed>
[ 2658.616081] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2658.820308] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2659.024292] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2659.228321] wlan0: authentication with <MAC address removed> timed out
[ 2668.139816] wlan0: authenticate with <MAC address removed>
[ 2668.144250] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2668.352076] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2668.556364] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2668.760310] wlan0: authentication with <MAC address removed> timed out
[ 2671.927906] wlan0: authenticate with <MAC address removed>
[ 2671.929528] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2672.132252] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2672.336282] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2672.544075] wlan0: authentication with <MAC address removed> timed out
[ 2675.716939] wlan0: authenticate with <MAC address removed>
[ 2675.724596] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2675.928071] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2676.132054] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2676.336634] wlan0: authentication with <MAC address removed> timed out
[ 2687.595358] wlan0: authenticate with <MAC address removed>
[ 2687.598145] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2693.098448] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2693.098591] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 2693.099349] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 2693.121119] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2693.121124] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2693.121126] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2693.121128] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2693.121130] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2693.121338] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2693.143540] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2693.155629] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2693.158908] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2693.259672] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2693.262796] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2693.301836] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2693.302848] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2702.908849] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2703.000076] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2707.438843] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2707.442167] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2707.445483] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2707.474521] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2713.608760] wlan0: authenticate with <MAC address removed>
[ 2713.610922] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2713.812329] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2714.016244] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2714.220326] wlan0: authentication with <MAC address removed> timed out
[ 2717.500551] wlan0: authenticate with <MAC address removed>
[ 2717.502703] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2717.704291] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2717.908297] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2718.112333] wlan0: authentication with <MAC address removed> timed out
[ 2721.286454] wlan0: authenticate with <MAC address removed>
[ 2721.287608] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2721.488302] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2721.692090] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2721.896108] wlan0: authentication with <MAC address removed> timed out
[ 2725.075338] wlan0: authenticate with <MAC address removed>
[ 2725.076706] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2725.280327] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2725.484319] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2725.688295] wlan0: authentication with <MAC address removed> timed out
[ 2742.073548] wlan0: authenticate with <MAC address removed>
[ 2742.074911] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2742.276053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2742.480067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2742.684147] wlan0: authentication with <MAC address removed> timed out
[ 2745.865911] wlan0: authenticate with <MAC address removed>
[ 2745.867314] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2746.068047] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2746.272087] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2746.476064] wlan0: authentication with <MAC address removed> timed out
[ 3067.099918] wlan0: authenticate with <MAC address removed>
[ 3067.101398] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3067.304279] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3067.508301] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3067.712073] wlan0: authentication with <MAC address removed> timed out
[ 3070.886270] wlan0: authenticate with <MAC address removed>
[ 3070.889253] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3071.092108] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3071.296103] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3071.500076] wlan0: authentication with <MAC address removed> timed out
[ 3074.675502] wlan0: authenticate with <MAC address removed>
[ 3074.677242] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3074.880323] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3075.084322] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3075.288323] wlan0: authentication with <MAC address removed> timed out
[ 3078.438164] wlan0: authenticate with <MAC address removed>
[ 3078.440650] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3078.644050] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3078.848259] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3079.052046] wlan0: authentication with <MAC address removed> timed out
[ 3082.256102] wlan0: authenticate with <MAC address removed>
[ 3082.259185] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3082.460076] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3082.664060] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3082.868217] wlan0: authentication with <MAC address removed> timed out
[ 3092.079595] wlan0: authenticate with <MAC address removed>
[ 3092.083131] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3092.284310] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3092.488261] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3092.692226] wlan0: authentication with <MAC address removed> timed out
[ 3103.859948] wlan0: authenticate with <MAC address removed>
[ 3103.861736] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3104.064329] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3104.268325] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3104.472322] wlan0: authentication with <MAC address removed> timed out
[ 3107.650538] wlan0: authenticate with <MAC address removed>
[ 3107.653510] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3107.856270] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3108.060044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3108.264252] wlan0: authentication with <MAC address removed> timed out
[ 3111.437936] wlan0: authenticate with <MAC address removed>
[ 3111.449257] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3111.652292] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3111.856137] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3112.060083] wlan0: authentication with <MAC address removed> timed out
[ 3115.200111] wlan0: authenticate with <MAC address removed>
[ 3115.202019] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3115.404244] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3115.612243] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3115.816042] wlan0: authentication with <MAC address removed> timed out
[ 3123.024794] wlan0: authenticate with <MAC address removed>
[ 3123.028547] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3123.232323] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3123.436164] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3123.640325] wlan0: authentication with <MAC address removed> timed out
[ 3126.798489] wlan0: authenticate with <MAC address removed>
[ 3126.799820] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3127.004048] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3127.208063] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3127.412072] wlan0: authentication with <MAC address removed> timed out
[ 3130.586763] wlan0: authenticate with <MAC address removed>
[ 3130.589224] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3130.792324] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3130.996330] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3131.200319] wlan0: authentication with <MAC address removed> timed out
[ 3134.348396] wlan0: authenticate with <MAC address removed>
[ 3134.349402] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3134.552215] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3134.756275] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3134.960305] wlan0: authentication with <MAC address removed> timed out
[ 3151.125706] wlan0: authenticate with <MAC address removed>
[ 3151.127132] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3151.328166] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3151.532305] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3151.736240] wlan0: authentication with <MAC address removed> timed out
[ 3154.958176] wlan0: authenticate with <MAC address removed>
[ 3154.959752] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3155.160328] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3155.364322] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3155.568093] wlan0: authentication with <MAC address removed> timed out
[ 3158.747406] wlan0: authenticate with <MAC address removed>
[ 3158.749109] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3158.952282] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3159.156326] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3159.360282] wlan0: authentication with <MAC address removed> timed out
[ 3162.524136] wlan0: authenticate with <MAC address removed>
[ 3162.526465] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3162.728066] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3162.932108] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3163.136083] wlan0: authentication with <MAC address removed> timed out
[ 3476.091776] wlan0: authenticate with <MAC address removed>
[ 3476.099387] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3476.300248] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3476.504221] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3476.708262] wlan0: authentication with <MAC address removed> timed out
[ 3479.882353] wlan0: authenticate with <MAC address removed>
[ 3479.884087] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3480.088324] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3480.292328] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3480.496325] wlan0: authentication with <MAC address removed> timed out
[ 3483.743616] wlan0: authenticate with <MAC address removed>
[ 3483.749312] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3483.952101] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3484.156074] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3484.360093] wlan0: authentication with <MAC address removed> timed out
[ 3487.560348] wlan0: authenticate with <MAC address removed>
[ 3487.562819] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3487.764295] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3487.968247] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3488.172323] wlan0: authentication with <MAC address removed> timed out
[ 3491.348506] wlan0: authenticate with <MAC address removed>
[ 3491.350187] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3491.552282] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3491.756278] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3491.960285] wlan0: authentication with <MAC address removed> timed out
[ 3513.160875] wlan0: authenticate with <MAC address removed>
[ 3513.162076] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3513.364301] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3513.568304] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3513.772304] wlan0: authentication with <MAC address removed> timed out
[ 3525.038377] wlan0: authenticate with <MAC address removed>
[ 3525.040161] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3525.244328] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3525.448300] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3525.652303] wlan0: authentication with <MAC address removed> timed out
[ 3532.111294] wlan0: authenticate with <MAC address removed>
[ 3532.112706] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3532.316286] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3532.520285] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3532.724321] wlan0: authentication with <MAC address removed> timed out
[ 3543.879254] wlan0: authenticate with <MAC address removed>
[ 3543.885419] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3544.088291] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3544.292282] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3544.496280] wlan0: authentication with <MAC address removed> timed out
[ 3547.724419] wlan0: authenticate with <MAC address removed>
[ 3547.725908] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3547.928075] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3548.132319] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3548.336282] wlan0: authentication with <MAC address removed> timed out
[ 3551.470966] wlan0: authenticate with <MAC address removed>
[ 3551.472409] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3551.676329] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3551.880323] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3552.084327] wlan0: authentication with <MAC address removed> timed out
[ 3560.060336] wlan0: authenticate with <MAC address removed>
[ 3560.061768] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3560.264129] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3560.468087] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3560.672308] wlan0: authentication with <MAC address removed> timed out
[ 3580.020590] wlan0: authenticate with <MAC address removed>
[ 3580.024425] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3580.228086] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3580.432085] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3580.636297] wlan0: authentication with <MAC address removed> timed out
[ 3720.583348] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 3720.583484] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 3720.586381] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 3720.605823] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 3720.605828] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 3720.605830] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 3720.605832] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 3720.605834] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 3720.606039] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3720.628223] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3720.634742] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3720.640232] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 3720.743653] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3720.746807] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 3720.781756] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3720.782771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3752.936357] wlan0: authenticate with <MAC address removed>
[ 3752.938355] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3753.140284] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3753.344068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3753.548357] wlan0: authentication with <MAC address removed> timed out
[ 3764.760670] wlan0: authenticate with <MAC address removed>
[ 3764.761676] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3764.964354] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3765.168703] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3765.372062] wlan0: authentication with <MAC address removed> timed out
[ 3792.570241] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 3792.570393] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 3792.570912] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 3792.590867] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 3792.590872] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 3792.590874] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 3792.590876] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 3792.590879] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 3792.591220] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3792.613397] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3792.620860] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3792.626306] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 3792.737651] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3792.740793] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 3792.770635] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3792.771660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3906.381824] wlan0: authenticate with <MAC address removed>
[ 3906.383378] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3906.584324] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3906.788292] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3906.992137] wlan0: authentication with <MAC address removed> timed out
[ 3962.351948] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 3962.352169] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 3962.353821] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 3962.375296] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 3962.375301] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 3962.375303] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 3962.375305] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 3962.375308] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 3962.375504] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3962.397779] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3962.406695] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3962.409975] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 3962.511662] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 3962.514783] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 3962.546300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3962.547326] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3979.397879] wlan0: authenticate with <MAC address removed>
[ 3979.399731] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3979.600242] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3979.804313] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3980.008342] wlan0: authentication with <MAC address removed> timed out
[ 3983.185367] wlan0: authenticate with <MAC address removed>
[ 3983.188487] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3983.392333] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3983.596148] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3983.800291] wlan0: authentication with <MAC address removed> timed out
[ 3986.973507] wlan0: authenticate with <MAC address removed>
[ 3986.984421] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3987.188230] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3987.392064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3987.596293] wlan0: authentication with <MAC address removed> timed out
[ 3990.758575] wlan0: authenticate with <MAC address removed>
[ 3990.759756] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 3990.960328] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 3991.164324] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 3991.368325] wlan0: authentication with <MAC address removed> timed out
[ 4021.695494] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 4021.776052] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 4024.150088] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 4024.152519] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4024.155832] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4024.186769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4035.820292] wlan0: authenticate with <MAC address removed>
[ 4035.822111] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4036.024293] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4036.228330] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4036.432322] wlan0: authentication with <MAC address removed> timed out
[ 4055.891236] wlan0: authenticate with <MAC address removed>
[ 4055.892548] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4056.096080] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4056.300089] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4056.504064] wlan0: authentication with <MAC address removed> timed out
[ 4069.521209] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 4069.521347] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 4069.522677] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 4069.542395] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 4069.542400] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 4069.542402] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 4069.542404] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 4069.542407] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 4069.542617] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4069.565057] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 4069.571639] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4069.575427] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4069.675672] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4069.678887] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4069.711529] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4069.712598] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4080.778964] wlan0: authenticate with <MAC address removed>
[ 4080.780910] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4080.988105] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4081.192161] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4081.396248] wlan0: authentication with <MAC address removed> timed out
[ 4084.564666] wlan0: authenticate with <MAC address removed>
[ 4084.566108] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4084.768326] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4084.972323] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4085.176320] wlan0: authentication with <MAC address removed> timed out
[ 4104.036354] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 4104.068029] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 4105.540678] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 4105.542994] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4105.546403] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4105.578775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4113.034427] wlan0: authenticate with <MAC address removed>
[ 4113.036518] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4113.240059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4113.444072] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4113.648224] wlan0: authentication with <MAC address removed> timed out
[ 4116.820849] wlan0: authenticate with <MAC address removed>
[ 4116.825188] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4117.028292] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4117.232326] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4117.436135] wlan0: authentication with <MAC address removed> timed out
[ 4128.699707] wlan0: authenticate with <MAC address removed>
[ 4128.702835] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4128.904103] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4129.108100] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4129.312092] wlan0: authentication with <MAC address removed> timed out
[ 4132.630200] wlan0: authenticate with <MAC address removed>
[ 4132.631518] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4132.832074] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4133.036074] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4133.240084] wlan0: authentication with <MAC address removed> timed out
[ 4144.426355] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 4144.426508] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 4144.429131] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 4144.451180] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 4144.451185] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 4144.451187] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 4144.451189] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 4144.451192] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 4144.451370] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4144.473719] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 4144.481001] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4144.484068] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4144.587772] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4144.590903] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4144.622568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4144.623586] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4154.502706] wlan0: authenticate with <MAC address removed>
[ 4154.507145] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4154.708056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4154.912073] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4155.116066] wlan0: authentication with <MAC address removed> timed out
[ 4158.291894] wlan0: authenticate with <MAC address removed>
[ 4158.298452] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4158.500084] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4158.704322] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4158.908316] wlan0: authentication with <MAC address removed> timed out
[ 4162.082620] wlan0: authenticate with <MAC address removed>
[ 4162.084118] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4162.288234] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4162.492179] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4162.696093] wlan0: authentication with <MAC address removed> timed out
[ 4165.862174] wlan0: authenticate with <MAC address removed>
[ 4165.863600] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4166.064324] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4166.268089] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4166.472066] wlan0: authentication with <MAC address removed> timed out
[ 4169.657671] wlan0: authenticate with <MAC address removed>
[ 4169.659007] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4169.860054] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4170.064332] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4170.268296] wlan0: authentication with <MAC address removed> timed out
[ 4177.949601] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 4177.992330] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 4179.054592] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 4179.056958] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 4179.062111] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 4179.094391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4278.738242] wlan0: authenticate with <MAC address removed>
[ 4278.754722] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4278.956282] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4279.160352] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4279.364297] wlan0: authentication with <MAC address removed> timed out
[ 4282.499596] wlan0: authenticate with <MAC address removed>
[ 4282.502630] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4282.704312] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4282.908326] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4283.112303] wlan0: authentication with <MAC address removed> timed out
[ 4294.274436] wlan0: authenticate with <MAC address removed>
[ 4294.281938] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4294.484321] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4294.688324] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4294.892324] wlan0: authentication with <MAC address removed> timed out
[ 4420.330815] wlan0: authenticate with <MAC address removed>
[ 4420.333629] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4420.536327] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4420.740325] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4420.944329] wlan0: authentication with <MAC address removed> timed out
[ 4424.221972] wlan0: authenticate with <MAC address removed>
[ 4424.223435] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4424.424268] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4424.628258] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4424.836258] wlan0: authentication with <MAC address removed> timed out
[ 4428.010667] wlan0: authenticate with <MAC address removed>
[ 4428.011838] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4428.212076] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4428.416104] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4428.624047] wlan0: authentication with <MAC address removed> timed out
[ 4431.807527] wlan0: authenticate with <MAC address removed>
[ 4431.810709] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4432.012379] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4432.216328] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4432.420057] wlan0: authentication with <MAC address removed> timed out
[ 4435.588824] wlan0: authenticate with <MAC address removed>
[ 4435.590460] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4435.792326] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4435.996087] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4436.200332] wlan0: authentication with <MAC address removed> timed out
[ 4439.377396] wlan0: authenticate with <MAC address removed>
[ 4439.378757] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4439.580065] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4439.788067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4439.992098] wlan0: authentication with <MAC address removed> timed out
[ 4745.047446] wlan0: authenticate with <MAC address removed>
[ 4745.056493] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4745.263986] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4745.468055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4745.672068] wlan0: authentication with <MAC address removed> timed out
[ 4748.835811] wlan0: authenticate with <MAC address removed>
[ 4748.837497] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4749.040321] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4749.244320] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4749.448328] wlan0: authentication with <MAC address removed> timed out
[ 4752.624908] wlan0: authenticate with <MAC address removed>
[ 4752.626218] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4752.828301] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4753.032285] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4753.236276] wlan0: authentication with <MAC address removed> timed out
[ 4756.413223] wlan0: authenticate with <MAC address removed>
[ 4756.416535] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4756.620063] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4756.824088] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4757.028119] wlan0: authentication with <MAC address removed> timed out
[ 4760.203254] wlan0: authenticate with <MAC address removed>
[ 4760.209009] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4760.412300] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4760.616304] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4760.820303] wlan0: authentication with <MAC address removed> timed out
[ 4770.029600] wlan0: authenticate with <MAC address removed>
[ 4770.032776] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4770.236091] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4770.440100] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4770.644304] wlan0: authentication with <MAC address removed> timed out
[ 4773.923988] wlan0: authenticate with <MAC address removed>
[ 4773.926004] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4774.128091] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4774.332306] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4774.536113] wlan0: authentication with <MAC address removed> timed out
[ 4777.712742] wlan0: authenticate with <MAC address removed>
[ 4777.714254] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4777.916354] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4778.120042] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4778.324072] wlan0: authentication with <MAC address removed> timed out
[ 4781.496964] wlan0: authenticate with <MAC address removed>
[ 4781.498124] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4781.700036] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4781.904051] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4782.108304] wlan0: authentication with <MAC address removed> timed out
[ 4785.393278] wlan0: authenticate with <MAC address removed>
[ 4785.395265] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4785.596289] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4785.800126] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4786.004255] wlan0: authentication with <MAC address removed> timed out
[ 4789.182896] wlan0: authenticate with <MAC address removed>
[ 4789.184179] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4789.388067] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4789.592225] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4789.796033] wlan0: authentication with <MAC address removed> timed out
[ 4798.089508] wlan0: authenticate with <MAC address removed>
[ 4798.091612] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4798.292321] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4798.496306] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4798.700280] wlan0: authentication with <MAC address removed> timed out
[ 4809.972365] wlan0: authenticate with <MAC address removed>
[ 4809.976416] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4810.180331] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4810.384329] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4810.588327] wlan0: authentication with <MAC address removed> timed out
[ 4829.938363] wlan0: authenticate with <MAC address removed>
[ 4829.939563] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4830.140128] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4830.344310] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4830.548268] wlan0: authentication with <MAC address removed> timed out
[ 4833.726667] wlan0: authenticate with <MAC address removed>
[ 4833.742729] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4833.944053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4834.148058] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4834.352129] wlan0: authentication with <MAC address removed> timed out
[ 4837.516556] wlan0: authenticate with <MAC address removed>
[ 4837.519444] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4837.724119] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4837.928052] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4838.136221] wlan0: authentication with <MAC address removed> timed out
[ 4841.304895] wlan0: authenticate with <MAC address removed>
[ 4841.307152] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4841.508310] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4841.712099] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4841.916282] wlan0: authentication with <MAC address removed> timed out
[ 4845.094932] wlan0: authenticate with <MAC address removed>
[ 4845.096509] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4845.300282] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4845.504323] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4845.708063] wlan0: authentication with <MAC address removed> timed out
[ 4848.881410] wlan0: authenticate with <MAC address removed>
[ 4848.882336] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4849.084087] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4849.292064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4849.496071] wlan0: authentication with <MAC address removed> timed out
[ 5059.502414] wlan0: authenticate with <MAC address removed>
[ 5059.505063] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5059.708137] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5059.912305] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5060.116094] wlan0: authentication with <MAC address removed> timed out
[ 5062.725694] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 5062.772060] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 5065.429099] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 5065.431452] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 5065.434785] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 5065.466364] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5077.442944] wlan0: authenticate with <MAC address removed>
[ 5077.448042] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5077.652309] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5077.856136] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5078.060308] wlan0: authentication with <MAC address removed> timed out
[ 5081.232661] wlan0: authenticate with <MAC address removed>
[ 5081.236199] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5081.440105] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5081.644289] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5081.848304] wlan0: authentication with <MAC address removed> timed out
[ 5085.021237] wlan0: authenticate with <MAC address removed>
[ 5085.027153] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5085.232061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5085.436234] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5085.640113] wlan0: authentication with <MAC address removed> timed out
[ 5088.811126] wlan0: authenticate with <MAC address removed>
[ 5088.813037] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5089.016326] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5089.220056] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5089.424323] wlan0: authentication with <MAC address removed> timed out
[ 5092.599074] wlan0: authenticate with <MAC address removed>
[ 5092.601624] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5092.804085] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5093.008100] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5093.212413] wlan0: authentication with <MAC address removed> timed out
[ 5096.387710] wlan0: authenticate with <MAC address removed>
[ 5096.394287] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5096.596086] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5096.800103] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5097.004200] wlan0: authentication with <MAC address removed> timed out
[ 5403.136930] wlan0: authenticate with <MAC address removed>
[ 5403.137951] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5403.341087] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5403.544088] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5403.748069] wlan0: authentication with <MAC address removed> timed out
[ 5406.877094] wlan0: authenticate with <MAC address removed>
[ 5406.878255] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5407.080244] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5407.284259] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5407.488276] wlan0: authentication with <MAC address removed> timed out
[ 5410.659570] wlan0: authenticate with <MAC address removed>
[ 5410.660850] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5410.864096] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5411.068327] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5411.272121] wlan0: authentication with <MAC address removed> timed out
[ 5428.056087] wlan0: authenticate with <MAC address removed>
[ 5428.057260] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5428.261033] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5428.464059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5428.668112] wlan0: authentication with <MAC address removed> timed out
[ 5431.771075] wlan0: authenticate with <MAC address removed>
[ 5431.777707] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5431.981069] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5432.184048] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5432.388061] wlan0: authentication with <MAC address removed> timed out
[ 5435.543824] wlan0: authenticate with <MAC address removed>
[ 5435.545672] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5435.748094] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5435.952070] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5436.156116] wlan0: authentication with <MAC address removed> timed out
[ 5439.331258] wlan0: authenticate with <MAC address removed>
[ 5439.333385] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5439.536072] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5439.740041] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5439.948292] wlan0: authentication with <MAC address removed> timed out
[ 5443.114527] wlan0: authenticate with <MAC address removed>
[ 5443.118259] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5443.320082] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5443.524080] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5443.728199] wlan0: authentication with <MAC address removed> timed out
[ 5446.910858] wlan0: authenticate with <MAC address removed>
[ 5446.914651] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5447.116329] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5447.320066] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5447.524134] wlan0: authentication with <MAC address removed> timed out
[ 5450.612246] wlan0: authenticate with <MAC address removed>
[ 5450.614726] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5450.816849] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5451.020097] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5451.224079] wlan0: authentication with <MAC address removed> timed out
[ 5459.098682] wlan0: authenticate with <MAC address removed>
[ 5459.102653] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5459.304305] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5459.508093] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5459.712301] wlan0: authentication with <MAC address removed> timed out
[ 5462.884752] wlan0: authenticate with <MAC address removed>
[ 5462.887988] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5463.092069] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5463.296312] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5463.500048] wlan0: authentication with <MAC address removed> timed out
[ 5487.010163] wlan0: authenticate with <MAC address removed>
[ 5487.013202] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5487.216272] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5487.420059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5487.624051] wlan0: authentication with <MAC address removed> timed out
[ 5498.826425] wlan0: authenticate with <MAC address removed>
[ 5498.830135] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5499.032094] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5499.236072] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5499.441381] wlan0: authentication with <MAC address removed> timed out
[ 5502.616465] wlan0: authenticate with <MAC address removed>
[ 5502.619918] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5502.820045] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5503.024307] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5503.228060] wlan0: authentication with <MAC address removed> timed out
[ 5506.355347] wlan0: authenticate with <MAC address removed>
[ 5506.359111] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5506.560077] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5506.764306] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5506.968065] wlan0: authentication with <MAC address removed> timed out
[ 5812.074819] wlan0: authenticate with <MAC address removed>
[ 5812.077777] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5812.280239] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5812.484034] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5812.688070] wlan0: authentication with <MAC address removed> timed out
[ 5823.954750] wlan0: authenticate with <MAC address removed>
[ 5823.956959] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5824.160045] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5824.364032] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5824.568270] wlan0: authentication with <MAC address removed> timed out
[ 5827.729994] wlan0: authenticate with <MAC address removed>
[ 5827.730924] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5827.932098] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5828.136058] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5828.340075] wlan0: authentication with <MAC address removed> timed out
[ 5831.531282] wlan0: authenticate with <MAC address removed>
[ 5831.533569] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5831.736124] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5831.940310] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5832.144045] wlan0: authentication with <MAC address removed> timed out
[ 5840.029251] wlan0: authenticate with <MAC address removed>
[ 5840.032760] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5840.236282] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5840.440115] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5840.644070] wlan0: authentication with <MAC address removed> timed out
[ 5843.820495] wlan0: authenticate with <MAC address removed>
[ 5843.823312] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5844.025509] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5844.228275] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5844.432084] wlan0: authentication with <MAC address removed> timed out
[ 5847.608144] wlan0: authenticate with <MAC address removed>
[ 5847.610444] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5847.812096] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5848.019551] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5848.220156] wlan0: authentication with <MAC address removed> timed out
[ 5859.499972] wlan0: authenticate with <MAC address removed>
[ 5859.501001] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5859.704051] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5859.908037] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5860.112027] wlan0: authentication with <MAC address removed> timed out
[ 5868.090439] wlan0: authenticate with <MAC address removed>
[ 5868.091686] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5868.294746] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5868.496075] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5868.700069] wlan0: authentication with <MAC address removed> timed out
[ 5871.877109] wlan0: authenticate with <MAC address removed>
[ 5871.879617] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5872.080310] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5872.284123] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5872.488095] wlan0: authentication with <MAC address removed> timed out
[ 5883.653272] wlan0: authenticate with <MAC address removed>
[ 5883.655570] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5883.856060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5884.060090] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5884.264060] wlan0: authentication with <MAC address removed> timed out
[ 5887.441460] wlan0: authenticate with <MAC address removed>
[ 5887.444958] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5887.648059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5887.852119] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5888.056555] wlan0: authentication with <MAC address removed> timed out
[ 5896.044696] wlan0: authenticate with <MAC address removed>
[ 5896.049755] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5896.252059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5896.456066] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5896.660171] wlan0: authentication with <MAC address removed> timed out
[ 5899.931445] wlan0: authenticate with <MAC address removed>
[ 5899.933370] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5900.140066] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5900.344086] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5900.548107] wlan0: authentication with <MAC address removed> timed out
[ 5903.725289] wlan0: authenticate with <MAC address removed>
[ 5903.729977] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5903.932038] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5904.136078] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5904.340040] wlan0: authentication with <MAC address removed> timed out
[ 5907.539309] wlan0: authenticate with <MAC address removed>
[ 5907.540250] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 5907.744072] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 5907.954773] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 5908.156045] wlan0: authentication with <MAC address removed> timed out
[ 6221.068084] wlan0: authenticate with <MAC address removed>
[ 6221.076477] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6221.280056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6221.484027] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6221.688069] wlan0: authentication with <MAC address removed> timed out
[ 6241.035931] wlan0: authenticate with <MAC address removed>
[ 6241.039248] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6241.240327] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6241.444179] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6241.648320] wlan0: authentication with <MAC address removed> timed out
[ 6249.023480] wlan0: authenticate with <MAC address removed>
[ 6249.029722] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6249.232074] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6249.436068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6249.640124] wlan0: authentication with <MAC address removed> timed out
[ 6252.811540] wlan0: authenticate with <MAC address removed>
[ 6252.812609] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6253.016028] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6253.221037] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6253.424114] wlan0: authentication with <MAC address removed> timed out
[ 6264.691391] wlan0: authenticate with <MAC address removed>
[ 6264.694047] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6264.896039] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6265.100281] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6265.304123] wlan0: authentication with <MAC address removed> timed out
[ 6268.480631] wlan0: authenticate with <MAC address removed>
[ 6268.485561] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6268.688050] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6268.892041] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6269.096833] wlan0: authentication with <MAC address removed> timed out
[ 6277.081558] wlan0: authenticate with <MAC address removed>
[ 6277.087444] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6277.288076] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6277.492097] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6277.696155] wlan0: authentication with <MAC address removed> timed out
[ 6280.870308] wlan0: authenticate with <MAC address removed>
[ 6280.871390] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6281.072123] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6281.276302] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6281.480091] wlan0: authentication with <MAC address removed> timed out
[ 6284.660123] wlan0: authenticate with <MAC address removed>
[ 6284.667253] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6284.868049] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6285.072043] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6285.276182] wlan0: authentication with <MAC address removed> timed out
[ 6288.448202] wlan0: authenticate with <MAC address removed>
[ 6288.453924] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6288.656114] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6288.860561] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6289.064136] wlan0: authentication with <MAC address removed> timed out
[ 6292.338862] wlan0: authenticate with <MAC address removed>
[ 6292.339911] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6292.540097] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6292.744311] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6292.948097] wlan0: authentication with <MAC address removed> timed out
[ 6302.055309] wlan0: authenticate with <MAC address removed>
[ 6302.056385] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6302.260314] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6302.464119] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6302.668207] wlan0: authentication with <MAC address removed> timed out
[ 6305.856689] wlan0: authenticate with <MAC address removed>
[ 6305.862826] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6306.064126] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6306.268095] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6306.472098] wlan0: authentication with <MAC address removed> timed out
[ 6309.644785] wlan0: authenticate with <MAC address removed>
[ 6309.646111] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6309.848080] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6310.052053] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6310.256083] wlan0: authentication with <MAC address removed> timed out
[ 6313.434178] wlan0: authenticate with <MAC address removed>
[ 6313.435429] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6313.636104] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6313.840137] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6314.044315] wlan0: authentication with <MAC address removed> timed out
[ 6317.143636] wlan0: authenticate with <MAC address removed>
[ 6317.144684] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6317.348030] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6317.552054] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6317.756081] wlan0: authentication with <MAC address removed> timed out
[ 6320.908782] wlan0: authenticate with <MAC address removed>
[ 6320.910005] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6321.112311] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6321.316305] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6321.520120] wlan0: authentication with <MAC address removed> timed out
[ 6324.801166] wlan0: authenticate with <MAC address removed>
[ 6324.806006] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6325.008290] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6325.216165] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6325.420110] wlan0: authentication with <MAC address removed> timed out
[ 6630.060904] wlan0: authenticate with <MAC address removed>
[ 6630.065595] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6630.268198] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6630.472065] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6630.679105] wlan0: authentication with <MAC address removed> timed out
[ 6641.938545] wlan0: authenticate with <MAC address removed>
[ 6641.940192] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6642.144057] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6642.348775] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6642.552021] wlan0: authentication with <MAC address removed> timed out
[ 6645.728252] wlan0: authenticate with <MAC address removed>
[ 6645.730162] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6645.932326] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6646.136133] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6646.340067] wlan0: authentication with <MAC address removed> timed out
[ 6649.517805] wlan0: authenticate with <MAC address removed>
[ 6649.519325] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6649.720233] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6649.924309] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6650.128180] wlan0: authentication with <MAC address removed> timed out
[ 6674.293619] wlan0: authenticate with <MAC address removed>
[ 6674.294505] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6674.496315] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6674.700053] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6674.904063] wlan0: authentication with <MAC address removed> timed out
[ 6683.261408] wlan0: authenticate with <MAC address removed>
[ 6683.264963] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6683.468074] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6683.672093] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6683.876241] wlan0: authentication with <MAC address removed> timed out
[ 6703.072806] wlan0: authenticate with <MAC address removed>
[ 6703.074501] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6703.276165] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6703.480093] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6703.684053] wlan0: authentication with <MAC address removed> timed out
[ 6706.861834] wlan0: authenticate with <MAC address removed>
[ 6706.863387] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6707.064311] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6707.268202] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6707.472048] wlan0: authentication with <MAC address removed> timed out
[ 6722.222079] wlan0: authenticate with <MAC address removed>
[ 6722.223523] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6722.424040] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6722.628060] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6722.832030] wlan0: authentication with <MAC address removed> timed out
[ 6733.999968] wlan0: authenticate with <MAC address removed>
[ 6734.006037] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 6734.208116] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 6734.412051] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 6734.616296] wlan0: authentication with <MAC address removed> timed out
[ 7047.143324] wlan0: authenticate with <MAC address removed>
[ 7047.148330] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7047.352064] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7047.556033] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7047.760064] wlan0: authentication with <MAC address removed> timed out
[ 7059.022021] wlan0: authenticate with <MAC address removed>
[ 7059.023386] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7059.224043] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7059.428060] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7059.632047] wlan0: authentication with <MAC address removed> timed out
[ 7067.102386] wlan0: authenticate with <MAC address removed>
[ 7067.106112] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7067.308051] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7067.512067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7067.716043] wlan0: authentication with <MAC address removed> timed out
[ 7078.990419] wlan0: authenticate with <MAC address removed>
[ 7078.993331] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7079.196050] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7079.400040] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7079.604026] wlan0: authentication with <MAC address removed> timed out
[ 7082.779510] wlan0: authenticate with <MAC address removed>
[ 7082.781175] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7082.984049] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7083.188034] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7083.392077] wlan0: authentication with <MAC address removed> timed out
[ 7092.094836] wlan0: authenticate with <MAC address removed>
[ 7092.099972] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7092.300065] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7092.504019] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7092.708038] wlan0: authentication with <MAC address removed> timed out
[ 7095.886829] wlan0: authenticate with <MAC address removed>
[ 7095.889427] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7096.092038] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7096.296039] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7096.500038] wlan0: authentication with <MAC address removed> timed out
[ 7099.629105] wlan0: authenticate with <MAC address removed>
[ 7099.631977] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7099.832062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7100.036059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7100.240047] wlan0: authentication with <MAC address removed> timed out
[ 7111.451961] wlan0: authenticate with <MAC address removed>
[ 7111.454242] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7111.656065] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7111.860056] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7112.064023] wlan0: authentication with <MAC address removed> timed out
[ 7115.240823] wlan0: authenticate with <MAC address removed>
[ 7115.243188] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7115.444036] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7115.648031] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7115.852050] wlan0: authentication with <MAC address removed> timed out
[ 7131.113204] wlan0: authenticate with <MAC address removed>
[ 7131.119809] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7131.320068] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7131.524036] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7131.728039] wlan0: authentication with <MAC address removed> timed out
[ 7134.902823] wlan0: authenticate with <MAC address removed>
[ 7134.908650] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7135.112028] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7135.316051] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7135.520027] wlan0: authentication with <MAC address removed> timed out
[ 7138.793385] wlan0: authenticate with <MAC address removed>
[ 7138.795375] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7138.996056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7139.200048] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7139.404039] wlan0: authentication with <MAC address removed> timed out
[ 7142.582233] wlan0: authenticate with <MAC address removed>
[ 7142.583539] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7142.784041] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7142.988230] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7143.192077] wlan0: authentication with <MAC address removed> timed out
[ 7448.047897] wlan0: authenticate with <MAC address removed>
[ 7448.048756] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7448.256032] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7448.460064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7448.664040] wlan0: authentication with <MAC address removed> timed out
[ 7451.774434] wlan0: authenticate with <MAC address removed>
[ 7451.776516] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7451.980041] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7452.184073] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7452.388188] wlan0: authentication with <MAC address removed> timed out
[ 7455.625619] wlan0: authenticate with <MAC address removed>
[ 7455.626731] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7455.828038] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7456.032058] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7456.236066] wlan0: authentication with <MAC address removed> timed out
[ 7467.608748] wlan0: authenticate with <MAC address removed>
[ 7467.609661] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7467.812067] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7468.016075] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7468.220047] wlan0: authentication with <MAC address removed> timed out
[ 7476.006088] wlan0: authenticate with <MAC address removed>
[ 7476.007744] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7476.208059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7476.412062] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7476.616072] wlan0: authentication with <MAC address removed> timed out
[ 7487.986470] wlan0: authenticate with <MAC address removed>
[ 7487.991610] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7488.192086] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7488.396036] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7488.600032] wlan0: authentication with <MAC address removed> timed out
[ 7491.878054] wlan0: authenticate with <MAC address removed>
[ 7491.883217] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7492.084065] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7492.288037] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7492.492056] wlan0: authentication with <MAC address removed> timed out
[ 7495.767215] wlan0: authenticate with <MAC address removed>
[ 7495.768332] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7495.972038] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7496.176050] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7496.380041] wlan0: authentication with <MAC address removed> timed out
[ 7504.061985] wlan0: authenticate with <MAC address removed>
[ 7504.064231] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7504.268078] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7504.472056] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7504.676281] wlan0: authentication with <MAC address removed> timed out
[ 7507.851036] wlan0: authenticate with <MAC address removed>
[ 7507.853748] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7508.056078] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7508.260126] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7508.464098] wlan0: authentication with <MAC address removed> timed out
[ 7511.621576] wlan0: authenticate with <MAC address removed>
[ 7511.622621] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7511.824062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7512.028092] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7512.232084] wlan0: authentication with <MAC address removed> timed out
[ 7515.428611] wlan0: authenticate with <MAC address removed>
[ 7515.430765] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7515.632042] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7515.836040] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7516.040064] wlan0: authentication with <MAC address removed> timed out
[ 7519.199296] wlan0: authenticate with <MAC address removed>
[ 7519.200269] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7519.404086] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7519.608063] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7519.812072] wlan0: authentication with <MAC address removed> timed out
[ 7523.006489] wlan0: authenticate with <MAC address removed>
[ 7523.007553] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7523.208050] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7523.412081] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7523.616033] wlan0: authentication with <MAC address removed> timed out
[ 7532.021612] wlan0: authenticate with <MAC address removed>
[ 7532.022530] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7532.224054] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7532.428083] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7532.633049] wlan0: authentication with <MAC address removed> timed out
[ 7543.877798] wlan0: authenticate with <MAC address removed>
[ 7543.883162] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7544.084069] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7544.288067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7544.492028] wlan0: authentication with <MAC address removed> timed out
[ 7857.144666] wlan0: authenticate with <MAC address removed>
[ 7857.146937] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7857.348051] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7857.552046] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7857.756037] wlan0: authentication with <MAC address removed> timed out
[ 7861.036271] wlan0: authenticate with <MAC address removed>
[ 7861.039814] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7861.240054] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7861.444084] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7861.648051] wlan0: authentication with <MAC address removed> timed out
[ 7864.788004] wlan0: authenticate with <MAC address removed>
[ 7864.789626] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7864.992098] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7865.196094] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7865.400075] wlan0: authentication with <MAC address removed> timed out
[ 7868.716311] wlan0: authenticate with <MAC address removed>
[ 7868.717229] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7868.920054] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7869.124052] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7869.328572] wlan0: authentication with <MAC address removed> timed out
[ 7885.100609] wlan0: authenticate with <MAC address removed>
[ 7885.105820] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7885.308087] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7885.512026] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7885.716032] wlan0: authentication with <MAC address removed> timed out
[ 7897.081667] wlan0: authenticate with <MAC address removed>
[ 7897.084513] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7897.288060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7897.492048] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7897.696062] wlan0: authentication with <MAC address removed> timed out
[ 7900.933068] wlan0: authenticate with <MAC address removed>
[ 7900.934072] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7901.136050] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7901.340045] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7901.544043] wlan0: authentication with <MAC address removed> timed out
[ 7904.660881] wlan0: authenticate with <MAC address removed>
[ 7904.662425] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7904.865048] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7905.068024] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7905.272062] wlan0: authentication with <MAC address removed> timed out
[ 7913.059598] wlan0: authenticate with <MAC address removed>
[ 7913.060733] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7913.264060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7913.468044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7913.672088] wlan0: authentication with <MAC address removed> timed out
[ 7916.845289] wlan0: authenticate with <MAC address removed>
[ 7916.848699] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7917.052061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7917.256038] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7917.460436] wlan0: authentication with <MAC address removed> timed out
[ 7920.634085] wlan0: authenticate with <MAC address removed>
[ 7920.635734] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7920.836049] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7921.040047] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7921.244030] wlan0: authentication with <MAC address removed> timed out
[ 7924.423171] wlan0: authenticate with <MAC address removed>
[ 7924.424064] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7924.628053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7924.832056] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7925.036070] wlan0: authentication with <MAC address removed> timed out
[ 7941.109946] wlan0: authenticate with <MAC address removed>
[ 7941.122881] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7941.324062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7941.528075] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7941.732063] wlan0: authentication with <MAC address removed> timed out
[ 7952.972938] wlan0: authenticate with <MAC address removed>
[ 7952.984159] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 7953.188043] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 7953.392061] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 7953.596082] wlan0: authentication with <MAC address removed> timed out
[ 8005.102219] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 8008.725330] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 8008.730003] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 8008.758939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8015.125846] wlan0: authenticate with <MAC address removed>
[ 8015.135426] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8015.137836] wlan0: authenticated
[ 8015.140221] wlan0: associate with <MAC address removed> (try 1/3)
[ 8015.157040] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=1)
[ 8015.162805] wlan0: associated
[ 8015.162841] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8157.109192] wlan0: authenticate with <MAC address removed>
[ 8157.110203] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8157.132826] wlan0: send auth to <MAC address removed> (try 2/3)
[ 8157.156961] wlan0: send auth to <MAC address removed> (try 3/3)
[ 8157.179372] wlan0: authentication with <MAC address removed> timed out
[ 8160.400869] wlan0: authenticate with <MAC address removed>
[ 8160.401756] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8160.604083] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8160.808057] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8161.012091] wlan0: authentication with <MAC address removed> timed out
[ 8169.272444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8202.101732] wlan0: authenticate with <MAC address removed>
[ 8202.105539] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8202.308028] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8202.512045] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8202.716055] wlan0: authentication with <MAC address removed> timed out
[ 8205.992502] wlan0: authenticate with <MAC address removed>
[ 8205.995973] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8206.196048] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8206.400042] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8206.604057] wlan0: authentication with <MAC address removed> timed out
[ 8209.784698] wlan0: authenticate with <MAC address removed>
[ 8209.787169] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8209.988030] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8210.192054] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8210.396233] wlan0: authentication with <MAC address removed> timed out
[ 8213.574715] wlan0: authenticate with <MAC address removed>
[ 8213.576041] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8213.780056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8213.984041] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8214.188057] wlan0: authentication with <MAC address removed> timed out
[ 8217.336993] wlan0: authenticate with <MAC address removed>
[ 8217.338001] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8217.540078] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8217.744068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8217.948053] wlan0: authentication with <MAC address removed> timed out
[ 8230.068976] wlan0: authenticate with <MAC address removed>
[ 8230.069805] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8230.272244] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8230.476035] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8230.680105] wlan0: authentication with <MAC address removed> timed out
[ 8233.860832] wlan0: authenticate with <MAC address removed>
[ 8233.862068] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8234.064048] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8234.268068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8234.472052] wlan0: authentication with <MAC address removed> timed out
[ 8258.038540] wlan0: authenticate with <MAC address removed>
[ 8258.039643] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8258.240062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8258.444061] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8258.648069] wlan0: authentication with <MAC address removed> timed out
[ 8261.829688] wlan0: authenticate with <MAC address removed>
[ 8261.830686] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8262.032268] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8262.236095] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8262.440310] wlan0: authentication with <MAC address removed> timed out
[ 8265.649636] wlan0: authenticate with <MAC address removed>
[ 8265.651013] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8265.852118] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8266.056044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8266.260037] wlan0: authentication with <MAC address removed> timed out
[ 8287.032968] wlan0: authenticate with <MAC address removed>
[ 8287.033980] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8287.236029] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8287.440064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8287.644077] wlan0: authentication with <MAC address removed> timed out
[ 8290.824114] wlan0: authenticate with <MAC address removed>
[ 8290.825347] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8291.028046] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8291.232236] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8291.436050] wlan0: authentication with <MAC address removed> timed out
[ 8294.599735] wlan0: authenticate with <MAC address removed>
[ 8294.600675] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8294.804051] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8295.008048] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8295.212091] wlan0: authentication with <MAC address removed> timed out
[ 8330.784604] wlan0: authenticate with <MAC address removed>
[ 8330.791700] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8330.992044] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8331.196052] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8331.400075] wlan0: authentication with <MAC address removed> timed out
[ 8334.673537] wlan0: authenticate with <MAC address removed>
[ 8334.674535] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8334.876101] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8335.080280] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8335.284179] wlan0: authentication with <MAC address removed> timed out
[ 8342.152701] wlan0: authenticate with <MAC address removed>
[ 8342.155174] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8342.356069] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8342.564074] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8342.768035] wlan0: authentication with <MAC address removed> timed out
[ 8345.928346] wlan0: authenticate with <MAC address removed>
[ 8345.930331] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8346.132114] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8346.336135] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8346.540116] wlan0: authentication with <MAC address removed> timed out
[ 8667.013289] wlan0: authenticate with <MAC address removed>
[ 8667.014632] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8667.216088] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8667.420064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8667.624110] wlan0: authentication with <MAC address removed> timed out
[ 8678.820594] wlan0: authenticate with <MAC address removed>
[ 8678.821805] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8679.024061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8679.228063] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8679.432078] wlan0: authentication with <MAC address removed> timed out
[ 8695.069864] wlan0: authenticate with <MAC address removed>
[ 8695.072609] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8695.276071] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8695.480056] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8695.684077] wlan0: authentication with <MAC address removed> timed out
[ 8698.792058] wlan0: authenticate with <MAC address removed>
[ 8698.795234] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8698.996053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8699.200053] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8699.404059] wlan0: authentication with <MAC address removed> timed out
[ 8702.564582] wlan0: authenticate with <MAC address removed>
[ 8702.565656] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8702.768038] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8702.972090] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8703.176077] wlan0: authentication with <MAC address removed> timed out
[ 8714.467326] wlan0: authenticate with <MAC address removed>
[ 8714.468316] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8714.672095] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8714.876879] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8715.080083] wlan0: authentication with <MAC address removed> timed out
[ 8723.073138] wlan0: authenticate with <MAC address removed>
[ 8723.076747] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8723.280045] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8723.484033] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8723.688029] wlan0: authentication with <MAC address removed> timed out
[ 8734.957615] wlan0: authenticate with <MAC address removed>
[ 8734.966433] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8735.168073] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8735.372103] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8735.576063] wlan0: authentication with <MAC address removed> timed out
[ 8738.748377] wlan0: authenticate with <MAC address removed>
[ 8738.750299] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8738.952087] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8739.156077] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8739.360040] wlan0: authentication with <MAC address removed> timed out
[ 8742.541045] wlan0: authenticate with <MAC address removed>
[ 8742.543445] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8742.744085] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8742.948124] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8743.152067] wlan0: authentication with <MAC address removed> timed out
[ 8751.043344] wlan0: authenticate with <MAC address removed>
[ 8751.044738] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8751.248144] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8751.452286] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8751.656064] wlan0: authentication with <MAC address removed> timed out
[ 8754.834570] wlan0: authenticate with <MAC address removed>
[ 8754.840326] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8755.044106] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8755.248091] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8755.452031] wlan0: authentication with <MAC address removed> timed out
[ 8758.628697] wlan0: authenticate with <MAC address removed>
[ 8758.638039] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8758.840072] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8759.044053] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8759.248276] wlan0: authentication with <MAC address removed> timed out
[ 8770.669157] wlan0: authenticate with <MAC address removed>
[ 8770.671361] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 8770.872118] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 8771.076061] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 8771.280084] wlan0: authentication with <MAC address removed> timed out
[ 9076.126946] wlan0: authenticate with <MAC address removed>
[ 9076.133253] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9076.336082] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9076.540069] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9076.744087] wlan0: authentication with <MAC address removed> timed out
[ 9087.987571] wlan0: authenticate with <MAC address removed>
[ 9087.990374] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9088.192059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9088.396046] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9088.600060] wlan0: authentication with <MAC address removed> timed out
[ 9091.793278] wlan0: authenticate with <MAC address removed>
[ 9091.794672] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9091.996286] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9092.200284] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9092.404057] wlan0: authentication with <MAC address removed> timed out
[ 9095.582502] wlan0: authenticate with <MAC address removed>
[ 9095.583543] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9095.784059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9095.988059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9096.192045] wlan0: authentication with <MAC address removed> timed out
[ 9104.081476] wlan0: authenticate with <MAC address removed>
[ 9104.083285] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9104.284060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9104.488064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9104.692075] wlan0: authentication with <MAC address removed> timed out
[ 9107.871304] wlan0: authenticate with <MAC address removed>
[ 9107.872498] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9108.076164] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9108.280065] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9108.489651] wlan0: authentication with <MAC address removed> timed out
[ 9111.685454] wlan0: authenticate with <MAC address removed>
[ 9111.686993] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9111.888245] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9112.092087] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9112.296259] wlan0: authentication with <MAC address removed> timed out
[ 9115.448260] wlan0: authenticate with <MAC address removed>
[ 9115.450664] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9115.652083] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9115.856071] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9116.060158] wlan0: authentication with <MAC address removed> timed out
[ 9132.038888] wlan0: authenticate with <MAC address removed>
[ 9132.041321] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9132.244167] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9132.448305] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9132.652079] wlan0: authentication with <MAC address removed> timed out
[ 9143.917332] wlan0: authenticate with <MAC address removed>
[ 9143.918563] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9144.120189] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9144.324324] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9144.528070] wlan0: authentication with <MAC address removed> timed out
[ 9147.704819] wlan0: authenticate with <MAC address removed>
[ 9147.705864] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9147.908098] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9148.116160] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9148.320290] wlan0: authentication with <MAC address removed> timed out
[ 9151.464153] wlan0: authenticate with <MAC address removed>
[ 9151.466218] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9151.668284] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9151.872161] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9152.076189] wlan0: authentication with <MAC address removed> timed out
[ 9160.073740] wlan0: authenticate with <MAC address removed>
[ 9160.083889] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9160.284164] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9160.488171] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9160.692161] wlan0: authentication with <MAC address removed> timed out
[ 9163.885143] wlan0: authenticate with <MAC address removed>
[ 9163.886858] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9164.088259] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9164.292254] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9164.496339] wlan0: authentication with <MAC address removed> timed out
[ 9485.119011] wlan0: authenticate with <MAC address removed>
[ 9485.120089] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9485.324304] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9485.528052] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9485.732080] wlan0: authentication with <MAC address removed> timed out
[ 9489.010365] wlan0: authenticate with <MAC address removed>
[ 9489.011437] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9489.212056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9489.416073] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9489.620237] wlan0: authentication with <MAC address removed> timed out
[ 9500.848176] wlan0: authenticate with <MAC address removed>
[ 9500.851823] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9501.052066] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9501.256043] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9501.460214] wlan0: authentication with <MAC address removed> timed out
[ 9504.667082] wlan0: authenticate with <MAC address removed>
[ 9504.677001] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9504.880323] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9505.084247] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9505.288055] wlan0: authentication with <MAC address removed> timed out
[ 9521.176064] wlan0: authenticate with <MAC address removed>
[ 9521.181066] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9521.384304] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9521.588228] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9521.792265] wlan0: authentication with <MAC address removed> timed out
[ 9533.043708] wlan0: authenticate with <MAC address removed>
[ 9533.045821] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9533.248308] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9533.452055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9533.656298] wlan0: authentication with <MAC address removed> timed out
[ 9549.213296] wlan0: authenticate with <MAC address removed>
[ 9549.223150] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9549.424268] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9549.628076] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9549.832082] wlan0: authentication with <MAC address removed> timed out
[ 9569.293269] wlan0: authenticate with <MAC address removed>
[ 9569.294164] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9569.496049] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9569.700044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9569.904246] wlan0: authentication with <MAC address removed> timed out
[ 9581.172973] wlan0: authenticate with <MAC address removed>
[ 9581.175949] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9581.376278] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9581.580251] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9581.784231] wlan0: authentication with <MAC address removed> timed out
[ 9894.112474] wlan0: authenticate with <MAC address removed>
[ 9894.116707] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9894.320223] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9894.524064] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9894.728038] wlan0: authentication with <MAC address removed> timed out
[ 9897.903761] wlan0: authenticate with <MAC address removed>
[ 9897.905556] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9898.108059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9898.312044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9898.516072] wlan0: authentication with <MAC address removed> timed out
[ 9922.170379] wlan0: authenticate with <MAC address removed>
[ 9922.174811] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9922.376028] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9922.580047] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9922.784216] wlan0: authentication with <MAC address removed> timed out
[ 9951.150472] wlan0: authenticate with <MAC address removed>
[ 9951.154587] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9951.359226] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9951.560153] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9951.764053] wlan0: authentication with <MAC address removed> timed out
[ 9963.029701] wlan0: authenticate with <MAC address removed>
[ 9963.033776] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9963.237241] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9963.440028] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9963.644053] wlan0: authentication with <MAC address removed> timed out
[ 9966.877034] wlan0: authenticate with <MAC address removed>
[ 9966.878628] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9967.080056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9967.284054] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9967.488044] wlan0: authentication with <MAC address removed> timed out
[ 9970.709033] wlan0: authenticate with <MAC address removed>
[ 9970.710850] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 9970.912383] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 9971.116019] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 9971.320245] wlan0: authentication with <MAC address removed> timed out
[10303.107186] wlan0: authenticate with <MAC address removed>
[10303.109536] wlan0: direct probe to <MAC address removed> (try 1/3)
[10303.312324] wlan0: direct probe to <MAC address removed> (try 2/3)
[10303.516242] wlan0: direct probe to <MAC address removed> (try 3/3)
[10303.720069] wlan0: authentication with <MAC address removed> timed out
[10314.984592] wlan0: authenticate with <MAC address removed>
[10314.985492] wlan0: direct probe to <MAC address removed> (try 1/3)
[10315.188070] wlan0: direct probe to <MAC address removed> (try 2/3)
[10315.392216] wlan0: direct probe to <MAC address removed> (try 3/3)
[10315.596283] wlan0: authentication with <MAC address removed> timed out
[10318.774023] wlan0: authenticate with <MAC address removed>
[10318.775078] wlan0: direct probe to <MAC address removed> (try 1/3)
[10318.976224] wlan0: direct probe to <MAC address removed> (try 2/3)
[10319.180034] wlan0: direct probe to <MAC address removed> (try 3/3)
[10319.384231] wlan0: authentication with <MAC address removed> timed out
[10322.562257] wlan0: authenticate with <MAC address removed>
[10322.563501] wlan0: direct probe to <MAC address removed> (try 1/3)
[10322.764052] wlan0: direct probe to <MAC address removed> (try 2/3)
[10322.968308] wlan0: direct probe to <MAC address removed> (try 3/3)
[10323.172067] wlan0: authentication with <MAC address removed> timed out
[10331.061661] wlan0: authenticate with <MAC address removed>
[10331.065725] wlan0: direct probe to <MAC address removed> (try 1/3)
[10331.268047] wlan0: direct probe to <MAC address removed> (try 2/3)
[10331.472042] wlan0: direct probe to <MAC address removed> (try 3/3)
[10331.676043] wlan0: authentication with <MAC address removed> timed out
[10334.850595] wlan0: authenticate with <MAC address removed>
[10334.851416] wlan0: direct probe to <MAC address removed> (try 1/3)
[10335.052037] wlan0: direct probe to <MAC address removed> (try 2/3)
[10335.256289] wlan0: direct probe to <MAC address removed> (try 3/3)
[10335.460069] wlan0: authentication with <MAC address removed> timed out
[10346.696595] wlan0: authenticate with <MAC address removed>
[10346.697750] wlan0: direct probe to <MAC address removed> (try 1/3)
[10346.900285] wlan0: direct probe to <MAC address removed> (try 2/3)
[10347.104271] wlan0: direct probe to <MAC address removed> (try 3/3)
[10347.308247] wlan0: authentication with <MAC address removed> timed out
[10350.518224] wlan0: authenticate with <MAC address removed>
[10350.521205] wlan0: direct probe to <MAC address removed> (try 1/3)
[10350.724038] wlan0: direct probe to <MAC address removed> (try 2/3)
[10350.928245] wlan0: direct probe to <MAC address removed> (try 3/3)
[10351.132061] wlan0: authentication with <MAC address removed> timed out
[10359.121700] wlan0: authenticate with <MAC address removed>
[10359.129790] wlan0: direct probe to <MAC address removed> (try 1/3)
[10359.332070] wlan0: direct probe to <MAC address removed> (try 2/3)
[10359.536312] wlan0: direct probe to <MAC address removed> (try 3/3)
[10359.740047] wlan0: authentication with <MAC address removed> timed out
[10362.875876] wlan0: authenticate with <MAC address removed>
[10362.877467] wlan0: direct probe to <MAC address removed> (try 1/3)
[10363.080227] wlan0: direct probe to <MAC address removed> (try 2/3)
[10363.284138] wlan0: direct probe to <MAC address removed> (try 3/3)
[10363.488533] wlan0: authentication with <MAC address removed> timed out
[10374.685012] wlan0: authenticate with <MAC address removed>
[10374.685966] wlan0: direct probe to <MAC address removed> (try 1/3)
[10374.888233] wlan0: direct probe to <MAC address removed> (try 2/3)
[10375.092063] wlan0: direct probe to <MAC address removed> (try 3/3)
[10375.296221] wlan0: authentication with <MAC address removed> timed out
[10378.438614] wlan0: authenticate with <MAC address removed>
[10378.442243] wlan0: direct probe to <MAC address removed> (try 1/3)
[10378.644065] wlan0: direct probe to <MAC address removed> (try 2/3)
[10378.848024] wlan0: direct probe to <MAC address removed> (try 3/3)
[10379.052091] wlan0: authentication with <MAC address removed> timed out
[10387.075625] wlan0: authenticate with <MAC address removed>
[10387.076760] wlan0: direct probe to <MAC address removed> (try 1/3)
[10387.280287] wlan0: direct probe to <MAC address removed> (try 2/3)
[10387.484096] wlan0: direct probe to <MAC address removed> (try 3/3)
[10387.688245] wlan0: authentication with <MAC address removed> timed out
[10712.020503] wlan0: authenticate with <MAC address removed>
[10712.024614] wlan0: direct probe to <MAC address removed> (try 1/3)
[10712.228076] wlan0: direct probe to <MAC address removed> (try 2/3)
[10712.432060] wlan0: direct probe to <MAC address removed> (try 3/3)
[10712.636029] wlan0: authentication with <MAC address removed> timed out
[10749.067094] wlan0: authenticate with <MAC address removed>
[10749.068207] wlan0: direct probe to <MAC address removed> (try 1/3)
[10749.272060] wlan0: direct probe to <MAC address removed> (try 2/3)
[10749.476246] wlan0: direct probe to <MAC address removed> (try 3/3)
[10749.680114] wlan0: authentication with <MAC address removed> timed out
[10760.847679] wlan0: authenticate with <MAC address removed>
[10760.849484] wlan0: direct probe to <MAC address removed> (try 1/3)
[10761.052098] wlan0: direct probe to <MAC address removed> (try 2/3)
[10761.256281] wlan0: direct probe to <MAC address removed> (try 3/3)
[10761.460222] wlan0: authentication with <MAC address removed> timed out
[10768.011672] wlan0: authenticate with <MAC address removed>
[10768.014381] wlan0: direct probe to <MAC address removed> (try 1/3)
[10768.216228] wlan0: direct probe to <MAC address removed> (try 2/3)
[10768.420067] wlan0: direct probe to <MAC address removed> (try 3/3)
[10768.624063] wlan0: authentication with <MAC address removed> timed out
[10771.800055] wlan0: authenticate with <MAC address removed>
[10771.801760] wlan0: direct probe to <MAC address removed> (try 1/3)
[10772.004039] wlan0: direct probe to <MAC address removed> (try 2/3)
[10772.208058] wlan0: direct probe to <MAC address removed> (try 3/3)
[10772.412040] wlan0: authentication with <MAC address removed> timed out
[10796.069409] wlan0: authenticate with <MAC address removed>
[10796.070831] wlan0: direct probe to <MAC address removed> (try 1/3)
[10796.272061] wlan0: direct probe to <MAC address removed> (try 2/3)
[10796.476048] wlan0: direct probe to <MAC address removed> (try 3/3)
[10796.680078] wlan0: authentication with <MAC address removed> timed out
[10815.987828] wlan0: authenticate with <MAC address removed>
[10815.989077] wlan0: direct probe to <MAC address removed> (try 1/3)
[10816.196297] wlan0: direct probe to <MAC address removed> (try 2/3)
[10816.400224] wlan0: direct probe to <MAC address removed> (try 3/3)
[10816.604081] wlan0: authentication with <MAC address removed> timed out
[11320.062195] wlan0: authenticate with <MAC address removed>
[11320.063594] wlan0: direct probe to <MAC address removed> (try 1/3)
[11320.264054] wlan0: direct probe to <MAC address removed> (try 2/3)
[11320.468232] wlan0: direct probe to <MAC address removed> (try 3/3)
[11320.672286] wlan0: authentication with <MAC address removed> timed out
[11331.897042] wlan0: authenticate with <MAC address removed>
[11331.898517] wlan0: direct probe to <MAC address removed> (try 1/3)
[11332.100306] wlan0: direct probe to <MAC address removed> (try 2/3)
[11332.304265] wlan0: direct probe to <MAC address removed> (try 3/3)
[11332.508269] wlan0: authentication with <MAC address removed> timed out
[11348.119523] wlan0: authenticate with <MAC address removed>
[11348.125109] wlan0: direct probe to <MAC address removed> (try 1/3)
[11348.328078] wlan0: direct probe to <MAC address removed> (try 2/3)
[11348.532057] wlan0: direct probe to <MAC address removed> (try 3/3)
[11348.736291] wlan0: authentication with <MAC address removed> timed out
[11351.865517] wlan0: authenticate with <MAC address removed>
[11351.866628] wlan0: direct probe to <MAC address removed> (try 1/3)
[11352.068065] wlan0: direct probe to <MAC address removed> (try 2/3)
[11352.272038] wlan0: direct probe to <MAC address removed> (try 3/3)
[11352.476027] wlan0: authentication with <MAC address removed> timed out
[11363.786582] wlan0: authenticate with <MAC address removed>
[11363.788698] wlan0: direct probe to <MAC address removed> (try 1/3)
[11363.992080] wlan0: direct probe to <MAC address removed> (try 2/3)
[11364.196047] wlan0: direct probe to <MAC address removed> (try 3/3)
[11364.400062] wlan0: authentication with <MAC address removed> timed out
[11367.615716] wlan0: authenticate with <MAC address removed>
[11367.616794] wlan0: direct probe to <MAC address removed> (try 1/3)
[11367.820068] wlan0: direct probe to <MAC address removed> (try 2/3)
[11368.024164] wlan0: direct probe to <MAC address removed> (try 3/3)
[11368.228084] wlan0: authentication with <MAC address removed> timed out
[11376.074948] wlan0: authenticate with <MAC address removed>
[11376.077662] wlan0: direct probe to <MAC address removed> (try 1/3)
[11376.280056] wlan0: direct probe to <MAC address removed> (try 2/3)
[11376.484081] wlan0: direct probe to <MAC address removed> (try 3/3)
[11376.688077] wlan0: authentication with <MAC address removed> timed out
[11380.035649] wlan0: authenticate with <MAC address removed>
[11380.037014] wlan0: direct probe to <MAC address removed> (try 1/3)
[11380.240050] wlan0: direct probe to <MAC address removed> (try 2/3)
[11380.444110] wlan0: direct probe to <MAC address removed> (try 3/3)
[11380.648057] wlan0: authentication with <MAC address removed> timed out
[11383.801906] wlan0: authenticate with <MAC address removed>
[11383.804609] wlan0: direct probe to <MAC address removed> (try 1/3)
[11384.008105] wlan0: direct probe to <MAC address removed> (try 2/3)
[11384.212079] wlan0: direct probe to <MAC address removed> (try 3/3)
[11384.416079] wlan0: authentication with <MAC address removed> timed out
[11387.646353] wlan0: authenticate with <MAC address removed>
[11387.648718] wlan0: direct probe to <MAC address removed> (try 1/3)
[11387.852088] wlan0: direct probe to <MAC address removed> (try 2/3)
[11388.056046] wlan0: direct probe to <MAC address removed> (try 3/3)
[11388.262227] wlan0: authentication with <MAC address removed> timed out
[11391.436226] wlan0: authenticate with <MAC address removed>
[11391.439523] wlan0: direct probe to <MAC address removed> (try 1/3)
[11391.640055] wlan0: direct probe to <MAC address removed> (try 2/3)
[11391.844055] wlan0: direct probe to <MAC address removed> (try 3/3)
[11392.048085] wlan0: authentication with <MAC address removed> timed out
[11395.223711] wlan0: authenticate with <MAC address removed>
[11395.227502] wlan0: direct probe to <MAC address removed> (try 1/3)
[11395.428039] wlan0: direct probe to <MAC address removed> (try 2/3)
[11395.632047] wlan0: direct probe to <MAC address removed> (try 3/3)
[11395.836043] wlan0: authentication with <MAC address removed> timed out
[11404.013488] wlan0: authenticate with <MAC address removed>
[11404.016170] wlan0: direct probe to <MAC address removed> (try 1/3)
[11404.220058] wlan0: direct probe to <MAC address removed> (try 2/3)
[11404.424094] wlan0: direct probe to <MAC address removed> (try 3/3)
[11404.628056] wlan0: authentication with <MAC address removed> timed out
[11407.819344] wlan0: authenticate with <MAC address removed>
[11407.820799] wlan0: direct probe to <MAC address removed> (try 1/3)
[11408.024073] wlan0: direct probe to <MAC address removed> (try 2/3)
[11408.228075] wlan0: direct probe to <MAC address removed> (try 3/3)
[11408.432067] wlan0: authentication with <MAC address removed> timed out
[11411.607808] wlan0: authenticate with <MAC address removed>
[11411.614230] wlan0: direct probe to <MAC address removed> (try 1/3)
[11411.816053] wlan0: direct probe to <MAC address removed> (try 2/3)
[11412.020075] wlan0: direct probe to <MAC address removed> (try 3/3)
[11412.224053] wlan0: authentication with <MAC address removed> timed out
[11415.378713] wlan0: authenticate with <MAC address removed>
[11415.379730] wlan0: direct probe to <MAC address removed> (try 1/3)
[11415.580066] wlan0: direct probe to <MAC address removed> (try 2/3)
[11415.784051] wlan0: direct probe to <MAC address removed> (try 3/3)
[11415.988043] wlan0: authentication with <MAC address removed> timed out
[11419.189005] wlan0: authenticate with <MAC address removed>
[11419.190127] wlan0: direct probe to <MAC address removed> (try 1/3)
[11419.392059] wlan0: direct probe to <MAC address removed> (try 2/3)
[11419.596067] wlan0: direct probe to <MAC address removed> (try 3/3)
[11419.800075] wlan0: authentication with <MAC address removed> timed out
[11729.054166] wlan0: authenticate with <MAC address removed>
[11729.055131] wlan0: direct probe to <MAC address removed> (try 1/3)
[11729.256069] wlan0: direct probe to <MAC address removed> (try 2/3)
[11729.460031] wlan0: direct probe to <MAC address removed> (try 3/3)
[11729.664188] wlan0: authentication with <MAC address removed> timed out
[11732.843721] wlan0: authenticate with <MAC address removed>
[11732.848786] wlan0: direct probe to <MAC address removed> (try 1/3)
[11733.052312] wlan0: direct probe to <MAC address removed> (try 2/3)
[11733.256087] wlan0: direct probe to <MAC address removed> (try 3/3)
[11733.460116] wlan0: authentication with <MAC address removed> timed out
[11736.634745] wlan0: authenticate with <MAC address removed>
[11736.635771] wlan0: direct probe to <MAC address removed> (try 1/3)
[11736.836069] wlan0: direct probe to <MAC address removed> (try 2/3)
[11737.040036] wlan0: direct probe to <MAC address removed> (try 3/3)
[11737.244277] wlan0: authentication with <MAC address removed> timed out
[11748.551344] wlan0: authenticate with <MAC address removed>
[11748.557266] wlan0: direct probe to <MAC address removed> (try 1/3)
[11748.760060] wlan0: direct probe to <MAC address removed> (try 2/3)
[11748.964090] wlan0: direct probe to <MAC address removed> (try 3/3)
[11749.168307] wlan0: authentication with <MAC address removed> timed out
[11757.099966] wlan0: authenticate with <MAC address removed>
[11757.105147] wlan0: direct probe to <MAC address removed> (try 1/3)
[11757.308255] wlan0: direct probe to <MAC address removed> (try 2/3)
[11757.512082] wlan0: direct probe to <MAC address removed> (try 3/3)
[11757.716288] wlan0: authentication with <MAC address removed> timed out
[11761.004466] wlan0: authenticate with <MAC address removed>
[11761.010507] wlan0: direct probe to <MAC address removed> (try 1/3)
[11761.212299] wlan0: direct probe to <MAC address removed> (try 2/3)
[11761.416277] wlan0: direct probe to <MAC address removed> (try 3/3)
[11761.620064] wlan0: authentication with <MAC address removed> timed out
[11764.795714] wlan0: authenticate with <MAC address removed>
[11764.800780] wlan0: direct probe to <MAC address removed> (try 1/3)
[11765.004086] wlan0: direct probe to <MAC address removed> (try 2/3)
[11765.208072] wlan0: direct probe to <MAC address removed> (try 3/3)
[11765.412066] wlan0: authentication with <MAC address removed> timed out
[11768.641573] wlan0: authenticate with <MAC address removed>
[11768.643714] wlan0: direct probe to <MAC address removed> (try 1/3)
[11768.844054] wlan0: direct probe to <MAC address removed> (try 2/3)
[11769.048031] wlan0: direct probe to <MAC address removed> (try 3/3)
[11769.252177] wlan0: authentication with <MAC address removed> timed out
[11785.170712] wlan0: authenticate with <MAC address removed>
[11785.171727] wlan0: direct probe to <MAC address removed> (try 1/3)
[11785.372238] wlan0: direct probe to <MAC address removed> (try 2/3)
[11785.576050] wlan0: direct probe to <MAC address removed> (try 3/3)
[11785.780290] wlan0: authentication with <MAC address removed> timed out
[11797.048874] wlan0: authenticate with <MAC address removed>
[11797.049793] wlan0: direct probe to <MAC address removed> (try 1/3)
[11797.252041] wlan0: direct probe to <MAC address removed> (try 2/3)
[11797.456039] wlan0: direct probe to <MAC address removed> (try 3/3)
[11797.660067] wlan0: authentication with <MAC address removed> timed out
[11800.838237] wlan0: authenticate with <MAC address removed>
[11800.839520] wlan0: direct probe to <MAC address removed> (try 1/3)
[11801.040247] wlan0: direct probe to <MAC address removed> (try 2/3)
[11801.244059] wlan0: direct probe to <MAC address removed> (try 3/3)
[11801.448062] wlan0: authentication with <MAC address removed> timed out
[11804.666529] wlan0: authenticate with <MAC address removed>
[11804.668356] wlan0: direct probe to <MAC address removed> (try 1/3)
[11804.872046] wlan0: direct probe to <MAC address removed> (try 2/3)
[11805.076076] wlan0: direct probe to <MAC address removed> (try 3/3)
[11805.280662] wlan0: authentication with <MAC address removed> timed out
[11813.127819] wlan0: authenticate with <MAC address removed>
[11813.130738] wlan0: direct probe to <MAC address removed> (try 1/3)
[11813.332232] wlan0: direct probe to <MAC address removed> (try 2/3)
[11813.536090] wlan0: direct probe to <MAC address removed> (try 3/3)
[11813.740077] wlan0: authentication with <MAC address removed> timed out
[11824.984840] wlan0: authenticate with <MAC address removed>
[11824.985802] wlan0: direct probe to <MAC address removed> (try 1/3)
[11825.188073] wlan0: direct probe to <MAC address removed> (try 2/3)
[11825.392052] wlan0: direct probe to <MAC address removed> (try 3/3)
[11825.596076] wlan0: authentication with <MAC address removed> timed out
[11828.794960] wlan0: authenticate with <MAC address removed>
[11828.800879] wlan0: direct probe to <MAC address removed> (try 1/3)
[11829.004068] wlan0: direct probe to <MAC address removed> (try 2/3)
[11829.208271] wlan0: direct probe to <MAC address removed> (try 3/3)
[11829.412073] wlan0: authentication with <MAC address removed> timed out
[11832.583853] wlan0: authenticate with <MAC address removed>
[11832.585097] wlan0: direct probe to <MAC address removed> (try 1/3)
[11832.788061] wlan0: direct probe to <MAC address removed> (try 2/3)
[11832.992063] wlan0: direct probe to <MAC address removed> (try 3/3)
[11833.196050] wlan0: authentication with <MAC address removed> timed out
[12138.048111] wlan0: authenticate with <MAC address removed>
[12138.053628] wlan0: direct probe to <MAC address removed> (try 1/3)
[12138.256309] wlan0: direct probe to <MAC address removed> (try 2/3)
[12138.460106] wlan0: direct probe to <MAC address removed> (try 3/3)
[12138.664034] wlan0: authentication with <MAC address removed> timed out
[12149.926856] wlan0: authenticate with <MAC address removed>
[12149.928002] wlan0: direct probe to <MAC address removed> (try 1/3)
[12150.132061] wlan0: direct probe to <MAC address removed> (try 2/3)
[12150.336069] wlan0: direct probe to <MAC address removed> (try 3/3)
[12150.544057] wlan0: authentication with <MAC address removed> timed out
[12174.196267] wlan0: authenticate with <MAC address removed>
[12174.200396] wlan0: direct probe to <MAC address removed> (try 1/3)
[12174.404112] wlan0: direct probe to <MAC address removed> (try 2/3)
[12174.608081] wlan0: direct probe to <MAC address removed> (try 3/3)
[12174.812221] wlan0: authentication with <MAC address removed> timed out
[12178.067196] wlan0: authenticate with <MAC address removed>
[12178.071246] wlan0: direct probe to <MAC address removed> (try 1/3)
[12178.272062] wlan0: direct probe to <MAC address removed> (try 2/3)
[12178.476273] wlan0: direct probe to <MAC address removed> (try 3/3)
[12178.680215] wlan0: authentication with <MAC address removed> timed out
[12181.875780] wlan0: authenticate with <MAC address removed>
[12181.881043] wlan0: direct probe to <MAC address removed> (try 1/3)
[12182.084098] wlan0: direct probe to <MAC address removed> (try 2/3)
[12182.288283] wlan0: direct probe to <MAC address removed> (try 3/3)
[12182.492350] wlan0: authentication with <MAC address removed> timed out
[12191.088432] wlan0: authenticate with <MAC address removed>
[12191.089493] wlan0: direct probe to <MAC address removed> (try 1/3)
[12191.292329] wlan0: direct probe to <MAC address removed> (try 2/3)
[12191.496093] wlan0: direct probe to <MAC address removed> (try 3/3)
[12191.700278] wlan0: authentication with <MAC address removed> timed out
[12194.881030] wlan0: authenticate with <MAC address removed>
[12194.885653] wlan0: direct probe to <MAC address removed> (try 1/3)
[12195.088098] wlan0: direct probe to <MAC address removed> (try 2/3)
[12195.292053] wlan0: direct probe to <MAC address removed> (try 3/3)
[12195.496060] wlan0: authentication with <MAC address removed> timed out
[12198.669938] wlan0: authenticate with <MAC address removed>
[12198.673646] wlan0: direct probe to <MAC address removed> (try 1/3)
[12198.878994] wlan0: direct probe to <MAC address removed> (try 2/3)
[12199.080046] wlan0: direct probe to <MAC address removed> (try 3/3)
[12199.284036] wlan0: authentication with <MAC address removed> timed out
[12202.459312] wlan0: authenticate with <MAC address removed>
[12202.462839] wlan0: direct probe to <MAC address removed> (try 1/3)
[12202.664072] wlan0: direct probe to <MAC address removed> (try 2/3)
[12202.868065] wlan0: direct probe to <MAC address removed> (try 3/3)
[12203.072244] wlan0: authentication with <MAC address removed> timed out
[12214.334422] wlan0: authenticate with <MAC address removed>
[12214.337662] wlan0: direct probe to <MAC address removed> (try 1/3)
[12214.540307] wlan0: direct probe to <MAC address removed> (try 2/3)
[12214.744324] wlan0: direct probe to <MAC address removed> (try 3/3)
[12214.948334] wlan0: authentication with <MAC address removed> timed out
[12222.018378] wlan0: authenticate with <MAC address removed>
[12222.025326] wlan0: direct probe to <MAC address removed> (try 1/3)
[12222.228283] wlan0: direct probe to <MAC address removed> (try 2/3)
[12222.432202] wlan0: direct probe to <MAC address removed> (try 3/3)
[12222.636135] wlan0: authentication with <MAC address removed> timed out
[12225.807600] wlan0: authenticate with <MAC address removed>
[12225.811842] wlan0: direct probe to <MAC address removed> (try 1/3)
[12226.012117] wlan0: direct probe to <MAC address removed> (try 2/3)
[12226.216120] wlan0: direct probe to <MAC address removed> (try 3/3)
[12226.420278] wlan0: authentication with <MAC address removed> timed out
[12229.560645] wlan0: authenticate with <MAC address removed>
[12229.563119] wlan0: direct probe to <MAC address removed> (try 1/3)
[12229.764326] wlan0: direct probe to <MAC address removed> (try 2/3)
[12229.968310] wlan0: direct probe to <MAC address removed> (try 3/3)
[12230.172310] wlan0: authentication with <MAC address removed> timed out
[12279.080074] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[12282.752962] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[12282.756028] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[12282.792557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12289.002633] wlan0: authenticate with <MAC address removed>
[12289.004400] wlan0: direct probe to <MAC address removed> (try 1/3)
[12289.208296] wlan0: direct probe to <MAC address removed> (try 2/3)
[12289.412104] wlan0: direct probe to <MAC address removed> (try 3/3)
[12289.616272] wlan0: authentication with <MAC address removed> timed out
[12300.882574] wlan0: authenticate with <MAC address removed>
[12300.883879] wlan0: direct probe to <MAC address removed> (try 1/3)
[12301.084203] wlan0: direct probe to <MAC address removed> (try 2/3)
[12301.288299] wlan0: direct probe to <MAC address removed> (try 3/3)
[12301.492271] wlan0: authentication with <MAC address removed> timed out
[12304.696054] wlan0: authenticate with <MAC address removed>
[12304.697207] wlan0: direct probe to <MAC address removed> (try 1/3)
[12304.900097] wlan0: direct probe to <MAC address removed> (try 2/3)
[12305.104076] wlan0: direct probe to <MAC address removed> (try 3/3)
[12305.308292] wlan0: authentication with <MAC address removed> timed out
[12308.561598] wlan0: authenticate with <MAC address removed>
[12308.563334] wlan0: direct probe to <MAC address removed> (try 1/3)
[12308.764301] wlan0: direct probe to <MAC address removed> (try 2/3)
[12308.968253] wlan0: direct probe to <MAC address removed> (try 3/3)
[12309.172321] wlan0: authentication with <MAC address removed> timed out
[12317.191869] wlan0: authenticate with <MAC address removed>
[12317.194671] wlan0: direct probe to <MAC address removed> (try 1/3)
[12317.396043] wlan0: direct probe to <MAC address removed> (try 2/3)
[12317.600282] wlan0: direct probe to <MAC address removed> (try 3/3)
[12317.804126] wlan0: authentication with <MAC address removed> timed out
[12321.054639] wlan0: authenticate with <MAC address removed>
[12321.055804] wlan0: direct probe to <MAC address removed> (try 1/3)
[12321.256302] wlan0: direct probe to <MAC address removed> (try 2/3)
[12321.460297] wlan0: direct probe to <MAC address removed> (try 3/3)
[12321.664098] wlan0: authentication with <MAC address removed> timed out
[12324.815506] wlan0: authenticate with <MAC address removed>
[12324.818722] wlan0: direct probe to <MAC address removed> (try 1/3)
[12325.020073] wlan0: direct probe to <MAC address removed> (try 2/3)
[12325.224071] wlan0: direct probe to <MAC address removed> (try 3/3)
[12325.428083] wlan0: authentication with <MAC address removed> timed out
[12328.601883] wlan0: authenticate with <MAC address removed>
[12328.603220] wlan0: direct probe to <MAC address removed> (try 1/3)
[12328.804297] wlan0: direct probe to <MAC address removed> (try 2/3)
[12329.008327] wlan0: direct probe to <MAC address removed> (try 3/3)
[12329.212326] wlan0: authentication with <MAC address removed> timed out
[12332.420997] wlan0: authenticate with <MAC address removed>
[12332.423823] wlan0: direct probe to <MAC address removed> (try 1/3)
[12332.624246] wlan0: direct probe to <MAC address removed> (try 2/3)
[12332.828240] wlan0: direct probe to <MAC address removed> (try 3/3)
[12333.032299] wlan0: authentication with <MAC address removed> timed out
[12342.042726] wlan0: authenticate with <MAC address removed>
[12342.043611] wlan0: direct probe to <MAC address removed> (try 1/3)
[12342.244113] wlan0: direct probe to <MAC address removed> (try 2/3)
[12342.448091] wlan0: direct probe to <MAC address removed> (try 3/3)
[12342.652075] wlan0: authentication with <MAC address removed> timed out
[12353.997918] wlan0: authenticate with <MAC address removed>
[12354.001481] wlan0: direct probe to <MAC address removed> (try 1/3)
[12354.204331] wlan0: direct probe to <MAC address removed> (try 2/3)
[12354.408063] wlan0: direct probe to <MAC address removed> (try 3/3)
[12354.612105] wlan0: authentication with <MAC address removed> timed out
[12357.786693] wlan0: authenticate with <MAC address removed>
[12357.790833] wlan0: direct probe to <MAC address removed> (try 1/3)
[12357.992288] wlan0: direct probe to <MAC address removed> (try 2/3)
[12358.196288] wlan0: direct probe to <MAC address removed> (try 3/3)
[12358.400323] wlan0: authentication with <MAC address removed> timed out
[12389.403361] wlan0: authenticate with <MAC address removed>
[12389.406557] wlan0: direct probe to <MAC address removed> (try 1/3)
[12389.608073] wlan0: direct probe to <MAC address removed> (try 2/3)
[12389.812307] wlan0: direct probe to <MAC address removed> (try 3/3)
[12390.016037] wlan0: authentication with <MAC address removed> timed out
[12400.729102] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[12404.551373] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[12404.555285] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[12404.585429] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12410.748763] wlan0: authenticate with <MAC address removed>
[12410.752174] wlan0: direct probe to <MAC address removed> (try 1/3)
[12410.956318] wlan0: direct probe to <MAC address removed> (try 2/3)
[12411.160146] wlan0: direct probe to <MAC address removed> (try 3/3)
[12411.364121] wlan0: authentication with <MAC address removed> timed out
[12414.641414] wlan0: authenticate with <MAC address removed>
[12414.643689] wlan0: direct probe to <MAC address removed> (try 1/3)
[12414.844077] wlan0: direct probe to <MAC address removed> (try 2/3)
[12415.048110] wlan0: direct probe to <MAC address removed> (try 3/3)
[12415.252124] wlan0: authentication with <MAC address removed> timed out
[12418.362408] wlan0: authenticate with <MAC address removed>
[12418.365361] wlan0: direct probe to <MAC address removed> (try 1/3)
[12418.568303] wlan0: direct probe to <MAC address removed> (try 2/3)
[12418.772057] wlan0: direct probe to <MAC address removed> (try 3/3)
[12418.976052] wlan0: authentication with <MAC address removed> timed out
[12422.251290] wlan0: authenticate with <MAC address removed>
[12422.252531] wlan0: direct probe to <MAC address removed> (try 1/3)
[12422.456092] wlan0: direct probe to <MAC address removed> (try 2/3)
[12422.660067] wlan0: direct probe to <MAC address removed> (try 3/3)
[12422.864053] wlan0: authentication with <MAC address removed> timed out
[12426.000410] wlan0: authenticate with <MAC address removed>
[12426.004401] wlan0: direct probe to <MAC address removed> (try 1/3)
[12426.208078] wlan0: direct probe to <MAC address removed> (try 2/3)
[12426.412061] wlan0: direct probe to <MAC address removed> (try 3/3)
[12426.616072] wlan0: authentication with <MAC address removed> timed out
[12429.781656] wlan0: authenticate with <MAC address removed>
[12429.783037] wlan0: direct probe to <MAC address removed> (try 1/3)
[12429.984278] wlan0: direct probe to <MAC address removed> (try 2/3)
[12430.188043] wlan0: direct probe to <MAC address removed> (try 3/3)
[12430.392291] wlan0: authentication with <MAC address removed> timed out
[12439.102665] wlan0: authenticate with <MAC address removed>
[12439.105655] wlan0: direct probe to <MAC address removed> (try 1/3)
[12439.308212] wlan0: direct probe to <MAC address removed> (try 2/3)
[12439.512077] wlan0: direct probe to <MAC address removed> (try 3/3)
[12439.716307] wlan0: authentication with <MAC address removed> timed out
[12442.888723] wlan0: authenticate with <MAC address removed>
[12442.889844] wlan0: direct probe to <MAC address removed> (try 1/3)
[12443.092288] wlan0: direct probe to <MAC address removed> (try 2/3)
[12443.296269] wlan0: direct probe to <MAC address removed> (try 3/3)
[12443.500288] wlan0: authentication with <MAC address removed> timed out
[12446.676597] wlan0: authenticate with <MAC address removed>
[12446.686892] wlan0: direct probe to <MAC address removed> (try 1/3)
[12446.888129] wlan0: direct probe to <MAC address removed> (try 2/3)
[12447.092086] wlan0: direct probe to <MAC address removed> (try 3/3)
[12447.296067] wlan0: authentication with <MAC address removed> timed out
[12450.463592] wlan0: authenticate with <MAC address removed>
[12450.466545] wlan0: direct probe to <MAC address removed> (try 1/3)
[12450.668125] wlan0: direct probe to <MAC address removed> (try 2/3)
[12450.872053] wlan0: direct probe to <MAC address removed> (try 3/3)
[12451.076092] wlan0: authentication with <MAC address removed> timed out
[12454.249970] wlan0: authenticate with <MAC address removed>
[12454.255779] wlan0: direct probe to <MAC address removed> (try 1/3)
[12454.456101] wlan0: direct probe to <MAC address removed> (try 2/3)
[12454.660066] wlan0: direct probe to <MAC address removed> (try 3/3)
[12454.864292] wlan0: authentication with <MAC address removed> timed out
[12464.070555] wlan0: authenticate with <MAC address removed>
[12464.073611] wlan0: direct probe to <MAC address removed> (try 1/3)
[12464.276227] wlan0: direct probe to <MAC address removed> (try 2/3)
[12464.480310] wlan0: direct probe to <MAC address removed> (try 3/3)
[12464.684070] wlan0: authentication with <MAC address removed> timed out
[12467.857023] wlan0: authenticate with <MAC address removed>
[12467.865881] wlan0: direct probe to <MAC address removed> (try 1/3)
[12468.068077] wlan0: direct probe to <MAC address removed> (try 2/3)
[12468.272278] wlan0: direct probe to <MAC address removed> (try 3/3)
[12468.476322] wlan0: authentication with <MAC address removed> timed out
[12471.649802] wlan0: authenticate with <MAC address removed>
[12471.653475] wlan0: direct probe to <MAC address removed> (try 1/3)
[12471.856074] wlan0: direct probe to <MAC address removed> (try 2/3)
[12472.060087] wlan0: direct probe to <MAC address removed> (try 3/3)
[12472.264089] wlan0: authentication with <MAC address removed> timed out
[12475.431017] wlan0: authenticate with <MAC address removed>
[12475.433521] wlan0: direct probe to <MAC address removed> (try 1/3)
[12475.636308] wlan0: direct probe to <MAC address removed> (try 2/3)
[12475.840096] wlan0: direct probe to <MAC address removed> (try 3/3)
[12476.044047] wlan0: authentication with <MAC address removed> timed out
[12479.223189] wlan0: authenticate with <MAC address removed>
[12479.227046] wlan0: direct probe to <MAC address removed> (try 1/3)
[12479.428091] wlan0: direct probe to <MAC address removed> (try 2/3)
[12479.632068] wlan0: direct probe to <MAC address removed> (try 3/3)
[12479.836068] wlan0: authentication with <MAC address removed> timed out
[12483.149305] wlan0: authenticate with <MAC address removed>
[12483.151431] wlan0: direct probe to <MAC address removed> (try 1/3)
[12483.352095] wlan0: direct probe to <MAC address removed> (try 2/3)
[12483.556053] wlan0: direct probe to <MAC address removed> (try 3/3)
[12483.760299] wlan0: authentication with <MAC address removed> timed out
[12486.900064] wlan0: authenticate with <MAC address removed>
[12486.901256] wlan0: direct probe to <MAC address removed> (try 1/3)
[12487.104314] wlan0: direct probe to <MAC address removed> (try 2/3)
[12487.308299] wlan0: direct probe to <MAC address removed> (try 3/3)
[12487.512319] wlan0: authentication with <MAC address removed> timed out
[12495.086712] wlan0: authenticate with <MAC address removed>
[12495.087808] wlan0: direct probe to <MAC address removed> (try 1/3)
[12495.288217] wlan0: direct probe to <MAC address removed> (try 2/3)
[12495.492046] wlan0: direct probe to <MAC address removed> (try 3/3)
[12495.696259] wlan0: authentication with <MAC address removed> timed out
[12498.874415] wlan0: authenticate with <MAC address removed>
[12498.876933] wlan0: direct probe to <MAC address removed> (try 1/3)
[12499.080158] wlan0: direct probe to <MAC address removed> (try 2/3)
[12499.284070] wlan0: direct probe to <MAC address removed> (try 3/3)
[12499.488053] wlan0: authentication with <MAC address removed> timed out
[12502.682566] wlan0: authenticate with <MAC address removed>
[12502.683705] wlan0: direct probe to <MAC address removed> (try 1/3)
[12502.884300] wlan0: direct probe to <MAC address removed> (try 2/3)
[12503.088057] wlan0: direct probe to <MAC address removed> (try 3/3)
[12503.292239] wlan0: authentication with <MAC address removed> timed out
[12506.447678] wlan0: authenticate with <MAC address removed>
[12506.448701] wlan0: direct probe to <MAC address removed> (try 1/3)
[12506.652051] wlan0: direct probe to <MAC address removed> (try 2/3)
[12506.856065] wlan0: direct probe to <MAC address removed> (try 3/3)
[12507.060216] wlan0: authentication with <MAC address removed> timed out
[12510.234681] wlan0: authenticate with <MAC address removed>
[12510.235769] wlan0: direct probe to <MAC address removed> (try 1/3)
[12510.436051] wlan0: direct probe to <MAC address removed> (try 2/3)
[12510.640046] wlan0: direct probe to <MAC address removed> (try 3/3)
[12510.844090] wlan0: authentication with <MAC address removed> timed out
[12514.022938] wlan0: authenticate with <MAC address removed>
[12514.024331] wlan0: direct probe to <MAC address removed> (try 1/3)
[12514.228111] wlan0: direct probe to <MAC address removed> (try 2/3)
[12514.432300] wlan0: direct probe to <MAC address removed> (try 3/3)
[12514.636067] wlan0: authentication with <MAC address removed> timed out
[12820.033408] wlan0: authenticate with <MAC address removed>
[12820.034829] wlan0: direct probe to <MAC address removed> (try 1/3)
[12820.236040] wlan0: direct probe to <MAC address removed> (try 2/3)
[12820.440032] wlan0: direct probe to <MAC address removed> (try 3/3)
[12820.644183] wlan0: authentication with <MAC address removed> timed out
[12823.734940] wlan0: authenticate with <MAC address removed>
[12823.736132] wlan0: direct probe to <MAC address removed> (try 1/3)
[12823.940048] wlan0: direct probe to <MAC address removed> (try 2/3)
[12824.144283] wlan0: direct probe to <MAC address removed> (try 3/3)
[12824.348086] wlan0: authentication with <MAC address removed> timed out
[12827.513130] wlan0: authenticate with <MAC address removed>
[12827.514081] wlan0: direct probe to <MAC address removed> (try 1/3)
[12827.716095] wlan0: direct probe to <MAC address removed> (try 2/3)
[12827.920114] wlan0: direct probe to <MAC address removed> (try 3/3)
[12828.124198] wlan0: authentication with <MAC address removed> timed out
[12839.393939] wlan0: authenticate with <MAC address removed>
[12839.395289] wlan0: direct probe to <MAC address removed> (try 1/3)
[12839.596117] wlan0: direct probe to <MAC address removed> (try 2/3)
[12839.800132] wlan0: direct probe to <MAC address removed> (try 3/3)
[12840.004232] wlan0: authentication with <MAC address removed> timed out
[12848.094669] wlan0: authenticate with <MAC address removed>
[12848.099828] wlan0: direct probe to <MAC address removed> (try 1/3)
[12848.300223] wlan0: direct probe to <MAC address removed> (try 2/3)
[12848.504091] wlan0: direct probe to <MAC address removed> (try 3/3)
[12848.708172] wlan0: authentication with <MAC address removed> timed out
[12851.880889] wlan0: authenticate with <MAC address removed>
[12851.884641] wlan0: direct probe to <MAC address removed> (try 1/3)
[12852.088064] wlan0: direct probe to <MAC address removed> (try 2/3)
[12852.292090] wlan0: direct probe to <MAC address removed> (try 3/3)
[12852.496231] wlan0: authentication with <MAC address removed> timed out
[12863.752722] wlan0: authenticate with <MAC address removed>
[12863.753672] wlan0: direct probe to <MAC address removed> (try 1/3)
[12863.956214] wlan0: direct probe to <MAC address removed> (try 2/3)
[12864.160085] wlan0: direct probe to <MAC address removed> (try 3/3)
[12864.364117] wlan0: authentication with <MAC address removed> timed out
[12885.145466] wlan0: authenticate with <MAC address removed>
[12885.146715] wlan0: direct probe to <MAC address removed> (try 1/3)
[12885.348111] wlan0: direct probe to <MAC address removed> (try 2/3)
[12885.552030] wlan0: direct probe to <MAC address removed> (try 3/3)
[12885.756064] wlan0: authentication with <MAC address removed> timed out
[12888.931343] wlan0: authenticate with <MAC address removed>
[12888.937259] wlan0: direct probe to <MAC address removed> (try 1/3)
[12889.140083] wlan0: direct probe to <MAC address removed> (try 2/3)
[12889.344064] wlan0: direct probe to <MAC address removed> (try 3/3)
[12889.548046] wlan0: authentication with <MAC address removed> timed out
[12892.719495] wlan0: authenticate with <MAC address removed>
[12892.720775] wlan0: direct probe to <MAC address removed> (try 1/3)
[12892.924306] wlan0: direct probe to <MAC address removed> (try 2/3)
[12893.128053] wlan0: direct probe to <MAC address removed> (try 3/3)
[12893.332307] wlan0: authentication with <MAC address removed> timed out
[12896.505722] wlan0: authenticate with <MAC address removed>
[12896.507110] wlan0: direct probe to <MAC address removed> (try 1/3)
[12896.708261] wlan0: direct probe to <MAC address removed> (try 2/3)
[12896.912047] wlan0: direct probe to <MAC address removed> (try 3/3)
[12897.116092] wlan0: authentication with <MAC address removed> timed out
[12904.064849] wlan0: authenticate with <MAC address removed>
[12904.066942] wlan0: direct probe to <MAC address removed> (try 1/3)
[12904.268051] wlan0: direct probe to <MAC address removed> (try 2/3)
[12904.472242] wlan0: direct probe to <MAC address removed> (try 3/3)
[12904.676053] wlan0: authentication with <MAC address removed> timed out
[12907.867076] wlan0: authenticate with <MAC address removed>
[12907.884315] wlan0: direct probe to <MAC address removed> (try 1/3)
[12908.088095] wlan0: direct probe to <MAC address removed> (try 2/3)
[12908.292225] wlan0: direct probe to <MAC address removed> (try 3/3)
[12908.496049] wlan0: authentication with <MAC address removed> timed out
[12911.654081] wlan0: authenticate with <MAC address removed>
[12911.661521] wlan0: direct probe to <MAC address removed> (try 1/3)
[12911.864322] wlan0: direct probe to <MAC address removed> (try 2/3)
[12912.068092] wlan0: direct probe to <MAC address removed> (try 3/3)
[12912.272058] wlan0: authentication with <MAC address removed> timed out
[12923.526243] wlan0: authenticate with <MAC address removed>
[12923.527375] wlan0: direct probe to <MAC address removed> (try 1/3)
[12923.728172] wlan0: direct probe to <MAC address removed> (try 2/3)
[12923.932060] wlan0: direct probe to <MAC address removed> (try 3/3)
[12924.136045] wlan0: authentication with <MAC address removed> timed out
[13229.064157] wlan0: authenticate with <MAC address removed>
[13229.069424] wlan0: direct probe to <MAC address removed> (try 1/3)
[13229.275137] wlan0: direct probe to <MAC address removed> (try 2/3)
[13229.476089] wlan0: direct probe to <MAC address removed> (try 3/3)
[13229.680080] wlan0: authentication with <MAC address removed> timed out
[13232.851060] wlan0: authenticate with <MAC address removed>
[13232.856813] wlan0: direct probe to <MAC address removed> (try 1/3)
[13233.060107] wlan0: direct probe to <MAC address removed> (try 2/3)
[13233.264074] wlan0: direct probe to <MAC address removed> (try 3/3)
[13233.468194] wlan0: authentication with <MAC address removed> timed out
[13236.641959] wlan0: authenticate with <MAC address removed>
[13236.645966] wlan0: direct probe to <MAC address removed> (try 1/3)
[13236.848030] wlan0: direct probe to <MAC address removed> (try 2/3)
[13237.052067] wlan0: direct probe to <MAC address removed> (try 3/3)
[13237.256085] wlan0: authentication with <MAC address removed> timed out
[13248.507345] wlan0: authenticate with <MAC address removed>
[13248.510378] wlan0: direct probe to <MAC address removed> (try 1/3)
[13248.712089] wlan0: direct probe to <MAC address removed> (try 2/3)
[13248.916050] wlan0: direct probe to <MAC address removed> (try 3/3)
[13249.120258] wlan0: authentication with <MAC address removed> timed out
[13265.004912] wlan0: authenticate with <MAC address removed>
[13265.011133] wlan0: direct probe to <MAC address removed> (try 1/3)
[13265.212460] wlan0: direct probe to <MAC address removed> (try 2/3)
[13265.420274] wlan0: direct probe to <MAC address removed> (try 3/3)
[13265.624044] wlan0: authentication with <MAC address removed> timed out
[13268.793983] wlan0: authenticate with <MAC address removed>
[13268.797353] wlan0: direct probe to <MAC address removed> (try 1/3)
[13269.000067] wlan0: direct probe to <MAC address removed> (try 2/3)
[13269.204255] wlan0: direct probe to <MAC address removed> (try 3/3)
[13269.408309] wlan0: authentication with <MAC address removed> timed out
[13272.584431] wlan0: authenticate with <MAC address removed>
[13272.588879] wlan0: direct probe to <MAC address removed> (try 1/3)
[13272.792220] wlan0: direct probe to <MAC address removed> (try 2/3)
[13272.996290] wlan0: direct probe to <MAC address removed> (try 3/3)
[13273.200054] wlan0: authentication with <MAC address removed> timed out
[13276.373620] wlan0: authenticate with <MAC address removed>
[13276.378245] wlan0: direct probe to <MAC address removed> (try 1/3)
[13276.580041] wlan0: direct probe to <MAC address removed> (try 2/3)
[13276.784146] wlan0: direct probe to <MAC address removed> (try 3/3)
[13276.988083] wlan0: authentication with <MAC address removed> timed out
[13285.076909] wlan0: authenticate with <MAC address removed>
[13285.082920] wlan0: direct probe to <MAC address removed> (try 1/3)
[13285.284241] wlan0: direct probe to <MAC address removed> (try 2/3)
[13285.488146] wlan0: direct probe to <MAC address removed> (try 3/3)
[13285.692067] wlan0: authentication with <MAC address removed> timed out
[13288.864967] wlan0: authenticate with <MAC address removed>
[13288.867737] wlan0: direct probe to <MAC address removed> (try 1/3)
[13289.068071] wlan0: direct probe to <MAC address removed> (try 2/3)
[13289.272117] wlan0: direct probe to <MAC address removed> (try 3/3)
[13289.480935] wlan0: authentication with <MAC address removed> timed out
[13292.652941] wlan0: authenticate with <MAC address removed>
[13292.656312] wlan0: direct probe to <MAC address removed> (try 1/3)
[13292.860352] wlan0: direct probe to <MAC address removed> (try 2/3)
[13293.064165] wlan0: direct probe to <MAC address removed> (try 3/3)
[13293.268053] wlan0: authentication with <MAC address removed> timed out
[13296.650807] wlan0: authenticate with <MAC address removed>
[13296.653826] wlan0: direct probe to <MAC address removed> (try 1/3)
[13296.856089] wlan0: direct probe to <MAC address removed> (try 2/3)
[13297.060054] wlan0: direct probe to <MAC address removed> (try 3/3)
[13297.264051] wlan0: authentication with <MAC address removed> timed out
[13300.436834] wlan0: authenticate with <MAC address removed>
[13300.439049] wlan0: direct probe to <MAC address removed> (try 1/3)
[13300.640052] wlan0: direct probe to <MAC address removed> (try 2/3)
[13300.844079] wlan0: direct probe to <MAC address removed> (try 3/3)
[13301.048062] wlan0: authentication with <MAC address removed> timed out
[13304.285150] wlan0: authenticate with <MAC address removed>
[13304.286375] wlan0: direct probe to <MAC address removed> (try 1/3)
[13304.488233] wlan0: direct probe to <MAC address removed> (try 2/3)
[13304.692288] wlan0: direct probe to <MAC address removed> (try 3/3)
[13304.896298] wlan0: authentication with <MAC address removed> timed out
[13313.031974] wlan0: authenticate with <MAC address removed>
[13313.034515] wlan0: direct probe to <MAC address removed> (try 1/3)
[13313.236310] wlan0: direct probe to <MAC address removed> (try 2/3)
[13313.440314] wlan0: direct probe to <MAC address removed> (try 3/3)
[13313.644231] wlan0: authentication with <MAC address removed> timed out
[13316.820609] wlan0: authenticate with <MAC address removed>
[13316.823024] wlan0: direct probe to <MAC address removed> (try 1/3)
[13317.024267] wlan0: direct probe to <MAC address removed> (try 2/3)
[13317.228132] wlan0: direct probe to <MAC address removed> (try 3/3)
[13317.432264] wlan0: authentication with <MAC address removed> timed out
[13320.598629] wlan0: authenticate with <MAC address removed>
[13320.604813] wlan0: direct probe to <MAC address removed> (try 1/3)
[13320.808100] wlan0: direct probe to <MAC address removed> (try 2/3)
[13321.012038] wlan0: direct probe to <MAC address removed> (try 3/3)
[13321.216049] wlan0: authentication with <MAC address removed> timed out
[13324.400714] wlan0: authenticate with <MAC address removed>
[13324.405112] wlan0: direct probe to <MAC address removed> (try 1/3)
[13324.608097] wlan0: direct probe to <MAC address removed> (try 2/3)
[13324.812060] wlan0: direct probe to <MAC address removed> (try 3/3)
[13325.016058] wlan0: authentication with <MAC address removed> timed out
[13328.187659] wlan0: authenticate with <MAC address removed>
[13328.193187] wlan0: direct probe to <MAC address removed> (try 1/3)
[13328.396267] wlan0: direct probe to <MAC address removed> (try 2/3)
[13328.600076] wlan0: direct probe to <MAC address removed> (try 3/3)
[13328.804230] wlan0: authentication with <MAC address removed> timed out
[13331.975252] wlan0: authenticate with <MAC address removed>
[13331.978210] wlan0: direct probe to <MAC address removed> (try 1/3)
[13332.180077] wlan0: direct probe to <MAC address removed> (try 2/3)
[13332.384094] wlan0: direct probe to <MAC address removed> (try 3/3)
[13332.588243] wlan0: authentication with <MAC address removed> timed out
[13404.477030] wlan0: authenticate with <MAC address removed>
[13404.479081] wlan0: direct probe to <MAC address removed> (try 1/3)
[13404.680309] wlan0: direct probe to <MAC address removed> (try 2/3)
[13404.884060] wlan0: direct probe to <MAC address removed> (try 3/3)
[13405.088292] wlan0: authentication with <MAC address removed> timed out
[13416.355756] wlan0: authenticate with <MAC address removed>
[13416.358124] wlan0: direct probe to <MAC address removed> (try 1/3)
[13416.560075] wlan0: direct probe to <MAC address removed> (try 2/3)
[13416.764119] wlan0: direct probe to <MAC address removed> (try 3/3)
[13416.968082] wlan0: authentication with <MAC address removed> timed out
[13738.102074] wlan0: authenticate with <MAC address removed>
[13738.103334] wlan0: direct probe to <MAC address removed> (try 1/3)
[13738.304280] wlan0: direct probe to <MAC address removed> (try 2/3)
[13738.508210] wlan0: direct probe to <MAC address removed> (try 3/3)
[13738.712291] wlan0: authentication with <MAC address removed> timed out
[13741.948157] wlan0: authenticate with <MAC address removed>
[13741.949310] wlan0: direct probe to <MAC address removed> (try 1/3)
[13742.152326] wlan0: direct probe to <MAC address removed> (try 2/3)
[13742.356329] wlan0: direct probe to <MAC address removed> (try 3/3)
[13742.560322] wlan0: authentication with <MAC address removed> timed out
[13750.119838] wlan0: authenticate with <MAC address removed>
[13750.132573] wlan0: direct probe to <MAC address removed> (try 1/3)
[13750.336332] wlan0: direct probe to <MAC address removed> (try 2/3)
[13750.540332] wlan0: direct probe to <MAC address removed> (try 3/3)
[13750.744328] wlan0: authentication with <MAC address removed> timed out
[13762.018823] wlan0: authenticate with <MAC address removed>
[13762.020076] wlan0: direct probe to <MAC address removed> (try 1/3)
[13762.224249] wlan0: direct probe to <MAC address removed> (try 2/3)
[13762.428259] wlan0: direct probe to <MAC address removed> (try 3/3)
[13762.632243] wlan0: authentication with <MAC address removed> timed out
[13765.851905] wlan0: authenticate with <MAC address removed>
[13765.853354] wlan0: direct probe to <MAC address removed> (try 1/3)
[13766.056301] wlan0: direct probe to <MAC address removed> (try 2/3)
[13766.260279] wlan0: direct probe to <MAC address removed> (try 3/3)
[13766.464317] wlan0: authentication with <MAC address removed> timed out
[13775.066228] wlan0: authenticate with <MAC address removed>
[13775.069731] wlan0: direct probe to <MAC address removed> (try 1/3)
[13775.272240] wlan0: direct probe to <MAC address removed> (try 2/3)
[13775.476069] wlan0: direct probe to <MAC address removed> (try 3/3)
[13775.680044] wlan0: authentication with <MAC address removed> timed out
[13778.857136] wlan0: authenticate with <MAC address removed>
[13778.858838] wlan0: direct probe to <MAC address removed> (try 1/3)
[13779.060304] wlan0: direct probe to <MAC address removed> (try 2/3)
[13779.264309] wlan0: direct probe to <MAC address removed> (try 3/3)
[13779.468497] wlan0: authentication with <MAC address removed> timed out
[13782.750765] wlan0: authenticate with <MAC address removed>
[13782.756179] wlan0: direct probe to <MAC address removed> (try 1/3)
[13782.960074] wlan0: direct probe to <MAC address removed> (try 2/3)
[13783.164046] wlan0: direct probe to <MAC address removed> (try 3/3)
[13783.368041] wlan0: authentication with <MAC address removed> timed out
[13794.626761] wlan0: authenticate with <MAC address removed>
[13794.628615] wlan0: direct probe to <MAC address removed> (try 1/3)
[13794.832049] wlan0: direct probe to <MAC address removed> (try 2/3)
[13795.036079] wlan0: direct probe to <MAC address removed> (try 3/3)
[13795.240057] wlan0: authentication with <MAC address removed> timed out
[13798.466686] wlan0: authenticate with <MAC address removed>
[13798.470067] wlan0: direct probe to <MAC address removed> (try 1/3)
[13798.672068] wlan0: direct probe to <MAC address removed> (try 2/3)
[13798.876191] wlan0: direct probe to <MAC address removed> (try 3/3)
[13799.080057] wlan0: authentication with <MAC address removed> timed out
[13806.080912] wlan0: authenticate with <MAC address removed>
[13806.083479] wlan0: direct probe to <MAC address removed> (try 1/3)
[13806.284038] wlan0: direct probe to <MAC address removed> (try 2/3)
[13806.488064] wlan0: direct probe to <MAC address removed> (try 3/3)
[13806.692035] wlan0: authentication with <MAC address removed> timed out
[13826.121999] wlan0: authenticate with <MAC address removed>
[13826.134029] wlan0: direct probe to <MAC address removed> (try 1/3)
[13826.336058] wlan0: direct probe to <MAC address removed> (try 2/3)
[13826.540071] wlan0: direct probe to <MAC address removed> (try 3/3)
[13826.744069] wlan0: authentication with <MAC address removed> timed out
[14131.073760] wlan0: authenticate with <MAC address removed>
[14131.075654] wlan0: direct probe to <MAC address removed> (try 1/3)
[14131.276056] wlan0: direct probe to <MAC address removed> (try 2/3)
[14131.480230] wlan0: direct probe to <MAC address removed> (try 3/3)
[14131.684066] wlan0: authentication with <MAC address removed> timed out
[14134.965162] wlan0: authenticate with <MAC address removed>
[14134.969772] wlan0: direct probe to <MAC address removed> (try 1/3)
[14135.172068] wlan0: direct probe to <MAC address removed> (try 2/3)
[14135.376107] wlan0: direct probe to <MAC address removed> (try 3/3)
[14135.580055] wlan0: authentication with <MAC address removed> timed out
[14138.753394] wlan0: authenticate with <MAC address removed>
[14138.758329] wlan0: direct probe to <MAC address removed> (try 1/3)
[14138.960061] wlan0: direct probe to <MAC address removed> (try 2/3)
[14139.164092] wlan0: direct probe to <MAC address removed> (try 3/3)
[14139.368074] wlan0: authentication with <MAC address removed> timed out
[14142.508957] wlan0: authenticate with <MAC address removed>
[14142.510235] wlan0: direct probe to <MAC address removed> (try 1/3)
[14142.712093] wlan0: direct probe to <MAC address removed> (try 2/3)
[14142.916047] wlan0: direct probe to <MAC address removed> (try 3/3)
[14143.120035] wlan0: authentication with <MAC address removed> timed out
[14146.275331] wlan0: authenticate with <MAC address removed>
[14146.276680] wlan0: direct probe to <MAC address removed> (try 1/3)
[14146.480059] wlan0: direct probe to <MAC address removed> (try 2/3)
[14146.684056] wlan0: direct probe to <MAC address removed> (try 3/3)
[14146.888079] wlan0: authentication with <MAC address removed> timed out
[14159.074767] wlan0: authenticate with <MAC address removed>
[14159.076198] wlan0: direct probe to <MAC address removed> (try 1/3)
[14159.280024] wlan0: direct probe to <MAC address removed> (try 2/3)
[14159.484079] wlan0: direct probe to <MAC address removed> (try 3/3)
[14159.688054] wlan0: authentication with <MAC address removed> timed out
[14170.988533] wlan0: authenticate with <MAC address removed>
[14170.989919] wlan0: direct probe to <MAC address removed> (try 1/3)
[14171.192066] wlan0: direct probe to <MAC address removed> (try 2/3)
[14171.396099] wlan0: direct probe to <MAC address removed> (try 3/3)
[14171.600072] wlan0: authentication with <MAC address removed> timed out
[14187.031810] wlan0: authenticate with <MAC address removed>
[14187.033330] wlan0: direct probe to <MAC address removed> (try 1/3)
[14187.236090] wlan0: direct probe to <MAC address removed> (try 2/3)
[14187.440031] wlan0: direct probe to <MAC address removed> (try 3/3)
[14187.644067] wlan0: authentication with <MAC address removed> timed out
[14198.965992] wlan0: authenticate with <MAC address removed>
[14198.970210] wlan0: direct probe to <MAC address removed> (try 1/3)
[14199.172096] wlan0: direct probe to <MAC address removed> (try 2/3)
[14199.376103] wlan0: direct probe to <MAC address removed> (try 3/3)
[14199.580057] wlan0: authentication with <MAC address removed> timed out
[14202.699206] wlan0: authenticate with <MAC address removed>
[14202.700733] wlan0: direct probe to <MAC address removed> (try 1/3)
[14202.904309] wlan0: direct probe to <MAC address removed> (try 2/3)
[14203.108110] wlan0: direct probe to <MAC address removed> (try 3/3)
[14203.312087] wlan0: authentication with <MAC address removed> timed out
[14216.094812] wlan0: authenticate with <MAC address removed>
[14216.095830] wlan0: direct probe to <MAC address removed> (try 1/3)
[14216.296109] wlan0: direct probe to <MAC address removed> (try 2/3)
[14216.500137] wlan0: direct probe to <MAC address removed> (try 3/3)
[14216.704065] wlan0: authentication with <MAC address removed> timed out
[14219.902645] wlan0: authenticate with <MAC address removed>
[14219.906767] wlan0: direct probe to <MAC address removed> (try 1/3)
[14220.108045] wlan0: direct probe to <MAC address removed> (try 2/3)
[14220.312034] wlan0: direct probe to <MAC address removed> (try 3/3)
[14220.516268] wlan0: authentication with <MAC address removed> timed out
[14231.678703] wlan0: authenticate with <MAC address removed>
[14231.687080] wlan0: direct probe to <MAC address removed> (try 1/3)
[14231.888052] wlan0: direct probe to <MAC address removed> (try 2/3)
[14232.092280] wlan0: direct probe to <MAC address removed> (try 3/3)
[14232.296087] wlan0: authentication with <MAC address removed> timed out
[14520.862347] wlan0: authenticate with <MAC address removed>
[14520.863532] wlan0: direct probe to <MAC address removed> (try 1/3)
[14521.064105] wlan0: direct probe to <MAC address removed> (try 2/3)
[14521.268028] wlan0: direct probe to <MAC address removed> (try 3/3)
[14521.472628] wlan0: authentication with <MAC address removed> timed out
[14524.650880] wlan0: authenticate with <MAC address removed>
[14524.652363] wlan0: direct probe to <MAC address removed> (try 1/3)
[14524.856064] wlan0: direct probe to <MAC address removed> (try 2/3)
[14525.060065] wlan0: direct probe to <MAC address removed> (try 3/3)
[14525.264052] wlan0: authentication with <MAC address removed> timed out
[14536.528851] wlan0: authenticate with <MAC address removed>
[14536.530145] wlan0: direct probe to <MAC address removed> (try 1/3)
[14536.732074] wlan0: direct probe to <MAC address removed> (try 2/3)
[14536.936063] wlan0: direct probe to <MAC address removed> (try 3/3)
[14537.140114] wlan0: authentication with <MAC address removed> timed out
[14562.915337] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[14562.915487] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[14562.916598] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[14562.935514] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[14562.935519] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[14562.935521] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[14562.935523] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[14562.935525] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[14562.935643] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14562.958003] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14562.965857] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14562.970420] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14563.068675] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14563.071730] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14563.100938] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14563.101444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14569.297096] wlan0: authenticate with <MAC address removed>
[14569.299649] wlan0: direct probe to <MAC address removed> (try 1/3)
[14569.500061] wlan0: direct probe to <MAC address removed> (try 2/3)
[14569.704066] wlan0: direct probe to <MAC address removed> (try 3/3)
[14569.908074] wlan0: authentication with <MAC address removed> timed out
[14573.086627] wlan0: authenticate with <MAC address removed>
[14573.095742] wlan0: direct probe to <MAC address removed> (try 1/3)
[14573.296092] wlan0: direct probe to <MAC address removed> (try 2/3)
[14573.500044] wlan0: direct probe to <MAC address removed> (try 3/3)
[14573.704091] wlan0: authentication with <MAC address removed> timed out
[14576.865609] wlan0: authenticate with <MAC address removed>
[14576.868836] wlan0: direct probe to <MAC address removed> (try 1/3)
[14577.072072] wlan0: direct probe to <MAC address removed> (try 2/3)
[14577.276043] wlan0: direct probe to <MAC address removed> (try 3/3)
[14577.480028] wlan0: authentication with <MAC address removed> timed out
[14588.734977] wlan0: authenticate with <MAC address removed>
[14588.743861] wlan0: direct probe to <MAC address removed> (try 1/3)
[14588.944095] wlan0: direct probe to <MAC address removed> (try 2/3)
[14589.148067] wlan0: direct probe to <MAC address removed> (try 3/3)
[14589.352304] wlan0: authentication with <MAC address removed> timed out
[14605.119070] wlan0: authenticate with <MAC address removed>
[14605.121485] wlan0: direct probe to <MAC address removed> (try 1/3)
[14605.324449] wlan0: direct probe to <MAC address removed> (try 2/3)
[14605.528224] wlan0: direct probe to <MAC address removed> (try 3/3)
[14605.732067] wlan0: authentication with <MAC address removed> timed out
[14625.189560] wlan0: authenticate with <MAC address removed>
[14625.192287] wlan0: direct probe to <MAC address removed> (try 1/3)
[14625.396427] wlan0: direct probe to <MAC address removed> (try 2/3)
[14625.601107] wlan0: direct probe to <MAC address removed> (try 3/3)
[14625.804278] wlan0: authentication with <MAC address removed> timed out
[14629.103680] wlan0: authenticate with <MAC address removed>
[14629.106287] wlan0: direct probe to <MAC address removed> (try 1/3)
[14629.308043] wlan0: direct probe to <MAC address removed> (try 2/3)
[14629.512095] wlan0: direct probe to <MAC address removed> (try 3/3)
[14629.716055] wlan0: authentication with <MAC address removed> timed out
[14655.438354] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[14655.438506] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[14655.440214] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[14655.461979] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[14655.461984] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[14655.461987] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[14655.461989] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[14655.461991] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[14655.462203] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14655.484527] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14655.491996] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14655.495542] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14655.595410] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14655.598995] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14655.631809] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14655.632994] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14685.168853] wlan0: authenticate with <MAC address removed>
[14685.172423] wlan0: direct probe to <MAC address removed> (try 1/3)
[14685.376096] wlan0: direct probe to <MAC address removed> (try 2/3)
[14685.580343] wlan0: direct probe to <MAC address removed> (try 3/3)
[14685.784079] wlan0: authentication with <MAC address removed> timed out
[14697.126349] wlan0: authenticate with <MAC address removed>
[14697.127931] wlan0: direct probe to <MAC address removed> (try 1/3)
[14697.328092] wlan0: direct probe to <MAC address removed> (try 2/3)
[14697.532122] wlan0: direct probe to <MAC address removed> (try 3/3)
[14697.736091] wlan0: authentication with <MAC address removed> timed out
[14701.031768] wlan0: authenticate with <MAC address removed>
[14701.034251] wlan0: direct probe to <MAC address removed> (try 1/3)
[14701.236042] wlan0: direct probe to <MAC address removed> (try 2/3)
[14701.440034] wlan0: direct probe to <MAC address removed> (try 3/3)
[14701.644047] wlan0: authentication with <MAC address removed> timed out
[14739.338846] wlan0: authenticate with <MAC address removed>
[14739.340117] wlan0: direct probe to <MAC address removed> (try 1/3)
[14739.544051] wlan0: direct probe to <MAC address removed> (try 2/3)
[14739.748075] wlan0: direct probe to <MAC address removed> (try 3/3)
[14739.952095] wlan0: authentication with <MAC address removed> timed out
[14743.175482] wlan0: authenticate with <MAC address removed>
[14743.176413] wlan0: direct probe to <MAC address removed> (try 1/3)
[14743.380039] wlan0: direct probe to <MAC address removed> (try 2/3)
[14743.584037] wlan0: direct probe to <MAC address removed> (try 3/3)
[14743.788069] wlan0: authentication with <MAC address removed> timed out
[14746.966981] wlan0: authenticate with <MAC address removed>
[14746.968279] wlan0: direct probe to <MAC address removed> (try 1/3)
[14747.172055] wlan0: direct probe to <MAC address removed> (try 2/3)
[14747.379254] wlan0: direct probe to <MAC address removed> (try 3/3)
[14747.580044] wlan0: authentication with <MAC address removed> timed out
[14786.953174] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[14786.953699] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[14786.954293] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[14786.973208] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[14786.973213] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[14786.973215] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[14786.973217] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[14786.973220] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[14786.974548] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14786.996867] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14787.005291] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14787.009683] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14787.111383] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14787.114490] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14787.145827] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14787.146865] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14804.412504] wlan0: authenticate with <MAC address removed>
[14804.415371] wlan0: direct probe to <MAC address removed> (try 1/3)
[14804.616045] wlan0: direct probe to <MAC address removed> (try 2/3)
[14804.820080] wlan0: direct probe to <MAC address removed> (try 3/3)
[14805.024093] wlan0: authentication with <MAC address removed> timed out
[14951.312544] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[14951.312677] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[14951.313195] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[14951.336516] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[14951.336522] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[14951.336524] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[14951.336526] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[14951.336528] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[14951.336745] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14951.359007] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14951.367631] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14951.372167] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14951.475312] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[14951.478746] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[14951.509460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14951.509960] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15130.152979] wlan0: authenticate with <MAC address removed>
[15130.158088] wlan0: direct probe to <MAC address removed> (try 1/3)
[15130.360118] wlan0: direct probe to <MAC address removed> (try 2/3)
[15130.567096] wlan0: direct probe to <MAC address removed> (try 3/3)
[15130.768084] wlan0: authentication with <MAC address removed> timed out
[15150.224459] wlan0: authenticate with <MAC address removed>
[15150.234986] wlan0: direct probe to <MAC address removed> (try 1/3)
[15150.436308] wlan0: direct probe to <MAC address removed> (try 2/3)
[15150.640310] wlan0: direct probe to <MAC address removed> (try 3/3)
[15150.844294] wlan0: authentication with <MAC address removed> timed out
[15158.080133] wlan0: authenticate with <MAC address removed>
[15158.082654] wlan0: direct probe to <MAC address removed> (try 1/3)
[15158.284233] wlan0: direct probe to <MAC address removed> (try 2/3)
[15158.488059] wlan0: direct probe to <MAC address removed> (try 3/3)
[15158.692040] wlan0: authentication with <MAC address removed> timed out
[15161.896900] wlan0: authenticate with <MAC address removed>
[15161.898182] wlan0: direct probe to <MAC address removed> (try 1/3)
[15162.100057] wlan0: direct probe to <MAC address removed> (try 2/3)
[15162.304047] wlan0: direct probe to <MAC address removed> (try 3/3)
[15162.508051] wlan0: authentication with <MAC address removed> timed out
[15165.685493] wlan0: authenticate with <MAC address removed>
[15165.686838] wlan0: direct probe to <MAC address removed> (try 1/3)
[15165.888063] wlan0: direct probe to <MAC address removed> (try 2/3)
[15166.092094] wlan0: direct probe to <MAC address removed> (try 3/3)
[15166.299085] wlan0: authentication with <MAC address removed> timed out
[15169.475383] wlan0: authenticate with <MAC address removed>
[15169.476688] wlan0: direct probe to <MAC address removed> (try 1/3)
[15169.680092] wlan0: direct probe to <MAC address removed> (try 2/3)
[15169.884136] wlan0: direct probe to <MAC address removed> (try 3/3)
[15170.088066] wlan0: authentication with <MAC address removed> timed out
[15173.365694] wlan0: authenticate with <MAC address removed>
[15173.366782] wlan0: direct probe to <MAC address removed> (try 1/3)
[15173.568060] wlan0: direct probe to <MAC address removed> (try 2/3)
[15173.772063] wlan0: direct probe to <MAC address removed> (try 3/3)
[15173.976055] wlan0: authentication with <MAC address removed> timed out
[15177.155239] wlan0: authenticate with <MAC address removed>
[15177.156732] wlan0: direct probe to <MAC address removed> (try 1/3)
[15177.360049] wlan0: direct probe to <MAC address removed> (try 2/3)
[15177.564070] wlan0: direct probe to <MAC address removed> (try 3/3)
[15177.768063] wlan0: authentication with <MAC address removed> timed out
[15186.063639] wlan0: authenticate with <MAC address removed>
[15186.065953] wlan0: direct probe to <MAC address removed> (try 1/3)
[15186.268212] wlan0: direct probe to <MAC address removed> (try 2/3)
[15186.472066] wlan0: direct probe to <MAC address removed> (try 3/3)
[15186.676066] wlan0: authentication with <MAC address removed> timed out
[15189.955688] wlan0: authenticate with <MAC address removed>
[15189.957927] wlan0: direct probe to <MAC address removed> (try 1/3)
[15190.160054] wlan0: direct probe to <MAC address removed> (try 2/3)
[15190.364060] wlan0: direct probe to <MAC address removed> (try 3/3)
[15190.568077] wlan0: authentication with <MAC address removed> timed out
[15193.743814] wlan0: authenticate with <MAC address removed>
[15193.745708] wlan0: direct probe to <MAC address removed> (try 1/3)
[15193.948037] wlan0: direct probe to <MAC address removed> (try 2/3)
[15194.152356] wlan0: direct probe to <MAC address removed> (try 3/3)
[15194.356085] wlan0: authentication with <MAC address removed> timed out
[15197.532526] wlan0: authenticate with <MAC address removed>
[15197.533595] wlan0: direct probe to <MAC address removed> (try 1/3)
[15197.736088] wlan0: direct probe to <MAC address removed> (try 2/3)
[15197.940077] wlan0: direct probe to <MAC address removed> (try 3/3)
[15198.144070] wlan0: authentication with <MAC address removed> timed out
[15201.424365] wlan0: authenticate with <MAC address removed>
[15201.425651] wlan0: direct probe to <MAC address removed> (try 1/3)
[15201.628072] wlan0: direct probe to <MAC address removed> (try 2/3)
[15201.832075] wlan0: direct probe to <MAC address removed> (try 3/3)
[15202.036079] wlan0: authentication with <MAC address removed> timed out
[15205.314996] wlan0: authenticate with <MAC address removed>
[15205.316106] wlan0: direct probe to <MAC address removed> (try 1/3)
[15205.520058] wlan0: direct probe to <MAC address removed> (try 2/3)
[15205.724044] wlan0: direct probe to <MAC address removed> (try 3/3)
[15205.928033] wlan0: authentication with <MAC address removed> timed out
[15214.123202] wlan0: authenticate with <MAC address removed>
[15214.129604] wlan0: direct probe to <MAC address removed> (try 1/3)
[15214.332125] wlan0: direct probe to <MAC address removed> (try 2/3)
[15214.536066] wlan0: direct probe to <MAC address removed> (try 3/3)
[15214.740120] wlan0: authentication with <MAC address removed> timed out
[15226.023529] wlan0: authenticate with <MAC address removed>
[15226.029315] wlan0: direct probe to <MAC address removed> (try 1/3)
[15226.232080] wlan0: direct probe to <MAC address removed> (try 2/3)
[15226.436074] wlan0: direct probe to <MAC address removed> (try 3/3)
[15226.640084] wlan0: authentication with <MAC address removed> timed out
[15229.891457] wlan0: authenticate with <MAC address removed>
[15229.892613] wlan0: direct probe to <MAC address removed> (try 1/3)
[15230.096065] wlan0: direct probe to <MAC address removed> (try 2/3)
[15230.300083] wlan0: direct probe to <MAC address removed> (try 3/3)
[15230.504031] wlan0: authentication with <MAC address removed> timed out
[15539.148786] wlan0: authenticate with <MAC address removed>
[15539.156320] wlan0: direct probe to <MAC address removed> (try 1/3)
[15539.360124] wlan0: direct probe to <MAC address removed> (try 2/3)
[15539.564048] wlan0: direct probe to <MAC address removed> (try 3/3)
[15539.768070] wlan0: authentication with <MAC address removed> timed out
[15551.201058] wlan0: authenticate with <MAC address removed>
[15551.203183] wlan0: direct probe to <MAC address removed> (try 1/3)
[15551.404096] wlan0: direct probe to <MAC address removed> (try 2/3)
[15551.608175] wlan0: direct probe to <MAC address removed> (try 3/3)
[15551.812070] wlan0: authentication with <MAC address removed> timed out
[15555.018592] wlan0: authenticate with <MAC address removed>
[15555.023169] wlan0: direct probe to <MAC address removed> (try 1/3)
[15555.224052] wlan0: direct probe to <MAC address removed> (try 2/3)
[15555.428066] wlan0: direct probe to <MAC address removed> (try 3/3)
[15555.632054] wlan0: authentication with <MAC address removed> timed out
[15558.807186] wlan0: authenticate with <MAC address removed>
[15558.809244] wlan0: direct probe to <MAC address removed> (try 1/3)
[15559.012095] wlan0: direct probe to <MAC address removed> (try 2/3)
[15559.216094] wlan0: direct probe to <MAC address removed> (try 3/3)
[15559.420078] wlan0: authentication with <MAC address removed> timed out
[15567.073733] wlan0: authenticate with <MAC address removed>
[15567.079710] wlan0: direct probe to <MAC address removed> (try 1/3)
[15567.280049] wlan0: direct probe to <MAC address removed> (try 2/3)
[15567.484309] wlan0: direct probe to <MAC address removed> (try 3/3)
[15567.688064] wlan0: authentication with <MAC address removed> timed out
[15570.992270] wlan0: authenticate with <MAC address removed>
[15570.993316] wlan0: direct probe to <MAC address removed> (try 1/3)
[15571.196073] wlan0: direct probe to <MAC address removed> (try 2/3)
[15571.400070] wlan0: direct probe to <MAC address removed> (try 3/3)
[15571.604047] wlan0: authentication with <MAC address removed> timed out
[15574.782219] wlan0: authenticate with <MAC address removed>
[15574.784821] wlan0: direct probe to <MAC address removed> (try 1/3)
[15574.988115] wlan0: direct probe to <MAC address removed> (try 2/3)
[15575.192036] wlan0: direct probe to <MAC address removed> (try 3/3)
[15575.396100] wlan0: authentication with <MAC address removed> timed out
[15578.602822] wlan0: authenticate with <MAC address removed>
[15578.604734] wlan0: direct probe to <MAC address removed> (try 1/3)
[15578.808075] wlan0: direct probe to <MAC address removed> (try 2/3)
[15579.012069] wlan0: direct probe to <MAC address removed> (try 3/3)
[15579.220057] wlan0: authentication with <MAC address removed> timed out
[15582.459156] wlan0: authenticate with <MAC address removed>
[15582.460167] wlan0: direct probe to <MAC address removed> (try 1/3)
[15582.665997] wlan0: direct probe to <MAC address removed> (try 2/3)
[15582.868087] wlan0: direct probe to <MAC address removed> (try 3/3)
[15583.072061] wlan0: authentication with <MAC address removed> timed out
[15586.251435] wlan0: authenticate with <MAC address removed>
[15586.258028] wlan0: direct probe to <MAC address removed> (try 1/3)
[15586.460099] wlan0: direct probe to <MAC address removed> (try 2/3)
[15586.664281] wlan0: direct probe to <MAC address removed> (try 3/3)
[15586.868089] wlan0: authentication with <MAC address removed> timed out
[15595.160617] wlan0: authenticate with <MAC address removed>
[15595.168218] wlan0: direct probe to <MAC address removed> (try 1/3)
[15595.372080] wlan0: direct probe to <MAC address removed> (try 2/3)
[15595.576050] wlan0: direct probe to <MAC address removed> (try 3/3)
[15595.780038] wlan0: authentication with <MAC address removed> timed out
[15607.141125] wlan0: authenticate with <MAC address removed>
[15607.152320] wlan0: direct probe to <MAC address removed> (try 1/3)
[15607.356058] wlan0: direct probe to <MAC address removed> (try 2/3)
[15607.560146] wlan0: direct probe to <MAC address removed> (try 3/3)
[15607.764132] wlan0: authentication with <MAC address removed> timed out
[15623.116500] wlan0: authenticate with <MAC address removed>
[15623.125835] wlan0: direct probe to <MAC address removed> (try 1/3)
[15623.328046] wlan0: direct probe to <MAC address removed> (try 2/3)
[15623.532035] wlan0: direct probe to <MAC address removed> (try 3/3)
[15623.736065] wlan0: authentication with <MAC address removed> timed out
[15643.084598] wlan0: authenticate with <MAC address removed>
[15643.091001] wlan0: direct probe to <MAC address removed> (try 1/3)
[15643.292079] wlan0: direct probe to <MAC address removed> (try 2/3)
[15643.496062] wlan0: direct probe to <MAC address removed> (try 3/3)
[15643.700584] wlan0: authentication with <MAC address removed> timed out
[15656.601400] wlan0: authenticate with <MAC address removed>
[15656.602843] wlan0: direct probe to <MAC address removed> (try 1/3)
[15656.804074] wlan0: direct probe to <MAC address removed> (try 2/3)
[15657.008072] wlan0: direct probe to <MAC address removed> (try 3/3)
[15657.212068] wlan0: authentication with <MAC address removed> timed out
[15660.370356] wlan0: authenticate with <MAC address removed>
[15660.371978] wlan0: direct probe to <MAC address removed> (try 1/3)
[15660.572062] wlan0: direct probe to <MAC address removed> (try 2/3)
[15660.776041] wlan0: direct probe to <MAC address removed> (try 3/3)
[15660.980044] wlan0: authentication with <MAC address removed> timed out
[15982.034479] wlan0: authenticate with <MAC address removed>
[15982.038732] wlan0: direct probe to <MAC address removed> (try 1/3)
[15982.240092] wlan0: direct probe to <MAC address removed> (try 2/3)
[15982.444059] wlan0: direct probe to <MAC address removed> (try 3/3)
[15982.648102] wlan0: authentication with <MAC address removed> timed out
[16001.950204] wlan0: authenticate with <MAC address removed>
[16001.954481] wlan0: direct probe to <MAC address removed> (try 1/3)
[16002.156120] wlan0: direct probe to <MAC address removed> (try 2/3)
[16002.360072] wlan0: direct probe to <MAC address removed> (try 3/3)
[16002.564061] wlan0: authentication with <MAC address removed> timed out
[16010.092381] wlan0: authenticate with <MAC address removed>
[16010.093686] wlan0: direct probe to <MAC address removed> (try 1/3)
[16010.296065] wlan0: direct probe to <MAC address removed> (try 2/3)
[16010.500089] wlan0: direct probe to <MAC address removed> (try 3/3)
[16010.704073] wlan0: authentication with <MAC address removed> timed out
[16013.881201] wlan0: authenticate with <MAC address removed>
[16013.882319] wlan0: direct probe to <MAC address removed> (try 1/3)
[16014.084061] wlan0: direct probe to <MAC address removed> (try 2/3)
[16014.288055] wlan0: direct probe to <MAC address removed> (try 3/3)
[16014.492099] wlan0: authentication with <MAC address removed> timed out
[16025.759386] wlan0: authenticate with <MAC address removed>
[16025.761094] wlan0: direct probe to <MAC address removed> (try 1/3)
[16025.964053] wlan0: direct probe to <MAC address removed> (try 2/3)
[16026.168051] wlan0: direct probe to <MAC address removed> (try 3/3)
[16026.372081] wlan0: authentication with <MAC address removed> timed out
[16029.571943] wlan0: authenticate with <MAC address removed>
[16029.573825] wlan0: direct probe to <MAC address removed> (try 1/3)
[16029.776049] wlan0: direct probe to <MAC address removed> (try 2/3)
[16029.980034] wlan0: direct probe to <MAC address removed> (try 3/3)
[16030.184053] wlan0: authentication with <MAC address removed> timed out
[16038.151536] wlan0: authenticate with <MAC address removed>
[16038.158896] wlan0: direct probe to <MAC address removed> (try 1/3)
[16038.360066] wlan0: direct probe to <MAC address removed> (try 2/3)
[16038.568121] wlan0: direct probe to <MAC address removed> (try 3/3)
[16038.772072] wlan0: authentication with <MAC address removed> timed out
[16041.907613] wlan0: authenticate with <MAC address removed>
[16041.909327] wlan0: direct probe to <MAC address removed> (try 1/3)
[16042.112039] wlan0: direct probe to <MAC address removed> (try 2/3)
[16042.317120] wlan0: direct probe to <MAC address removed> (try 3/3)
[16042.520037] wlan0: authentication with <MAC address removed> timed out
[16045.754838] wlan0: authenticate with <MAC address removed>
[16045.755782] wlan0: direct probe to <MAC address removed> (try 1/3)
[16045.956119] wlan0: direct probe to <MAC address removed> (try 2/3)
[16046.160161] wlan0: direct probe to <MAC address removed> (try 3/3)
[16046.364086] wlan0: authentication with <MAC address removed> timed out
[16063.030568] wlan0: authenticate with <MAC address removed>
[16063.033315] wlan0: direct probe to <MAC address removed> (try 1/3)
[16063.236051] wlan0: direct probe to <MAC address removed> (try 2/3)
[16063.440067] wlan0: direct probe to <MAC address removed> (try 3/3)
[16063.644035] wlan0: authentication with <MAC address removed> timed out
[16066.855845] wlan0: authenticate with <MAC address removed>
[16066.859520] wlan0: direct probe to <MAC address removed> (try 1/3)
[16067.060119] wlan0: direct probe to <MAC address removed> (try 2/3)
[16067.264098] wlan0: direct probe to <MAC address removed> (try 3/3)
[16067.468110] wlan0: authentication with <MAC address removed> timed out
[16070.714654] wlan0: authenticate with <MAC address removed>
[16070.718018] wlan0: direct probe to <MAC address removed> (try 1/3)
[16070.920061] wlan0: direct probe to <MAC address removed> (try 2/3)
[16071.124065] wlan0: direct probe to <MAC address removed> (try 3/3)
[16071.328093] wlan0: authentication with <MAC address removed> timed out
[16074.503146] wlan0: authenticate with <MAC address removed>
[16074.504345] wlan0: direct probe to <MAC address removed> (try 1/3)
[16074.708091] wlan0: direct probe to <MAC address removed> (try 2/3)
[16074.912085] wlan0: direct probe to <MAC address removed> (try 3/3)
[16075.116087] wlan0: authentication with <MAC address removed> timed out
[16086.383577] wlan0: authenticate with <MAC address removed>
[16086.385355] wlan0: direct probe to <MAC address removed> (try 1/3)
[16086.588071] wlan0: direct probe to <MAC address removed> (try 2/3)
[16086.792085] wlan0: direct probe to <MAC address removed> (try 3/3)
[16086.996094] wlan0: authentication with <MAC address removed> timed out

****************** done ******************


```


And here the other set of outputs:

```
~$ cat /etc/pm/power.d
cat: /etc/pm/power.d: It's a directory

```

```
~$ grep -R "iwlwifi" /etc/modprobe.d/
/etc/modprobe.d/iwlwifi.conf~:options iwlwifi
/etc/modprobe.d/iwlwifi.conf:options iwlwifi 11n_disable=1 swcrypto=1

```

```
~$ grep -R [[:graph:]] /sys/module/iwlwifi/parameters
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/swcrypto:1
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/bt_coex_active:N
/sys/module/iwlwifi/parameters/11n_disable:1
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0

```

```
~$ dmesg | grep 80211
[  691.227753] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1608.859931] cfg80211: Calling CRDA to update world regulatory domain
[ 1608.865769] cfg80211: World regulatory domain updated:
[ 1608.865773] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1608.865775] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1608.865777] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1608.865779] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1608.865781] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1608.865783] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1608.912428] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1740.842491] cfg80211: Calling CRDA to update world regulatory domain
[ 1740.853655] cfg80211: World regulatory domain updated:
[ 1740.853665] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1740.853672] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1740.853678] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1740.853684] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1740.853690] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1740.853695] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1760.842789] cfg80211: Calling CRDA to update world regulatory domain
[ 1760.845965] cfg80211: World regulatory domain updated:
[ 1760.845968] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1760.845971] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1760.845973] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1760.845975] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1760.845977] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1760.845979] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1928.261187] cfg80211: Calling CRDA to update world regulatory domain
[ 1928.265532] cfg80211: World regulatory domain updated:
[ 1928.265536] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1928.265539] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1928.265541] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1928.265543] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1928.265545] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1928.265547] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1928.310084] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2015.993579] cfg80211: Calling CRDA to update world regulatory domain
[ 2015.997437] cfg80211: World regulatory domain updated:
[ 2015.997441] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2015.997443] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2015.997445] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2015.997447] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2015.997449] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2015.997451] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2016.044362] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2347.035802] cfg80211: Calling CRDA to update world regulatory domain
[ 2347.039871] cfg80211: World regulatory domain updated:
[ 2347.039876] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2347.039879] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2347.039881] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2347.039883] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2347.039885] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2347.039886] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2347.085544] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2509.724753] cfg80211: Calling CRDA to update world regulatory domain
[ 2509.730011] cfg80211: World regulatory domain updated:
[ 2509.730016] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2509.730018] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2509.730020] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2509.730022] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2509.730024] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2509.730026] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2509.777457] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2564.094438] cfg80211: Calling CRDA to update world regulatory domain
[ 2564.104518] cfg80211: World regulatory domain updated:
[ 2564.104521] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2564.104524] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2564.104526] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2564.104527] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2564.104529] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2564.104531] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.093169] cfg80211: Calling CRDA to update world regulatory domain
[ 2693.101057] cfg80211: World regulatory domain updated:
[ 2693.101061] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2693.101063] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.101065] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.101067] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2693.101069] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.101071] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.143540] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3720.578356] cfg80211: Calling CRDA to update world regulatory domain
[ 3720.585535] cfg80211: World regulatory domain updated:
[ 3720.585539] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3720.585542] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3720.585544] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3720.585546] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3720.585548] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3720.585550] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3720.628223] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3792.565224] cfg80211: Calling CRDA to update world regulatory domain
[ 3792.569502] cfg80211: World regulatory domain updated:
[ 3792.569506] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3792.569509] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3792.569511] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3792.569513] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3792.569515] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3792.569516] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3792.613397] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 3962.346367] cfg80211: Calling CRDA to update world regulatory domain
[ 3962.357842] cfg80211: World regulatory domain updated:
[ 3962.357847] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3962.357850] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3962.357852] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3962.357854] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3962.357856] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3962.357858] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3962.397779] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 4069.515932] cfg80211: Calling CRDA to update world regulatory domain
[ 4069.523485] cfg80211: World regulatory domain updated:
[ 4069.523488] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4069.523491] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4069.523493] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4069.523495] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4069.523497] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4069.523499] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4069.565057] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 4144.421306] cfg80211: Calling CRDA to update world regulatory domain
[ 4144.427306] cfg80211: World regulatory domain updated:
[ 4144.427310] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4144.427312] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4144.427314] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4144.427316] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4144.427318] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4144.427320] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4144.473719] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 8153.982352] cfg80211: Calling CRDA to update world regulatory domain
[ 8153.992623] cfg80211: World regulatory domain updated:
[ 8153.992628] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8153.992630] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8153.992632] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8153.992634] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8153.992636] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8153.992638] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14562.906628] cfg80211: Calling CRDA to update world regulatory domain
[14562.915862] cfg80211: World regulatory domain updated:
[14562.915865] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14562.915867] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14562.915869] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14562.915871] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14562.915873] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14562.915875] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14562.958003] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14655.430458] cfg80211: Calling CRDA to update world regulatory domain
[14655.439493] cfg80211: World regulatory domain updated:
[14655.439496] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14655.439498] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.439500] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.439502] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14655.439504] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.439506] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.484527] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14786.945771] cfg80211: Calling CRDA to update world regulatory domain
[14786.948858] cfg80211: World regulatory domain updated:
[14786.948862] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14786.948865] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.948867] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.948869] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14786.948871] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.948873] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.996867] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14951.307568] cfg80211: Calling CRDA to update world regulatory domain
[14951.315834] cfg80211: World regulatory domain updated:
[14951.315839] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14951.315841] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.315843] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.315845] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14951.315847] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.315849] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.359007] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

```

---

### Post by varunendra on 2013-10-27
> **nicoeoc said:**
> 
```
~$ cat /etc/pm/power.d
cat: /etc/pm/power.d: It's a directory

```

My mistake! It should have been "ls", not "cat", corrected in the original post. :redface:

Please try the corrected command and post back the output.

And try this -
```
sudo iwconfig wlan0 txpower 20
```
..then check if the value was accepted -
```
iwconfig wlan0
```
Does the "Tx-Power" change to 20 dBm? It may or may not, as not all cards support multiple tx powers. So if it doesn't stick or doesn't help, then disabling N-channel in the router itself is our next best hope. Please refer to its user manual to see how to change its channel mode to b/g only (or post its exact model no. so we may try to look it up on the net).

---

### Post by nicoeoc on 2013-10-27
Hi, corrected commands:

```
~$ ls /etc/pm/power.d
wireless

```

```
~$ grep -R "iwlwifi" /etc/modprobe.d/
/etc/modprobe.d/iwlwifi.conf~:options iwlwifi
/etc/modprobe.d/iwlwifi.conf:options iwlwifi 11n_disable=1 swcrypto=1

```

```
~$ grep -R [[:graph:]] /sys/module/iwlwifi/parameters
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/swcrypto:1
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/11n_disable:1
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0

```

```
~$ dmesg | grep 80211
[14655.430458] cfg80211: Calling CRDA to update world regulatory domain
[14655.439493] cfg80211: World regulatory domain updated:
[14655.439496] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14655.439498] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.439500] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.439502] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14655.439504] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.439506] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14655.484527] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14786.945771] cfg80211: Calling CRDA to update world regulatory domain
[14786.948858] cfg80211: World regulatory domain updated:
[14786.948862] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14786.948865] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.948867] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.948869] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14786.948871] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.948873] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14786.996867] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[14951.307568] cfg80211: Calling CRDA to update world regulatory domain
[14951.315834] cfg80211: World regulatory domain updated:
[14951.315839] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[14951.315841] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.315843] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.315845] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[14951.315847] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.315849] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14951.359007] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[18114.828311] cfg80211: Calling CRDA to update world regulatory domain
[18114.833479] cfg80211: World regulatory domain updated:
[18114.833483] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[18114.833486] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18114.833488] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18114.833490] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[18114.833492] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18114.833494] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18114.878179] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[27128.718849] cfg80211: Calling CRDA to update world regulatory domain
[27128.722383] cfg80211: World regulatory domain updated:
[27128.722387] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[27128.722389] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27128.722392] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27128.722394] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[27128.722395] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27128.722397] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27183.709188] cfg80211: Calling CRDA to update world regulatory domain
[27183.722803] cfg80211: World regulatory domain updated:
[27183.722815] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[27183.722822] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27183.722828] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27183.722834] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[27183.722840] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[27183.722845] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```


For tx-power:

```
~$ sudo iwconfig wlan0 txpower 20
[sudo] password for "user": 

~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

For n-channel management I can find nothing, here are some links referring to my router model:

[http://www.plus.net/support/broadband/hardware/technicolor-582n-wireless.shtml](http://www.plus.net/support/broadband/hardware/technicolor-582n-wireless.shtml)
[https://www.ono.es/resources/files/ayuda-y-soporte/internet/equipos/documentacion/THOMSON/TD5130/THOMSON_TD5130_Manual_Ingles.pdf](https://www.ono.es/resources/files/ayuda-y-soporte/internet/equipos/documentacion/THOMSON/TD5130/THOMSON_TD5130_Manual_Ingles.pdf)

---

### Post by varunendra on 2013-10-27
Hmm.. interesting router, probably designed by Steve Jobs himself. 

Since we can't test with N channel fully disabled (on both the router and the driver), let's try something radical. That is, enable it on the driver as well. There is only one usual combination that you don't seem to have tried yet (since 11n_disable and swcrypto were enabled all along since we started). Please do -
```
sudo sed -i 's/11n.*1/swcrypto=1 bt_coex_active=N/' /etc/modprobe.d/iwlwifi.conf
```
Then check -
```
cat /etc/modprobe.d/iwlwifi.conf
```
It should now be -
```
options iwlwifi swcrypto=1 bt_coex_active=N
```
..that is, 11n_disable=1 gone! Like I said, it is radical to our approach to disable it completely, let's see if it can surprise us.

To make the change effective, either reboot, or -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwldvm
```
..with this, we are probably at the end of whatever can be sensibly tried with the driver itself, maybe forcing a lower speed could be my next advice if this doesn't help.

---

### Post by nicoeoc on 2013-10-27
This doesn't seem to help either. What I'm going to do is a new fresh install of ubuntu 13.10, and then check things we've been doing again.

Regarding the router I must tell you this wifi problem is old, and at least 3 different routers (for adsl company changes) have had the same problem... 

Frustation levels at max.

Thanks anyway for your help, when I'm done reinstalling SO I'll pass by again.

---

### Post by varunendra on 2013-10-27
..And I'd be keen to hear about the progress.

As a side note, could you try 12.04.3 as well? Just a test in Live mode, no installation. This driver (+ this card that you have) used to work nicely in kernel 3.8 that 12.04.3 comes with by default. Saucy, as well as the kernel 3.11 in it are rather new and I don't have much evidence about the driver included in it to be able to judge or even guess its performance.

Latest is not always the greatest.

---

### Post by nicoeoc on 2013-10-30
Hello again, I have just fresh-installed Ubuntu 12.04 amd64, and have checked everything we did before with no progress. It recognizes networks, it recognize mine, but can't connect to it.

I post updated commands:

**lshw -C network, lspci -nn | grep 0280, ~$ iwconfig, ~$ rfkill list all**
```
~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:9b:56:54
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-32-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f6cfe000-f6cfffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:44:48:2b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f6bfc000-f6bfffff ioport:ce00(size=256)



~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]



~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



~$ rfkill list all
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

**swcrypto=1, 11n_disable=1, bt_coex_active=N:**
```
sudo modprobe -rv iwldvm
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko

~$ sudo modprobe -v iwlwifi swcrypto=1
insmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko swcrypto=1

~$ sudo modprobe -v iwldvm


~$ sudo modprobe -rv iwldvm
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko

~$ sudo modprobe -v iwlwifi 11n_disable=1
insmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1

~$ sudo modprobe -v iwldvm


~$ sudo modprobe -rv iwldvm
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko

~$ sudo modprobe -v iwlwifi bt_coex_active=N
insmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko bt_coex_active=N

~$ sudo modprobe -v iwldvm


~$ sudo modprobe -rv iwldvm
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko

~$ sudo modprobe -v iwlwifi swcrypto=1 11n_disable=1 bt_coex_active=N
insmod /lib/modules/3.8.0-32-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko swcrypto=1 11n_disable=1 bt_coex_active=N

~$ sudo modprobe -v iwldvm
```

**varunendra Wireless script:**
```



*************** info trace ***************


***** uname -a *****


Linux espe-laptop 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


***** lspci *****


09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:0406]
    Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi


***** lsusb *****


Bus 001 Device 003: ID 0c45:6400 Microdia 
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


iwldvm                249093  0 
mac80211              630977  1 iwldvm
iwlwifi               183603  1 iwldvm
cfg80211              525326  3 iwldvm,mac80211,iwlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    WLAN_87D6:       Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA
    WLAN_2188:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA
    Vodafone9E47:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    WLAN_9771:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    WLAN_E439:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WPA
    Orange-E129:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Orange-e3f2:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    WLAN_03EB:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    Orange-2CF8:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    vodafone606A:    Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 25 WPA
    JAZZTEL_576C:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    FTE-ACD6:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    jaycasnat:       Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_4DAC:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 24 WPA
    WLAN_0BE8:       Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 20 WPA
    WLAN_5564:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 20 WPA
    WLAN_82:         Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WEP
    WLAN_620C:       Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 19 WPA
    WLAN_5F95:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    LCA:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    WLAN_5450:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_FEBA:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    vodafone74E2:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA
    VodafoneBCEC:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA
    vodafone9392:    Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 22 WPA
    Jazztel_6C:      Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ONO2475FA:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    WiFi277490:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    JAZZTEL_13EC:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    WLAN_4830:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    WLAN_A737:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    WLAN_E6:         Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"WLAN_87D6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000045be0ff118b
                    Extra: Last beacon: 2940ms ago
                    IE: Unknown: 0009574C414E5F38374436
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A080000000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Jazztel_6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004571767817f
                    Extra: Last beacon: 3108ms ago
                    IE: Unknown: 000A4A617A7A74656C5F3643
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Orange-E129"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a6eba0e002
                    Extra: Last beacon: 3084ms ago
                    IE: Unknown: 000B4F72616E67652D45313239
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0506000501000800
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000080C00000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C332C001EFFFF000000000000000000000000000080C00000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD050009860100
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WLAN_03EB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000340de6f5719
                    Extra: Last beacon: 3188ms ago
                    IE: Unknown: 0009574C414E5F30334542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLAN_4830"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a908e36161
                    Extra: Last beacon: 3192ms ago
                    IE: Unknown: 0009574C414E5F34383330
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000026127A
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"WLAN_4DAC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f0a4dbc0d2
                    Extra: Last beacon: 2816ms ago
                    IE: Unknown: 0009574C414E5F34444143
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000A0267C4DAC103C000101
                    IE: Unknown: 05050001008001
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030009127A
                    IE: Unknown: DD07000C4304000000
          Cell 07 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WLAN_0BE8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ae0456a16d
                    Extra: Last beacon: 2904ms ago
                    IE: Unknown: 0009574C414E5F30424538
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010C
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88000A026810BE8103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160C070700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000F127A
                    IE: Unknown: DD07000C4304000000
          Cell 08 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"WLAN_5564"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s




***** resolv.conf *****


nameserver 127.0.0.1


***** blacklist *****


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


***** modinfo *****


filename:       /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     EECB8DFF0B4BD5CD4432F8E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-32-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.8.0-32-generic SMP mod_unload modversions 
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




***** udev rules *****


# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[    9.541303] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[    9.815557] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[   11.099907] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   11.099910] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   11.099913] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   11.099915] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   11.099917] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[   11.099919] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   11.100054] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   11.656230] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.337854] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   20.340920] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[   20.542019] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   20.545145] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[   20.683891] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.684321] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.331026] wlan0: authenticate with <MAC address removed>
[   29.333851] wlan0: direct probe to <MAC address removed> (try 1/3)
[   29.536040] wlan0: direct probe to <MAC address removed> (try 2/3)
[   29.740040] wlan0: direct probe to <MAC address removed> (try 3/3)
[   29.944014] wlan0: authentication with <MAC address removed> timed out
[   78.553481] wlan0: authenticate with <MAC address removed>
[   78.557823] wlan0: direct probe to <MAC address removed> (try 1/3)
[   78.760019] wlan0: direct probe to <MAC address removed> (try 2/3)
[   78.964023] wlan0: direct probe to <MAC address removed> (try 3/3)
[   79.168028] wlan0: authentication with <MAC address removed> timed out
[   93.033082] wlan0: authenticate with <MAC address removed>
[   93.035811] wlan0: direct probe to <MAC address removed> (try 1/3)
[   93.237293] wlan0: direct probe to <MAC address removed> (try 2/3)
[   93.440136] wlan0: direct probe to <MAC address removed> (try 3/3)
[   93.644036] wlan0: authentication with <MAC address removed> timed out
[  125.987673] wlan0: authenticate with <MAC address removed>
[  125.990291] wlan0: direct probe to <MAC address removed> (try 1/3)
[  126.192025] wlan0: direct probe to <MAC address removed> (try 2/3)
[  126.396040] wlan0: direct probe to <MAC address removed> (try 3/3)
[  126.600022] wlan0: authentication with <MAC address removed> timed out
[  142.728759] wlan0: authenticate with <MAC address removed>
[  142.731214] wlan0: direct probe to <MAC address removed> (try 1/3)
[  142.932060] wlan0: direct probe to <MAC address removed> (try 2/3)
[  143.136016] wlan0: direct probe to <MAC address removed> (try 3/3)
[  143.340040] wlan0: authentication with <MAC address removed> timed out
[  156.181320] wlan0: authenticate with <MAC address removed>
[  156.186310] wlan0: direct probe to <MAC address removed> (try 1/3)
[  156.388058] wlan0: direct probe to <MAC address removed> (try 2/3)
[  156.592058] wlan0: direct probe to <MAC address removed> (try 3/3)
[  156.796056] wlan0: authentication with <MAC address removed> timed out
[  172.921232] wlan0: authenticate with <MAC address removed>
[  172.923110] wlan0: direct probe to <MAC address removed> (try 1/3)
[  173.124040] wlan0: direct probe to <MAC address removed> (try 2/3)
[  173.328048] wlan0: direct probe to <MAC address removed> (try 3/3)
[  173.532786] wlan0: authentication with <MAC address removed> timed out
[  181.699652] wlan0: authenticate with <MAC address removed>
[  181.701497] wlan0: direct probe to <MAC address removed> (try 1/3)
[  181.904024] wlan0: direct probe to <MAC address removed> (try 2/3)
[  182.108022] wlan0: direct probe to <MAC address removed> (try 3/3)
[  182.312043] wlan0: authentication with <MAC address removed> timed out
[  190.423757] wlan0: authenticate with <MAC address removed>
[  190.428075] wlan0: direct probe to <MAC address removed> (try 1/3)
[  190.632128] wlan0: direct probe to <MAC address removed> (try 2/3)
[  190.836044] wlan0: direct probe to <MAC address removed> (try 3/3)
[  191.040047] wlan0: authentication with <MAC address removed> timed out
[  199.122880] wlan0: authenticate with <MAC address removed>
[  199.124378] wlan0: direct probe to <MAC address removed> (try 1/3)
[  199.328051] wlan0: direct probe to <MAC address removed> (try 2/3)
[  199.532041] wlan0: direct probe to <MAC address removed> (try 3/3)
[  199.736046] wlan0: authentication with <MAC address removed> timed out
[  207.823123] wlan0: authenticate with <MAC address removed>
[  207.825639] wlan0: direct probe to <MAC address removed> (try 1/3)
[  208.028060] wlan0: direct probe to <MAC address removed> (try 2/3)
[  208.232177] wlan0: direct probe to <MAC address removed> (try 3/3)
[  208.436057] wlan0: authentication with <MAC address removed> timed out
[  227.189895] wlan0: authenticate with <MAC address removed>
[  227.191409] wlan0: direct probe to <MAC address removed> (try 1/3)
[  227.392031] wlan0: direct probe to <MAC address removed> (try 2/3)
[  227.596041] wlan0: direct probe to <MAC address removed> (try 3/3)
[  227.800020] wlan0: authentication with <MAC address removed> timed out
[  235.866646] wlan0: authenticate with <MAC address removed>
[  235.868547] wlan0: direct probe to <MAC address removed> (try 1/3)
[  236.072039] wlan0: direct probe to <MAC address removed> (try 2/3)
[  236.276022] wlan0: direct probe to <MAC address removed> (try 3/3)
[  236.480021] wlan0: authentication with <MAC address removed> timed out
[  244.566451] wlan0: authenticate with <MAC address removed>
[  244.577424] wlan0: direct probe to <MAC address removed> (try 1/3)
[  244.780036] wlan0: direct probe to <MAC address removed> (try 2/3)
[  244.984029] wlan0: direct probe to <MAC address removed> (try 3/3)
[  245.188018] wlan0: authentication with <MAC address removed> timed out
[  261.351941] wlan0: authenticate with <MAC address removed>
[  261.354553] wlan0: direct probe to <MAC address removed> (try 1/3)
[  261.556029] wlan0: direct probe to <MAC address removed> (try 2/3)
[  261.760028] wlan0: direct probe to <MAC address removed> (try 3/3)
[  261.964057] wlan0: authentication with <MAC address removed> timed out
[  595.425432] wlan0: authenticate with <MAC address removed>
[  595.430190] wlan0: direct probe to <MAC address removed> (try 1/3)
[  595.632149] wlan0: direct probe to <MAC address removed> (try 2/3)
[  595.836034] wlan0: direct probe to <MAC address removed> (try 3/3)
[  596.040030] wlan0: authentication with <MAC address removed> timed out
[  604.124567] wlan0: authenticate with <MAC address removed>
[  604.126140] wlan0: direct probe to <MAC address removed> (try 1/3)
[  604.328865] wlan0: direct probe to <MAC address removed> (try 2/3)
[  604.532053] wlan0: direct probe to <MAC address removed> (try 3/3)
[  604.736803] wlan0: authentication with <MAC address removed> timed out
[  620.953185] wlan0: authenticate with <MAC address removed>
[  620.955875] wlan0: direct probe to <MAC address removed> (try 1/3)
[  621.156084] wlan0: direct probe to <MAC address removed> (try 2/3)
[  621.360089] wlan0: direct probe to <MAC address removed> (try 3/3)
[  621.564029] wlan0: authentication with <MAC address removed> timed out
[  658.268212] wlan0: authenticate with <MAC address removed>
[  658.270765] wlan0: direct probe to <MAC address removed> (try 1/3)
[  658.472057] wlan0: direct probe to <MAC address removed> (try 2/3)
[  658.676078] wlan0: direct probe to <MAC address removed> (try 3/3)
[  658.880040] wlan0: authentication with <MAC address removed> timed out
[  666.968331] wlan0: authenticate with <MAC address removed>
[  666.973587] wlan0: direct probe to <MAC address removed> (try 1/3)
[  667.176048] wlan0: direct probe to <MAC address removed> (try 2/3)
[  667.380066] wlan0: direct probe to <MAC address removed> (try 3/3)
[  667.584054] wlan0: authentication with <MAC address removed> timed out
[  683.753291] wlan0: authenticate with <MAC address removed>
[  683.755158] wlan0: direct probe to <MAC address removed> (try 1/3)
[  683.956067] wlan0: direct probe to <MAC address removed> (try 2/3)
[  684.160044] wlan0: direct probe to <MAC address removed> (try 3/3)
[  684.364077] wlan0: authentication with <MAC address removed> timed out
[  692.597993] wlan0: authenticate with <MAC address removed>
[  692.601133] wlan0: direct probe to <MAC address removed> (try 1/3)
[  692.804051] wlan0: direct probe to <MAC address removed> (try 2/3)
[  693.008060] wlan0: direct probe to <MAC address removed> (try 3/3)
[  693.212077] wlan0: authentication with <MAC address removed> timed out
[  706.354072] wlan0: authenticate with <MAC address removed>
[  706.360488] wlan0: direct probe to <MAC address removed> (try 1/3)
[  706.564036] wlan0: direct probe to <MAC address removed> (try 2/3)
[  706.768022] wlan0: direct probe to <MAC address removed> (try 3/3)
[  706.972022] wlan0: authentication with <MAC address removed> timed out
[  715.177222] wlan0: authenticate with <MAC address removed>
[  715.182466] wlan0: direct probe to <MAC address removed> (try 1/3)
[  715.384035] wlan0: direct probe to <MAC address removed> (try 2/3)
[  715.588037] wlan0: direct probe to <MAC address removed> (try 3/3)
[  715.792057] wlan0: authentication with <MAC address removed> timed out
[  731.858308] wlan0: authenticate with <MAC address removed>
[  731.862896] wlan0: direct probe to <MAC address removed> (try 1/3)
[  732.064016] wlan0: direct probe to <MAC address removed> (try 2/3)
[  732.268022] wlan0: direct probe to <MAC address removed> (try 3/3)
[  732.472014] wlan0: authentication with <MAC address removed> timed out
[  748.548838] wlan0: authenticate with <MAC address removed>
[  748.552341] wlan0: direct probe to <MAC address removed> (try 1/3)
[  748.756037] wlan0: direct probe to <MAC address removed> (try 2/3)
[  748.960020] wlan0: direct probe to <MAC address removed> (try 3/3)
[  749.164037] wlan0: authentication with <MAC address removed> timed out
[  768.047363] wlan0: authenticate with <MAC address removed>
[  768.048881] wlan0: direct probe to <MAC address removed> (try 1/3)
[  768.252031] wlan0: direct probe to <MAC address removed> (try 2/3)
[  768.456021] wlan0: direct probe to <MAC address removed> (try 3/3)
[  768.660022] wlan0: authentication with <MAC address removed> timed out
[  792.990343] wlan0: authenticate with <MAC address removed>
[  792.992264] wlan0: direct probe to <MAC address removed> (try 1/3)
[  793.196251] wlan0: direct probe to <MAC address removed> (try 2/3)
[  793.400066] wlan0: direct probe to <MAC address removed> (try 3/3)
[  793.604067] wlan0: authentication with <MAC address removed> timed out
[  817.874168] wlan0: authenticate with <MAC address removed>
[  817.877500] wlan0: direct probe to <MAC address removed> (try 1/3)
[  818.080066] wlan0: direct probe to <MAC address removed> (try 2/3)
[  818.284062] wlan0: direct probe to <MAC address removed> (try 3/3)
[  818.488075] wlan0: authentication with <MAC address removed> timed out
[ 1126.366129] wlan0: authenticate with <MAC address removed>
[ 1126.371110] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1126.572069] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1126.776040] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1126.980056] wlan0: authentication with <MAC address removed> timed out
[ 1135.059966] wlan0: authenticate with <MAC address removed>
[ 1135.066121] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1135.268105] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1135.472045] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1135.676075] wlan0: authentication with <MAC address removed> timed out
[ 1143.717009] wlan0: authenticate with <MAC address removed>
[ 1143.718637] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1143.920087] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1144.124080] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1144.328077] wlan0: authentication with <MAC address removed> timed out
[ 1152.421192] wlan0: authenticate with <MAC address removed>
[ 1152.423115] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1152.624043] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1152.828040] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1153.032059] wlan0: authentication with <MAC address removed> timed out
[ 1169.199115] wlan0: authenticate with <MAC address removed>
[ 1169.202870] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1169.404039] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1169.608050] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1169.812015] wlan0: authentication with <MAC address removed> timed out
[ 1177.917597] wlan0: authenticate with <MAC address removed>
[ 1177.919804] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1178.120059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1178.324055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1178.528065] wlan0: authentication with <MAC address removed> timed out
[ 1191.030378] wlan0: authenticate with <MAC address removed>
[ 1191.032162] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1191.236081] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1191.440073] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1191.644054] wlan0: authentication with <MAC address removed> timed out
[ 1199.743019] wlan0: authenticate with <MAC address removed>
[ 1199.746308] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1199.948061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1200.152073] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1200.356057] wlan0: authentication with <MAC address removed> timed out
[ 1216.665504] wlan0: authenticate with <MAC address removed>
[ 1216.667179] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1216.868062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1217.072062] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1217.276058] wlan0: authentication with <MAC address removed> timed out
[ 1225.332503] wlan0: authenticate with <MAC address removed>
[ 1225.334313] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1225.536063] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1225.740055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1225.944056] wlan0: authentication with <MAC address removed> timed out
[ 1233.986457] wlan0: authenticate with <MAC address removed>
[ 1233.988692] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1234.192052] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1234.396057] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1234.600055] wlan0: authentication with <MAC address removed> timed out
[ 1242.740235] wlan0: authenticate with <MAC address removed>
[ 1242.742292] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1242.944059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1243.148055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1243.352076] wlan0: authentication with <MAC address removed> timed out
[ 1262.317118] wlan0: authenticate with <MAC address removed>
[ 1262.319584] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1262.520019] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1262.724014] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1262.928031] wlan0: authentication with <MAC address removed> timed out
[ 1271.002359] wlan0: authenticate with <MAC address removed>
[ 1271.004396] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1271.208062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1271.412053] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1271.616056] wlan0: authentication with <MAC address removed> timed out
[ 1279.707361] wlan0: authenticate with <MAC address removed>
[ 1279.709199] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1279.912020] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1280.116019] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1280.320043] wlan0: authentication with <MAC address removed> timed out
[ 1288.309079] wlan0: authenticate with <MAC address removed>
[ 1288.310812] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1288.512291] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1288.716061] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1288.920052] wlan0: authentication with <MAC address removed> timed out
[ 1296.948101] wlan0: authenticate with <MAC address removed>
[ 1296.949863] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1297.152042] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1297.356054] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1297.560049] wlan0: authentication with <MAC address removed> timed out
[ 1305.653922] wlan0: authenticate with <MAC address removed>
[ 1305.661693] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1305.864073] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1306.068074] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1306.272128] wlan0: authentication with <MAC address removed> timed out
[ 1317.126756] wlan0: authenticate with <MAC address removed>
[ 1317.128556] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1317.332724] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1317.536071] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1317.740073] wlan0: authentication with <MAC address removed> timed out
[ 1325.788531] wlan0: authenticate with <MAC address removed>
[ 1325.790338] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1325.992055] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1326.196066] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1326.400055] wlan0: authentication with <MAC address removed> timed out
[ 1334.390680] wlan0: authenticate with <MAC address removed>
[ 1334.394359] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1334.596040] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1334.800039] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1335.004060] wlan0: authentication with <MAC address removed> timed out
[ 1343.131441] wlan0: authenticate with <MAC address removed>
[ 1343.135780] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1343.336039] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1343.540060] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1343.744064] wlan0: authentication with <MAC address removed> timed out
[ 1351.886325] wlan0: authenticate with <MAC address removed>
[ 1351.888844] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1352.092042] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1352.296029] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1352.500040] wlan0: authentication with <MAC address removed> timed out
[ 1360.641747] wlan0: authenticate with <MAC address removed>
[ 1360.643641] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1360.844039] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1361.048022] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1361.252031] wlan0: authentication with <MAC address removed> timed out
[ 1677.128273] wlan0: authenticate with <MAC address removed>
[ 1677.130247] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1677.332059] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1677.536440] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1677.740080] wlan0: authentication with <MAC address removed> timed out
[ 1685.825473] wlan0: authenticate with <MAC address removed>
[ 1685.828688] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1686.032045] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1686.236044] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1686.440040] wlan0: authentication with <MAC address removed> timed out
[ 1694.537029] wlan0: authenticate with <MAC address removed>
[ 1694.539259] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1694.740051] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1694.944067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1695.148052] wlan0: authentication with <MAC address removed> timed out
[ 1727.344781] wlan0: authenticate with <MAC address removed>
[ 1727.351026] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1727.552064] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1727.756069] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1727.960072] wlan0: authentication with <MAC address removed> timed out
[ 1740.105624] wlan0: authenticate with <MAC address removed>
[ 1740.107495] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1740.308060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1740.512057] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1740.716064] wlan0: authentication with <MAC address removed> timed out
[ 1748.810283] wlan0: authenticate with <MAC address removed>
[ 1748.812734] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1749.016044] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1749.220054] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1749.424058] wlan0: authentication with <MAC address removed> timed out
[ 1757.616525] wlan0: authenticate with <MAC address removed>
[ 1757.618680] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1757.820030] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1758.024028] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1758.228042] wlan0: authentication with <MAC address removed> timed out
[ 1782.602172] wlan0: authenticate with <MAC address removed>
[ 1782.604186] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1782.808048] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1783.012068] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1783.216038] wlan0: authentication with <MAC address removed> timed out
[ 1791.286723] wlan0: authenticate with <MAC address removed>
[ 1791.292920] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1791.496028] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1791.700021] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1791.904041] wlan0: authentication with <MAC address removed> timed out
[ 1811.172705] wlan0: authenticate with <MAC address removed>
[ 1811.174832] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1811.376062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1811.580076] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1811.784665] wlan0: authentication with <MAC address removed> timed out
[ 1819.841188] wlan0: authenticate with <MAC address removed>
[ 1819.844348] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1820.048079] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1820.252084] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1820.456073] wlan0: authentication with <MAC address removed> timed out
[ 1828.580295] wlan0: authenticate with <MAC address removed>
[ 1828.582373] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1828.784064] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1828.988059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1829.192063] wlan0: authentication with <MAC address removed> timed out
[ 1842.630641] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 1842.630894] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[ 1842.639473] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 1842.639478] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 1842.639480] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 1842.639482] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 1842.639484] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 1842.639486] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 1842.639591] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1842.662761] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1842.675535] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1842.678589] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1842.880847] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1842.883962] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1843.032537] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1843.033400] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1850.474590] wlan0: authenticate with <MAC address removed>
[ 1850.486509] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1850.688022] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1850.892040] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1851.096054] wlan0: authentication with <MAC address removed> timed out
[ 1867.369470] wlan0: authenticate with <MAC address removed>
[ 1867.376127] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1867.580061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1867.784049] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1867.988054] wlan0: authentication with <MAC address removed> timed out
[ 1892.413724] wlan0: authenticate with <MAC address removed>
[ 1892.418843] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1892.620055] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1892.824014] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1893.028054] wlan0: authentication with <MAC address removed> timed out
[ 1900.355556] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 1900.356533] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 1905.605864] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 1905.608142] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1905.611221] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1905.759788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1913.259463] wlan0: authenticate with <MAC address removed>
[ 1913.261483] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1913.464060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1913.668029] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1913.872060] wlan0: authentication with <MAC address removed> timed out
[ 1944.899162] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 1944.952023] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 1974.063702] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 1974.063993] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[ 1974.072155] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 1974.072160] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 1974.072162] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 1974.072164] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 1974.072166] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 1974.072169] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 1974.072272] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1974.091880] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1974.103036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1982.871395] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 1982.873722] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1982.876900] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1983.085073] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 1983.088176] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 1983.232218] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1990.815439] wlan0: authenticate with <MAC address removed>
[ 1990.817635] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1991.020029] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1991.224058] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1991.428055] wlan0: authentication with <MAC address removed> timed out
[ 1999.547553] wlan0: authenticate with <MAC address removed>
[ 1999.548714] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1999.752043] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1999.956042] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2000.160067] wlan0: authentication with <MAC address removed> timed out
[ 2024.577634] wlan0: authenticate with <MAC address removed>
[ 2024.580143] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2024.784064] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2024.988060] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2025.192049] wlan0: authentication with <MAC address removed> timed out
[ 2054.170067] wlan0: authenticate with <MAC address removed>
[ 2054.171105] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2054.372042] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2054.576041] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2054.780028] wlan0: authentication with <MAC address removed> timed out
[ 2062.869745] wlan0: authenticate with <MAC address removed>
[ 2062.876160] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2063.080056] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2063.284059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2063.488057] wlan0: authentication with <MAC address removed> timed out
[ 2071.572123] wlan0: authenticate with <MAC address removed>
[ 2071.573188] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2071.776021] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2071.980022] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2072.184018] wlan0: authentication with <MAC address removed> timed out
[ 2080.868448] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to disable radio.
[ 2080.869623] iwlwifi 0000:0c:00.0: Not sending command - RF KILL
[ 2095.663313] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 2095.663785] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[ 2095.673276] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2095.673281] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2095.673283] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2095.673285] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 2095.673288] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2095.673290] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2095.673395] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2095.693395] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2095.705122] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2102.383487] iwlwifi 0000:0c:00.0: RF_KILL bit toggled to enable radio.
[ 2102.385788] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2102.388982] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2102.596989] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2102.600103] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2102.751072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2110.290478] wlan0: authenticate with <MAC address removed>
[ 2110.294992] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2110.496082] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2110.700098] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2110.904090] wlan0: authentication with <MAC address removed> timed out
[ 2127.173136] wlan0: authenticate with <MAC address removed>
[ 2127.174905] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2127.376031] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2127.580057] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2127.784061] wlan0: authentication with <MAC address removed> timed out
[ 2135.880308] wlan0: authenticate with <MAC address removed>
[ 2135.882375] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2136.084028] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2136.288021] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2136.492018] wlan0: authentication with <MAC address removed> timed out
[ 2144.592853] wlan0: authenticate with <MAC address removed>
[ 2144.600558] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2144.804138] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2145.008059] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2145.212057] wlan0: authentication with <MAC address removed> timed out
[ 2153.263380] wlan0: authenticate with <MAC address removed>
[ 2153.268643] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2153.472060] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2153.676040] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2153.880055] wlan0: authentication with <MAC address removed> timed out
[ 2161.936283] wlan0: authenticate with <MAC address removed>
[ 2161.939292] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2162.140061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2162.344767] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2162.548082] wlan0: authentication with <MAC address removed> timed out
[ 2166.985029] iwlwifi 0000:0c:00.0: irq 46 for MSI/MSI-X
[ 2166.985517] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[ 2166.995397] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2166.995402] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2166.995404] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2166.995406] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 2166.995408] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2166.995411] iwlwifi 0000:0c:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2166.995514] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2167.018635] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2167.029440] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2167.034248] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2167.237072] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[ 2167.240188] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[ 2167.391575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2167.392477] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2174.994553] wlan0: authenticate with <MAC address removed>
[ 2174.997055] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2175.200062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2175.404070] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2175.608094] wlan0: authentication with <MAC address removed> timed out
[ 2191.791713] wlan0: authenticate with <MAC address removed>
[ 2191.797363] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2192.000057] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2192.204056] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2192.408067] wlan0: authentication with <MAC address removed> timed out
[ 2200.488849] wlan0: authenticate with <MAC address removed>
[ 2200.490008] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2200.692053] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2200.896060] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2201.100055] wlan0: authentication with <MAC address removed> timed out
[ 2209.109434] wlan0: authenticate with <MAC address removed>
[ 2209.111141] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2209.312055] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2209.516055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2209.720059] wlan0: authentication with <MAC address removed> timed out
[ 2217.809954] wlan0: authenticate with <MAC address removed>
[ 2217.811047] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2218.012061] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2218.216027] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2218.420037] wlan0: authentication with <MAC address removed> timed out
[ 2226.510670] wlan0: authenticate with <MAC address removed>
[ 2226.516938] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2226.720044] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2226.924018] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2227.128041] wlan0: authentication with <MAC address removed> timed out
[ 2302.483736] wlan0: authenticate with <MAC address removed>
[ 2302.485426] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2302.688042] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2302.892057] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2303.096058] wlan0: authentication with <MAC address removed> timed out
[ 2311.187759] wlan0: authenticate with <MAC address removed>
[ 2311.190364] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2311.392062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2311.596052] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2311.800041] wlan0: authentication with <MAC address removed> timed out
[ 2344.000814] wlan0: authenticate with <MAC address removed>
[ 2344.005513] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2344.208065] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2344.413319] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2344.616078] wlan0: authentication with <MAC address removed> timed out
[ 2352.747666] wlan0: authenticate with <MAC address removed>
[ 2352.749132] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2352.952055] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2353.156055] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2353.360057] wlan0: authentication with <MAC address removed> timed out


****************** done ******************



```

**ls /etc/pm/power.d, grep -R "iwlwifi" /etc/modprobe.d/, grep -R [[:graph:]] /sys/module/iwlwifi/parameters, dmesg | grep 80211:**

```
~$ ls /etc/pm/power.d
wireless


:~$ grep -R "iwlwifi" /etc/modprobe.d/


~$ grep -R [[:graph:]] /sys/module/iwlwifi/parameters
/sys/module/iwlwifi/parameters/5ghz_disable:N
/sys/module/iwlwifi/parameters/swcrypto:1
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/auto_agg:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/amsdu_size_8K:1
/sys/module/iwlwifi/parameters/bt_ch_inhibition:Y
/sys/module/iwlwifi/parameters/fw_restart:1
/sys/module/iwlwifi/parameters/bt_coex_active:N
/sys/module/iwlwifi/parameters/11n_disable:1
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/plcp_check:Y
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/power_level:0


~$ dmesg | grep 80211
[    9.037016] cfg80211: Calling CRDA to update world regulatory domain
[   11.656230] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1842.625950] cfg80211: Calling CRDA to update world regulatory domain
[ 1842.662761] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1974.058898] cfg80211: Calling CRDA to update world regulatory domain
[ 1974.091880] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2095.661043] cfg80211: Calling CRDA to update world regulatory domain
[ 2095.693395] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2166.982735] cfg80211: Calling CRDA to update world regulatory domain
[ 2167.018635] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```




Finally I ran this:
```
~$ sudo sed -i 's/11n.*1/swcrypto=1 bt_coex_active=N/' /etc/modprobe.d/iwlwifi.conf
sed: can't read /etc/modprobe.d/iwlwifi.conf: No such file or directory
```

I see I'm lacking a file but don't dare to create it without asking here before, as maybe it's better to mantain the just installed Ubuntu as clean as possible.

Here we go again! thanks again for your attention : )

---

### Post by varunendra on 2013-11-04
> **nicoeoc said:**
> Hello again, I have just fresh-installed Ubuntu 12.04 amd64....
....
Finally I ran this:
```
~$ sudo sed -i 's/11n.*1/swcrypto=1 bt_coex_active=N/' /etc/modprobe.d/iwlwifi.conf
sed: can't read /etc/modprobe.d/iwlwifi.conf: No such file or directory
```

I see I'm lacking a file but don't dare to create it without asking here before, as maybe it's better to mantain the just installed Ubuntu as clean as possible.

Here we go again! thanks again for your attention : )

I'm so sorry I couldn't reply earlier. I got totally wrapped up in some personal matters at home, and probably would be for a little more time. The above file doesn't exist in a fresh installation of 12.04 (while it definitely does in 13.04 and later), so if we need some custom parameters, we need to create it.

This is how (assuming we need parameter "bt_coex_active=N") -
```
echo "options iwlwifi bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
(Note that the above file 'Overwrites' the "iwlwifi.conf" file if it already exists. In my experience so far, there is no harm in doing so.)

To try multiple parameters simultaneously (with an example of 3 most commonly used parameters) -
```
echo "options iwlwifi swcrypto=1 bt_coex_active=N 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

I would recommend to use only "swcrypto=1" and "bt_coex_active=N" at first. If that doesn't help, you may try the "11n_disable=1" as well.

There is also a new parameter "**5ghz_disable**" in the driver that didn't exist in the previous one (which is interesting by the way). You may try using it as well (to disable 5GHz band support, which I believe your router doesn't support anyway) -
```
echo "options iwlwifi swcrypto=1 5ghz_disable=Y" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

So now there are 4 parameters to play with which are likely to help in many cases. Of course you can always use them in the 'temporary' mode as mentioned in post #7 to test if any (or any combination) of them actually helps, before making them permanent as mentioned above.

Please try these and post back how it goes. **I may not be able to respond quickly for a few days, but there are others, much better than me, who I'm sure will post if they noticed the thread and have something to add.** Feel free to PM anyone who you think may likely be able to help.

**PS:**
I haven't read much about it, but there seems to be a firmware "[DD-WRT]("http://www.dd-wrt.co.in/site/index")" that can be used to replace the proprietary firmware on many **(But NOT ALL!)** routers to make it more compatible in most cases. **[COLOR="#FF0000"]CAUTION ![/COLOR]** Replacing firmware can be risky, so consider it as the last option and do some research before doing so.

---

### Post by nicoeoc on 2013-11-11
Hi again, just wanted to let you know that I kind of gave up on this, my workaround if you can call it so has been just to configure another router as a bridge so I can have internet via ethernet even being away from the source router... 

I tried what you last posted with no progress, so by now we can let this as SO UNSOLVED xD and just wait if in the near future we can have an actual solution, maybe an update for 13.10 or something. Either that or me coming here to give it another try because my router bridge fails at some point ; )

Greetings and thank you very much for your help.

---

