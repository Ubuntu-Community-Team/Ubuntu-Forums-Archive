---
title: "Slow Wireless speed in UBUNTU 14.04"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by murat12 on 2016-03-27
okay. i have broadcom43142 wifi card. i know it has problems in linux. So i decided to buy USB wireless card. but it doesn't solve my problem. still slow download speed. in windows i can get 300 / 400 kbps. but in ubuntu i only get 30 / 40 kbps. like %90 reduced. since i get slow int speed with usb wireless adapter too i think problem is on OS or ISP or something like that. my usb wireless adapter has ralink 5370 chipset.  i have tried lot of things but still cant solve my problems. pls help me. sorry for bad english. :(



```
########## wireless info START ##########

Report from: 27 Mar 2016 20:08 EEST +0300

Booted last: 27 Mar 2016 19:34 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0940]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:2009 Lite-On Technology Corp. 
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlwifi               188416  0 
brcmsmac              569344  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
bcma                   53248  1 brcmsmac
wl                   6369280  0 
rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              712704  4 brcmsmac,rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              16384  1 rt2800lib
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
mxm_wmi                16384  1 nouveau
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20480  3 i915_bpo,acer_wmi,nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
cfg80211              524288  5 wl,iwlwifi,brcmsmac,mac80211,rt2x00lib

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:1001
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20762 (20.7 KB)  TX bytes:21682 (21.6 KB)
          Interrupt:19 

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:10.34.19.74  Bcast:10.34.31.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19031635 (19.0 MB)  TX bytes:2360771 (2.3 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

virbr0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:"KYKWIFI"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'KYKWIFI' [AC4]>   
          Bit Rate=72.2 Mb/s   Tx-Power=13 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:63  Invalid misc:346   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.34.16.1      0.0.0.0         UG    0      0        0 wlan1
10.34.16.0      0.0.0.0         255.255.240.0   U     9      0        0 wlan1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search kykwifi.com 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1019     1  0 19:33 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC2]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 35
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC4]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 65
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    Bedikar:         Infra, <MAC 'Bedikar' [AN6]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

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

- Device: wlan1  [KYKWIFI 1] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC2]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 29
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    *KYKWIFI:        Infra, <MAC 'KYKWIFI' [AC4]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 49
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22

  IPv4 Settings:
    Address:         10.34.19.74
    Prefix:          20 (255.255.240.0)
    Gateway:         10.34.16.1

    DNS:             10.106.4.20
    DNS:             8.8.8.8

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

no-auto-default=<MAC 'eth0' [IF]>,<MAC address>,16:7D:48:68:49:70,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bedikar]] (600 root)
[connection] id=Bedikar | type=802-11-wireless
[802-11-wireless] ssid=Bedikar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI 1]] (600 root)
[connection] id=KYKWIFI 1 | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan1' [IF]> | mtu=1500
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Asus]] (600 root)
[connection] id=Asus | type=802-11-wireless
[802-11-wireless] ssid=Asus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI]] (600 root)
[connection] id=KYKWIFI | type=802-11-wireless
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan0' [IF]> | mtu=1492
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dsplab2.4]] (600 root)
[connection] id=dsplab2.4 | type=802-11-wireless
[802-11-wireless] ssid=dsplab2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/free-1215N]] (600 root)
[connection] id=free-1215N | type=802-11-wireless
[802-11-wireless] ssid=free-1215N | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ab2016]] (600 root)
[connection] id=ab2016 | type=802-11-wireless
[802-11-wireless] ssid=ab2016 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Noctiluca]] (600 root)
[connection] id=Noctiluca | type=802-11-wireless
[802-11-wireless] ssid=Noctiluca | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

virbr0    no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
wlan1     13 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'KYKWIFI' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: <MAC 'KYKWIFI' [AC2]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: <MAC 'KYKWIFI' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
          Cell 04 - Address: <MAC 'KYKWIFI' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 10100ms ago
          Cell 05 - Address: <MAC 'KYKWIFI' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'KYKWIFI' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004762228143
                    Extra: Last beacon: 68ms ago
          Cell 02 - Address: <MAC 'KYKWIFI' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004762c81b12
                    Extra: Last beacon: 68ms ago

##### module infos ######################

[iwlwifi]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     884420C3D4A6AC329614AEA
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[brcmsmac]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5F866C1008CB05E51B96C2E
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[wl]
filename:       /lib/modules/3.19.0-56-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[rt2800usb]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CDB4A56A88AAEC3126F6347
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

[rt2800usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
wl
brcmsmac

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt61pci.conf]
options rt61pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   25.297763] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   25.360498] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   25.600175] r8169 0000:02:00.1 eth0: link down
[   50.924824] wlan1: authenticate with <MAC 'KYKWIFI' [AC4]>
[   50.938458] wlan1: send auth to <MAC 'KYKWIFI' [AC4]> (try 1/3)
[   50.939851] wlan1: authenticated
[   50.943452] wlan1: associate with <MAC 'KYKWIFI' [AC4]> (try 1/3)
[   50.984030] wlan1: RX AssocResp from <MAC 'KYKWIFI' [AC4]> (capab=0x421 status=0 aid=56)
[   50.987045] wlan1: associated
[   51.023555] wlan1: Limiting TX power to 13 dBm as advertised by <MAC 'KYKWIFI' [AC4]> (repeated 5 times)
[ 1488.495601] wlan1: deauthenticating from <MAC 'KYKWIFI' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1503.934270] wlan1: authenticate with <MAC 'KYKWIFI' [AC4]>
[ 1503.953115] wlan1: send auth to <MAC 'KYKWIFI' [AC4]> (try 1/3)
[ 1503.954490] wlan1: authenticated
[ 1503.954803] wlan1: associate with <MAC 'KYKWIFI' [AC4]> (try 1/3)
[ 1503.982193] wlan1: RX AssocResp from <MAC 'KYKWIFI' [AC4]> (capab=0x421 status=0 aid=56)
[ 1503.985236] wlan1: associated
[ 1504.013839] wlan1: Limiting TX power to 13 dBm as advertised by <MAC 'KYKWIFI' [AC4]>
[ 2124.598405] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

---

### Post by praseodym on 2016-03-27
It loads a lot of unnecessary drivers:
```

sudo modprobe -rfv brcmsmac iwlwifi wl rt2800usb
sudo modprobe -v wl rt2800usb
```

---

### Post by murat12 on 2016-03-27
> **praseodym said:**
> It loads a lot of unnecessary drivers:
```

sudo modprobe -rfv brcmsmac iwlwifi wl rt2800usb
sudo modprobe -v wl rt2800usb
```

did it. problem still exists.

---

### Post by chili555 on 2016-03-27
Frankly, I'd rather get the Broadcom working correctly than any rt2800usb device. I'd suggest that we try to tweak the Broadcom first before we give up and work on the USB.

If you agree, please remove the USB and set it aside for now. Next, please open a terminal and do:```
sudo gedit /etc/modules
```Use nano or kate or leafpad if you don't have the text editor gedit. Now, the file includes:```
lp
rtc
wl
brcmsmac

```Please remove the last two lines so that it reads:```
lp
rtc

```Proofread carefully, save and close the text editor.

Next, I notice this:> Region: Europe/Istanbul (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOORThe time zone you've set suggests that you are possibly at or near Istanbul. However, the country code the wireless driver is using is set to DE for Germany. It often helps connectivity if the router and its firmware are on the correct channels and match the wireless card and its driver.

Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Finally, I see this:> Cell 04 - Address: <MAC 'KYKWIFI' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=61/70  Signal level=-49 dBm  
                    [COLOR="#FF0000"]Encryption key:off[/COLOR]
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 10100ms agoHaving no encryption at all is extremely unsafe and insecure. Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Reboot the computer, again with the USB disconnected and let us see another wireless-info.

---

### Post by murat12 on 2016-03-27
thanks for the reply. i did regdomain settings. but i forgot the mention that i dont have access the router. Im staying in dormitory. We have usernames and passwords for internet accsess. So our wifi doesnt have Encryption . But this problem still exist in other networks. Like in library in windows i can get 3-5 mbps while getting 700-900 kbps in ubuntu.

---

### Post by chili555 on 2016-03-27
> **murat12 said:**
> thanks for the reply. i did regdomain settings. but i forgot the mention that i dont have access the router. Im staying in dormitory. We have usernames and passwords for internet accsess. So our wifi doesnt have Encryption . But this problem still exist in other networks. Like in library in windows i can get 3-5 mbps while getting 700-900 kbps in ubuntu.May we see a new wireless-info as you posted in the original post?

---

### Post by murat12 on 2016-03-27
here.
```

########## wireless info START ##########

Report from: 28 Mar 2016 01:28 EEST +0300

Booted last: 27 Mar 2016 19:34 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0940]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:2009 Lite-On Technology Corp. 
Bus 001 Device 026: ID 0bb4:0c03 HTC (High Tech Computer Corp.) Android Phone [Fairphone First Edition (FP1)]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
6: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              16384  1 rt2800lib
wl                   6369280  0 
brcmsmac              569344  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
bcma                   53248  1 brcmsmac
mac80211              712704  4 brcmsmac,rt2x00lib,rt2x00usb,rt2800lib
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
mxm_wmi                16384  1 nouveau
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20480  3 i915_bpo,acer_wmi,nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
cfg80211              524288  4 wl,brcmsmac,mac80211,rt2x00lib

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.34.18.141  Bcast:10.34.31.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:21113 errors:0 dropped:0 overruns:0 frame:54584
          TX packets:21204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24545022 (24.5 MB)  TX bytes:2440160 (2.4 MB)
          Interrupt:19 

##### iwconfig ##########################

eth0      no wireless extensions.

virbr0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"KYKWIFI"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'KYKWIFI' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.34.16.1      0.0.0.0         UG    0      0        0 wlan0
10.34.16.0      0.0.0.0         255.255.240.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search kykwifi.com 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1019     1  0 Mar27 ?        00:00:03 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [KYKWIFI] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
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
    *KYKWIFI:        Infra, <MAC 'KYKWIFI' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 67

  IPv4 Settings:
    Address:         10.34.18.141
    Prefix:          20 (255.255.240.0)
    Gateway:         10.34.16.1

    DNS:             10.106.4.20
    DNS:             8.8.8.8

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

no-auto-default=<MAC 'eth0' [IF]>,<MAC address>,16:7D:48:68:49:70,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bedikar]] (600 root)
[connection] id=Bedikar | type=802-11-wireless
[802-11-wireless] ssid=Bedikar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI 1]] (600 root)
[connection] id=KYKWIFI 1 | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC address> | mtu=1500
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Asus]] (600 root)
[connection] id=Asus | type=802-11-wireless
[802-11-wireless] ssid=Asus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI]] (600 root)
[connection] id=KYKWIFI | type=802-11-wireless
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan0' [IF]> | mtu=1492
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dsplab2.4]] (600 root)
[connection] id=dsplab2.4 | type=802-11-wireless
[802-11-wireless] ssid=dsplab2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/free-1215N]] (600 root)
[connection] id=free-1215N | type=802-11-wireless
[802-11-wireless] ssid=free-1215N | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ab2016]] (600 root)
[connection] id=ab2016 | type=802-11-wireless
[802-11-wireless] ssid=ab2016 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Noctiluca]] (600 root)
[connection] id=Noctiluca | type=802-11-wireless
[802-11-wireless] ssid=Noctiluca | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

virbr0    no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.442 GHz (Channel 7)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'KYKWIFI' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CDB4A56A88AAEC3126F6347
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[wl]
filename:       /lib/modules/3.19.0-56-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[brcmsmac]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5F866C1008CB05E51B96C2E
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 wd_disable=1 swcrypto=1 led_mode=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt61pci.conf]
options rt61pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[19056.687900] ieee80211 phy3: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[21252.339530] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)

########## wireless info END ############


```

---

### Post by Hadaka on 2016-03-27
Hi, your Regdomain is unchanged, please Copy and paste these 2 lines one line at a time.
```
sudo iw reg set TR
sudo sed -i 's/^REG.*=$/&TR/' /etc/default/crda
```
thanks

---

### Post by murat12 on 2016-03-27
> **Hadaka said:**
> Hi, your Regdomain is unchanged, please Copy and paste these 2 lines one line at a time.
```
sudo iw reg set TR
sudo sed -i 's/^REG.*=$/&TR/' /etc/default/crda
```
thanks

did it thanks. problem still exists. should i reboot system ?

---

### Post by jeremy31 on 2016-03-27
Reboot and run the wireless script again before doing anything else, post the new results

---

### Post by chili555 on 2016-03-27
> **murat12 said:**
> did it thanks. problem still exists. should i reboot system ?Yes, because all the wrong drivers are still loaded. A new wireless-info, please.

---

### Post by murat12 on 2016-03-27
i have restarted system. here is the new wireless-info.
```



########## wireless info START ##########

Report from: 28 Mar 2016 02:18 EEST +0300

Booted last: 28 Mar 2016 02:17 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0940]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:2009 Lite-On Technology Corp. 
Bus 001 Device 006: ID 0bb4:0c03 HTC (High Tech Computer Corp.) Android Phone [Fairphone First Edition (FP1)]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

wl                   6369280  0 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
cfg80211              524288  1 wl
mxm_wmi                16384  1 nouveau
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20480  3 i915_bpo,acer_wmi,nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.34.18.141  Bcast:10.34.31.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:2734
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72672 (72.6 KB)  TX bytes:42594 (42.5 KB)
          Interrupt:19 

##### iwconfig ##########################

eth0      no wireless extensions.

virbr0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"KYKWIFI"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'KYKWIFI' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.34.16.1      0.0.0.0         UG    0      0        0 wlan0
10.34.16.0      0.0.0.0         255.255.240.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search kykwifi.com 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root       994     1  0 02:17 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [KYKWIFI] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
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
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC3]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 54
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC2]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    *KYKWIFI:        Infra, <MAC 'KYKWIFI' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 67

  IPv4 Settings:
    Address:         10.34.18.141
    Prefix:          20 (255.255.240.0)
    Gateway:         10.34.16.1

    DNS:             10.106.4.20
    DNS:             8.8.8.8

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

no-auto-default=<MAC 'eth0' [IF]>,<MAC address>,16:7D:48:68:49:70,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bedikar]] (600 root)
[connection] id=Bedikar | type=802-11-wireless
[802-11-wireless] ssid=Bedikar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI 1]] (600 root)
[connection] id=KYKWIFI 1 | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC address> | mtu=1500
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Asus]] (600 root)
[connection] id=Asus | type=802-11-wireless
[802-11-wireless] ssid=Asus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI]] (600 root)
[connection] id=KYKWIFI | type=802-11-wireless
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan0' [IF]> | mtu=1492
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dsplab2.4]] (600 root)
[connection] id=dsplab2.4 | type=802-11-wireless
[802-11-wireless] ssid=dsplab2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/free-1215N]] (600 root)
[connection] id=free-1215N | type=802-11-wireless
[802-11-wireless] ssid=free-1215N | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ab2016]] (600 root)
[connection] id=ab2016 | type=802-11-wireless
[802-11-wireless] ssid=ab2016 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Noctiluca]] (600 root)
[connection] id=Noctiluca | type=802-11-wireless
[802-11-wireless] ssid=Noctiluca | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

virbr0    no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'KYKWIFI' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
          Cell 02 - Address: <MAC 'KYKWIFI' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 5876ms ago
          Cell 03 - Address: <MAC 'KYKWIFI' [AC3]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
          Cell 04 - Address: <MAC 'KYKWIFI' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
          Cell 05 - Address: <MAC 'KYKWIFI' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-56-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 wd_disable=1 swcrypto=1 led_mode=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt61pci.conf]
options rt61pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   16.998535] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-04ca-2009.hcd failed with error -2
[   16.998540] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-04ca-2009.hcd not found
[   24.780828] r8169 0000:02:00.1 eth0: link down
[   93.137732] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by Hadaka on 2016-03-27
Hi your wireless report is still showing incorrect values for "iw reg get"
please Copy and paste one line at a time..
```
sudo iw reg set TR
sudo sed -i 's/^REG.*=$/&TR/' /etc/default/crda
```
please post the output of these commands.
thanks

---

### Post by murat12 on 2016-03-28
> **Hadaka said:**
> Hi your wireless report is still showing incorrect values for "iw reg get"
please Copy and paste one line at a time..
```
sudo iw reg set TR
sudo sed -i 's/^REG.*=$/&TR/' /etc/default/crda
```
please post the output of these commands.
thanks

thanks for the answer. i did what you said. theres no output. when i run ```
iw reg get
``` after thos commands i get 
```
country 98:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 20), (N/A, 20), NO-OUTDOOR
    (5250 - 5330 @ 20), (N/A, 20), NO-OUTDOOR, DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR 
```
output. but after reboot its gone.how to make it permament.

here is the new wireles info
```


########## wireless info START ##########

Report from: 28 Mar 2016 15:22 EEST +0300

Booted last: 28 Mar 2016 15:17 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0940]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:2009 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6369280  0 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
mxm_wmi                16384  1 nouveau
cfg80211              524288  1 wl
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  20480  3 i915_bpo,acer_wmi,nouveau

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.34.18.141  Bcast:10.34.31.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1420 errors:0 dropped:0 overruns:0 frame:3059
          TX packets:1774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1127918 (1.1 MB)  TX bytes:289710 (289.7 KB)
          Interrupt:19 

##### iwconfig ##########################

eth0      no wireless extensions.

virbr0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"KYKWIFI"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'KYKWIFI' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.34.16.1      0.0.0.0         UG    0      0        0 wlan0
10.34.16.0      0.0.0.0         255.255.240.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search kykwifi.com 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root       926     1  0 15:17 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [KYKWIFI] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
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
    FLORA_YURDU:     Infra, <MAC 'FLORA_YURDU' [AN1]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 7 WPA2
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AN3]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 14
    *KYKWIFI:        Infra, <MAC 'KYKWIFI' [AC1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 59

  IPv4 Settings:
    Address:         10.34.18.141
    Prefix:          20 (255.255.240.0)
    Gateway:         10.34.16.1

    DNS:             10.106.4.20
    DNS:             8.8.8.8

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

no-auto-default=<MAC 'eth0' [IF]>,<MAC address>,16:7D:48:68:49:70,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bedikar]] (600 root)
[connection] id=Bedikar | type=802-11-wireless
[802-11-wireless] ssid=Bedikar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI 1]] (600 root)
[connection] id=KYKWIFI 1 | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC address> | mtu=1500
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Asus]] (600 root)
[connection] id=Asus | type=802-11-wireless
[802-11-wireless] ssid=Asus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI]] (600 root)
[connection] id=KYKWIFI | type=802-11-wireless
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan0' [IF]> | mtu=1492
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dsplab2.4]] (600 root)
[connection] id=dsplab2.4 | type=802-11-wireless
[802-11-wireless] ssid=dsplab2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/free-1215N]] (600 root)
[connection] id=free-1215N | type=802-11-wireless
[802-11-wireless] ssid=free-1215N | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ab2016]] (600 root)
[connection] id=ab2016 | type=802-11-wireless
[802-11-wireless] ssid=ab2016 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Noctiluca]] (600 root)
[connection] id=Noctiluca | type=802-11-wireless
[802-11-wireless] ssid=Noctiluca | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country 98:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 20), (N/A, 20), NO-OUTDOOR
    (5250 - 5330 @ 20), (N/A, 20), NO-OUTDOOR, DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

virbr0    no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'KYKWIFI' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-56-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 wd_disable=1 swcrypto=1 led_mode=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt61pci.conf]
options rt61pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   17.175861] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-04ca-2009.hcd not found
[   17.205355] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.209910] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.355222] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   23.384678] r8169 0000:02:00.1 eth0: link down
[  332.732080] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############



```

---

### Post by chili555 on 2016-03-28
> in ubuntu i only get 30 / 40 kbps. The card and driver think you can go a fair bit faster:> Capabilities:
    Speed:           72 Mb/s
Now, what is your actual speed as shown at [http://www.speedtest.net/](http://www.speedtest.net/)  ?

---

### Post by Hadaka on 2016-03-28
Hi please do again, COPY and paste..
```
sudo iw reg set TR
sudo sed -i 's/^REG.*=$/&TR/' /etc/default/crda
```
  
To make this permanent please do..
```
sudo gedit /etc/default/crda
```
it will look like this..
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=**[COLOR=#ff0000]98[/COLOR]**
```
Turkish.
```
"de&#287;i&#351;im **[COLOR=#ff0000]98[/COLOR]** için **[COLOR=#ff0000]TR[/COLOR]**"
"de&#287;i&#351;tirmek 98 ile TR
```
 Change 
REGDOMAIN=**[COLOR=#ff0000]98[/COLOR]** to REGDOMAIN=**[COLOR=#ff0000]TR[/COLOR]**
Be sure to use capitol letters,uppercase,NO spaces.
then when finished, click **Save** then exit.
boot and post the output of..
```
cat /etc/default/crda
```
thanks.

---

### Post by murat12 on 2016-03-28
> **Hadaka said:**
> Hi please do again, COPY and paste..
```
sudo iw reg set TR
sudo sed -i 's/^REG.*=$/&TR/' /etc/default/crda
```
  
To make this permanent please do..
```
sudo gedit /etc/default/crda
```
it will look like this..
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=**[COLOR=#ff0000]98[/COLOR]**
```
Turkish.
```
"de&#287;i&#351;im **[COLOR=#ff0000]98[/COLOR]** için **[COLOR=#ff0000]TR[/COLOR]**"
"de&#287;i&#351;tirmek 98 ile TR
```
 Change 
REGDOMAIN=**[COLOR=#ff0000]98[/COLOR]** to REGDOMAIN=**[COLOR=#ff0000]TR[/COLOR]**
Be sure to use capitol letters,uppercase,NO spaces.
then when finished, click **Save** then exit.
boot and post the output of..
```
cat /etc/default/crda
```
thanks.

ok. did it again. here is output.
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=TR



```

speedtest results. dont believe it lol. 1Mbps is lie. i onyl get 0.3 - 0.5 Mbps.  also it should be like 3-5 Mbps. 
[URL="http://www.speedtest.net/my-result/5204797885"][IMG]http://www.speedtest.net/result/5204797885.png[/IMG]
[/URL]

---

### Post by praseodym on 2016-03-28
Try a newer driver:
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```
Reboot

---

### Post by murat12 on 2016-03-28
did it. problem still exists.
new wireless info.
```

########## wireless info START ##########

Report from: 29 Mar 2016 01:34 EEST +0300

Booted last: 29 Mar 2016 01:28 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0940]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:2009 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

wl                   6447104  0 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cfg80211              524288  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  20480  3 i915_bpo,acer_wmi,nouveau

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.34.18.141  Bcast:10.34.31.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:12184 errors:0 dropped:0 overruns:0 frame:24941
          TX packets:15461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10628714 (10.6 MB)  TX bytes:10326536 (10.3 MB)
          Interrupt:19 

##### iwconfig ##########################

eth0      no wireless extensions.

virbr0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"KYKWIFI"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'KYKWIFI' [AC1]>   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.34.16.1      0.0.0.0         UG    0      0        0 wlan0
10.34.16.0      0.0.0.0         255.255.240.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search kykwifi.com 8.8.4.4

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1002     1  0 01:28 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [KYKWIFI] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
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
    Connectify-cnnctfy: Infra, <MAC 'Connectify-cnnctfy' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC4]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 47
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    *KYKWIFI:        Infra, <MAC 'KYKWIFI' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 68
    KYKWIFI:         Infra, <MAC 'KYKWIFI' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20

  IPv4 Settings:
    Address:         10.34.18.141
    Prefix:          20 (255.255.240.0)
    Gateway:         10.34.16.1

    DNS:             10.106.4.20
    DNS:             8.8.8.8

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

no-auto-default=<MAC 'eth0' [IF]>,<MAC address>,16:7D:48:68:49:70,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bedikar]] (600 root)
[connection] id=Bedikar | type=802-11-wireless
[802-11-wireless] ssid=Bedikar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI 1]] (600 root)
[connection] id=KYKWIFI 1 | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC address> | mtu=1500
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Asus]] (600 root)
[connection] id=Asus | type=802-11-wireless
[802-11-wireless] ssid=Asus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI]] (600 root)
[connection] id=KYKWIFI | type=802-11-wireless
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan0' [IF]> | mtu=1492
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dsplab2.4]] (600 root)
[connection] id=dsplab2.4 | type=802-11-wireless
[802-11-wireless] ssid=dsplab2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/free-1215N]] (600 root)
[connection] id=free-1215N | type=802-11-wireless
[802-11-wireless] ssid=free-1215N | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ab2016]] (600 root)
[connection] id=ab2016 | type=802-11-wireless
[802-11-wireless] ssid=ab2016 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Noctiluca]] (600 root)
[connection] id=Noctiluca | type=802-11-wireless
[802-11-wireless] ssid=Noctiluca | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country 98:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 20), (N/A, 20), NO-OUTDOOR
    (5250 - 5330 @ 20), (N/A, 20), NO-OUTDOOR, DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

virbr0    no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'KYKWIFI' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
          Cell 02 - Address: <MAC 'Connectify-cnnctfy' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Connectify-cnnctfy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'KYKWIFI' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
          Cell 04 - Address: <MAC 'KYKWIFI' [AC4]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"KYKWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-56-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
license:        MIXED/Proprietary
srcversion:     0A5EF81B9A5728319E2F56E
depends:        cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 wd_disable=1 swcrypto=1 led_mode=1
options iwlwifi wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt61pci.conf]
options rt61pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   16.815315] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-04ca-2009.hcd failed with error -2
[   16.815322] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-04ca-2009.hcd not found
[   25.530075] r8169 0000:02:00.1 eth0: link down

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-03-28
I would try ```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```

Delete the line no-auto-default
and changed managed=true to managed=false
Save and reboot

---

### Post by murat12 on 2016-03-28
did it. problem still exists.  i have 2Mbps speedtest result now. But apt-get still downlading updates etc in 30-40kbps.Also i have tried uget and its slow too. :(

---

### Post by murat12 on 2016-03-29
im in school now. here is the speedtes resuslts.
[[IMG]http://www.speedtest.net/result/5206350501.png[/IMG]]("http://www.speedtest.net/my-result/5206350501")

but when i tried to install update via apt-get (i have selected best server from meniu). i only get 100-300 kbps. some time it jump around 600-700 but immideatly drop again. so again its like %80 - 90 reduced.
here new wireless info.
```

########## wireless info START ##########

Report from: 29 Mar 2016 12:08 EEST +0300

Booted last: 29 Mar 2016 11:35 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0940]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:2009 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wl                   6447104  0 
mxm_wmi                16384  1 nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
cfg80211              524288  1 wl
video                  20480  3 i915_bpo,acer_wmi,nouveau

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.158.127  Bcast:192.168.159.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179945 errors:0 dropped:0 overruns:0 frame:51141
          TX packets:83224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169175765 (169.1 MB)  TX bytes:19030144 (19.0 MB)
          Interrupt:19 

##### iwconfig ##########################

eth0      no wireless extensions.

virbr0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'eduroam' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.144.1   0.0.0.0         UG    0      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
192.168.144.0   0.0.0.0         255.255.240.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search ktu.edu.tr

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1008     1  0 11:35 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [eduroam] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC 'eduroam' [AN1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2 Enterprise
    KTU-Portal:      Infra, <MAC 'KTU-Portal' [AC2]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 94
    KTU-Portal:      Infra, <MAC 'KTU-Portal' [AC3]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 35
    *eduroam:        Infra, <MAC 'eduroam' [AC1]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2 Enterprise

  IPv4 Settings:
    Address:         192.168.158.127
    Prefix:          20 (255.255.240.0)
    Gateway:         192.168.144.1

    DNS:             10.0.0.126

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bedikar]] (600 root)
[connection] id=Bedikar | type=802-11-wireless
[802-11-wireless] ssid=Bedikar | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI 1]] (600 root)
[connection] id=KYKWIFI 1 | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC address> | mtu=1500
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Asus]] (600 root)
[connection] id=Asus | type=802-11-wireless
[802-11-wireless] ssid=Asus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KYKWIFI]] (600 root)
[connection] id=KYKWIFI | type=802-11-wireless | permissions=user:murat:;
[802-11-wireless] ssid=KYKWIFI | mac-address=<MAC 'wlan0' [IF]> | mtu=1492
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dsplab2.4]] (600 root)
[connection] id=dsplab2.4 | type=802-11-wireless
[802-11-wireless] ssid=dsplab2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/free-1215N]] (600 root)
[connection] id=free-1215N | type=802-11-wireless
[802-11-wireless] ssid=free-1215N | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ab2016]] (600 root)
[connection] id=ab2016 | type=802-11-wireless
[802-11-wireless] ssid=ab2016 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Noctiluca]] (600 root)
[connection] id=Noctiluca | type=802-11-wireless
[802-11-wireless] ssid=Noctiluca | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country TR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 20), (N/A, 20)
    (5250 - 5330 @ 20), (N/A, 20), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

virbr0    no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency:2.447 GHz (Channel 8)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'eduroam' [AC1]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'KTU-Portal' [AC2]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"KTU-Portal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 03 - Address: <MAC 'KTU-Portal' [AC3]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"KTU-Portal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-56-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
license:        MIXED/Proprietary
srcversion:     0A5EF81B9A5728319E2F56E
depends:        cfg80211
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0D:22:80:B1:1C:0F:54:77:D5:8C:80:D7:06:21:62:5D:AE:0F:BC:8D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 wd_disable=1 swcrypto=1 led_mode=1
options iwlwifi wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rt61pci.conf]
options rt61pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  509.361247] WARNING: CPU: 3 PID: 4062 at /build/linux-lts-vivid-ZTSmDy/linux-lts-vivid-3.19.0/drivers/base/firmware_class.c:1128 _request_firmware+0x469/0xbd0()
[  509.361331]  [<ffffffff81508d86>] ? _request_firmware+0x76/0xbd0
[  509.361337]  [<ffffffff81509179>] _request_firmware+0x469/0xbd0
[  509.361340]  [<ffffffff81509915>] request_firmware+0x35/0x50
[  509.361393] bluetooth hci0: firmware: brcm/BCM43142A0-04ca-2009.hcd will not be loaded
[  509.361395] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-04ca-2009.hcd not found
[  511.445737] r8169 0000:02:00.1 eth0: link down

########## wireless info END ############


```

---

### Post by chili555 on 2016-03-29
> when i tried to install update via apt-get (i have selected best server from meniu). i only get 100-300 kbps. some time it jump around 600-700 but immideatly drop again. so again its like %80 - 90 reduced.I would be shocked if the Ubuntu servers were ever much faster than that.

Frankly, if you are getting 12 Mbps from a Uni access point, I think you are as good as it gets.

---

### Post by murat12 on 2016-04-01
speedtest results showing around 2Mbit now. But when i tried to install file cant go beyond 30kbps. 

help me guys i dont want to use windows :(.

can watch 480p videos on youtube cant get dl speed more than 30-50 kbps :s

---

### Post by murat12 on 2016-04-13
i have installed manjaro linux. in manjaro thers no problem in internet speed. also in ubuntu some networks works normal but some networks are slow. starbucks like networks works fine but national academic networks which you login via web with username and password are slow. anyway i will wait to 16.04. if it solve my problem then good. otherwise i will stick with manjoro thx all ;((

---

### Post by Hadaka on 2016-04-13
Great to see you found a solution to resolve your speed issues by
loading an os that satisfies your needs. Please mark this thread solved
so others may learn from your actions for a resolution. Mark the thread
solved by going to your first post of this thread, click Thread Tools and
chose solved.
thanks.

---

