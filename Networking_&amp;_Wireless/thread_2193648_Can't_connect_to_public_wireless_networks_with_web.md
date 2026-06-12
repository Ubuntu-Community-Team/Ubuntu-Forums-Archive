---
title: "Can't connect to public wireless networks with web logins"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by JarekErvin on 2013-12-14
Hi all,

I'm having trouble accessing public internet accounts at places like Starbucks, hotels, etc., where the network prompts a browser-based login. I've poked around on a number of old forum posts here and elsewhere with people having similar problems, but haven't found anything that exactly speaks to my issue. If I've overlooked something, please let me know, but either way, I'd greatly appreciate whatever advice anyone may have.

Essentially the problem appears to be this:
When connecting to a network of the type described above, my computer appears to successfully connect (at least based on GUI - not sure what's happening on a deeper level). But when I open a browser or other web-based application (bit torrent, etc.), nothing happens. In the case of Firefox, the screen sits on a blank white screen appearing to load. As far as I can tell, the issue seems not to be specific to any browser. I've tried using both Firefox and Chrome to no avail.

Not sure what I can do to fix this. Any insights would be much appreciated.

Thanks!

Jarek

Edit:

I should add, I've also spent a good bit of time messing around with browser settings and wireless settings, which also proved unsuccessful; it doesn't appear to be the fault of proxy/firewall settings as far as I can tell. I'm happy to try anything you might suggest, though.

---

### Post by varunendra on 2013-12-15
I thing all such networks use Enterprise security that use a CA-Certificate for additional security.

When you seem to be connected, a connection with the SSID name should be created. If, for example, this connection name is "Public Wifi", then try this command to see if a line exists or not in its 'Key file' -
```
sudo cat "/etc/NetworkManager/system-connections/Public Wifi"
```
(you don't need to use the double quotes if the name does not contain blank space. DO NOT post its contents here, as it may contain the security key)
Do you see a line "**system-ca-certs=true**" in it? If yes, changing it to "false" may solve the problem.

If there is no such line in the keyfile, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by JarekErvin on 2013-12-24
Varun,

Thanks very much for the great reply. Sorry it took me a bit to write back, but I was out of the USA for work until yesterday.

I followed your suggestions, and found that the entry you mention *was* missing from the keyfile. I used the script you linked, and have posted the output below. Just to be clear, I'm running it from a coffee shop wireless network (my sole access point to internet for the moment) that does not use the kind of login that is giving me trouble. Not sure if that is helpful/unhelpful/irrelevant, but I noticed that the output includes info about it.



```


*************** info trace ***************

***** uname -a *****

Linux jarek-K55N 3.8.0-33-generic #48-Ubuntu SMP Wed Oct 23 09:16:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

***** lspci *****

04:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:1186]
	Kernel driver in use: ath9k
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: ASUSTeK Computer Inc. Device [1043:105b]
	Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 002: ID 04f2:b354 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"Cafe Twelve"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=39 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:61   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413629  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
cfg80211              511019  3 ath,ath9k,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

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


- Device: wlan0  [Cafe Twelve] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Tenda_2A7970:    Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 50 WPA
    skydog:          Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Courtney's Wi-Fi Network: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Grover Net:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    HOME-04E8:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Athena:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    RageCage:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    laser netgear:   Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA2
    ReeseRoccoJohn:  Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Didi:            Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Shazam:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    TonyNet:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    CharlieSalonWIFI:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    zipcarwireless:  Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    504N:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA2
    whodini:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WEP
    KidsOn12:        Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WEP
    11FX08160799:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    mozheng:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    sgrout:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    TWCWiFi:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    xfinitywifi:     Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32
    xfinitywifi:     Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19
    *Cafe Twelve:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA2
    khallman-HP-Wireless: Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    CableWiFi:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79
    xfinitywifi:     Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 34
    Tony's OtherNet: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    MJTnet:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    belkin.194:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    optimumwifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57
    cshapiro:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    12StGym:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14
    Hugs:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    Droo TraxX:      Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Omar:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HOME-FD2D:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Wifi4Ganstaz:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    belkin.b19:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Adams Loft:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    muffin1:         Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA
    Wifi4Ganstaz-guest: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    VSSEPTA8007:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    JKR3rd:          Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    mooses:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    InterWeb:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.67
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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Cafe Twelve"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000B43616665205477656C7665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD840050F204104A00011010440001021041000100103B000103104700105E643B0C03165E8AFCF9ECDBE11FC1361021000D4E4554474541522C20496E632E1023000A574E44523337303076331024000A574E44523337303076331042000230311054000800060050F20400011011000A574E4452333730307633100800020084103C000103
                    IE: Unknown: DD090010180208F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Shazam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001cd562c490a
                    Extra: Last beacon: 3724ms ago
                    IE: Unknown: 00065368617A616D
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7C0050F204104A0001101044000102103B00010310470010079CE48F21946CA60E3A61598AAC118E1021000D4E4554474541522C20496E632E10230005523633303010240005523633303010420004343533361054000800060050F2040001101100055236333030100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001249966d180
                    Extra: Last beacon: 3724ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01088B960C1218243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070655534F010D1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A0C001BFFFE000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004a1b9f0f180
                    Extra: Last beacon: 20192ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 01088B960C1218243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070655534F010D1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A0C001BFFFE000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"CableWiFi"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001249966d181
                    Extra: Last beacon: 3704ms ago
                    IE: Unknown: 00094361626C6557694669
                    IE: Unknown: 01088B960C1218243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070655534F010D1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A0C001BFFFE000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F20201010C0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-04E8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c081256008
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0009484F4D452D30344538
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020066127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DDA70050F204104A0001101044000102103B000103104700102880288028801880A8800026F33D04E81021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B41505310080002210C103C0001011049000600372A000120
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0812d4baf
                    Extra: Last beacon: 3192ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020066127A
                    IE: Unknown: DD07000C4300000000
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c08031cb9c
                    Extra: Last beacon: 19664ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020059127A
                    IE: Unknown: DD07000C4300000000
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c08128bbdb
                    Extra: Last beacon: 3488ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020066127A
                    IE: Unknown: DD07000C4300000000
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Omar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020ed0615877
                    Extra: Last beacon: 280ms ago
                    IE: Unknown: 00044F6D6172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0503004F0000
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F03010008
                    IE: Unknown: DD310050F204104A00011010440001021047001085CBFD950DE41C1ABF48B1433DE319E0103C0001031049000600372A000120
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ada8abd1ed
                    Extra: Last beacon: 380ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0506000100660004
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Tony's OtherNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b9407f263f
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 000F546F6E792773204F746865724E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027424
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710208
                    IE: Unknown: DD0E0017F20700010106F81EDFF973D7
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"RageCage"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f647ac1c6
                    Extra: Last beacon: 352ms ago
                    IE: Unknown: 00085261676543616765
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6B0050F204104A0001101044000102103B00010310470010DB316D82465D213D832FEBB160FF2202102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180201F0000000
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Grover Net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000078e8e63968
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 000A47726F766572204E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F20700010106907240146CB7
                    IE: Unknown: DD090010180200001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 15 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"skydog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000d0dfbec8a1e
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0006736B79646F67
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34090F0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001000000000000010000000F4EC38A98ACC1021000754502D4C494E4B10230009544C2D57523834314E10240007362E302F372E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101
          Cell 16 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"sgrout"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000473b6f95181
                    Extra: Last beacon: 336ms ago
                    IE: Unknown: 00067367726F7574
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0600032F010001
          Cell 17 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TonyNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002b9407cf9fc
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0007546F6E794E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027424
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710320
                    IE: Unknown: DD0E0017F20700010106F81EDFF973D7
          Cell 18 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Courtney's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017a1c1b2185
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 0018436F7572746E657927732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F2070001010690724017916F
                    IE: Unknown: DD090010180201001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 19 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"zipcarwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001d614e8b3063
                    Extra: Last beacon: 16516ms ago
                    IE: Unknown: 000E7A6970636172776972656C657373
                    IE: Unknown: 010882040B0C12161824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E030089000F00FF031900776972656C65737330312E7068696C0002000027
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
          Cell 20 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000094075369
                    Extra: Last beacon: 3084ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 070A555320010B1E010B1E00
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0700109104000500
                    IE: Unknown: 050700010000000000
          Cell 21 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"CharlieSalonWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001568c1ed195
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 0010436861726C696553616C6F6E57494649
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 22 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"InterWeb"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c6084d22
                    Extra: Last beacon: 16516ms ago
                    IE: Unknown: 0008496E746572576562
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403080800000000000000000000000000000000000000
                    IE: Unknown: 3D1603080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700100000000000001000000084C9B24F837D10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363031104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363031100800020080103C000103104900140024E26002000101600000020001600100020001
          Cell 23 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VSSEPTA8007"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000092eb091dd
                    Extra: Last beacon: 1312ms ago
                    IE: Unknown: 000B5653534550544138303037
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 070A555320010B1E010B1E00
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0700109104000500
                    IE: Unknown: 050700010000000000
          Cell 24 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"laser netgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001905912a7
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000D6C61736572206E657467656172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34040D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700100000000000001000000030469A0EE9671021000D4E6574676561722C20496E632E1023000757504E3832344E1024000456324831104200046E6F6E651054000800060050F20400011011001957504E3832344E28576972656C6573732041502D322E344729100800020086103C000103
          Cell 25 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Tenda_2A7970"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024b214c5d52
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000C54656E64615F324137393730
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 26 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"JKR3rd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000189739f137a6
                    Extra: Last beacon: 19136ms ago
                    IE: Unknown: 00064A4B52337264
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000101104700102880288028801880A8800014D1C7EDF0103C000101
                    IE: Unknown: 0505000101F104
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AFC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1605000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040072127A
                    IE: Unknown: DD1E00904C33FC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405000400000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 27 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"KidsOn12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000110d52da0e00
                    Extra: Last beacon: 1884ms ago
                    IE: Unknown: 00084B6964734F6E3132
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010C0195D086A98BFE6071C179F8061F75E1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407080000000000000000000000000000000000000000
          Cell 28 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Athena"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000061b104e3318
                    Extra: Last beacon: 2140ms ago
                    IE: Unknown: 0006417468656E61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301720320
                    IE: Unknown: DD0E0017F207000101069027E45D54C9
          Cell 29 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"mooses"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ca099162e
                    Extra: Last beacon: 18424ms ago
                    IE: Unknown: 00066D6F6F736573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001900000000000000000000000000000000000000
                    IE: Unknown: 3D160B001900000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000001C7EE53339C0103C000103
          Cell 30 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ReeseRoccoJohn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002303686c142
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 000E5265657365526F63636F4A6F686E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880C4393A0CAB78103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1609070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500006A127A
                    IE: Unknown: DD07000C4300000000
          Cell 31 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"muffin1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b8e6277d0a
                    Extra: Last beacon: 16516ms ago
                    IE: Unknown: 00076D756666696E31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001300000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010503652678902C12713DE62201FA43D4E102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180202F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409001300000000000000000000000000000000000000
          Cell 32 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Wifi4Ganstaz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001fec5e13193
                    Extra: Last beacon: 17964ms ago
                    IE: Unknown: 000C576966693447616E7374617A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000
          Cell 33 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Droo TraxX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000010943d3e0
                    Extra: Last beacon: 17832ms ago
                    IE: Unknown: 000A44726F6F205472617858
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A001900000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016C0120
          Cell 34 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002303670ed2d
                    Extra: Last beacon: 1628ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1609070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500006A127A
                    IE: Unknown: DD07000C4300000000
          Cell 35 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002303670f48f
                    Extra: Last beacon: 1628ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1609070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500006A127A
                    IE: Unknown: DD07000C4300000000
          Cell 36 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002303670fcf1
                    Extra: Last beacon: 1624ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1609070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500006A127A
                    IE: Unknown: DD07000C4300000000
          Cell 37 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"TWCWiFi"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012499654180
                    Extra: Last beacon: 3744ms ago
                    IE: Unknown: 000754574357694669
                    IE: Unknown: 01088B960C1218243048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 070655534F010D1E
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1A0C001BFFFE000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101090003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 38 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"mozheng"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000df67473204
                    Extra: Last beacon: 2428ms ago
                    IE: Unknown: 00076D6F7A68656E67
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010010
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A6E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 39 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME-2223"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000100d6fb9299
                    Extra: Last beacon: 2388ms ago
                    IE: Unknown: 0009484F4D452D32323233
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 050400010022
                    IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880001DD159AFA0103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607030000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500002B127A
                    IE: Unknown: DD07000C4303000000
          Cell 40 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004db2d6c26d
                    Extra: Last beacon: 1852ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 050400010040
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050043127A
                    IE: Unknown: DD07000C4303000000
          Cell 41 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"cshapiro"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d2d23bad7b1
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0008637368617069726F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 42 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"MJTnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000017ca0df93b33
                    Extra: Last beacon: 304ms ago
                    IE: Unknown: 00064D4A546E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010620C9D023900F
                    IE: Unknown: DD0B0017F20100010100000007


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

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DD97D617F7C24BA9D111D21
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
vermagic:       3.8.0-33-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0078E2DDCA5F8B073A36467
depends:        ath
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-33-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.2/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.954875] ath: EEPROM regdomain: 0x60
[   12.954880] ath: EEPROM indicates we should expect a direct regpair map
[   12.954886] ath: Country alpha2 being used: 00
[   12.954888] ath: Regpair used: 0x60
[   18.313952] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.317047] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.629607] wlan0: authenticate with <MAC address removed>
[   20.639068] wlan0: send auth to <MAC address removed> (try 1/3)
[   20.641056] wlan0: authenticated
[   20.644275] wlan0: associate with <MAC address removed> (try 1/3)
[   20.652724] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=39)
[   20.652771] wlan0: associated
[   20.652781] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************


```



Thanks again for helping!

Best,

Jarek

---

### Post by varunendra on 2013-12-26
Everything in the report looks pretty solid to me except the kernel version. Kernel 3.8.0-33 is a bit old for 13.04 now. The ath9k was apparently suffering some serious regressions in kernel 3.8 series but has improved quite a lot in newer kernels.

Please update your system a couple of times and see if you get some better performance with the newer driver. I am personally using 12.04 but believe the latest kernel for 13.04 is some version from 3.11 series.

Of course a newer driver will only help if the fault is at the driver's part. Does it work nicely for other networks? Are you sure the settings in Network Manager are as they should by for public networks? If unsure, I suggest deleting all the existing connections and recreate them when the newer driver is installed.

---

### Post by JarekErvin on 2014-01-03
Thanks again for the reply!

I updated to 3.8.0-34. I'm not sure if that's recent enough, but it's still not working on public networks.

It does seem fine with most networks otherwise. I'm not sure if there's a setting I've got wrong, but everything looks fine on that front to the best of my knowledge.

Cheers,

Jarek

---

### Post by JarekErvin on 2014-01-03
Oh pardon, I missed the line about the 3.11 series. I'll check out that and see if it helps.

Jarek

EDITED:

I've run a few updates, which got me up to 3.08.35. I'm writing this while using Amtrak's network, which requires a browser login. So I'm hoping the problem may be solved. I'll post something if there are still problems, but if not, thanks once more, Varun!

EDITED 2:
It's working on the original Starbucks network that gave me trouble in the first place. I'm marking this as solved!

---

