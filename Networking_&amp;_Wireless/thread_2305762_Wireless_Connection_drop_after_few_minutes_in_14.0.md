---
title: "Wireless Connection drop after few minutes in 14.04LTS"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by ladiesman2989 on 2015-12-09
hello sir i just install ubuntu 14.04 LTS in my laptop and im having wifi connection issue, seems to be dropping after 10 minutes then seems to be ok again.here is the log i attach below


[ATTACH=CONFIG]266059[/ATTACH]


```
########## wireless info START ##########

Report from: 09 Dec 2015 12:38 MYT +0800

Booted last: 09 Dec 2015 12:33 MYT +0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:00:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:050e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 8086:0189 Intel Corp. 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 1b96:0006 N-Trig 
Bus 003 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                237568  0 
mac80211              708608  1 iwldvm
iwlwifi               188416  1 iwldvm
dell_wmi               16384  0 
mxm_wmi                16384  1 nouveau
cfg80211              524288  3 iwlwifi,mac80211,iwldvm
sparse_keymap          16384  1 dell_wmi
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau

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
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1196002 (1.1 MB)  TX bytes:231802 (231.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Virus Found -Error 404"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Virus Found -Error 404' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:122   Missed beacon:0

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

root       901     1  0 12:33 ?        00:00:00 NetworkManager

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

  Wired Properties
    Carrier:         off

- Device: wlan0  [Virus Found -Error 404] --------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
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
    HomeWifi:        Infra, <MAC 'HomeWifi' [AC4]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    A2E059:          Infra, <MAC 'A2E059' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    angpunan:        Infra, <MAC 'angpunan' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 82 WEP
    annannwong:      Infra, <MAC 'annannwong' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WEP
    ong5869:         Infra, <MAC 'ong5869' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    *Virus Found -Error 404: Infra, <MAC 'Virus Found -Error 404' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 81 WPA2
    Streamyx_Mobility01: Infra, <MAC 'Streamyx_Mobility01' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WEP
    raju:            Infra, <MAC 'raju' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    alvin:           Infra, <MAC 'alvin' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    nmkm:            Infra, <MAC 'nmkm' [AC6]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WEP

  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/Virus Found -Error 404]] (600 root)
[connection] id=Virus Found -Error 404 | type=802-11-wireless
[802-11-wireless] ssid=Virus Found -Error 404 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kuala_Lumpur (based on set time zone)

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
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Virus Found -Error 404' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"Virus Found -Error 404"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000025f2ac57
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ong5869' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ong5869"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003dea6a02c
                    Extra: Last beacon: 0ms ago
          Cell 03 - Address: <MAC 'angpunan' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"angpunan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011bbd3aca4
                    Extra: Last beacon: 0ms ago
          Cell 04 - Address: <MAC 'HomeWifi' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"HomeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001297741d6
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'annannwong' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"annannwong"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e4d7f052f
                    Extra: Last beacon: 0ms ago
          Cell 06 - Address: <MAC 'nmkm' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"nmkm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000240e8f7149
                    Extra: Last beacon: 2696ms ago
          Cell 07 - Address: <MAC 'A2E059' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"A2E059"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000056632ef3c1
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Streamyx_Mobility01' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Streamyx_Mobility01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b0a60cde4
                    Extra: Last beacon: 0ms ago

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     E3CBEE01463DF37AB9C5AB1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     CF64E5D8C60C4D423DAAC64
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
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

[cfg80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EB:BC:4F:7D:1A:69:D3:75:88:1E:66:DF:A5:32:D0:F6:1E:AC:58:5E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x008a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.777460] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   15.152020] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.152023] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.152024] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.152026] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   15.152147] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   15.340726] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.251622] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   17.258355] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   17.326292] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   17.333024] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   17.392666] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.573350] r8169 0000:06:00.0 eth0: link down
[   17.573385] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.628072] wlan0: authenticate with <MAC 'Virus Found -Error 404' [AC1]>
[   18.632037] wlan0: send auth to <MAC 'Virus Found -Error 404' [AC1]> (try 1/3)
[   18.634336] wlan0: authenticated
[   18.636305] wlan0: associate with <MAC 'Virus Found -Error 404' [AC1]> (try 1/3)
[   18.640269] wlan0: RX AssocResp from <MAC 'Virus Found -Error 404' [AC1]> (capab=0x411 status=0 aid=2)
[   18.643448] wlan0: associated
[   18.643516] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.896932] wlan0: deauthenticating from <MAC 'Virus Found -Error 404' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   18.905181] wlan0: authenticate with <MAC 'Virus Found -Error 404' [AC1]>
[   18.906008] wlan0: send auth to <MAC 'Virus Found -Error 404' [AC1]> (try 1/3)
[   18.907866] wlan0: authenticated
[   18.912038] wlan0: associate with <MAC 'Virus Found -Error 404' [AC1]> (try 1/3)
[   18.916108] wlan0: RX AssocResp from <MAC 'Virus Found -Error 404' [AC1]> (capab=0x411 status=0 aid=2)
[   18.918428] wlan0: associated

########## wireless info END ############

```

---

### Post by Hadaka on 2015-12-09
Hi there are a couple of adjustments you could make that should help
first, your router ssid and the TKIP setting, please access your routers configuration
and change from TKIP to  wpa2. also..
```
Virus Found -Error 404
``` is a unique ssid but linux does not do well
with spaces in the ssid name..perhaps some underscores will help.
Since this is a new load, it is recommended that the system be brought current.
With an internet connection,preferably wired Please open a terminal and do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
then do..
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```
*IF the above changes dont help you can delete them with..
```
sudo sed -i '/^options iwlwifi 11n_disable=8/ d' /etc/modprobe.d/iwlwifi.conf
sudo sed -i '/^options mac80211 probe_wait_ms=1000/ d' /etc/modprobe.d/mac80211.conf
```

---

### Post by ladiesman2989 on 2015-12-09
thanks for the reply sir,working good so far,will report to you after two day..gonna try to download marshmallow source


working fine here sir..how to marked this thread as solved?

---

### Post by Vikas_K_R on 2015-12-12
Hi Hadaka, I got same issues with my HP laptop having Realtek RTL8723BE PCIe Wireless. It would connect for very short duration and then disconnect and again connect. Connects to IPad hotspot but won't TP-Link modem at all. Would your above solution work on my laptop? Thanks for support.

---

### Post by Hadaka on 2015-12-12
Glad that worked for you !
 please mark this thread solved by clicking TOOLS
then solved. 
thanks.


*@Vikas_K_R ,you have a totally different card
these commands will not work with it. Please start your
own thread.

---

