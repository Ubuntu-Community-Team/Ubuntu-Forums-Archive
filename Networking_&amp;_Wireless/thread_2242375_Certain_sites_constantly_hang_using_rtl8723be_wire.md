---
title: "Certain sites constantly hang using rtl8723be wireless card"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by jonasb2 on 2014-09-01
I have a reasonably new laptop and never got my wireless working perfectly. At first the card wasn't even detected but that got fixed with a new kernel package. Then it would completely disconnect after a while as decribed in this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070). I believe that is (mostly?) fixed with the solution in #39 in that bug report (echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf).

The problem I seem to have now is that on certain sites after a bit of clicking around they seem to hang and keep loading indefinitly long. I mostly experienced this with hotmail, facebook and google. I thought it might have something to do with them all being https sites, but I tried clicking around on launchpad which also is https, but didn't run into any problems (albeit a difference is that I am not logged in on Launchpad). So I got to thinking: it always hangs when it needs to load info that it did not load innitially and this without a complete page refresh. For example, scrolling down for extra search results in google or for older news in facebook. (While for example launchpad opens a new page (with it's own url) for every click, which works without problems.) 
* This happens using both firefox and chromium. 
* When I plug in the LAN cable, I don't seem to have the issue any more.
* When a site is hanging and trying to load, other sites still work, but a speedtest does seem to indicate lower download speeds.

```

########## wireless info START ##########

Report from: 27 Aug 2014 15:57 CEST +0200

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi_backlight=vendor, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be

##### lsusb #####

Bus 002 Device 002: ID 1058:10b8 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e71:d9ff:fede:358d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:690655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1029181214 (1.0 GB)  TX bytes:34044208 (34.0 MB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Busseniers"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC addr Busseniers>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:356   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Busseniers] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    telenet-25FD6:   Infra, <MAC addr telenet-25FD6>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    telenet-8CCA9:   Infra, <MAC addr telenet-8CCA9>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    telenet-6E468:   Infra, <MAC addr telenet-6E468>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    bbox2-82e9:      Infra, <MAC addr bbox2-82e9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Snow:            Infra, <MAC addr Snow>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    telenet-8C762:   Infra, <MAC addr telenet-8C762>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    bbox2-e10c:      Infra, <MAC addr bbox2-e10c>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WEP
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    FON_BELGACOM:    Infra, <MAC addr FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    *Busseniers:     Infra, <MAC addr Busseniers>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    FON_BELGACOM:    Infra, <MAC addr FON_BELGACOM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54
    telenet-86DCF:   Infra, <MAC addr telenet-86DCF>, Freq 2442 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    bbox2-1204:      Infra, <MAC addr bbox2-1204>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WEP
    FON_BELGACOM:    Infra, <MAC addr FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

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

##### iw reg get #####

country BE:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #####

Channel occupancy:

     10   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)
     4   WLAPs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Busseniers>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Busseniers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002f1cf75d
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000aa00a33636
                    Extra: Last beacon: 64ms ago
          Cell 03 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000532dc854bf
                    Extra: Last beacon: 64ms ago
          Cell 04 - Address: <MAC addr FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003d488b977
                    Extra: Last beacon: 64ms ago
          Cell 05 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"telenet-42681"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000aa00dfc173
                    Extra: Last beacon: 292ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr Snow>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-8 dBm  
                    Encryption key:on
                    ESSID:"Snow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e0d71ee8a
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC addr telenet-25FD6>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"telenet-25FD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000532dc844db
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr bbox2-1204>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-8 dBm  
                    Encryption key:on
                    ESSID:"bbox2-1204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003d48960a1
                    Extra: Last beacon: 64ms ago
          Cell 09 - Address: <MAC addr bbox2-e10c>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"bbox2-e10c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000899a07f052
                    Extra: Last beacon: 64ms ago
          Cell 10 - Address: <MAC addr FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000899a073d86
                    Extra: Last beacon: 64ms ago
          Cell 11 - Address: <MAC addr FON_BELGACOM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000182373ef5c0
                    Extra: Last beacon: 64ms ago
          Cell 12 - Address: <MAC addr bbox2-82e9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"bbox2-82e9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000182373e2601
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC addr telenet-86DCF>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"telenet-86DCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000083d2c49ac41
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC addr telenet-8CCA9>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"telenet-8CCA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000449f7b2d4
                    Extra: Last beacon: 472ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC addr telenet-6E468>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"telenet-6E468"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000448664de1
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000448665dce
                    Extra: Last beacon: 64ms ago
          Cell 17 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000449f838bb
                    Extra: Last beacon: 64ms ago

##### module infos #####

[rtl8723be]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

##### module parameters #####

[rtl8723be]
debug: 0
fwlps: N
ips: Y
msi: N
swenc: N
swlps: N

##### /etc/modules #####

lp
rtc

##### blacklists #####

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

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    3.001046] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x461f00)
[    3.701141] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    4.343640] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.343976] rtlwifi: wireless switch is on
[    6.830890] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    8.574170] wlan0: authenticate with <MAC addr Busseniers>
[    8.588560] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[    8.590697] wlan0: authenticated
[    8.590941] rtl8723be 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[    8.592243] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[    8.594923] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=2)
[    8.595025] wlan0: associated
[    8.595068] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    8.634363] wlan0: deauthenticating from <MAC addr Busseniers> by local choice (reason=2)
[    8.656576] wlan0: authenticate with <MAC addr Busseniers>
[    8.656706] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[    8.661858] wlan0: authenticated
[    8.662265] rtl8723be 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[    8.664529] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[    8.667395] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=2)
[    8.667492] wlan0: associated
[ 1159.649536] wlan0: Connection to AP <MAC addr Busseniers> lost
[ 1174.754171] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1179.896150] wlan0: authenticate with <MAC addr Busseniers>
[ 1179.896293] wlan0: direct probe to <MAC addr Busseniers> (try 1/3)
[ 1180.098833] wlan0: direct probe to <MAC addr Busseniers> (try 2/3)
[ 1180.303026] wlan0: direct probe to <MAC addr Busseniers> (try 3/3)
[ 1180.507002] wlan0: authentication with <MAC addr Busseniers> timed out
[ 1182.325148] wlan0: authenticate with <MAC addr Busseniers>
[ 1182.335038] wlan0: direct probe to <MAC addr Busseniers> (try 1/3)
[ 1182.537162] wlan0: send auth to <MAC addr Busseniers> (try 2/3)
[ 1183.337321] wlan0: send auth to <MAC addr Busseniers> (try 3/3)
[ 1184.350316] wlan0: authentication with <MAC addr Busseniers> timed out
[ 1186.669750] wlan0: authenticate with <MAC addr Busseniers>
[ 1186.678894] wlan0: direct probe to <MAC addr Busseniers> (try 1/3)
[ 1186.880283] wlan0: send auth to <MAC addr Busseniers> (try 2/3)
[ 1188.329405] wlan0: send auth to <MAC addr Busseniers> (try 3/3)
[ 1189.330326] wlan0: authentication with <MAC addr Busseniers> timed out
[ 1201.986003] wlan0: authenticate with <MAC addr Busseniers>
[ 1201.995134] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[ 1201.999206] wlan0: authenticated
[ 1201.999722] rtl8723be 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1202.000452] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[ 1202.004381] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=2)
[ 1202.004511] wlan0: associated
[ 1202.004636] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1234.956053] wlan0: deauthenticating from <MAC addr Busseniers> by local choice (reason=3)
[ 1237.575004] Modules linked in: nls_utf8 isofs rfcomm bnep snd_hda_codec_hdmi snd_hda_codec_via uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev arc4 rtsx_pci_ms memstick joydev btusb bluetooth snd_hda_intel snd_hda_codec snd_hwdep intel_rapl coretemp snd_pcm kvm_intel kvm rtl8723be crct10dif_pclmul crc32_pclmul snd_page_alloc ghash_clmulni_intel btcoexist cryptd snd_seq_midi snd_seq_midi_event rtl8723_common snd_rawmidi rtl_pci rtlwifi mac80211 snd_seq serio_raw snd_seq_device cfg80211 snd_timer snd soundcore wmi mac_hid i915 video drm_kms_helper drm parport_pc i2c_algo_bit ppdev lp parport usb_storage rtsx_pci_sdmmc psmouse rtsx_pci r8169 ahci mii libahci (repeated 3 times)
[ 1237.745076] rtlwifi: wireless switch is on
[ 1241.450852] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1243.175653] wlan0: authenticate with <MAC addr Busseniers>
[ 1243.182522] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[ 1243.184853] wlan0: authenticated
[ 1243.185169] rtl8723be 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1243.187956] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[ 1243.190711] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=2)
[ 1243.190810] wlan0: associated
[ 1243.190825] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1243.223600] wlan0: deauthenticating from <MAC addr Busseniers> by local choice (reason=2)
[ 1243.245125] wlan0: authenticate with <MAC addr Busseniers>
[ 1243.245420] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[ 1243.247669] wlan0: authenticated
[ 1243.248320] rtl8723be 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1243.252031] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[ 1243.256000] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=2)
[ 1243.256108] wlan0: associated

########## wireless info END ############
```

I should also mention I'm pretty new to linux so maybe it's something stupid or simple and make sure to ask for extra infoof needed. 
I hope somebody can help me! Thanks!

---

### Post by Hadaka on 2014-09-01
Hi, your wireless report shows this,,
```
rtl8723be 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
```
Please change your router setting to wpa2 aes from tkip and also set your encryption
to something other than wep. your slow downs are likely caused by 1/2 your neighborhood
using your wireless connection as having wep is pretty much an advertizement saying,,,
FREE WIFI help yourself.

---

### Post by jonasb2 on 2014-09-01
Thank you! It didn't fix the issue, but I should be a bit more secure now :). And it may have done something, facebook seems to hang less and be more fluent. Or I may imagine that :p. Considering that it is only with specific sites, that I don't have issues on other (windows) computers or using wired internet and that I have nice neighbours, getting my bandwidth stolen couldn't really have been it.

What do sites like outlook/hotmail and facebook have in common? The thingy that makes them fancy enough to let you surf without changing url: is that javascript or what is it called? 
When I try to open an email in hotmail, it sometimes works in like 1 sec, like it should, but way too often it tries and tries and tries and then after 1 minute or so it gives an error "could not connect to outlook". During one such attempt I had it make a new wireless script output:

```

########## wireless info START ##########

Report from: 01 Sep 2014 22:43 CEST +0200

Script from: 30 Aug 2014 19:00 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi_backlight=vendor, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e71:d9ff:fede:358d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9966435 (9.9 MB)  TX bytes:5203573 (5.2 MB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Busseniers"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC addr Busseniers>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:309   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Busseniers] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    telenet-6E468:   Infra, <MAC addr telenet-6E468>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    bbox2-82e9:      Infra, <MAC addr bbox2-82e9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    telenet-8CCA9:   Infra, <MAC addr telenet-8CCA9>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    bbox2-e10c:      Infra, <MAC addr bbox2-e10c>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WEP
    bbox2-1204:      Infra, <MAC addr bbox2-1204>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WEP
    FON_BELGACOM:    Infra, <MAC addr FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 16
    FON_BELGACOM:    Infra, <MAC addr FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87
    FON_BELGACOM:    Infra, <MAC addr FON_BELGACOM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    *Busseniers:     Infra, <MAC addr Busseniers>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    telenet-25FD6:   Infra, <MAC addr telenet-25FD6>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    telenet-42681:   Infra, <MAC addr telenet-42681>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    TELENETHOMESPOT: Infra, <MAC addr TELENETHOMESPOT>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    telenet-86DCF:   Infra, <MAC addr telenet-86DCF>, Freq 2442 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Snow:            Infra, <MAC addr Snow>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

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

##### iw reg get #####

country BE:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #####

Channel occupancy:

     10   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)
     4   WLAPs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Busseniers>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Busseniers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e917062e
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006e8f46e6
                    Extra: Last beacon: 8ms ago
          Cell 03 - Address: <MAC addr telenet-42681>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"telenet-42681"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011440de3173
                    Extra: Last beacon: 3520ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr bbox2-1204>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"bbox2-1204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006e8fe093
                    Extra: Last beacon: 8ms ago
          Cell 05 - Address: <MAC addr telenet-25FD6>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"telenet-25FD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bd6e308173
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr bbox2-e10c>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"bbox2-e10c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000070d9990e0
                    Extra: Last beacon: 8ms ago
          Cell 07 - Address: <MAC addr FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000070d991f18
                    Extra: Last beacon: 8ms ago
          Cell 08 - Address: <MAC addr Snow>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Snow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005284427752
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bd6e2d6351
                    Extra: Last beacon: 240ms ago
          Cell 10 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011440dca173
                    Extra: Last beacon: 3572ms ago
          Cell 11 - Address: <MAC addr bbox2-82e9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"bbox2-82e9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ec77959361
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC addr FON_BELGACOM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ec77966394
                    Extra: Last beacon: 8ms ago
          Cell 13 - Address: <MAC addr telenet-86DCF>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"telenet-86DCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008a76c49738f
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC addr telenet-8CCA9>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-14 dBm  
                    Encryption key:on
                    ESSID:"telenet-8CCA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e89ebc8bd
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-12 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e89f04fbc
                    Extra: Last beacon: 8ms ago
          Cell 16 - Address: <MAC addr TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e8893f016
                    Extra: Last beacon: 8ms ago
          Cell 17 - Address: <MAC addr telenet-6E468>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-12 dBm  
                    Encryption key:on
                    ESSID:"telenet-6E468"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e8893e033
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

##### module parameters #####

[rtl8723be]
debug: 0
fwlps: N
ips: Y
msi: N
swenc: N
swlps: N

##### /etc/modules #####

lp
rtc

##### blacklists #####

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

##### rc.local #####

rfkill block bluetooth
exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    3.007370] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x461f00)
[    4.829758] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    4.855603] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.855922] rtlwifi: wireless switch is on
[    7.375500] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    9.097543] wlan0: authenticate with <MAC addr Busseniers>
[    9.108450] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[    9.116470] wlan0: authenticated
[    9.120503] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[    9.123425] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=1)
[    9.123528] wlan0: associated
[    9.124193] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    9.256539] wlan0: deauthenticating from <MAC addr Busseniers> by local choice (reason=2)
[    9.281209] wlan0: authenticate with <MAC addr Busseniers>
[    9.281329] wlan0: send auth to <MAC addr Busseniers> (try 1/3)
[    9.285575] wlan0: authenticated
[    9.288617] wlan0: associate with <MAC addr Busseniers> (try 1/3)
[    9.291305] wlan0: RX AssocResp from <MAC addr Busseniers> (capab=0x431 status=0 aid=1)
[    9.291403] wlan0: associated

########## wireless info END ############
```

---

### Post by jonasb2 on 2014-09-03
No more ideas? This makes my laptop nearly unusable...

---

### Post by jonasb2 on 2014-09-11
I'm afraid my issue still hasn't been solved... Any ideas on how I can detect what's happening?

---

### Post by varunendra on 2014-09-14
Please try what is suggested here : [http://ubuntuforums.org/showpost.php?p=13119513](http://ubuntuforums.org/showpost.php?p=13119513)

I'm quite hopeful with "ips=N" parameter, but I'm still just testing it with this particular driver. Seems to have solved at least one case above.

---

### Post by jonasb2 on 2014-09-15
> **varunendra said:**
> Please try what is suggested here : [http://ubuntuforums.org/showpost.php?p=13119513](http://ubuntuforums.org/showpost.php?p=13119513)

I'm quite hopeful with "ips=N" parameter, but I'm still just testing it with this particular driver. Seems to have solved at least one case above.

Thank you,but still not fixed :(. Other people seem to be disconnecting completely (which I also had but fixed with the fwlps=0 parameter, but I seem to disconnect only from certain sites, while the rest keeps working.
I'm considering switching to linux mint, but don't really have high hopes of that being a fix either...

---

### Post by varunendra on 2014-09-16
If the problem is in the driver, switching to mint won't help, as both Ubuntu and Mint use the same kernel versions, means same drivers and settings. In fact, no other distro will help in that case unless it uses the latest kernel (which you can also install on Ubuntu manually).

For now, I think you should post a fresh wireless_script report showing the current settings. I personally prefer this one : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by jonasb2 on 2014-09-16
> **varunendra said:**
> If the problem is in the driver, switching to mint won't help, as both Ubuntu and Mint use the same kernel versions, means same drivers and settings. In fact, no other distro will help in that case unless it uses the latest kernel (which you can also install on Ubuntu manually).
Yeah, I was afraid it would be like that...

> **varunendra said:**
> For now, I think you should post a fresh wireless_script report showing the current settings. I personally prefer this one : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Laptop-Jonas 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7865 MB
Uptime : 14:38:09 up 17 min,  2 users,  load average: 0,80, 0,48, 0,32


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Busseniers"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Busseniers>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=10/70  Signal level=-100 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         yes           no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (6): debug=0 | fwlps=N | ips=N | msi=N | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [Busseniers] | 802.11 WiFi | rtl8723be | connected   | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    telenet-25FD6:   Infra, <MAC C-06 telenet-25FD6>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    bbox2-82e9:      Infra, <MAC C-09 bbox2-82e9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    telenet-8CCA9:   Infra, <MAC C-15 telenet-8CCA9>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Snow:            Infra, <MAC C-03 Snow>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    telenet-6E468:   Infra, <MAC C-13 telenet-6E468>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    bbox2-e10c:      Infra, <MAC C-02 bbox2-e10c>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    TELENETHOMESPOT: Infra, <MAC C-12 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    FON_BELGACOM:    Infra, <MAC C-08 FON_BELGACOM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    TELENETHOMESPOT: Infra, <MAC C-14 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    TELENETHOMESPOT: Infra, <MAC C-NA TELENETHOMESPOT 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    TELENETHOMESPOT: Infra, <MAC C-05 TELENETHOMESPOT>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    FON_BELGACOM:    Infra, <MAC C-04 FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    *Busseniers:     Infra, <MAC C-01 Busseniers>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    telenet-86DCF:   Infra, <MAC C-10 telenet-86DCF>, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    bbox2-1204:      Infra, <MAC C-07 bbox2-1204>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
    FON_BELGACOM:    Infra, <MAC C-11 FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    telenet-42681:   Infra, <MAC C-17 telenet-42681>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    FON_BELGACOM:    Infra, <MAC C-NA FON_BELGACOM 3>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77

    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
---------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Busseniers           : ssid=Busseniers | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.631/1.824/2.017/0.193 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.033/0.036/0.039/0.003 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_BE.UTF-8)
country BE:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Busseniers>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"Busseniers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007653639271
                    Extra: Last beacon: 116ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 bbox2-e10c>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"bbox2-e10c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009ec619b01a
                    Extra: Last beacon: 184ms ago
          Cell 03 - Address: <MAC C-03 Snow>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Snow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001797d1a4c1f
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009ec618fee6
                    Extra: Last beacon: 232ms ago
          Cell 05 - Address: <MAC C-05 TELENETHOMESPOT>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009bdf152d51
                    Extra: Last beacon: 2100ms ago
          Cell 06 - Address: <MAC C-06 telenet-25FD6>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"telenet-25FD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009bdf151d64
                    Extra: Last beacon: 2104ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 bbox2-1204>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"bbox2-1204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005383c66a7
                    Extra: Last beacon: 768ms ago
          Cell 08 - Address: <MAC C-08 FON_BELGACOM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000313706047cb
                    Extra: Last beacon: 2436ms ago
          Cell 09 - Address: <MAC C-09 bbox2-82e9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"bbox2-82e9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000313705f77e0
                    Extra: Last beacon: 2096ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 telenet-86DCF>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"telenet-86DCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009ce642fd176
                    Extra: Last beacon: 2136ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005383d9220
                    Extra: Last beacon: 512ms ago
          Cell 12 - Address: <MAC C-12 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009c2e7dc41b
                    Extra: Last beacon: 24ms ago
          Cell 13 - Address: <MAC C-13 telenet-6E468>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"telenet-6E468"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000530e0dfec2
                    Extra: Last beacon: 16ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000530ce745de
                    Extra: Last beacon: 18332ms ago
          Cell 15 - Address: <MAC C-15 telenet-8CCA9>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"telenet-8CCA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009c2e7dac3d
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 telenet-8C762>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"telenet-8C762"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009c256f3ff4
                    Extra: Last beacon: 1088ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 telenet-42681>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"telenet-42681"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009c2c7b22f3
                    Extra: Last beacon: 1088ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)

[btcoexist]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     3CC61E00E2CEF446293F879
depends:        

[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        

[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
rfkill block bluetooth
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rtl8723be.conf    : options rtl8723be fwlps=N ips=N


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=032b92cb-bfb1-49bf-907c-e5e503b15992 ro quiet splash acpi_backlight=vendor vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.954634] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.955170] audit: initializing netlink socket (disabled)
[    2.153172] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.006717] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x461f00)
[    3.712973] wmi: Mapper loaded
[    3.882801] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    4.084067] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.084385] rtlwifi: wireless switch is on
[    5.764355] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.950236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.950899] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.674798] wlan0: authenticate with <MAC C-01 Busseniers>
[    8.677442] wlan0: send auth to <MAC C-01 Busseniers> (try 1/3)
[    8.681940] wlan0: authenticated
[    8.684316] wlan0: associate with <MAC C-01 Busseniers> (try 1/3)
[    8.689246] wlan0: RX AssocResp from <MAC C-01 Busseniers> (capab=0x431 status=0 aid=2)
[    8.689353] wlan0: associated
[    8.689401] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    8.807091] wlan0: deauthenticating from <MAC C-01 Busseniers> by local choice (reason=2)
[    8.828180] wlan0: authenticate with <MAC C-01 Busseniers>
[    8.828309] wlan0: send auth to <MAC C-01 Busseniers> (try 1/3)
[    8.831019] wlan0: authenticated
[    8.835794] wlan0: associate with <MAC C-01 Busseniers> (try 1/3)
[    8.840081] wlan0: RX AssocResp from <MAC C-01 Busseniers> (capab=0x431 status=0 aid=2)
[    8.840180] wlan0: associated

    ======== Done ========
```

---

### Post by varunendra on 2014-09-16
> **jonasb2 said:**
> ```

wlan0     IEEE 802.11bgn  ESSID:"Busseniers"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Busseniers>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          **Link Quality=[COLOR="#FF0000"]10/70[/COLOR]**  Signal level=-100 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0
....
....
iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Busseniers>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    **[COLOR="#006400"]Quality=70/70[/COLOR]**  Signal level=-16 dBm  
                    Encryption key:on
```
Which one of the above is true :confused:
Is the signal strength fluctuating? If not, how good it generally is?

I just yesterday got my hands over a laptop with this same card (or at least the driver), and it didn't have any fluctuating issues. If the signal strength is actually good, I think we can only try either another driver parameter, or a newer driver from backports.

---

### Post by jonasb2 on 2014-09-17
Did some tests and kept bit of an eye on it. It seems  to mostly work 100% (70/70), but does regularly have a short drop to around 30/70 or even around 10/70. Think this is an issue? As far as I can see it's not behaving differently when it is hanging: most of the time it stays on full signal strength. There also is no such issue on the other laptop (windows 7) or smartphone (android): they neither hang nor fluctuate (for so far I see, but it might be too short to be displayed).
I do believe it is the driver, to me it feels the signal strength is at most a small and separate issue (but I'm a newb :p).
I noticed that when hotmail is hanging, it's hard to kick it back in action: opening it in a different browser or tab, closing the tab and I believe even closing the browser typically don't solve it. But it does start working again when some time has gone over it. Rebooting the driver always seems to fix it instantly ("sudo rmmod rtl8723be && sudo modprobe rtl8723be" is what I mean with rebooting the driver).
So I guess we should play with parameters a bit? Do I just try out parameter settings until it works? If so can you give me some tips?
And I don't say this enough: thanks for your efforts already!

---

### Post by varunendra on 2014-09-17
Before trying the driver parameter, please try two more things -

1) Set "IPv6" to "Ignore" in Network Manager.
2) Try changing the default DNS to a faster or better tested one, for example, Google's 8.8.8.8. To make this change (assuming your current setting is to use DHCP for IP assignment), select "Method" to "Automatic (DHCP) address only" under "IPv4 Settings" tab in Network Manager. Then in the "DNS Servers" field, type : **8.8.8.8, 8.8.4.4** > Save > Close > reconnect.

Confirm the DNS change with the output of -
```
nm-tool
```
It should now show "8.8.8.8" and "8.8.4.4" in front of "DNS :", instead of current "192.168.1.1".

If these two changes don't seem to help, try the driver parameter "swenc=Y" with -
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be **swenc=Y**
```
The other two parameters will load automatically from the conf file. If this seems to help, we can add this one to the conf file too to make it permanent.

Some current drivers seem to cause problem (e.g. "iwlwifi") if reloaded on a running system. But you said it is working fine for you (what you call "driver reboot"). So there shouldn't be a problem, but let me know if reloading with this parameter suggested above causes any problems. I would like to test it in permanent mode then, at least once before considering it worthless.

Oh, and if none of the above helps, please run the script again and post back a fresh report while the above changes are applied.

---

### Post by jonasb2 on 2014-09-17
The first 2 suggestions didn't do anything. Stuff actually felt to be slower (but possibly imagination). With these changes and without changing parameters, I already had it happen once that it failed to reload the driver, something I never had happen before.
I then applied the parameter, but that broke stuff completely: no connection is being re-established: sometimes it's trying to connect, sometimes not even that. And all signs of a driver seemed to be gone (if you click on the internet-thingy at the top-right it didn't show anything wifi-related any more). I tried to do my 'reboot driver' thingy, but that didn't help, I suppose the parameter was still being applied? Here is the script-output of when things were broken:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Laptop-Jonas 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7865 MB
Uptime : 21:32:39 up 4 min,  2 users,  load average: 0,39, 0,37, 0,18


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         yes           no
7: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (6): debug=0 | fwlps=N | ips=N | msi=N | swenc=Y | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | rtl8723be | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    telenet-6E468:   Infra, <MAC C-08 telenet-6E468>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    telenet-8CCA9:   Infra, <MAC C-09 telenet-8CCA9>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    telenet-8C762:   Infra, <MAC C-15 telenet-8C762>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    telenet-25FD6:   Infra, <MAC C-06 telenet-25FD6>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    bbox2-82e9:      Infra, <MAC C-13 bbox2-82e9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    telenet-86DCF:   Infra, <MAC C-07 telenet-86DCF>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Snow:            Infra, <MAC C-01 Snow>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    bbox2-e10c:      Infra, <MAC C-03 bbox2-e10c>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP
    TELENETHOMESPOT: Infra, <MAC C-11 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    FON_BELGACOM:    Infra, <MAC C-04 FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    FON_BELGACOM:    Infra, <MAC C-14 FON_BELGACOM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    TELENETHOMESPOT: Infra, <MAC C-05 TELENETHOMESPOT>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    TELENETHOMESPOT: Infra, <MAC C-10 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    telenet-42681:   Infra, <MAC C-NA telenet-42681 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    bbox2-1204:      Infra, <MAC C-NA bbox2-1204 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
    TELENETHOMESPOT: Infra, <MAC C-12 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    TELENETHOMESPOT: Infra, <MAC C-NA TELENETHOMESPOT 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    FON_BELGACOM:    Infra, <MAC C-NA FON_BELGACOM 3>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    telenet-C0CC9:   Infra, <MAC C-NA telenet-C0CC9 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Busseniers:      Infra, <MAC C-02 Busseniers>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169     | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Busseniers           : ssid=Busseniers | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_BE.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Snow>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Snow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019364a4ded4
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Busseniers>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Busseniers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000903a9e4f07
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 bbox2-e10c>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"bbox2-e10c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8abda6b1c
                    Extra: Last beacon: 12ms ago
          Cell 04 - Address: <MAC C-04 FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8abd9b74e
                    Extra: Last beacon: 12ms ago
          Cell 05 - Address: <MAC C-05 TELENETHOMESPOT>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5c3914c08
                    Extra: Last beacon: 480ms ago
          Cell 06 - Address: <MAC C-06 telenet-25FD6>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"telenet-25FD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5c677fb3e
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 telenet-86DCF>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"telenet-86DCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009e848a27757
                    Extra: Last beacon: 24048ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 telenet-6E468>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"telenet-6E468"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cf55c25b8
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 telenet-8CCA9>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"telenet-8CCA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b615bac8a9
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b615bbf7d8
                    Extra: Last beacon: 12ms ago
          Cell 11 - Address: <MAC C-11 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cf55df5cc
                    Extra: Last beacon: 12ms ago
          Cell 12 - Address: <MAC C-12 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-10 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b60b52a751
                    Extra: Last beacon: 23612ms ago
          Cell 13 - Address: <MAC C-13 bbox2-82e9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"bbox2-82e9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000032d57d00662
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 FON_BELGACOM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000032d57d0d65f
                    Extra: Last beacon: 12ms ago
          Cell 15 - Address: <MAC C-15 telenet-8C762>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"telenet-8C762"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b60cbaf173
                    Extra: Last beacon: 212ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)

[btcoexist]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     3CC61E00E2CEF446293F879
depends:        

[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        

[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
rfkill block bluetooth
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rtl8723be.conf    : options rtl8723be fwlps=N ips=N


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=032b92cb-bfb1-49bf-907c-e5e503b15992 ro quiet splash acpi_backlight=vendor vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.966969] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.967505] audit: initializing netlink socket (disabled)
[    2.155512] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.020079] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x461f00)
[    3.634070] wmi: Mapper loaded
[    3.963809] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    4.263379] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.263690] rtlwifi: wireless switch is on
[    5.593541] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.858970] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.859953] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.586849] wlan0: authenticate with <MAC C-02 Busseniers>
[    8.587160] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[    8.589407] wlan0: authenticated
[    8.594539] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[    8.597236] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[    8.597343] wlan0: associated
[    8.597385] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    8.744761] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=2)
[    8.768266] wlan0: authenticate with <MAC C-02 Busseniers>
[    8.768395] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[    8.771514] wlan0: authenticated
[    8.776114] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[    8.779894] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[    8.780010] wlan0: associated
[   39.887612] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[   40.052638] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   40.052912] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[   40.053213] rtlwifi: wireless switch is on
[   40.536370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.536402] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.592608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.594796] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.552491] wlan0: authenticate with <MAC C-02 Busseniers>
[   41.552624] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[   41.556269] wlan0: authenticated
[   41.557664] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[   41.563315] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[   41.563416] wlan0: associated
[   41.563455] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.889892] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[   63.010805] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   63.011075] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[   63.011373] rtlwifi: wireless switch is on
[   63.498733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.498769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.551390] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.554532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   65.321828] wlan0: authenticate with <MAC C-02 Busseniers>
[   65.331495] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[   65.333772] wlan0: authenticated
[   65.336862] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[   65.340855] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[   65.340951] wlan0: associated
[   65.340990] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.359202] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=2)
[   65.385406] wlan0: authenticate with <MAC C-02 Busseniers>
[   65.385527] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[   65.389329] wlan0: authenticated
[   65.392915] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[   65.396408] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[   65.396500] wlan0: associated
[   78.145927] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[   78.287471] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   78.288212] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[   78.289086] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.289178] rtlwifi: wireless switch is on
[   78.407899] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.485591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   78.488663] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  108.021547] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[  108.023400] ieee80211 phy4: Selected rate control algorithm 'rtl_rc'
[  108.023961] rtlwifi: wireless switch is on
[  108.515296] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  108.516364] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  109.468496] wlan0: authenticate with <MAC C-02 Busseniers>
[  109.468626] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  109.474183] wlan0: authenticated
[  109.475200] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[  109.478945] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[  109.479058] wlan0: associated
[  109.479107] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  124.959393] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  125.101628] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[  125.102270] ieee80211 phy5: Selected rate control algorithm 'rtl_rc'
[  125.102682] rtlwifi: wireless switch is on
[  125.222564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.313556] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.802227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.802724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  126.768983] wlan0: authenticate with <MAC C-02 Busseniers>
[  126.769119] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  126.771391] wlan0: authenticated
[  126.773528] wlan0: associate with <MAC C-02 Busseniers> (try 1/3)
[  126.780077] wlan0: RX AssocResp from <MAC C-02 Busseniers> (capab=0x431 status=0 aid=1)
[  126.780179] wlan0: associated
[  126.780220] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  135.269040] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  143.381540] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[  143.381797] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  143.382100] rtlwifi: wireless switch is on
[  143.875124] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  143.875718] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  154.000232] wlan0: authenticate with <MAC C-02 Busseniers>
[  154.000374] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  154.002750] wlan0: authenticated
[  159.020889] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  169.138611] wlan0: authenticate with <MAC C-02 Busseniers>
[  169.138757] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  169.141010] wlan0: authenticated
[  174.145740] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  184.664832] wlan0: authenticate with <MAC C-02 Busseniers>
[  184.665083] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  184.667377] wlan0: authenticated
[  189.677454] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  200.702199] wlan0: authenticate with <MAC C-02 Busseniers>
[  200.702409] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  200.704020] wlan0: authenticated
[  205.710989] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  217.286840] wlan0: authenticate with <MAC C-02 Busseniers>
[  217.286984] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  217.289811] wlan0: authenticated
[  222.298942] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)
[  242.336934] wlan0: authenticate with <MAC C-02 Busseniers>
[  242.337311] wlan0: send auth to <MAC C-02 Busseniers> (try 1/3)
[  242.339606] wlan0: authenticated
[  247.347526] wlan0: deauthenticating from <MAC C-02 Busseniers> by local choice (reason=3)

    ======== Done ========
```
And in attachement is a current script output (so without new parameter since I rebooted)
[ATTACH]256498[/ATTACH]

---

### Post by varunendra on 2014-09-17
```

module parameters ~~~~~~~~~~~~~~~~~~
....
rtl8723be     (6): debug=0 | fwlps=N | ips=N | msi=N | **[COLOR="#0000FF"]swenc=N[/COLOR]** | swlps=N
....
```

Didn't take a thorough look at the report (in a hurry), but parameter "swenc=Y" wasn't applied anymore after the second driver reload, as highlighted above.

Suspecting the driver/networking crash due to reload could be a result of one of the recent kernel developments, please try it in permanent mode by adding it to the conf file -
```
sudo sed -i 's/^options.*/& swenc=Y/' /etc/modprobe.d/rtl8723be.conf
```
Reboot and check connectivity. If the problem gets worse, remove it with -
```
sudo sed -i 's/ swenc=y//' /etc/modprobe.d/rtl8723be.conf
```

Let us see if it could hit the jackpot.

---

### Post by jonasb2 on 2014-09-18
> **varunendra said:**
> Didn't take a thorough look at the report (in a hurry), but parameter "swenc=Y" wasn't applied anymore after the second driver reload, as highlighted above.
Yeah, I rebooted the pc for the second script-output (in attachment) so that is to be expected, I just added it in case you'd want to see the effect of the DNS changes with working internet. In the first output (the one in code tags), the "swenc=Y" parameter is showing.
> **varunendra said:**
> Let us see if it could hit the jackpot.
Nope :( but thanks for the effort again! Internet is working now though with the parameter in effect. But hotmail/outlook (what I always use to test) still hangs after opening a bunch of mails. Here is the new report:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Laptop-Jonas 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7865 MB
Uptime : 14:52:38 up 5 min,  2 users,  load average: 0,66, 0,46, 0,21


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Busseniers"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Busseniers>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         yes           no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (6): debug=0 | fwlps=N | ips=N | msi=N | swenc=Y | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [Busseniers] | 802.11 WiFi | rtl8723be | connected   | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    telenet-6E468:   Infra, <MAC C-10 telenet-6E468>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    telenet-8CCA9:   Infra, <MAC C-16 telenet-8CCA9>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    telenet-25FD6:   Infra, <MAC C-06 telenet-25FD6>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    telenet-42681:   Infra, <MAC C-14 telenet-42681>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Snow:            Infra, <MAC C-02 Snow>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    bbox2-82e9:      Infra, <MAC C-08 bbox2-82e9>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    bbox2-e10c:      Infra, <MAC C-03 bbox2-e10c>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
    TELENETHOMESPOT: Infra, <MAC C-11 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    TELENETHOMESPOT: Infra, <MAC C-12 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    TELENETHOMESPOT: Infra, <MAC C-07 TELENETHOMESPOT>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54
    TELENETHOMESPOT: Infra, <MAC C-15 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    FON_BELGACOM:    Infra, <MAC C-09 FON_BELGACOM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    FON_BELGACOM:    Infra, <MAC C-04 FON_BELGACOM>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    *Busseniers:     Infra, <MAC C-01 Busseniers>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    telenet-86DCF:   Infra, <MAC C-18 telenet-86DCF>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    telenet-8C762:   Infra, <MAC C-13 telenet-8C762>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    bbox2-1204:      Infra, <MAC C-05 bbox2-1204>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP
    FON_BELGACOM:    Infra, <MAC C-NA FON_BELGACOM 3>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    TELENETHOMESPOT: Infra, <MAC C-17 TELENETHOMESPOT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34

    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
---------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Busseniers           : ssid=Busseniers | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.393/2.403/2.413/0.010 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.038/0.061/0.085/0.024 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_BE.UTF-8)
country BE:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Busseniers>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-8 dBm  
                    Encryption key:on
                    ESSID:"Busseniers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009ec262f690
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Snow>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Snow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a1ec5a9fee
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 bbox2-e10c>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"bbox2-e10c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c7329108e0
                    Extra: Last beacon: 72ms ago
          Cell 04 - Address: <MAC C-04 FON_BELGACOM>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c732904e20
                    Extra: Last beacon: 72ms ago
          Cell 05 - Address: <MAC C-05 bbox2-1204>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"bbox2-1204"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002da5aabc93
                    Extra: Last beacon: 27652ms ago
          Cell 06 - Address: <MAC C-06 telenet-25FD6>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"telenet-25FD6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c44e41ae1e
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 TELENETHOMESPOT>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c44e47da5e
                    Extra: Last beacon: 72ms ago
          Cell 08 - Address: <MAC C-08 bbox2-82e9>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"bbox2-82e9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033bddf616f7
                    Extra: Last beacon: 3268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 FON_BELGACOM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000033bddf6e729
                    Extra: Last beacon: 27652ms ago
          Cell 10 - Address: <MAC C-10 telenet-6E468>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"telenet-6E468"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007b7b9c5712
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007b7d40f3d6
                    Extra: Last beacon: 72ms ago
          Cell 12 - Address: <MAC C-12 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c49d985c92
                    Extra: Last beacon: 72ms ago
          Cell 13 - Address: <MAC C-13 telenet-8C762>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"telenet-8C762"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c4948f8173
                    Extra: Last beacon: 832ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 telenet-42681>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"telenet-42681"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c49babd4dd
                    Extra: Last beacon: 812ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c49a07b317
                    Extra: Last beacon: 456ms ago
          Cell 16 - Address: <MAC C-16 telenet-8CCA9>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"telenet-8CCA9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c49d93e864
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 TELENETHOMESPOT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c494943173
                    Extra: Last beacon: 476ms ago
          Cell 18 - Address: <MAC C-18 telenet-86DCF>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-4 dBm  
                    Encryption key:on
                    ESSID:"telenet-86DCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009f6d34be039
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)

[btcoexist]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     3CC61E00E2CEF446293F879
depends:        

[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        

[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
rfkill block bluetooth
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rtl8723be.conf    : options rtl8723be fwlps=N ips=N swenc=Y


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=032b92cb-bfb1-49bf-907c-e5e503b15992 ro quiet splash acpi_backlight=vendor vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.966941] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.967475] audit: initializing netlink socket (disabled)
[    2.161529] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.039516] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x461f00)
[    4.041359] wmi: Mapper loaded
[    4.179930] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    4.228481] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.228829] rtlwifi: wireless switch is on
[    6.057561] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.138227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.138796] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.046079] wlan0: authenticate with <MAC C-01 Busseniers>
[    8.046214] wlan0: send auth to <MAC C-01 Busseniers> (try 1/3)
[    8.048336] wlan0: authenticated
[    8.051518] wlan0: associate with <MAC C-01 Busseniers> (try 1/3)
[    8.055738] wlan0: RX AssocResp from <MAC C-01 Busseniers> (capab=0x431 status=0 aid=1)
[    8.055834] wlan0: associated
[    8.055847] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

### Post by varunendra on 2014-09-19
> **jonasb2 said:**
> ```

iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Busseniers"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Busseniers>   
          **[COLOR="#B22222"]Bit Rate=18 Mb/s[/COLOR]**   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0
```

As highlighted above, your connection speed seems to be fixed at 18 Mb/s constantly in all your reports. Have you fixed it to that value manually using some file/setting possibly not being captured by the script? What mode is being used in the router? It is recommended to try b/g mixed mode or g-only mode to see if it helps connecting at a higher speed.

If the router is already using 'g' mode, you may try a higher speed with -
```
sudo iwconfig wlan0 rate 48M
```
Then check -
```
iwconfig
```
Does it now show the speed as 48 Mb/s ? Is the connection stable at this speed? Some other acceptable values higher than 18M are 24M, 36M.

The above command will try to fix the speed at defined value (48M in above command). You can set it to 'auto' mode with -
```
sudo iwconfig wlan0 rate **48M auto**
```
..or just 'auto' instead of '48M auto'. Currently it seems to be _fixed_ (possibly 'forced') at 18M.

---

### Post by jonasb2 on 2014-10-21
Ok, so I took a bit of a break in trying to fix this (nothing was working, I moved, and I spent some time testing). But I'm back now and it's still not fixed!
To answer the previous post: 
- the modem was on g-mode
- setting the rate to 48M did show the change in iwconfig and at first I thought this fixed it, but eventually it started to hang anyway. Possibly it did take longer than usual, but afterwards I noticed that it can function quite a while without hanging, also on 18M
- both commands involving setting the rate to auto, resulted in it 18 Mb/s in iwconfig

Script output with 48M rate. I also moved, so new modem and stuff.:
```


########## wireless info START ##########


Report from: 21 Oct 2014 12:46 CEST +0200


Booted last: 21 Oct 2014 11:43 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, acpi_backlight=vendor


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
    Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8723be              87260  0 
btcoexist              55886  1 rtl8723be
rtl8723_common         23427  1 rtl8723be
rtl_pci                27306  1 rtl8723be
wmi                    19379  0 
rtl8192cu              68579  0 
rtl_usb                22809  1 rtl8192cu
rtlwifi                69157  4 rtl_pci,rtl_usb,rtl8192cu,rtl8723be
rtl8192c_common        58270  1 rtl8192cu
mac80211              687021  5 rtl_pci,rtl_usb,rtlwifi,rtl8192cu,rtl8723be
cfg80211              521225  2 mac80211,rtlwifi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6e71:d9ff:fede:358d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4817693 (4.8 MB)  TX bytes:4296123 (4.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"bbox2-9070"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'bbox2-9070' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:318   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [bbox2-9070] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    D-Link DSL-2740B:Infra, <MAC 'D-Link DSL-2740B' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    Mobistar-e1bc:   Infra, <MAC 'Mobistar-e1bc' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    bbox2-d75e:      Infra, <MAC 'bbox2-d75e' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    Philips WiFi:    Infra, <MAC 'Philips WiFi' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA
    FON_BELGACOM:    Infra, <MAC 'FON_BELGACOM' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87
    *bbox2-9070:     Infra, <MAC 'bbox2-9070' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    AUTO_FON_BELGACOM: Infra, <MAC 'AUTO_FON_BELGACOM' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2 Enterprise
    FON_BELGACOM:    Infra, <MAC 'FON_BELGACOM' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    telenet-2EE3B:   Infra, <MAC 'telenet-2EE3B' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    wifi22_4:        Infra, <MAC 'wifi22_4' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    Sitecom2ab259:   Infra, <MAC 'Sitecom2ab259' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Osmii:           Infra, <MAC 'Osmii' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57
    telenet-B0F23:   Infra, <MAC 'telenet-B0F23' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    FON_BELGACOM:    Infra, <MAC 'FON_BELGACOM' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37


  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Busseniers 1]] (600 root)
[connection] id=Busseniers 1 | type=802-11-wireless
[802-11-wireless] ssid=Busseniers | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-9070 2]] (600 root)
[connection] id=bbox2-9070 2 | type=802-11-wireless
[802-11-wireless] ssid=bbox2-9070 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Busseniers]] (600 root)
[connection] id=Busseniers | type=802-11-wireless
[802-11-wireless] ssid=Busseniers | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/bbox2-9070 1]] (600 root)
[connection] id=bbox2-9070 1 | type=802-11-wireless
[802-11-wireless] ssid=bbox2-9070 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-9070]] (600 root)
[connection] id=bbox2-9070 | type=802-11-wireless
[802-11-wireless] ssid=bbox2-9070 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HowestWireless]] (600 root)
[ipv6] method=auto
[connection] id=HowestWireless | type=802-11-wireless
[802-11-wireless] ssid=HowestWireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Brussels (based on set time zone)


country BE:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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


##### iwlist scan #######################


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'bbox2-9070' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"bbox2-9070"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a72f210e4
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FON_BELGACOM' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000327534b79a
                    Extra: Last beacon: 172ms ago
          Cell 03 - Address: <MAC 'FON_BELGACOM' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a732d5184
                    Extra: Last beacon: 236ms ago
          Cell 04 - Address: <MAC 'bbox2-d75e' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"bbox2-d75e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032752e7a88
                    Extra: Last beacon: 528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'AUTO_FON_BELGACOM' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"AUTO_FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003275364181
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'Mobistar-e1bc' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Mobistar-e1bc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000480e64925b
                    Extra: Last beacon: 2816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'wifi22_4' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"wifi22_4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010626d719b
                    Extra: Last beacon: 2468ms ago
          Cell 08 - Address: <MAC 'D-Link DSL-2740B' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"D-Link DSL-2740B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b27a8af65
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtl8192cu]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2E1D92552336F091BDEB88E
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     085B283910CF6CA0B4CAE2C
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtl8192c_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A279C50E29ED7F277EAF738
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
debug: 0
fwlps: N
ips: N
msi: N
swenc: Y
swlps: N


[rtl8192cu]
debug: 0
swenc: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


rtl8192cu
lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/net-rtl8192cu.conf]
options rtl8192cu swenc=1


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N swenc=Y


##### rc.local ##########################


rfkill block bluetooth
echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 1486.204160] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 1486.206523] rtlwifi: wireless switch is on
[ 1486.941305] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1488.729857] wlan0: authenticate with <MAC 'bbox2-9070' [AC1]>
[ 1488.747690] wlan0: send auth to <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1488.752739] wlan0: authenticated
[ 1488.759151] wlan0: associate with <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1488.762200] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC1]> (capab=0x431 status=0 aid=1)
[ 1488.762353] wlan0: associated
[ 1488.762490] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1488.788363] wlan0: deauthenticating from <MAC 'bbox2-9070' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 1488.799881] wlan0: authenticate with <MAC 'bbox2-9070' [AC1]>
[ 1488.810390] wlan0: send auth to <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1488.813336] wlan0: authenticated
[ 1488.823059] wlan0: associate with <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1488.825942] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC1]> (capab=0x431 status=0 aid=1)
[ 1488.826081] wlan0: associated
[ 1544.962225] wlan0: deauthenticating from <MAC 'bbox2-9070' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1545.188013] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[ 1545.189235] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[ 1545.190893] rtlwifi: wireless switch is on
[ 1545.950400] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1547.714501] wlan0: authenticate with <MAC 'bbox2-9070' [AC1]>
[ 1547.724964] wlan0: send auth to <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1547.727797] wlan0: authenticated
[ 1547.732249] wlan0: associate with <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1547.735300] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC1]> (capab=0x431 status=0 aid=1)
[ 1547.735456] wlan0: associated
[ 1547.735577] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1547.766434] wlan0: deauthenticating from <MAC 'bbox2-9070' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 1547.781587] wlan0: authenticate with <MAC 'bbox2-9070' [AC1]>
[ 1547.792060] wlan0: send auth to <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1547.794295] wlan0: authenticated
[ 1547.799898] wlan0: associate with <MAC 'bbox2-9070' [AC1]> (try 1/3)
[ 1547.805411] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC1]> (capab=0x431 status=0 aid=1)
[ 1547.805549] wlan0: associated


########## wireless info END ############



```


I have also tried with an USB adapter so that it would use a different driver. I went with d-link DWA-131 B1, which uses rtl8192cu driver as I understand. Internet works, but hangs even faster. It feels like it is the same issue to me and that would mean the driver is not to blame. I tested with original driver module removed "sudo rmmod rtl8723be". Here is a script output:
```


########## wireless info START ##########


Report from: 21 Oct 2014 13:47 CEST +0200


Booted last: 21 Oct 2014 11:43 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, acpi_backlight=vendor


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
	Subsystem: CLEVO/KAPOK Computer Device [1558:5470]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:0248 Acer, Inc 
Bus 001 Device 005: ID 2001:330d D-Link Corp. 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
5: phy4: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8723_common         23427  0 
rtl_pci                27306  0 
wmi                    19379  0 
rtl8192cu              68579  0 
rtl_usb                22809  1 rtl8192cu
rtlwifi                69157  3 rtl_pci,rtl_usb,rtl8192cu
rtl8192c_common        58270  1 rtl8192cu
mac80211              687021  4 rtl_pci,rtl_usb,rtlwifi,rtl8192cu
cfg80211              521225  2 mac80211,rtlwifi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7262:b8ff:fe96:7916/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59333 (59.3 KB)  TX bytes:32381 (32.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:"bbox2-9070"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'bbox2-9070' [AC5]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan1  [bbox2-9070 1] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    D-Link DSL-2740B:Infra, <MAC 'D-Link DSL-2740B' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    AUTO_FON_BELGACOM: Infra, <MAC 'AUTO_FON_BELGACOM' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    Osmii:           Infra, <MAC 'Osmii' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    bbox2-d75e:      Infra, <MAC 'bbox2-d75e' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    Philips WiFi:    Infra, <MAC 'Philips WiFi' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WPA
    Mobistar-e1bc:   Infra, <MAC 'Mobistar-e1bc' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    wifi22_4:        Infra, <MAC 'wifi22_4' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WEP
    FON_BELGACOM:    Infra, <MAC 'FON_BELGACOM' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4
    *bbox2-9070:     Infra, <MAC 'bbox2-9070' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2
    telenet-2EE3B:   Infra, <MAC 'telenet-2EE3B' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    Sitecom2ab259:   Infra, <MAC 'Sitecom2ab259' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2
    FON_BELGACOM:    Infra, <MAC 'FON_BELGACOM' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Busseniers 1]] (600 root)
[connection] id=Busseniers 1 | type=802-11-wireless
[802-11-wireless] ssid=Busseniers | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-9070 2]] (600 root)
[connection] id=bbox2-9070 2 | type=802-11-wireless
[802-11-wireless] ssid=bbox2-9070 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Busseniers]] (600 root)
[connection] id=Busseniers | type=802-11-wireless
[802-11-wireless] ssid=Busseniers | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/bbox2-9070 1]] (600 root)
[connection] id=bbox2-9070 1 | type=802-11-wireless
[802-11-wireless] ssid=bbox2-9070 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-9070]] (600 root)
[connection] id=bbox2-9070 | type=802-11-wireless
[802-11-wireless] ssid=bbox2-9070 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HowestWireless]] (600 root)
[ipv6] method=auto
[connection] id=HowestWireless | type=802-11-wireless
[802-11-wireless] ssid=HowestWireless | mac-address=<MAC address>
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Brussels (based on set time zone)


country BE:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan1     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      9   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan1     Scan completed :
          Cell 01 - Address: <MAC 'Osmii' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Osmii"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000aaf798b173
                    Extra: Last beacon: 1332ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FON_BELGACOM' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b4ae7973c
                    Extra: Last beacon: 188ms ago
          Cell 03 - Address: <MAC 'TELENETHOMESPOT' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000043008a173
                    Extra: Last beacon: 6952ms ago
          Cell 04 - Address: <MAC 'bbox2-d75e' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"bbox2-d75e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000334ecef181
                    Extra: Last beacon: 180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'bbox2-9070' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"bbox2-9070"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b4ca413ca
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'AUTO_FON_BELGACOM' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"AUTO_FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000334ed08181
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'Philips WiFi' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Philips WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004344d4d122
                    Extra: Last beacon: 7480ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Mobistar-e1bc' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Mobistar-e1bc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000048e81af231
                    Extra: Last beacon: 1052ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'wifi22_4' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"wifi22_4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000113bbcb19b
                    Extra: Last beacon: 7520ms ago
          Cell 10 - Address: <MAC 'D-Link DSL-2740B' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"D-Link DSL-2740B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c015a547a
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'telenet-2EE3B' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"telenet-2EE3B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000430071173
                    Extra: Last beacon: 7108ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'FON_BELGACOM' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"FON_BELGACOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000334ecd6181
                    Extra: Last beacon: 336ms ago
          Cell 13 - Address: <MAC 'Sitecom2ab259' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Sitecom2ab259"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001174da45173
                    Extra: Last beacon: 6520ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'TELENETHOMESPOT' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000aaf7940173
                    Extra: Last beacon: 1588ms ago


lo        Interface doesn't support scanning.


0000000000000000


##### module infos ######################


[rtl8723_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtl8192cu]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     2E1D92552336F091BDEB88E
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     085B283910CF6CA0B4CAE2C
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[rtl8192c_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A279C50E29ED7F277EAF738
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8192cu]
debug: 0
swenc: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


rtl8192cu
lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/net-rtl8192cu.conf]
options rtl8192cu swenc=1


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N swenc=Y


##### rc.local ##########################


rfkill block bluetooth
echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 1547.735300] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC5]> (capab=0x431 status=0 aid=1)
[ 1547.735456] wlan0: associated
[ 1547.735577] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1547.766434] wlan0: deauthenticating from <MAC 'bbox2-9070' [AC5]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 1547.781587] wlan0: authenticate with <MAC 'bbox2-9070' [AC5]>
[ 1547.792060] wlan0: send auth to <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 1547.794295] wlan0: authenticated
[ 1547.799898] wlan0: associate with <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 1547.805411] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC5]> (capab=0x431 status=0 aid=1)
[ 1547.805549] wlan0: associated
[ 7119.556350] wlan0: deauthenticating from <MAC 'bbox2-9070' [AC5]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 7119.769576] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[ 7119.770807] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[ 7119.772564] rtlwifi: wireless switch is on
[ 7120.259172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7121.389821] wlan0: authenticate with <MAC 'bbox2-9070' [AC5]>
[ 7121.400318] wlan0: send auth to <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 7121.402825] wlan0: authenticated
[ 7121.405425] wlan0: associate with <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 7121.409549] wlan0: RX AssocResp from <MAC 'bbox2-9070' [AC5]> (capab=0x431 status=0 aid=1)
[ 7121.409699] wlan0: associated
[ 7121.409813] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7579.672068] rtl8192cu: Chip version 0x11
[ 7579.715847] rtl8192cu: MAC address: <MAC 'wlan1' [IF]>
[ 7579.715871] rtl8192cu: Board Type 0
[ 7579.716021] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 7579.716153] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 7579.718101] ieee80211 phy4: Selected rate control algorithm 'rtl_rc'
[ 7579.720591] rtlwifi: wireless switch is on
[ 7579.788931] rtl8192cu: MAC auto ON okay!
[ 7579.817785] rtl8192cu: Tx queue select: 0x05
[ 7580.198269] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 7581.737696] wlan1: authenticate with <MAC 'bbox2-9070' [AC5]>
[ 7581.767019] wlan1: send auth to <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 7581.770376] wlan1: authenticated
[ 7581.773133] wlan1: associate with <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 7581.799641] wlan1: RX AssocResp from <MAC 'bbox2-9070' [AC5]> (capab=0x431 status=0 aid=3)
[ 7581.799886] wlan1: associated
[ 7581.801077] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 7581.825204] wlan1: deauthenticating from <MAC 'bbox2-9070' [AC5]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 7581.838641] wlan1: authenticate with <MAC 'bbox2-9070' [AC5]>
[ 7581.850503] wlan1: send auth to <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 7581.877192] wlan1: authenticated
[ 7581.880881] wlan1: associate with <MAC 'bbox2-9070' [AC5]> (try 1/3)
[ 7581.901825] wlan1: RX AssocResp from <MAC 'bbox2-9070' [AC5]> (capab=0x431 status=0 aid=3)
[ 7581.902065] wlan1: associated
[ 7592.541305] wlan0: deauthenticating from <MAC 'bbox2-9070' [AC5]> by local choice (Reason: 3=DEAUTH_LEAVING)


########## wireless info END ############

```

---

### Post by varunendra on 2014-10-22
The default rtl8192cu driver has been reported many times for similar issues, so no surprise you experience the same. A patched version of it seemed to do the trick for most of the users who reported the problem, but I'm not sure whether it will compile on the latest kernels or not : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

Regarding your native card, there is one more thing you can try, based on a positive experience from one user (and negative from another, wifi totally broke for him, forcing him to revert the change). Please try replacing the "swenc" option with the "msi=1" option -
```
sudo sed -i 's/swenc=Y/msi=Y/' /etc/modprobe.d/rtl8723be.conf
```
Reboot with the usb adapter removed, and try the internal connection again. If it happens to be totally disabled like for the other user who tried it, remove this option with -
```
sudo sed -i 's/ msi=Y//' /etc/modprobe.d/rtl8723be.conf
```
..and let us know it failed. :(

---

### Post by jonasb2 on 2014-10-22
> **varunendra said:**
> ..and let us know it failed. :(
... yep!... :(

It works for a short time and then disconnects from the current wifi network, which then doesn't show up between the possible wifi networks anymore (but others are still showing). Reloading the driver module shows it as connected again, but I did not actually manage to access anything online (and shortly later it disconnects again).

---

