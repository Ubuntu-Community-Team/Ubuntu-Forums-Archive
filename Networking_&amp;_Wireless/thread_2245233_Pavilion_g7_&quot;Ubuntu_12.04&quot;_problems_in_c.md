---
title: "Pavilion g7 &quot;Ubuntu 12.04&quot; problems in conecting to &quot;some&quot; wi-fi"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by Leonardo_Alvarez on 2014-09-22
I have an Ubuntu 12.04 installed on a PC Pavilion g7. I have connented without any problem to a lot of wi-fi. But now I'm not able to connect to a wi-fi that is in the place were I'm living. This wi-fi connect very well to Windows machines

---

### Post by wyliecoyoteuk on 2014-09-22
sometimes it is a dhcp failure.
if you can, use a manual ip, subnet mask, gateway and DNS and it may work ok.

---

### Post by jeremy31 on 2014-09-22
Please follow the instructions to run the wireless script and post results from here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Leonardo_Alvarez on 2014-09-23
Again, more information
My laptop HP Pavilion g7 with Ubuntu 12.04 installed normally have connected to any wi-fi, but now refuse to connect to a to a particular wi-fi. It "detects" the wi-fi but ask again and again for the password withiout establishing the conection:

1) The data of the wi-fi are:
```
% /sbin/iw wlan0 link
Connected to e0:3f:49:6a:94:c8 (on wlan0)
        SSID: NORSAR-VESTBYGT-2.4GHZ
        freq: 2437
        RX: 3090 bytes (30 packets)
        TX: 506 bytes (5 packets)
        signal: -83 dBm
        tx bitrate: 28.9 MBit/s MCS 3 short GI

        bss flags:      short-slot-time
        dtim period:    0
        beacon int:     100


```2) The data of the wi-fi adaptor present in my laptop are:
```
% lspci -v 
         ...
         ...
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
        Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0200000 (64-bit, non-prefetchable) [size=512K]
        Expansion ROM at f0400000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
         ...
         ...


```3) The result of the scan of wi-fi is:         
```
% sudo /sbin/iw wlan0 scan
          ...
          ...
       BSS e0:3f:49:6a:94:c8 (on wlan0)
        TSF: 21829130157 usec (0d, 06:03:49)
        freq: 2437
        beacon interval: 100
        capability: ESS Privacy ShortSlotTime (0x0411)
        signal: -83.00 dBm
        last seen: 680 ms ago
        Information elements from Probe Response frame:
        SSID: NORSAR-VESTBYGT-2.4GHZ
        Supported rates: 1.0* 2.0* 5.5* 11.0* 18.0 24.0 36.0 54.0 
        DS Parameter set: channel 6
        ERP: Barker_Preamble_Mode
        RSN:     * Version: 1
                 * Group cipher: CCMP
                 * Pairwise ciphers: CCMP
                 * Authentication suites: PSK
                 * Capabilities: 16-PTKSA-RC (0x000c)
        Extended supported rates: 6.0 9.0 12.0 48.0 
        HT capabilities:
                Capabilities: 0x19bd
                        RX LDPC
                        HT20
                        SM Power Save disabled
                        RX Greenfield
                        RX HT20 SGI
                        TX STBC
                        RX STBC 1-stream
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 4 usec (0x05)
                HT RX MCS rate indexes supported: 0-23
                HT TX MCS rate indexes are undefined
        HT operation:
                 * primary channel: 6
                 * secondary channel offset: no secondary
                 * STA channel width: 20 MHz
                 * RIFS: 1
                 * HT protection: no
                 * non-GF present: 1
                 * OBSS non-GF present: 0
                 * dual beacon: 0
                 * dual CTS protection: 0
                 * STBC beacon: 0
                 * L-SIG TXOP Prot: 0
                 * PCO active: 0
                 * PCO phase: 0
        Extended capabilities: HT Information Exchange Supported, 3
        WMM:     * Parameter version 1
                 * u-APSD
                 * BE: CW 15-1023, AIFSN 3
                 * BK: CW 15-1023, AIFSN 7
                 * VI: CW 7-15, AIFSN 2, TXOP 3008 usec
                 * VO: CW 3-7, AIFSN 2, TXOP 1504 usec
          ...
          ...

```
What shoudl I do?

---

### Post by Leonardo_Alvarez on 2014-09-23
My laptop HP Pavilion g7, with Ubuntu 12.04 installed, normally have connected to any wi-fi, but now refuses to connect to a to a particular wi-fi. It "detects" the wi-fi but ask again and agin for the password withiout establishing a real conection:

1) The data of the wi-fi are:
```
% /sbin/iw wlan0 link
Connected to e0:3f:49:6a:94:c8 (on wlan0)
        SSID: NORSAR-VESTBYGT-2.4GHZ
        freq: 2437
        RX: 3090 bytes (30 packets)
        TX: 506 bytes (5 packets)
        signal: -83 dBm
        tx bitrate: 28.9 MBit/s MCS 3 short GI

        bss flags:      short-slot-time
        dtim period:    0
        beacon int:     100
```

2) The data of the wi-fi adaptor present in my laptop are:
```
% lspci -v 
         ...
         ...
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
        Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0200000 (64-bit, non-prefetchable) [size=512K]
        Expansion ROM at f0400000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
         ...
         ...
```

3) The result of the scan of wi-fi is:         
```
% sudo /sbin/iw wlan0 scan
          ...
          ...
       BSS e0:3f:49:6a:94:c8 (on wlan0)
        TSF: 21829130157 usec (0d, 06:03:49)
        freq: 2437
        beacon interval: 100
        capability: ESS Privacy ShortSlotTime (0x0411)
        signal: -83.00 dBm
        last seen: 680 ms ago
        Information elements from Probe Response frame:
        SSID: NORSAR-VESTBYGT-2.4GHZ
        Supported rates: 1.0* 2.0* 5.5* 11.0* 18.0 24.0 36.0 54.0 
        DS Parameter set: channel 6
        ERP: Barker_Preamble_Mode
        RSN:     * Version: 1
                 * Group cipher: CCMP
                 * Pairwise ciphers: CCMP
                 * Authentication suites: PSK
                 * Capabilities: 16-PTKSA-RC (0x000c)
        Extended supported rates: 6.0 9.0 12.0 48.0 
        HT capabilities:
                Capabilities: 0x19bd
                        RX LDPC
                        HT20
                        SM Power Save disabled
                        RX Greenfield
                        RX HT20 SGI
                        TX STBC
                        RX STBC 1-stream
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 4 usec (0x05)
                HT RX MCS rate indexes supported: 0-23
                HT TX MCS rate indexes are undefined
        HT operation:
                 * primary channel: 6
                 * secondary channel offset: no secondary
                 * STA channel width: 20 MHz
                 * RIFS: 1
                 * HT protection: no
                 * non-GF present: 1
                 * OBSS non-GF present: 0
                 * dual beacon: 0
                 * dual CTS protection: 0
                 * STBC beacon: 0
                 * L-SIG TXOP Prot: 0
                 * PCO active: 0
                 * PCO phase: 0
        Extended capabilities: HT Information Exchange Supported, 3
        WMM:     * Parameter version 1
                 * u-APSD
                 * BE: CW 15-1023, AIFSN 3
                 * BK: CW 15-1023, AIFSN 7
                 * VI: CW 7-15, AIFSN 2, TXOP 3008 usec
                 * VO: CW 3-7, AIFSN 2, TXOP 1504 usec
          ...
          ...
```

What should I do?

---

### Post by varunendra on 2014-09-23
Is the encryption WPA2 in the router? If not, please set it as such (WPA2-PSK with AES). If it is already as suggested, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by coffeecat on 2014-09-23
Threads merged. Please do not post the same thing in different threads - it dilutes the community's ability to help.

I've added code tags to your two (nearly identical) posts. Please follow varunendra's advice about using code tags when posting outputs.

---

### Post by Leonardo_Alvarez on 2014-09-23
Yes, in the router there is WPA2. In graphic method of configuration, as wireless security I selected  WPA and WPA2 personal. It gives the option of  WPA and WPA2 enterprise, but it is not my case. The running of the script gave the following result (i ran it in the place where I'm working, where I'm am conceted to a wi-fi named "norsar")
```


########## wireless info START ##########

Report from: 22 Sep 2014 17:25 COT -0500

Booted last: 22 Sep 2014 13:39 COT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.5.0-54-generic #81~precise1-Ubuntu SMP Tue Jul 15 04:02:22 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Classic (No effects)

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
    Kernel driver in use: ath9k

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:184b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 0766:0001 Jess-Link Products Co., Ltd 
Bus 007 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
ath9k                 133223  0 
mac80211              555318  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              399752  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
cfg80211              208382  3 ath9k,mac80211,ath
wmi                    19257  1 hp_wmi

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

vboxnet0  Link encap:Ethernet  HWaddr <MAC 'vboxnet0' [IF]>  
          inet addr:192.168.56.1  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:38735 (38.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.10.20.98  Bcast:10.10.20.255  Mask:255.255.255.0
          inet6 addr: fe80::2ed0:5aff:fe78:6dbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77220 errors:0 dropped:3 overruns:0 frame:0
          TX packets:36217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65022504 (65.0 MB)  TX bytes:4042678 (4.0 MB)

##### iwconfig ##########################

vboxnet0  no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"norsar"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'norsar' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:56  Invalid misc:364   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.20.1      0.0.0.0         UG    0      0        0 wlan0
10.10.20.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.56.0    0.0.0.0         255.255.255.0   U     0      0        0 vboxnet0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

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

  Wired Properties
    Carrier:         off

- Device: wlan0  [norsar] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *norsar:         Infra, <MAC 'norsar' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    norsar:          Infra, <MAC 'norsar' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    norsar:          Infra, <MAC 'norsar' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA
    BasicInternet:   Infra, <MAC 'BasicInternet' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    UniK Guest:      Infra, <MAC 'UniK Guest' [AN5]>, Freq 2437 MHz, Rate 0 Mb/s, Strength 24

  IPv4 Settings:
    Address:         10.10.20.98
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.20.1

    DNS:             193.156.135.72
    DNS:             8.8.8.8

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/CrossEyed Cat]] (600 root)
[connection] id=CrossEyed Cat | type=802-11-wireless
[802-11-wireless] ssid=CrossEyed Cat | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SemiWifi_Pool]] (600 root)
[connection] id=SemiWifi_Pool | type=802-11-wireless
[802-11-wireless] ssid=SemiWifi_Pool | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CENAIS]] (600 root)
[connection] id=CENAIS | type=802-11-wireless
[802-11-wireless] ssid=CENAIS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/seminole-203]] (600 root)
[connection] id=seminole-203 | type=802-11-wireless
[802-11-wireless] ssid=seminole-203 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MIA-WiFi]] (600 root)
[connection] id=MIA-WiFi | type=802-11-wireless
[802-11-wireless] ssid=MIA-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SemiWifi_Norte]] (600 root)
[connection] id=SemiWifi_Norte | type=802-11-wireless
[802-11-wireless] ssid=SemiWifi_Norte | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/sismologia]] (600 root)
[connection] id=sismologia | type=802-11-wireless
[802-11-wireless] ssid=sismologia | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NORSAR-VESTBYGT-2.4GHZ 1]] (600 root)
[connection] id=NORSAR-VESTBYGT-2.4GHZ 1 | type=802-11-wireless
[802-11-wireless] ssid=NORSAR-VESTBYGT-2.4GHZ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SemiWifi_Este]] (600 root)
[connection] id=SemiWifi_Este | type=802-11-wireless
[802-11-wireless] ssid=SemiWifi_Este | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NORSAR-VESTBYGT-2.4GHZ]] (600 root)
[connection] id=NORSAR-VESTBYGT-2.4GHZ | type=802-11-wireless
[802-11-wireless] ssid=NORSAR-VESTBYGT-2.4GHZ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/norsar]] (600 root)
[connection] id=norsar | type=802-11-wireless
[802-11-wireless] ssid=norsar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotel  Riu  Panama  Plaza]] (600 root)
[connection] id=Hotel  Riu  Panama  Plaza | type=802-11-wireless
[802-11-wireless] ssid=Hotel  Riu  Panama  Plaza | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/INTERNET]] (600 root)
[connection] id=INTERNET | type=802-11-wireless
[802-11-wireless] ssid=INTERNET | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/2WIRE869]] (600 root)
[connection] id=2WIRE869 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE869 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/seminole-restaurante]] (600 root)
[connection] id=seminole-restaurante | type=802-11-wireless
[802-11-wireless] ssid=seminole-restaurante | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Alcalde]] (600 root)
[connection] id=Alcalde | type=802-11-wireless
[802-11-wireless] ssid=Alcalde | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/seminole-403]] (600 root)
[connection] id=seminole-403 | type=802-11-wireless
[802-11-wireless] ssid=seminole-403 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/conferences]] (600 root)
[connection] id=conferences | type=802-11-wireless
[802-11-wireless] ssid=conferences | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/seminole-102]] (600 root)
[connection] id=seminole-102 | type=802-11-wireless
[802-11-wireless] ssid=seminole-102 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NORSARGUEST]] (600 root)
[connection] id=NORSARGUEST | type=802-11-wireless
[802-11-wireless] ssid=NORSARGUEST | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Bogota (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

vboxnet0  no frequency information.

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

sudo: unable to resolve host Olympus
vboxnet0  Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'norsar' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"norsar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000573d8fabbfc5
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'norsar' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"norsar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000573da7079533
                    Extra: Last beacon: 3372ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'norsar' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"norsar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000573db99f399b
                    Extra: Last beacon: 2332ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'king' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"king"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002e86730177
                    Extra: Last beacon: 2180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'UniK' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"UniK"

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C8BAA1E567FF833D1510BA6
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[mac80211]
filename:       /lib/modules/3.5.0-54-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEC330950D8489DA9D7A071
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath9k_common]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     1673D73171C827FC143E431
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D2CC7E665A1FF9DC10231D9
depends:        ath
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

[ath]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8C339DF4D303827C9304BB0
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 

[cfg80211]
filename:       /lib/modules/3.5.0-54-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     74571C7FA6F4E9D34760CDF
depends:        
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[ath9k_hw]
force_new_ani: 0

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

[/etc/modprobe.d/blacklist-local.conf]
blacklist fglrx_updates

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x0bda:0x8176 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   21.187136] wlan0: authenticate with <MAC 'norsar' [AC1]>
[   21.191763] wlan0: send auth to <MAC 'norsar' [AC1]> (try 1/3)
[   21.393892] wlan0: send auth to <MAC 'norsar' [AC1]> (try 2/3)
[   21.395579] wlan0: authenticated
[   21.401904] wlan0: associate with <MAC 'norsar' [AC1]> (try 1/3)
[   21.404198] wlan0: RX AssocResp from <MAC 'norsar' [AC1]> (capab=0x431 status=0 aid=5)
[   21.404397] wlan0: associated
[   21.404913] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by varunendra on 2014-09-24
Sorry for the delay in reply, there seems to be some bug in the forums due to which threads don't appear in my search results (by my ID) if they are moved/merged AFTER I have posted in them. Fortunately, this tab was open (besides tens of others), and only now did I happen to notice and refresh it to see the new posts.

Anyway, please try this for now -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

And assuming from your previous posts that it is the "NORSAR-VESTBYGT-2.4GHZ" access-point that you are having difficulty connecting to, I suggest changing its SSID (in the router of course, if you have admin access to it) to something simpler - something that doesn't contain ALL CAPS or blank spaces or special characters other than hyphen (-) or underscore (_). No need to do this though if the "nohwcrypt=1" parameter suggested above is alone sufficient to solve the problem.

Oh, and you seem to have two saved profiles for connecting to the same SSID. I suggest deleting them both, and let a single new one be created automatically when you attempt to connect to it this time.

If these changes don't help, please post a fresh wireless_script report created when you try connecting to the problematic AP, and it fails.

One more thing - Is a fresh install of 14.04 an option for you? Or even 12.04.5 directly from its DVD/USB? Just asking because I see you are still using kernel version 3.5.., while current kernel versions are 3.13+. Newer is not always better, but in this case it may be.

---

### Post by Leonardo_Alvarez on 2014-09-26
The problem continues after doing what you indicated in your post. Here is the wirelles-script result done after that in the place where I can connect
```

########## wireless info START ##########
Report from: 25 Sep 2014 22:02 COT -0500
Booted last: 25 Sep 2014 21:51 COT -0500
Script from: 20 Sep 2014 23:04 UTC +0000
##### release ###########################
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
##### kernel ############################
Linux 3.5.0-54-generic #81~precise1-Ubuntu SMP Tue Jul 15 04:02:22 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7
##### desktop ###########################
GNOME Classic (No effects)
##### lspci #############################
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
    Kernel driver in use: ath9k
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:184b]
    Kernel driver in use: r8169
##### lsusb #############################
Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 007 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
##### PCMCIA card info ##################
##### rfkill ############################
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
##### lsmod #############################
hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
ath9k                 133223  0 
mac80211              555318  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              399752  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
cfg80211              208382  3 ath9k,mac80211,ath
wmi                    19257  1 hp_wmi
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
          inet6 addr: fe80::2ed0:5aff:fe78:6dbe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40365 (40.3 KB)  TX bytes:46345 (46.3 KB)
##### iwconfig ##########################
eth0      no wireless extensions.
lo        no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:"NORSAR-VESTBYGT-2.4GHZ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>   
          Bit Rate=7.2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:5   Missed beacon:0
##### route #############################
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
##### resolv.conf #######################
##### nm-tool ###########################
NetworkManager Tool
State: connecting
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
- Device: wlan0  [NORSAR-VESTBYGT-2.4GHZ] --------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 
    NextGenTel_AE:   Infra, <MAC 'NextGenTel_AE' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    Telenor8045mer:  Infra, <MAC 'Telenor8045mer' [AC3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Telenor-62457325:Infra, <MAC 'Telenor-62457325' [AC2]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 7 WPA2
    privat9254bok:   Infra, <MAC 'privat9254bok' [AC5]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 29 WEP
    EZ-base:         Infra, <MAC 'EZ-base' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Getbox-7CB0EF:   Infra, <MAC 'Getbox-7CB0EF' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    NORSAR-VESTBYGT-2.4GHZ: Infra, <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
##### NetworkManager.state ##############
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
##### NetworkManager.conf ###############
[main]
plugins=ifupdown,keyfile
dns=dnsmasq
no-auto-default=<MAC 'eth0' [IF]>,
[ifupdown]
managed=false
##### NetworkManager profiles ###########
[[/etc/NetworkManager/system-connections/CrossEyed Cat]] (600 root)
[connection] id=CrossEyed Cat | type=802-11-wireless
[802-11-wireless] ssid=CrossEyed Cat | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/SemiWifi_Pool]] (600 root)
[connection] id=SemiWifi_Pool | type=802-11-wireless
[802-11-wireless] ssid=SemiWifi_Pool | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/CENAIS]] (600 root)
[connection] id=CENAIS | type=802-11-wireless
[802-11-wireless] ssid=CENAIS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/seminole-203]] (600 root)
[connection] id=seminole-203 | type=802-11-wireless
[802-11-wireless] ssid=seminole-203 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/MIA-WiFi]] (600 root)
[connection] id=MIA-WiFi | type=802-11-wireless
[802-11-wireless] ssid=MIA-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/SemiWifi_Norte]] (600 root)
[connection] id=SemiWifi_Norte | type=802-11-wireless
[802-11-wireless] ssid=SemiWifi_Norte | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/sismologia]] (600 root)
[connection] id=sismologia | type=802-11-wireless
[802-11-wireless] ssid=sismologia | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/SemiWifi_Este]] (600 root)
[connection] id=SemiWifi_Este | type=802-11-wireless
[802-11-wireless] ssid=SemiWifi_Este | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/NORSAR-VESTBYGT-2.4GHZ]] (600 root)
[connection] id=NORSAR-VESTBYGT-2.4GHZ | type=802-11-wireless
[802-11-wireless] ssid=NORSAR-VESTBYGT-2.4GHZ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/norsar]] (600 root)
[connection] id=norsar | type=802-11-wireless
[802-11-wireless] ssid=norsar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/Hotel  Riu  Panama  Plaza]] (600 root)
[connection] id=Hotel  Riu  Panama  Plaza | type=802-11-wireless
[802-11-wireless] ssid=Hotel  Riu  Panama  Plaza | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/INTERNET]] (600 root)
[connection] id=INTERNET | type=802-11-wireless
[802-11-wireless] ssid=INTERNET | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/2WIRE869]] (600 root)
[connection] id=2WIRE869 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE869 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/seminole-restaurante]] (600 root)
[connection] id=seminole-restaurante | type=802-11-wireless
[802-11-wireless] ssid=seminole-restaurante | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/Alcalde]] (600 root)
[connection] id=Alcalde | type=802-11-wireless
[802-11-wireless] ssid=Alcalde | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
[[/etc/NetworkManager/system-connections/seminole-403]] (600 root)
[connection] id=seminole-403 | type=802-11-wireless
[802-11-wireless] ssid=seminole-403 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/conferences]] (600 root)
[connection] id=conferences | type=802-11-wireless
[802-11-wireless] ssid=conferences | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto
[[/etc/NetworkManager/system-connections/seminole-102]] (600 root)
[connection] id=seminole-102 | type=802-11-wireless
[802-11-wireless] ssid=seminole-102 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto
##### iw reg get ########################
Region: America/Bogota (based on set time zone)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
##### iwlist channels ###################
eth0      no frequency information.
lo        no frequency information.
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
          Current Frequency:2.437 GHz (Channel 6)
##### iwlist scan #######################
Channel occupancy:
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
sudo: unable to resolve host Olympus
eth0      Interface doesn't support scanning.
lo        Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NORSAR-VESTBYGT-2.4GHZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000077839b187
                    Extra: Last beacon: 388ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Telenor-62457325' [AC2]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=13/70  Signal level=-97 dBm  
                    Encryption key:on
                    ESSID:"Telenor-62457325"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000096fb9183
                    Extra: Last beacon: 1696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Telenor8045mer' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Telenor8045mer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a14dc183
                    Extra: Last beacon: 1160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NextGenTel_AE' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NextGenTel_AE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000021455286
                    Extra: Last beacon: 872ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'privat9254bok' [AC5]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"privat9254bok"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003c50b6121a3
                    Extra: Last beacon: 236ms ago
          Cell 06 - Address: <MAC 'Getbox-7D2DCF' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Getbox-7D2DCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000108c29d0147
                    Extra: Last beacon: 1216ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
##### module infos ######################
[ath9k]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C8BAA1E567FF833D1510BA6
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
[mac80211]
filename:       /lib/modules/3.5.0-54-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEC330950D8489DA9D7A071
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
[ath9k_common]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     1673D73171C827FC143E431
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
[ath9k_hw]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D2CC7E665A1FF9DC10231D9
depends:        ath
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)
[ath]
filename:       /lib/modules/3.5.0-54-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8C339DF4D303827C9304BB0
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
[cfg80211]
filename:       /lib/modules/3.5.0-54-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     74571C7FA6F4E9D34760CDF
depends:        
intree:         Y
vermagic:       3.5.0-54-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
##### module parameters #################
[ath9k]
blink: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500
[ath9k_hw]
force_new_ani: 0
[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00
##### /etc/modules ######################
lp
rtc
##### modprobe options ##################
[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1
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
[/etc/modprobe.d/blacklist-local.conf]
blacklist fglrx_updates
[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off
[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
##### rc.local ##########################
exit 0
##### pm-utils ##########################
##### udev rules ########################
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x0bda:0x8176 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
##### dmesg #############################
[  631.893919] wlan0: authenticate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
[  631.902002] wlan0: send auth to <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  631.907647] wlan0: authenticated
[  631.913107] wlan0: associate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  631.917752] wlan0: RX AssocResp from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=5)
[  631.917819] wlan0: associated
[  639.939447] wlan0: deauthenticated from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (Reason: 15)
[  641.050569] wlan0: authenticate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
[  641.058991] wlan0: send auth to <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  641.061075] wlan0: authenticated
[  641.065751] wlan0: associate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  641.069579] wlan0: RX AssocResp from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=5)
[  641.069636] wlan0: associated
[  649.061149] wlan0: deauthenticated from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (Reason: 15)
[  650.171264] wlan0: authenticate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
[  650.179949] wlan0: send auth to <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  650.182174] wlan0: authenticated
[  650.190483] wlan0: associate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  650.194318] wlan0: RX AssocResp from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=5)
[  650.194376] wlan0: associated
[  658.176759] wlan0: deauthenticated from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (Reason: 15)
[  659.283999] wlan0: authenticate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
[  659.292391] wlan0: send auth to <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  659.294413] wlan0: authenticated
[  659.299192] wlan0: associate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  659.303050] wlan0: RX AssocResp from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=5)
[  659.303117] wlan0: associated
[  667.283450] wlan0: deauthenticated from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (Reason: 15)
[  668.392723] wlan0: authenticate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
[  668.400841] wlan0: send auth to <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  668.402847] wlan0: authenticated
[  668.407962] wlan0: associate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  668.415106] wlan0: RX AssocResp from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=5)
[  668.415173] wlan0: associated
[  678.400387] wlan0: disassociating from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> by local choice (reason=3)
[  678.412702] wlan0: deauthenticating from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> by local choice (reason=3)
[  678.810816] wlan0: authenticate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]>
[  678.818365] wlan0: send auth to <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  678.823113] wlan0: authenticated
[  678.829300] wlan0: associate with <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (try 1/3)
[  678.848426] wlan0: RX AssocResp from <MAC 'NORSAR-VESTBYGT-2.4GHZ' [AC1]> (capab=0x411 status=0 aid=5)
[  678.848487] wlan0: associated
########## wireless info END ############

```
Concerning upgrading, I will upgrate the system to 12.04.05 after finishing my work here. To upgrade to another version is more difficicult. I live in Cuba, where there is a bad Internet conection, and for using a version of Linux efficiently I have to download the hole repositories for this version.

---

### Post by varunendra on 2014-09-26
Although you do seem to have created the options file, the change is not effective in the report above. My mistake, I should have told you that it will take effect after a reboot.

But the SSID of the router also doesn't seem to have changed. Did you change it? If yes, please remember to reboot the router also.

By the way, the signal strength of the concerned Access Point seems too weak to be stable. Anything below 35/70 is not a 'good' signal. If it even connects successfully at 22/70, just say a big "Thank you" to your card for whatever it can deliver with that.

If you can't download and install a newer version, and if you are super sure that the signal strength is not so bad, we can try compiling a relatively newer (not latest) driver from backports (method is [here]("http://ubuntuforums.org/showpost.php?p=12963298"), version will change). But really, I don't expect anything good if the signal strength is truly that weak.

---

### Post by Leonardo_Alvarez on 2014-09-27
Thank you very much!!!
The program seems to be solved since your last recommdation. When I boot again my laptop yesterday it got connected, but very unstable. Then I decided to install the new driver and the stability of the connection growed. At this moment it has been working continuosly for 8 hours. You were also right in that the signal is very bad. It is a problem in this place, were there is an AP that services 3 appartments and mine is located in the worst position.

---

### Post by varunendra on 2014-09-27
Nice to hear that the newer driver is working better.

If the connection seems satisfactorily good, tested across several reboots, several hours, please consider marking the thread as [SOLVED] using "Thread Tools" link above the first post. It may help others having same problem as you. :)

---

