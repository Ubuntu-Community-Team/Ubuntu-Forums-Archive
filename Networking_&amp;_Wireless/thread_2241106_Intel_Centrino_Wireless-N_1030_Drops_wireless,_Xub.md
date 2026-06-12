---
title: "Intel Centrino Wireless-N 1030 Drops wireless, Xubuntu 14.04"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by Ben_Shaver on 2014-08-24
Hi forums! :) After installing Xubuntu recently, I can't seem to stay connected to wireless, it's drops about every 5 minutes unfortunately. I've attached the script file that the guide at the top of the forums said to add. Any help would be greatly appreciated! I'd love to not be stuck sitting at my desk with my laptop of all things.```
########## wireless info START ##########

Report from: 24 Aug 2014 04:03 PDT -0700

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Xubuntu

##### lspci #####

01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:04d7]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2881 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 dell_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::868f:69ff:febc:4685/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:499846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:620137861 (620.1 MB)  TX bytes:21652242 (21.6 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4e80:93ff:fe77:e38b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:535320 (535.3 KB)  TX bytes:13353 (13.3 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"OrcaWiFi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC addr OrcaWiFi>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0  [OrcaWiFi] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HP-Print-CB-Deskjet 3520 series: Infra, <MAC addr HP-Print-CB-Deskjet 3520 series>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *OrcaWiFi:       Infra, <MAC addr OrcaWiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    HOME-C3E5:       Infra, <MAC addr HOME-C3E5>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    ISaidNO:         Infra, <MAC addr ISaidNO>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    HOME-0F4E:       Infra, <MAC addr HOME-0F4E>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    EmeraldDog:      Infra, <MAC addr EmeraldDog>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    EmeraldDog-guest:Infra, <MAC addr EmeraldDog-guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    HP-Print-42-ENVY 4500 series: Infra, <MAC addr HP-Print-42-ENVY 4500 series>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24
    NLWiFi:          Infra, <MAC addr NLWiFi>, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA
    733TH:           Infra, <MAC addr 733TH>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels #####

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

##### iwlist scan #####

Channel occupancy:

     2   WLAPs on   Frequency:2.412 GHz (Channel 1)
     2   WLAPs on   Frequency:2.437 GHz (Channel 6)
     4   WLAPs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr OrcaWiFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"OrcaWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004252c2ca1
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr EmeraldDog>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"EmeraldDog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bc067832f5
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr EmeraldDog-guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"EmeraldDog-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bc06784258
                    Extra: Last beacon: 24ms ago
          Cell 04 - Address: <MAC addr HP-Print-CB-Deskjet 3520 series>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-CB-Deskjet 3520 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000025539b76e9e
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000255365f1b07
                    Extra: Last beacon: 96ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC addr HOME-C3E5>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"HOME-C3E5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000074442d20f6
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HumpALump"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fe39ff95c
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr HOME-0F4E>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HOME-0F4E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5fc90c1a7
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos #####

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

##### module parameters #####

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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
# PCI device 0x8086:0x008a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   16.759789] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   16.760024] iwlwifi 0000:01:00.0: irq 48 for MSI/MSI-X
[   16.918424] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   16.936065] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.936066] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.936067] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.936069] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   16.936167] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   16.956034] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.764385] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   21.771022] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[   21.837360] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   21.844094] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[   21.927431] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   22.792452] wlan0: authenticate with <MAC addr OrcaWiFi>
[   22.798712] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[   22.802379] wlan0: authenticated
[   22.805670] wlan0: associate with <MAC addr OrcaWiFi> (try 1/3)
[   22.809674] wlan0: RX AssocResp from <MAC addr OrcaWiFi> (capab=0x431 status=0 aid=4)
[   22.815820] wlan0: associated
[   22.815829] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1450.251204] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1450.252036] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1450.355954] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[ 1450.359285] wlan0: authenticated
[ 1450.359951] wlan0: associate with <MAC addr OrcaWiFi> (try 1/3)
[ 1450.365644] wlan0: RX AssocResp from <MAC addr OrcaWiFi> (capab=0x431 status=0 aid=4)
[ 1450.372455] wlan0: associated

########## wireless info END ############


```

---

### Post by varunendra on 2014-08-25
Hi Ben,

Your access-point is using WPA/WPA2 mixed mode, please change it to pure WPA2-PSK with AES (CCMP). Also, if the channel is set to 'auto', make sure to fix it to 1 or 11 (or 'any' other channel, it's just that channels 1, 6 and 11 usually offer best signal quality). Reboot the router after saving the changes.

If this alone doesn't seem to solve the problem, additionally try a driver parameter -
```
sudo modprobe -rv iwlwifi
sudo modprobe -v iwlwifi 11n_disable=8
```
The first command will remove the driver disabling the wifi. The second one will reload it with "11n_disable=8" parameter. This change will be lost at next boot. If it seems to help, can be made permanent.

However, if they don't seem to help, please post back a fresh report with above changes applied. I recommend trying a slightly different script first as it provides slightly more info that may be useful : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Ben_Shaver on 2014-08-25
Hi varunendra, I've changed my router to only use WPA2 with AES, but can't seem to find anything "channel" related, I'm fairly new at messing with routers, and don't quite know my way around them yet. Besides that, running those two commands made it impossible to connect to wireless at all, it would simply be connecting endlessly. I ran the script you provided many times, and the output never saved... So I ran the same script as I did last time (Used ethernet to download it since wireless wasn't working, if that matters) 

```
########## wireless info START ##########


Report from: 25 Aug 2014 20:32 PDT -0700


Script from: 17 Aug 2014 02:46 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Xubuntu


##### lspci #####


01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
	Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:04d7]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2881 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
wmi                    19177  1 dell_wmi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::868f:69ff:febc:4685/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2889237 (2.8 MB)  TX bytes:200060 (200.0 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1
search home


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    HP-Print-CB-Deskjet 3520 series: Infra, <MAC addr HP-Print-CB-Deskjet 3520 series>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    ISaidNO:         Infra, <MAC addr ISaidNO>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    HOME-0F4E:       Infra, <MAC addr HOME-0F4E>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    EmeraldDog:      Infra, <MAC addr EmeraldDog>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    733TH:           Infra, <MAC addr 733TH>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    HOME-C3E5:       Infra, <MAC addr HOME-C3E5>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    HumpALump:       Infra, <MAC addr HumpALump>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    joshua:          Infra, <MAC addr joshua>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    EmeraldDog-guest:Infra, <MAC addr EmeraldDog-guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19
    linksys:         Infra, <MAC addr linksys>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    NETGEAR69:       Infra, <MAC addr NETGEAR69>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    HOME-82D2:       Infra, <MAC addr HOME-82D2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    bejnet:          Infra, <MAC addr bejnet>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HP-Print-42-ENVY 4500 series: Infra, <MAC addr HP-Print-42-ENVY 4500 series>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20
    OrcaWiFi:        Infra, <MAC addr OrcaWiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    xfinitywifi:     Infra, <MAC addr xfinitywifi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


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


##### iwlist scan #####


Channel occupancy:


     3   WLAPs on   Frequency:2.412 GHz (Channel 1)
     4   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.452 GHz (Channel 9)
     4   WLAPs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr HP-Print-CB-Deskjet 3520 series>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-CB-Deskjet 3520 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000277299f5073
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr OrcaWiFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"OrcaWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000870ee316
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr HOME-0F4E>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HOME-0F4E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d7ea98a1b7
                    Extra: Last beacon: 304ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr ISaidNO>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ISaidNO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000005ac22b5c
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr HumpALump>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"HumpALump"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000031d890c075
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr joshua>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"joshua"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014b71bd6b3
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC addr EmeraldDog>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"EmeraldDog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ddf66ca237
                    Extra: Last beacon: 540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr EmeraldDog-guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"EmeraldDog-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ddf66cad22
                    Extra: Last beacon: 540ms ago
          Cell 09 - Address: <MAC addr 733TH>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"733TH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014e3ac024b
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC addr HP-Print-42-ENVY 4500 series>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-42-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000262e433659b
                    Extra: Last beacon: 28ms ago
          Cell 11 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000002772639ba43
                    Extra: Last beacon: 480ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC addr HOME-C3E5>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"HOME-C3E5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009634198185
                    Extra: Last beacon: 284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos #####


[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512


[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


##### module parameters #####


[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1


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
# PCI device 0x8086:0x008a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   27.270997] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[   27.271242] iwlwifi 0000:01:00.0: irq 49 for MSI/MSI-X
[   27.467240] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   27.496521] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   27.496526] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   27.496528] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   27.496531] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   27.496635] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   27.519392] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   30.831194] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   30.837896] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[   30.903531] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[   30.910165] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[   30.991195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   31.913405] wlan0: authenticate with <MAC addr OrcaWiFi>
[   31.925106] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[   32.028630] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[   32.030500] wlan0: authenticated
[   32.032622] wlan0: associate with <MAC addr OrcaWiFi> (try 1/3)
[   32.036150] wlan0: RX AssocResp from <MAC addr OrcaWiFi> (capab=0x431 status=0 aid=1)
[   32.041461] wlan0: associated
[   32.041489] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  659.242899] wlan0: deauthenticated from <MAC addr OrcaWiFi> (Reason: 6)
[  659.286319] wlan0: authenticate with <MAC addr OrcaWiFi>
[  659.294934] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[  659.397850] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[  659.399596] wlan0: authenticated
[  659.401891] wlan0: associate with <MAC addr OrcaWiFi> (try 1/3)
[  659.405464] wlan0: RX AssocResp from <MAC addr OrcaWiFi> (capab=0x431 status=0 aid=1)
[  659.411881] wlan0: associated
[  755.468255] wlan0: deauthenticated from <MAC addr OrcaWiFi> (Reason: 6)
[  771.249463] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  846.657471] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[  846.664136] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[  846.773977] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  847.754224] wlan0: authenticate with <MAC addr OrcaWiFi>
[  847.763206] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[  847.868297] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[  847.870240] wlan0: authenticated
[  847.872284] wlan0: associate with <MAC addr OrcaWiFi> (try 1/3)
[  847.875792] wlan0: RX AssocResp from <MAC addr OrcaWiFi> (capab=0x431 status=0 aid=1)
[  847.881140] wlan0: associated
[  847.881173] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  847.889669] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=2)
[  847.898688] wlan0: authenticate with <MAC addr OrcaWiFi>
[  847.907382] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[  847.909165] wlan0: authenticated
[  847.912302] wlan0: associate with <MAC addr OrcaWiFi> (try 1/3)
[  847.915839] wlan0: RX AssocResp from <MAC addr OrcaWiFi> (capab=0x431 status=0 aid=1)
[  847.918240] wlan0: associated
[ 1288.589213] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)
[ 1339.041027] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1339.041293] iwlwifi 0000:01:00.0: irq 49 for MSI/MSI-X
[ 1339.043399] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[ 1339.067027] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 1339.067032] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 1339.067035] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 1339.067038] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[ 1339.067160] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 1339.084418] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1339.094916] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 1339.102270] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[ 1339.171561] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 1339.178183] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[ 1339.300652] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 1349.921062] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 1349.927751] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[ 1350.035302] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1357.332933] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[ 1357.339589] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[ 1357.459015] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1367.519255] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1367.530705] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1367.636533] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[ 1367.638425] wlan0: authenticated
[ 1372.539580] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)
[ 1382.664333] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1382.673226] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1382.775919] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[ 1382.777698] wlan0: authenticated
[ 1387.677285] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)
[ 1398.197938] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1398.206568] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1398.311714] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[ 1398.313675] wlan0: authenticated
[ 1403.215527] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)
[ 1414.244918] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1414.253631] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1414.359714] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[ 1414.361581] wlan0: authenticated
[ 1419.259305] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)
[ 1431.320731] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1431.330191] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1431.436561] wlan0: send auth to <MAC addr OrcaWiFi> (try 2/3)
[ 1431.439558] wlan0: authenticated
[ 1436.339159] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)
[ 1456.374411] wlan0: authenticate with <MAC addr OrcaWiFi>
[ 1456.383704] wlan0: send auth to <MAC addr OrcaWiFi> (try 1/3)
[ 1456.386350] wlan0: authenticated
[ 1461.391447] wlan0: deauthenticating from <MAC addr OrcaWiFi> by local choice (reason=3)


########## wireless info END ############
```

---

### Post by varunendra on 2014-08-26
Yeah, that script does have a bug in one of its 'sed' commands that sometimes causes a blank file for some users, that's why I used the word 'first' (assuming you may need to run the regular one).

Anyway, it doesn't look like the encryption change took effect -
> **Ben_Shaver said:**
> ```
          Cell 02 - Address: <MAC addr OrcaWiFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"OrcaWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000870ee316
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    **IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1**
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
I usually don't believe the nm-tool part shown immediately after a change, but the 'iwlist scan' part quoted above shows live results, and it is still showing WPA (1) there. Did you save the change before rebooting the router? If yes, perhaps try again and reboot the laptop too this time.

Also, regarding the driver parameter, we (I and my respected senior chili555) were doing some tests a few days earlier with iwlwifi driver, and he also reported the same connection looping problem after reloading the driver with 'modprobe'. Based on that experience, let's try making the desired change permanent and see if it helps.

ONLY if the change in encryption (confirm with "sudo iwlist scan" result as shown above) doesn't help, try the parameter in permanent mode -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot and retry to connect. Does it work now?

Reverting the above parameter change, if required, is as easy as running the command -
```
sudo sed -i '/11n_disable/ d' /etc/modprobe.d/iwlwifi.conf
```
..followed by a reboot (since manual reloading of driver causes looping trouble in your case as you saw).

---

### Post by Ben_Shaver on 2014-08-26
Thank you so much!!! :D  The last command you gave me worked! That and I couldn't find a "just WPA2-PSK" option in my router. But that doesn't seem to matter, haha. Thanks for helping me figure this out, and for taking the time to reply. I'll mark this as solved.

---

### Post by varunendra on 2014-08-26
> **Ben_Shaver said:**
> The last command you gave me worked!

:-s

So you didn't (couldn't) apply WPA2 only mode, and the 'really' _last_ command (sudo sed -i....) was about reverting the change with parameter. Then what did we change after all?

I hope by "last command" you mean the "echo options...." one. :p

Whatever that meant, glad you got it fixed. Hope it remains stable and keeps your smile as wide as this - :D

---

### Post by Ben_Shaver on 2014-08-26
Sorry I was kind of unclear, the echo command is what made it work, haha. As for the whole WPA2 thing, I got sorta confused, but found it and turned it on (after running the echo command and wireless was working).

---

### Post by jeremy31 on 2014-08-26
> **Ben_Shaver said:**
> Sorry I was kind of unclear, the echo command is what made it work, haha. As for the whole WPA2 thing, I got sorta confused, but found it and turned it on (after running the echo command and wireless was working).

Your PC must be fussy about the modprobe commands with iwlwifi like at least one of mine are- I have 3 laptops with Intel wifi.  On my fussy machine(s) one I run modprobe -r iwlwifi, nothing will allow me to connect other than a reboot, even when I modprobe iwlwifi back in and all the correct modules are loaded

At least you are up and running which is good

---

