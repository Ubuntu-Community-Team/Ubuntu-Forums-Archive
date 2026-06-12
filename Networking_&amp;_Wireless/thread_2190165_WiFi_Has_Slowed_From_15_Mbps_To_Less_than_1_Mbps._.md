---
title: "WiFi Has Slowed From 15 Mbps To Less than 1 Mbps. What's Up?"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by Smallwheels on 2013-11-26
My 13.04 machine has slowed considerably. I connect wirelessly to a router using an external antenna. I know that the position of the antenna matters a lot. I have checked the position of the router and my antenna. Nothing has changed yet my connection speed has diminished greatly. To try to get a better connection I moved the antenna around. It has a small effect. My other computer (which is a laptop without an external antenna) directly beside the antenna for the Ubuntu machine is connecting at 15+ Mbps. I don't understand what could have caused this change.

It's after 1 o'clock in the morning. I doubt there are many people using the internet in my neighborhood. There are 26 connections in the area. I'm the only one using this router at this time, though the other computer is connected it is in sleep mode. 

Thank you for any assistance you can give. 

I followed the instructions at this link regarding wireless troubleshooting; [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385) 

This is the resulting information: 
```
   
*************** info trace ***************

***** uname -a *****

Linux michael-NY801AV-ABA-p6100z 3.8.0-33-generic #48-Ubuntu SMP Wed Oct 23 09:16:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a6c]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 004: ID 03f0:7711 Hewlett-Packard 
Bus 001 Device 005: ID 0480:a009 Toshiba America Info. Systems, Inc. 
Bus 001 Device 008: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 007: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:".brenda1091-guest"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

r8712u                187938  0 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [.brenda1091-guest] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
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
    .brenda1091:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    OrangeGiraffe:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    Missoula:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Zedhedz:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 46 WPA2
    chewy69:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    belkin.84c:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    SPHERE:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 43 WPA WPA2
    myqwest1234:     Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 43 WPA WPA2
    belkin.456:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 23 WPA WPA2
    TealOak:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    WyoKat:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    Verizon MiFi2200 6F5A Secure: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 26 WPA
    SPHERE 2:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    NETGEAR63:       Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 7 WPA2
    Belkin.3E6D:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 58 WEP
    belkin.8b8.guests: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 43
    *.brenda1091-guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    CenturyLink8961: Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    myrouter:        Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    chewy69-guest:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    GBMEDVEC59:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    gigi61702-wireless: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    Mike/Donna:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    Hanks:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    Mike/Donna-guest:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7
    myqwest0676:     Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2

  IPv4 Settings:
    Address:         192.168.33.111
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.33.1

    DNS:             69.145.248.4
    DNS:             69.146.17.2
    DNS:             69.144.49.29


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:".brenda1091-guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: <MAC address removed>
                    ESSID:"belkin.8b8.guests"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  
          Cell 03 - Address: <MAC address removed>
                    ESSID:"belkin.84c"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20401000050f20401000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=44/100  
          Cell 04 - Address: <MAC address removed>
                    ESSID:"Missoula"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700103F11CAEB25B1A6254BB988B38CB724DF1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    Signal level=62/100  
          Cell 05 - Address: <MAC address removed>
                    ESSID:"Belkin.3E6D"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Signal level=72/100  
          Cell 06 - Address: <MAC address removed>
                    ESSID:"Zedhedz"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=70/100  
          Cell 07 - Address: <MAC address removed>
                    ESSID:"myqwest2871"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=7/100  
          Cell 08 - Address: <MAC address removed>
                    ESSID:"TealOak"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=43/100  
          Cell 09 - Address: <MAC address removed>
                    ESSID:"Verizon MiFi2200 6F5A Secure"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 10 - Address: <MAC address removed>
                    ESSID:"NETGEAR63"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=26/100  
          Cell 11 - Address: <MAC address removed>
                    ESSID:"chewy69"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=44/100  
          Cell 12 - Address: <MAC address removed>
                    ESSID:"chewy69-guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=44/100  
          Cell 13 - Address: <MAC address removed>
                    ESSID:"myrouter"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B000103104700105563FF295AB3A0C974846F7E9F95A93C1021000D4E4554474541522C20496E632E10230009574E5233353030763210240009574E523335303076321042000230311054000800060050F204000110110009574E52333530307632100800020084
                    Signal level=10/100  
          Cell 14 - Address: <MAC address removed>
                    ESSID:"myqwest1234"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
                    Signal level=44/100  
          Cell 15 - Address: <MAC address removed>
                    ESSID:"SPHERE 2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA60050F204104A0001101044000102103B00010310470010000000000000100000004494FC7164DB102100064E54474541521023000B574E323030305250547632102400016E1042001253657269616C204E756D62657220486572651054000800060050F204000110110018574E32303030525054763228576972656C65737320415029100800020086103C000103104900140024E26002000101600000020001600100020001
                    Signal level=47/100  
          Cell 16 - Address: <MAC address removed>
                    ESSID:"SPHERE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 17 - Address: <MAC address removed>
                    ESSID:"Mike/Donna-guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=7/100  
          Cell 18 - Address: <MAC address removed>
                    ESSID:"WyoKat"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    Signal level=42/100  
          Cell 19 - Address: <MAC address removed>
                    ESSID:"Mike/Donna"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B000103104700108C0CEC77BDF441EB64D45F9155EAA92D102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    Signal level=7/100  
          Cell 20 - Address: <MAC address removed>
                    ESSID:".brenda1091"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=100/100  
          Cell 21 - Address: <MAC address removed>
                    ESSID:"myqwest0676"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
                    Signal level=7/100  
          Cell 22 - Address: <MAC address removed>
                    ESSID:"belkin.456"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A000110104400010210470010BC329E001DD811B2860108863B9A1456103C000101
                    Signal level=42/100  
          Cell 23 - Address: <MAC address removed>
                    ESSID:"CenturyLink8961"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA50050F204104A0001101044000102103B00010310470010BC329E001DD811B28601B2B2DC9D2708102100175A7958454C20546563686E6F6C6F67792C20436F72702E1023001B5A7958454C20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F2040001101100095A7958454C2041505310080002210C103C0001011049000600372A000120
                    Signal level=42/100  
          Cell 24 - Address: <MAC address removed>
                    ESSID:"OrangeGiraffe"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    Signal level=42/100  


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

***** modinfo *****

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     58CE600D1431D9135F597E5
alias:          usb:v0409p02B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp845Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3325d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3341d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3339d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0049d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0058d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4901d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3336d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3335d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3334d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3333d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3342d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p646Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0752d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0063d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0059d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE034d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1791d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*in*
depends:        
staging:        Y
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:07.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0bda:0x8172 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   11.642854] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   11.675905] r8712u: Staging version
[   11.675938] r8712u: register rtl8712_netdev_ops to netdev_ops
[   11.675940] r8712u: USB_SPEED_HIGH with 4 endpoints
[   11.682340] r8712u: Boot from EFUSE: Autoload OK
[   14.412562] r8712u: CustomerID = 0x0000
[   14.412569] r8712u: MAC Address from efuse = <MAC address removed>
[   14.412571] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   17.764433] r8712u: 1 RCR=0x153f00e
[   17.765177] r8712u: 2 RCR=0x553f00e
[   17.872349] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.872751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.180351] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.813474] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.894061] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 0
[   45.337181] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 320, tid = 0
[ 4056.856211] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 60544, tid = 0
[14975.985070] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 48544, tid = 0
[15101.392351] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15121.960812] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15122.031679] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 0
[15316.563564] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 33072, tid = 0
[25620.033442] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 59680, tid = 0
[75395.789931] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 4
[77579.266324] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 40128, tid = 0
[78900.574324] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 8704, tid = 0
[79818.365310] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 5
[81540.528822] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 59280, tid = 0
[82980.377328] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 34816, tid = 0
[83340.154322] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 11472, tid = 0
[83460.676702] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 26160, tid = 0
[84741.049694] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 3
[100619.897830] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 64528, tid = 0
[100740.001558] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 64704, tid = 0
[118379.535540] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 9536, tid = 0
[124436.287668] r8712u: Staging version
[124436.287756] r8712u: register rtl8712_netdev_ops to netdev_ops
[124436.287762] r8712u: USB_SPEED_HIGH with 4 endpoints
[124436.288859] r8712u: Boot from EFUSE: Autoload OK
[124436.678192] r8712u: CustomerID = 0x0000
[124436.678205] r8712u: MAC Address from efuse = <MAC address removed>
[124436.678210] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[124437.916567] r8712u: 1 RCR=0x153f00e
[124437.917306] r8712u: 2 RCR=0x553f00e
[124438.024410] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[124438.025216] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[124438.332404] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[124459.240680] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[124459.544186] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 0
[124482.254308] r8712u: [r8712_got_addbareq_event_callback] mac = <MAC address removed>, seq = 0, tid = 0

****************** done ******************
      
```

---

### Post by Smallwheels on 2013-11-26
One more bit of information, the upload speed hasn't changed. Download speed is at .48 Mbps while upload speed is 1.75 Mbps.

---

### Post by varunendra on 2013-11-27
> **Smallwheels said:**
> ```

***** dmesg *****

[   11.642854] **[COLOR="#FF0000"]r8712u[/COLOR]**: module is from the staging directory, the quality is unknown, you have been warned.
```

The only thing I can suggest with this card/driver is to try disabling N channel in the router. Refer to your router's user manual to see how to change the channel to b/g mode only. Currently it seems to be in b/g/n mode.

If that doesn't help, then buying a different, better supported wireless adapter is the best (and probably the only) option. Although we can try a few more shots if you wish, like disabling IPv6, using google's DNS etc.

---

### Post by tgalati4 on 2013-11-27
Perhaps turn on narrow-band, it will reduce interference when there are a lot of wireless networks squawking at once.  Even though you may be logged on late at night, there are still a lot of antennas calling out at once.  With only 11 bands and really only 3 bands (1, 6, 11) because of signal spread, once you get past 10 networks, the throughput will get reduced to maintain connectivity.

```
modinfo r8712u
```

The laptop probably has 2 antennas (one on each side of the screen) and this gives it a 3 dB advantage by averaging or taking the stronger of the 2 antennas.  The laptop's wireless card and driver probably has better interference handling.

---

### Post by Smallwheels on 2013-11-27
Varunendra thank you for your suggestion. The router belongs to my roommate and I doubt she will let me fiddle with it. She gets annoyed whenever I have problems with the router. I have handled some other issues with it and she doesn't like me using her computer. I can understand not wanting to let somebody else access the computer. 

Getting a better card or connector might work. Since I'll be moving in a month or two the expense won't be worth the trouble. My new location might give me no problems at all. I'll wait until then to buy a new wireless connection. 

Tgalati4 thank you too. Is there a way to switch to narrow band using just my computer or is that something that must be done on the router? If I can do it on my machine please let me know how.

---

### Post by kurt18947 on 2013-11-27
Here's an outside chance.  What model is your room mate's router?  Quite a number of recent models have a guest network function that offers a separate SSID.  If the router in question has that, I wonder if she could set the guest network to G only or B & G speeds.  It shouldn't impact her use at all if my understanding is correct.  It's too bad you have an RTL8191SU chip, I have some USB RTL819**2**SU devices and they're perfect.

---

### Post by tgalati4 on 2013-11-28
If you open a terminal and use the command that I provided, then it might reveal a switch for that driver.  Some routers have a setting, but you have to log into the router with administrative privileges to change it.  If you change it on the laptop or wireless card that you are using, then the router may switch to narrow band for your session only.  Regardless, troubleshooting wireless for a router that you don't own is difficult.

---

### Post by Smallwheels on 2013-12-17
> **tgalati4 said:**
> Regardless, troubleshooting wireless for a router that you don't own is difficult.For some reason the problem vanished. Maybe it was the clogged airwaves. The router did act up a couple of days ago and I unplugged it and plugged it back in. It is functioning properly. A tech guy who does troubleshooting for the ISP said that wireless routers tend to wear out after about three years. I know this one is at least two years old. 

I intend to make a beer can antenna holder to go around my desktop's external WiFi antenna. Maybe that will focus my machines broadcast signal as well as block the signals of the neighbors computers and routers, thus giving my machine priority over the weaker signals. It's worth a shot.

---

