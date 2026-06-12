---
title: "Need help with Wifi card not accepting a connection"
date: 2015-03-25
forum: Networking &amp; Wireless
---

### Post by daftgr33n on 2015-03-25
I have an HP pavilion dm4, it has a Intel Corporation Centrino Wireless-N + WiMAX 6150 in it. It sees the wifi and will attempt to connect, but thats as far as it will go.

Thanks in advance

```

########## wireless info START ##########

Report from: 25 Mar 2015 12:12 CDT -0500

Booted last: 25 Mar 2015 11:49 CDT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
    Kernel driver in use: iwlwifi

0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:1793]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 0a5c:21e1 Broadcom Corp. HP Portable SoftSailing
Bus 002 Device 003: ID 08ff:2665 AuthenTec, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:e258 Suyin Corp. HP TrueVision HD Integrated Webcam
Bus 001 Device 003: ID 8087:07d7 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: i2400m-usb:1-1.4:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
3: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630669  1 iwldvm
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fe69:b885/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17325881 (17.3 MB)  TX bytes:2597597 (2.5 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9181 (9.1 KB)  TX bytes:19297 (19.2 KB)

wmx0      Link encap:Ethernet  HWaddr <MAC 'wmx0' [IF]>  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

wmx0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             24.116.0.53
    DNS:             24.116.2.50

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    THE WIFI:        Infra, <MAC 'THE WIFI' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2
    MOTOROLA-F5149:  Infra, <MAC 'MOTOROLA-F5149' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    ATT952:          Infra, <MAC 'ATT952' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    ATT3x9a2a9:      Infra, <MAC 'ATT3x9a2a9' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29

- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wmx0' [IF]>

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

no-auto-default=<MAC address>,<MAC 'wmx0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/THE WIFI]] (600 root)
[connection] id=THE WIFI | type=802-11-wireless
[802-11-wireless] ssid=THE WIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

wmx0      no frequency information.

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

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wmx0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MOTOROLA-F5149' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MOTOROLA-F5149"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012382ba274
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT952' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ATT952"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000872915a906
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT3x9a2a9' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"ATT3x9a2a9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000014bfe99a7
                    Extra: Last beacon: 16ms ago
          Cell 04 - Address: <MAC 'THE WIFI' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"THE WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002180d23064
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     496F157C6045EF8314B48BC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-48-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
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

[cfg80211]
filename:       /lib/modules/3.13.0-48-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi bt_coex_active=0

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0886 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   20.291474] i2400m_usb 1-1.4:1.0: firmware interface version 9.3.2
[   20.301932] iwlwifi 0000:09:00.0: L1 Enabled - LTR Disabled
[   20.302136] iwlwifi 0000:09:00.0: Radio type=0x1-0x2-0x0
[   20.432003] iwlwifi 0000:09:00.0: L1 Enabled - LTR Disabled
[   20.432195] iwlwifi 0000:09:00.0: Radio type=0x1-0x2-0x0
[   20.483159] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   20.742895] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   49.978945] wlan0: authenticate with <MAC 'THE WIFI' [AC4]>
[   49.985927] wlan0: send auth to <MAC 'THE WIFI' [AC4]> (try 1/3)
[   49.989852] wlan0: authenticated
[   49.992986] wlan0: associate with <MAC 'THE WIFI' [AC4]> (try 1/3)
[   49.996912] wlan0: RX AssocResp from <MAC 'THE WIFI' [AC4]> (capab=0x411 status=0 aid=6)
[   50.001844] wlan0: associated
[   50.001900] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.077157] wlan0: deauthenticating from <MAC 'THE WIFI' [AC4]> by local choice (reason=3)
[   65.472545] wlan0: authenticate with <MAC 'THE WIFI' [AC4]>
[   65.477357] wlan0: send auth to <MAC 'THE WIFI' [AC4]> (try 1/3)
[   65.480200] wlan0: authenticated
[   65.482129] wlan0: associate with <MAC 'THE WIFI' [AC4]> (try 1/3)
[   65.485860] wlan0: RX AssocResp from <MAC 'THE WIFI' [AC4]> (capab=0x411 status=0 aid=6)
[   65.489369] wlan0: associated
[  107.623956] wlan0: deauthenticating from <MAC 'THE WIFI' [AC4]> by local choice (reason=3)
[  110.280662] wlan0: authenticate with <MAC 'THE WIFI' [AC4]>
[  110.291592] wlan0: send auth to <MAC 'THE WIFI' [AC4]> (try 1/3)
[  110.294484] wlan0: authenticated
[  110.296328] wlan0: associate with <MAC 'THE WIFI' [AC4]> (try 1/3)
[  110.300015] wlan0: RX AssocResp from <MAC 'THE WIFI' [AC4]> (capab=0x411 status=0 aid=6)
[  110.304202] wlan0: associated
[  127.120973] wlan0: deauthenticating from <MAC 'THE WIFI' [AC4]> by local choice (reason=3)
[  145.384967] iwlwifi 0000:09:00.0: RF_KILL bit toggled to disable radio.
[  145.466208] iwlwifi 0000:09:00.0: Not sending command - RF KILL
[  871.054657] iwlwifi 0000:09:00.0: RF_KILL bit toggled to enable radio.
[  871.416608] iwlwifi 0000:09:00.0: L1 Enabled - LTR Disabled
[  871.416913] iwlwifi 0000:09:00.0: Radio type=0x1-0x2-0x0
[  871.472483] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by slickymaster on 2015-03-25
Hi daftgr33n, welcome to the forums.

I'm moving your thread to the **Networking & Wireless** sub-forum, which is the proper place for it.

In order to help us, helping you, please have a read at [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") and post back here the resulting wireless-info.txt

---

### Post by daftgr33n on 2015-03-25
Sorry about that, I updated the required info.

---

