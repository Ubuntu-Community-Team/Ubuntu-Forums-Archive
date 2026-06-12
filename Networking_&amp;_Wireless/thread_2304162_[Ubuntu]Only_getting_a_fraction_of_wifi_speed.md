---
title: "[Ubuntu]Only getting a fraction of wifi speed"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by bbbaiiq on 2015-11-24
On windows, I would get near exactly the speed I should have gotten. Now, I've moved over to Ubuntu 14.04 LTS and I can only get a fraction of the speed. I've tried many solutions but have gotten none to work.

uname -r gives me 3.19.8-992-generic
Pretty sure my adapter is rtl8188ee

---

### Post by ian-weisser on 2015-11-25
Have you searched this forum for other threads with rtl8188ee?

---

### Post by Bucky Ball on 2015-11-25
> **ian-weisser said:**
> Have you searched this forum for other threads with rtl8188ee?

And also, give the output of this, between code tags (see last link in my signature) please:

```
sudo lshw -C network
```

Let's confirm the card before lurching much further. :)

---

### Post by bbbaiiq on 2015-11-25
I have searched for things related. I've done this [http://ubuntuforums.org/showthread.php?t=2196571](http://ubuntuforums.org/showthread.php?t=2196571) but with a newer backport. I've done this [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) and had no luck with that. I tried this today [http://ubuntuforums.org/showthread.php?t=2219952](http://ubuntuforums.org/showthread.php?t=2219952) with no luck. It may be very likely I could have done anything wrong, I am very very new to linux.
 
sudo lshw -C network gives
```
*-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 10:08:b1:64:e7:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.19.8-992-generic firmware=N/A ip=192.168.1.64 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 ioport:4000(size=256) memory:b2500000-b2503fff

```

---

### Post by Bucky Ball on 2015-11-25
Looks like you have the correct driver installed from your output, but yes, something you've done may be blocking it. Could you perhaps run the wirelessinfoscript linked in my signature and post a link or the output between code tags here, please? (See last link in signature for code tags.)

---

### Post by bbbaiiq on 2015-11-25
Here you go
```
########## wireless info START ##########

Report from: 25 Nov 2015 13:02 EST -0500

Booted last: 24 Nov 2015 22:34 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.8-992-generic #201511172100 SMP Wed Nov 18 02:02:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Hewlett-Packard Company Device [103c:227e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14017  0 
sparse_keymap          13948  1 hp_wmi
rtl8188ee             134121  0 
rtl_pci                39740  1 rtl8188ee
rtlwifi               105667  2 rtl_pci,rtl8188ee
mac80211              631958  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              532240  2 mac80211,rtlwifi
compat                 21657  4 cfg80211,mac80211,rtlwifi,rtl8188ee
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5021695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2524286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7457318128 (7.4 GB)  TX bytes:177129346 (177.1 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33762 errors:0 dropped:1 overruns:0 frame:0
          TX packets:10062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9752822 (9.7 MB)  TX bytes:1578499 (1.5 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tiffany"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Tiffany' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-16 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       870     1  0 Nov24 ?        00:00:04 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [Tiffany] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    tlacad62:        Infra, <MAC 'tlacad62' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA2
    NETGEAR98:       Infra, <MAC 'NETGEAR98' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 50 WPA2
    ESHome:          Infra, <MAC 'ESHome' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2
    Kenny:           Infra, <MAC 'Kenny' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Cowboys88:       Infra, <MAC 'Cowboys88' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    rob01:           Infra, <MAC 'rob01' [AN6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 40 WPA2
    CHEOBORI:        Infra, <MAC 'CHEOBORI' [AN7]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    NETGEAR68:       Infra, <MAC 'NETGEAR68' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    *Tiffany:        Infra, <MAC 'Tiffany' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Vicky1955:       Infra, <MAC 'Vicky1955' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2
    HP-Print-15-Photosmart 6520: Infra, <MAC 'HP-Print-15-Photosmart 6520' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    tlabf714:        Infra, <MAC 'tlabf714' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    jordans mom:     Infra, <MAC 'jordans mom' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Bryant:          Infra, <MAC 'Bryant' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    Frank101:        Infra, <MAC 'Frank101' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    ngHub_319448NC02722: Infra, <MAC 'ngHub_319448NC02722' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Cail:            Infra, <MAC 'Cail' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    TG1672GB2:       Infra, <MAC 'TG1672GB2' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    TopCop:          Infra, <MAC 'TopCop' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4

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

[[/etc/NetworkManager/system-connections/GABBYCJ]] (600 root)
[connection] id=GABBYCJ | type=802-11-wireless
[802-11-wireless] ssid=GABBYCJ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tiffany]] (600 root)
[connection] id=Tiffany | type=802-11-wireless
[802-11-wireless] ssid=Tiffany | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ESHome]] (600 root)
[connection] id=ESHome | type=802-11-wireless
[802-11-wireless] ssid=ESHome | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ResidentialWiFi]] (600 root)
[connection] id=ResidentialWiFi | type=802-11-wireless
[802-11-wireless] ssid=ResidentialWiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      9   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tiffany' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"Tiffany"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c16a8b213
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR68' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR68"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000041b469193
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'tlabf714' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"tlabf714"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000063ff2861c2
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'tla98386' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"tla98386"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007ab59f0907e
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'tlacad62' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"tlacad62"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c0abec317
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HP-Print-15-Photosmart 6520' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-15-Photosmart 6520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000087cf2b094d
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Cail' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Cail"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000058d2499195
                    Extra: Last beacon: 1280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NETGEAR98' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR98"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000243ccf1619c
                    Extra: Last beacon: 1864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'CenturyLink1108' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1108"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=8002aadc05bc31c9
                    Extra: Last beacon: 168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Kenny' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Kenny"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000243cb82380c
                    Extra: Last beacon: 1828ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Frank101' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Frank101"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000243cc151174
                    Extra: Last beacon: 1824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'jordans mom' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"jordans mom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000243ca9fa145
                    Extra: Last beacon: 200ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'ngHub_319448NC02722' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ngHub_319448NC02722"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001fef8a161a1
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/3.19.8-992-generic/updates/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     521127E57F4409EF9EC91CF
depends:        rtlwifi,rtl_pci,compat,mac80211
vermagic:       3.19.8-992-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.8-992-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     65C8EF01D1257B1C68B9AAF
depends:        mac80211,rtlwifi
vermagic:       3.19.8-992-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.8-992-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     371B96DA3019935E30DFC60
depends:        mac80211,compat,cfg80211
vermagic:       3.19.8-992-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.8-992-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
srcversion:     8D0872D1723FB1AC022A4CC
depends:        cfg80211,compat
vermagic:       3.19.8-992-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.8-992-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     75463EDBD0CFDDF127DF5B4
depends:        compat
vermagic:       3.19.8-992-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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
blacklist uvcvideo

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

[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[19343.419615] rtlwifi: rtlwifi: wireless switch is on
[19346.469575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19346.500808] r8169 0000:09:00.0 eth0: link down
[19346.500952] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[19348.196454] wlan0: authenticate with <MAC 'Tiffany' [AC1]>
[19348.216914] wlan0: send auth to <MAC 'Tiffany' [AC1]> (try 1/3)
[19348.218392] wlan0: authenticated
[19348.220116] wlan0: associate with <MAC 'Tiffany' [AC1]> (try 1/3)
[19348.225288] wlan0: RX AssocResp from <MAC 'Tiffany' [AC1]> (capab=0xc11 status=0 aid=3)
[19348.225547] wlan0: associated
[19348.225573] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19348.443861] wlan0: deauthenticating from <MAC 'Tiffany' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[19348.454077] wlan0: authenticate with <MAC 'Tiffany' [AC1]>
[19348.464126] wlan0: send auth to <MAC 'Tiffany' [AC1]> (try 1/3)
[19348.465672] wlan0: authenticated
[19348.468269] wlan0: associate with <MAC 'Tiffany' [AC1]> (try 1/3)
[19348.480199] wlan0: RX AssocResp from <MAC 'Tiffany' [AC1]> (capab=0xc11 status=0 aid=3)
[19348.480513] wlan0: associated

########## wireless info END ############
```

---

### Post by bbbaiiq on 2015-11-27
bump?

---

### Post by ian-weisser on 2015-11-27
Look through your output.
What channel is 'Tiffany' on?
How many other networks share that channel?
What can you change about that?

---

### Post by bbbaiiq on 2015-11-27
Encryption is WPA2-AES which I've seen could make a difference but it doesn't in my case. Channel is 11 and switching between 1 and 6 had no benefit. There are 6 clients in all on the network, none of which are using bandwidth or anything like that.

---

