---
title: "WIFI connection on Ubuntu 14.04 doesn't last long"
date: 2015-07-10
forum: Networking &amp; Wireless
---

### Post by carlo12 on 2015-07-10
Hi everyone 

I am an Ubuntu user since 4 months and since the beginning I had a lot of troubles regarding WIFI connection.The problem is that my wifi connects but only for few minutes. 1 week ago i was able to fix almost all of the problems except for the internet connection. I've already red some threads and at first i thought that the problem was the network manager so i replaced it with WICD but the  problem is still there : the wifi is always connected but i have no internet and the weirdest thing is that when I ping my ip it works. Can someone please help me to solve this problem?
My Wifi card is a DWA 131 rev b

Thanks.

---

### Post by praseodym on 2015-07-10
Please run the wireless-script from the sticky-thread and show the output.

---

### Post by carlo12 on 2015-07-11
hmm...sorry but i'm new to the forum...can you please tell me what is a sticky-thread?

---

### Post by howefield on 2015-07-11
> **carlo12 said:**
> hmm...sorry but i'm new to the forum...can you please tell me what is a sticky-thread?

At the top of each forum or sub forum, you may find some posts which are permanently on view (until they are unstuck) - they are prefixed with the word sticky, funnily enough.

---

### Post by carlo12 on 2015-07-11
Ok thanks so...of what script was he talking about?

---

### Post by Vladlenin5000 on 2015-07-11
> **carlo12 said:**
> Ok thanks so...of what script was he talking about?

It's explained in that sticky and that sticky has the title "[Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108")" (I turned it into an hyperlink for your convenience).
Please post back if you have any trouble following the instructions there.

---

### Post by carlo12 on 2015-07-11
Ok thanks a lot
So this is the result : [ATTACH=CONFIG]263139[/ATTACH]
Oh and i don't know if this helps but i forgot to tell you that the error that I get from Chrome and Firefox is [COLOR=#777777][FONT=sans]DNS_PROBE_FINISHED_NO_INTERNET    

[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-07-11
OK, before anything else, I'll post your results in plain text to make it easier for others helping you:

```
########## wireless info START ##########

Report from: 11 Jul 2015 18:14 CEST +0200

Booted last: 11 Jul 2015 18:09 CEST +0200

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:2a94]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 1532:0202 Razer USA, Ltd 
Bus 006 Device 002: ID 1532:0037 Razer USA, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2001:330d D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:ba08 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
rtl8192cu              67741  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                64255  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              652777  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              494362  2 mac80211,rtlwifi

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
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7262:b8ff:fea3:1856/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:974974 (974.9 KB)  TX bytes:260913 (260.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Freebox-9318EC"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'Freebox-9318EC' [AC4]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 192.168.1.254

##### network managers ##################

Installed:

    Wicd

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Freebox-9318EC]] (600 root)
[connection] id=Freebox-9318EC | type=802-11-wireless
[802-11-wireless] ssid=Freebox-9318EC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      5   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FreeWifi_secure' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef3527508e
                    Extra: Last beacon: 1352ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'FreeWifi_secure' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000663cdb0240
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC 'FREEBOX_MAMADOU' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FREEBOX_MAMADOU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000663cdc815f
                    Extra: Last beacon: 1012ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Freebox-9318EC' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Freebox-9318EC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a6dcd4800
                    Extra: Last beacon: 108ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'FreeWifi' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a6dd27a0a
                    Extra: Last beacon: 72ms ago
          Cell 06 - Address: <MAC 'FreeWifi_secure' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e2175e8160
                    Extra: Last beacon: 460ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'FreeWifi_secure' [AC7]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a6dd29116
                    Extra: Last beacon: 140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'FreeWifi' [AC8]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e217630160
                    Extra: Last beacon: 200ms ago
          Cell 09 - Address: <MAC 'Freebox-madieu' [AC9]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Freebox-madieu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e217600160
                    Extra: Last beacon: 428ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'FreeWifi' [AC10]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef3527c094
                    Extra: Last beacon: 1284ms ago
          Cell 11 - Address: <MAC 'Bbox-90BEFE' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Bbox-90BEFE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000069e94eacf1
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Toolabarry' [AC12]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Toolabarry"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef35282fa2
                    Extra: Last beacon: 1372ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'FreeWifi_secure' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000104ab8826a
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     93FD064658D2AD5B6991075
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     94CFED30E3318E18EC4B740
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
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
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
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

[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

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

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/net-rtm8192cu.conf]
options rtl8192cu swenc=1

##### rc.local ##########################

echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   20.008508] rtl8192cu: MAC auto ON okay!
[   20.043267] rtl8192cu: Tx queue select: 0x05
[   20.422068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.470510] rtl8192cu: MAC auto ON okay!
[   29.524047] rtl8192cu: Tx queue select: 0x05
[   29.890564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.260637] rtl8192cu: MAC auto ON okay!
[   30.293519] rtl8192cu: Tx queue select: 0x05
[   30.651939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.568480] wlan0: authenticate with <MAC 'Freebox-9318EC' [AC4]>
[   33.591723] wlan0: send auth to <MAC 'Freebox-9318EC' [AC4]> (try 1/3)
[   33.685282] wlan0: authenticated
[   33.688024] wlan0: associate with <MAC 'Freebox-9318EC' [AC4]> (try 1/3)
[   33.792021] wlan0: associate with <MAC 'Freebox-9318EC' [AC4]> (try 2/3)
[   33.792275] wlan0: RX AssocResp from <MAC 'Freebox-9318EC' [AC4]> (capab=0x411 status=0 aid=1)
[   33.792322] wlan0: associated
[   33.792333] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```


So, your device is a **Realtek 8192cu** (this is what really matters, not the make/model; many manufacturers/assemblers use the same brand and model with different revision numbers for several different chipsets).
There are known issues with the default driver for this one. It should work but it doesn't. 
The usual solution is to install a driver that works:

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install [COLOR=#333333][FONT=Ubuntu]rtl8192cu-dkms[/FONT][/COLOR]
```

You may also need to blacklist the current driver **8192****cu**. Do NOT blacklist the newly installed **rtl8192cu**.

---

### Post by carlo12 on 2015-07-13
Thank you Vladlenin5000 for your help , it finally works :D\\:D/

---

### Post by bismaya on 2015-09-07
Hi Vladlenin5000,

I desperately need your help.

The  problem is almost similar to the one described in this thread. I am  unable to use WiFi on my Dell Inspiron laptop. However, the wifi works  on my ipad and mobile phone. When I plug it in via the ethernet, it  works flawlessly. I am using Ubuntu 12.04.5 and wireless driver is Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036].

I am posting the results of the wireless info script.


I followed your advice about the sticky thread and am posing the results here.

File:[ATTACH]264294[/ATTACH]


The results in plain text are:
```

########## wireless info START ##########

Report from: 07 Sep 2015 07:11 EDT -0400

Booted last: 07 Sep 2015 00:00 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.8.0-44-generic #66~precise1-Ubuntu SMP Tue Jul 15 04:01:04 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Dell Device [1028:05f3]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:64af Microdia 

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 152312  0 
mac80211              631503  1 ath9k
ath3k                  12968  0 
ath9k_common           14053  1 ath9k
bluetooth             247324  12 rfcomm,bnep,ath3k,btusb
ath9k_hw              422615  2 ath9k,ath9k_common
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
cfg80211              526422  3 ath9k,mac80211,ath
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
mxm_wmi                13021  1 nouveau
wmi                    19256  3 nouveau,dell_wmi,mxm_wmi
dell_laptop            17425  0 
dcdbas                 14449  1 dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.0.80
netmask 255.255.255.0
gateway 192.168.1.0
auto wlan0
iface wlan0 inet static
address 10.10.0.1
netmask 255.255.255.0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.137  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:649993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:363071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:947233485 (947.2 MB)  TX bytes:29465206 (29.4 MB)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.10.0.2  Bcast:10.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828490 (828.4 KB)  TX bytes:120748 (120.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Hattori_Hanzo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Hattori_Hanzo' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:72   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
10.10.0.0       0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.0.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1543     1  0 05:24 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.137
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             206.248.154.22
    DNS:             206.248.154.170

- Device: wlan0  [Hattori_Hanzo] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    This is the password: Infra, <MAC 'This is the password' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2
    Rogers92773:     Infra, <MAC 'Rogers92773' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    chandra401:      Infra, <MAC 'chandra401' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    *Hattori_Hanzo:  Infra, <MAC 'Hattori_Hanzo' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    Rogers93569:     Infra, <MAC 'Rogers93569' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    cedarbrae:       Infra, <MAC 'cedarbrae' [AC6]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 9 WPA
    Rogers62397:     Infra, <MAC 'Rogers62397' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2

  IPv4 Settings:
    Address:         10.10.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.0.1

    DNS:             8.8.4.4
    DNS:             208.67.222.222

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SPDAS]] (600 root)
[connection] id=SPDAS | type=802-11-wireless
[802-11-wireless] ssid=SPDAS | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Guptas]] (600 root)
[connection] id=Guptas | type=802-11-wireless
[802-11-wireless] ssid=Guptas | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=bismaya-Inspiron-3437 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RJPK]] (600 root)
[connection] id=RJPK | type=802-11-wireless
[802-11-wireless] ssid=RJPK | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Airport O-Zone Free WiFi]] (600 root)
[connection] id=Airport O-Zone Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=Airport O-Zone Free WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Lipu_rosy]] (600 root)
[connection] id=Lipu_rosy | type=802-11-wireless
[802-11-wireless] ssid=Lipu_rosy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hattori_Hanzo]] (600 root)
[connection] id=Hattori_Hanzo | type=802-11-wireless
[802-11-wireless] ssid=Hattori_Hanzo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOKIA Lumia 520_0866]] (600 root)
[connection] id=NOKIA Lumia 520_0866 | type=802-11-wireless
[802-11-wireless] ssid=NOKIA Lumia 520_0866 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ARRU]] (600 root)
[connection] id=ARRU | type=802-11-wireless
[802-11-wireless] ssid=ARRU | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Gopinath]] (600 root)
[connection] id=Gopinath | type=802-11-wireless
[802-11-wireless] ssid=Gopinath | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Monster]] (600 root)
[connection] id=Monster | type=802-11-wireless
[802-11-wireless] ssid=Monster | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UbuntuAdhoc]] (600 root)
[connection] id=UbuntuAdhoc | type=802-11-wireless
[802-11-wireless] ssid=UbuntuAdhoc | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/_Free_ORD_Wi-Fi]] (600 root)
[connection] id=_Free_ORD_Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=_Free_ORD_Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/_Heathrow Wi-Fi]] (600 root)
[connection] id=_Heathrow Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=_Heathrow Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Wifi_U]] (600 root)
[connection] id=Wifi_U | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=Wifi_U | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/MBlze-Wonder]] (600 root)
[connection] id=MBlze-Wonder | type=802-11-wireless
[802-11-wireless] ssid=MBlze-Wonder | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Micromax A89]] (600 root)
[connection] id=Micromax A89 | type=802-11-wireless
[802-11-wireless] ssid=Micromax A89 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BSNL]] (600 root)
[connection] id=BSNL | type=802-11-wireless
[802-11-wireless] ssid=BSNL | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CHETAN MTS]] (600 root)
[connection] id=CHETAN MTS | type=802-11-wireless
[802-11-wireless] ssid=CHETAN MTS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UbuntuAdhoc~]] (600 root)
[connection] id=UbuntuAdhoc | type=802-11-wireless
[802-11-wireless] ssid=UbuntuAdhoc | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/ARU]] (600 root)
[connection] id=ARU | type=802-11-wireless
[802-11-wireless] ssid=ARU | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Micromax A89 1]] (600 root)
[connection] id=Micromax A89 1 | type=802-11-wireless
[802-11-wireless] ssid=Micromax A89 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/anki]] (600 root)
[connection] id=anki | type=802-11-wireless
[802-11-wireless] ssid=anki | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IIT_KOLKATA]] (600 root)
[connection] id=IIT_KOLKATA | type=802-11-wireless
[802-11-wireless] ssid=IIT_KOLKATA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/chandra401]] (600 root)
[connection] id=chandra401 | type=802-11-wireless
[802-11-wireless] ssid=chandra401 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

virbr0    no frequency information.

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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Hattori_Hanzo' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"Hattori_Hanzo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e23ad4edcf
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Rogers92773' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Rogers92773"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001fa5ccf180
                    Extra: Last beacon: 268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'chandra401' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"chandra401"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000032c1163db98
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Rogers93569' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Rogers93569"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ee3793180
                    Extra: Last beacon: 19136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'This is the password' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"This is the password"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008aa39a180
                    Extra: Last beacon: 288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'cedarbrae' [AC6]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"cedarbrae"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b01fed613e
                    Extra: Last beacon: 16184ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b01fed6778
                    Extra: Last beacon: 16184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Rogers62397' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"Rogers62397"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024e3737180
                    Extra: Last beacon: 15860ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5031CBAE76B30EF3459FAA2
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[mac80211]
filename:       /lib/modules/3.8.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1FF78E380549BFAADC883E4
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath3k]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     CB17E74D27AA42F11344621
depends:        bluetooth
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 

[ath9k_common]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     3D03F9DDA976A5AB5EAA737
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     3FC27688A6C53D91F60FDBA
depends:        ath
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/3.8.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5627B8DA4AC105006A960BE
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 

[cfg80211]
filename:       /lib/modules/3.8.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     37EA28891FFED476061D81A
depends:        
intree:         Y
vermagic:       3.8.0-44-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
btcoex_enable: 0
enable_diversity: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
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

[/etc/pm/sleep.d/67hw_hook] (755 root)
case $1 in
    #suspend to disK
    hibernate)
        dbus-send --system /com/huawei/utps2/linux/powermgr com.huawei.utps2.linux.powermgr.Hibernate
        ;;
    #suspend to RAM
    suspend)
        dbus-send --system /com/huawei/utps2/linux/powermgr com.huawei.utps2.linux.powermgr.Suspend
        ;;
    #resume from disk
    thaw)
        dbus-send --system /com/huawei/utps2/linux/powermgr com.huawei.utps2.linux.powermgr.Thaw
        ;;
    #resume from RAM
    resume)
        dbus-send --system /com/huawei/utps2/linux/powermgr com.huawei.utps2.linux.powermgr.Resume
        ;;
    *)
        echo hello
        ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x05c6:0x6001 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

##### dmesg #############################

[ 3828.683547] wlan0: deauthenticating from <MAC 'Hattori_Hanzo' [AC1]> by local choice (reason=3)
[ 3833.181308] wlan0: authenticate with <MAC 'Hattori_Hanzo' [AC1]>
[ 3833.189408] wlan0: send auth to <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 3833.191495] wlan0: authenticated
[ 3833.192148] ath9k 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3833.192159] ath9k 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3833.192383] wlan0: associate with <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 3833.195018] wlan0: RX AssocResp from <MAC 'Hattori_Hanzo' [AC1]> (capab=0x411 status=0 aid=3)
[ 3833.195192] wlan0: associated
[ 3856.081799] wlan0: deauthenticating from <MAC 'Hattori_Hanzo' [AC1]> by local choice (reason=3)
[ 3858.647430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3861.435540] wlan0: authenticate with <MAC 'Hattori_Hanzo' [AC1]>
[ 3861.443610] wlan0: send auth to <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 3861.445561] wlan0: authenticated
[ 3861.445701] ath9k 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3861.445705] ath9k 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3861.447126] wlan0: associate with <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 3861.449695] wlan0: RX AssocResp from <MAC 'Hattori_Hanzo' [AC1]> (capab=0x411 status=0 aid=3)
[ 3861.449930] wlan0: associated
[ 3861.449938] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3869.444679] wlan0: deauthenticating from <MAC 'Hattori_Hanzo' [AC1]> by local choice (reason=3)
[ 3870.564606] wlan0: authenticate with <MAC 'Hattori_Hanzo' [AC1]>
[ 3870.572789] wlan0: send auth to <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 3870.574877] wlan0: authenticated
[ 3870.575180] ath9k 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3870.575186] ath9k 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3870.576268] wlan0: associate with <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 3870.578841] wlan0: RX AssocResp from <MAC 'Hattori_Hanzo' [AC1]> (capab=0x411 status=0 aid=3)
[ 3870.579030] wlan0: associated
[ 6400.086424] wlan0: deauthenticating from <MAC 'Hattori_Hanzo' [AC1]> by local choice (reason=3)
[ 6409.788981] wlan0: authenticate with <MAC 'Hattori_Hanzo' [AC1]>
[ 6409.800174] wlan0: send auth to <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 6409.802265] wlan0: authenticated
[ 6409.802561] ath9k 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 6409.802571] ath9k 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 6409.804236] wlan0: associate with <MAC 'Hattori_Hanzo' [AC1]> (try 1/3)
[ 6409.806813] wlan0: RX AssocResp from <MAC 'Hattori_Hanzo' [AC1]> (capab=0x411 status=0 aid=3)
[ 6409.807096] wlan0: associated

########## wireless info END ############

```


Can someone please help me out? It tried resetting the router, it didnt work.

Turns out that my Wireless card had a long issue with Ubuntu. Found the solutions in the forums. It started working now. Anyone having similar problems are free to use this code and see if that works. Worked for me!

```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf

sudo modprobe -rfv ath9k

sudo modprobe -v ath9k
```

Reference Thread. [http://ubuntuforums.org/archive/index.php/t-2190930.html](http://ubuntuforums.org/archive/index.php/t-2190930.html)

---

### Post by prasanna9 on 2015-09-08
Hello am not able to connect to wifi , my wifi adapter  is qualcomm  atheros AR9285 802.11b/g/n.when i try to connect it automatically  disconnect and used to ask me wifi password several tme.so can any body  please help me?
Note- kernel driver in use is ath9k

---

