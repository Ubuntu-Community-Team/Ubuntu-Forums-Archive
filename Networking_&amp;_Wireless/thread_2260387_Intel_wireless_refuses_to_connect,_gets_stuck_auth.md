---
title: "Intel wireless refuses to connect, gets stuck authentication loop"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by oli480 on 2015-01-11
I've tried many obvious (and not so obvious) things on the internet in order to solve this, including modprobe, installing iwl drivers, upgrading my kernel, toggling wireless, checking "available to all users" etc etc. 
 
it's worked a couple of times, but never reliably after rebooting. Network manager can see the networks, and connects fine to insecure ones, but upon trying to connect to secure networks it gets stuck in an endless loop of: trying to connect, then asking for credentials.

I've installed the latest iwl firmware and for some reason it worked, but after another reboot we are back to square one...

Below is the output of the wireless diagnosis script - 

```


########## wireless info START ##########

Report from: 11 Jan 2015 16:44 GMT +0000

Booted last: 11 Jan 2015 16:27 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-28-lowlatency #38-Ubuntu SMP PREEMPT Sat Dec 13 16:41:52 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2db Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                236379  0 
mac80211              664980  1 iwldvm
iwlwifi               183377  1 iwldvm
cfg80211              506569  3 iwlwifi,mac80211,iwldvm
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.32  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fe1a:5902/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:288897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:387161143 (387.1 MB)  TX bytes:32906090 (32.9 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
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
    3DS Use Guest :  Infra, <MAC '3DS Use Guest ' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    119CA:           Infra, <MAC '119CA' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    SKY684E9:        Infra, <MAC 'SKY684E9' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Jungleland:      Infra, <MAC 'Jungleland' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    TALKTALK-EB0AD0: Infra, <MAC 'TALKTALK-EB0AD0' [AN5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    my-networkID:     Infra, <MAC 'my-networkID' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    VM828061-2G_EXT: Infra, <MAC 'VM828061-2G_EXT' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.32
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/my-networkID]] (600 root)
[connection] id=my-networkID | type=802-11-wireless
[802-11-wireless] ssid=my-networkID | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/my-networkID 1]] (600 root)
[connection] id=my-networkID 1 | type=802-11-wireless
[802-11-wireless] ssid=my-networkID | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
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
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'my-networkID' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"my-networkID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021ac6b0044b
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '3DS Use Guest ' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"3DS Use Guest "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=6400021ac6b015ab
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SKY684E9' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SKY684E9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006dddd0dec
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '119CA' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"119CA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f1bf12c7a5
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'SKY684E9' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"SKY684E9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006dbfe61c6
                    Extra: Last beacon: 3001ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     092C5F7885F1C7B9B99605B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        48:97:64:4D:1F:53:4B:D0:2F:AF:80:60:33:E8:AC:F2:1F:84:99:63
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        48:97:64:4D:1F:53:4B:D0:2F:AF:80:60:33:E8:AC:F2:1F:84:99:63
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     BD7C2C63BC84182E21AF290
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        48:97:64:4D:1F:53:4B:D0:2F:AF:80:60:33:E8:AC:F2:1F:84:99:63
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.16.0-28-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        48:97:64:4D:1F:53:4B:D0:2F:AF:80:60:33:E8:AC:F2:1F:84:99:63
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
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0085 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    9.261868] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    9.320644] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.320650] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.320653] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.320656] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    9.320803] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    9.377886] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.720558] bluetooth hci0: Direct firmware load failed with error -2
[    9.721903] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-21e6.hcd not found
[   12.776713] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   12.783618] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   13.047299] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   13.057507] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   13.139517] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  105.460802] wlan0: authenticate with <MAC 'my-networkID' [AC1]>
[  105.465799] wlan0: send auth to <MAC 'my-networkID' [AC1]> (try 1/3)
[  105.467949] wlan0: authenticated
[  105.468161] wlan0: waiting for beacon from <MAC 'my-networkID' [AC1]>
[  109.040078] wlan0: authenticate with <MAC 'my-networkID' [AC1]>
[  109.043182] wlan0: send auth to <MAC 'my-networkID' [AC1]> (try 1/3)
[  109.045386] wlan0: authenticated
[  109.045589] wlan0: waiting for beacon from <MAC 'my-networkID' [AC1]>
[  113.016768] wlan0: authenticate with <MAC 'my-networkID' [AC1]>
[  113.018828] wlan0: send auth to <MAC 'my-networkID' [AC1]> (try 1/3)
[  113.021017] wlan0: authenticated
[  113.021215] wlan0: waiting for beacon from <MAC 'my-networkID' [AC1]>
[  117.493122] wlan0: authenticate with <MAC 'my-networkID' [AC1]>
[  117.495688] wlan0: send auth to <MAC 'my-networkID' [AC1]> (try 1/3)
[  117.497872] wlan0: authenticated
[  117.498067] wlan0: waiting for beacon from <MAC 'my-networkID' [AC1]>

########## wireless info END ############

```

I noticed that "iwldvm" is being used, and thought that might be a problem. But I'm not sure... 

Help would really be appriciated! :)

---

### Post by chili555 on 2015-01-12
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Finally, Network Manager will default to ethernet if it's available. Please make your tests with the ethernet detached.

---

### Post by oli480 on 2015-01-17
Thanks, I followed all those steps, which got my wifi working well for the past week - it even got the 5g band of my router (virgin media superhub 2) showing up!

I think changing the router settings to WPA2 and fixed channels helped the most, alongside ignoring ipv6. 

Unfortunately, during the past couple of days, the 5G portion disappeared, and today my laptop won't connect to networks again :( Tried restarting, switching off and on wireless / all networking, no dice. 

The difference now is that no passcode prompt comes up - it just tries connecting for a couple of minutes then gives up.

Any more ideas? Here's the wifi diagnosis details this time - 

```

########## wireless info START ##########

Report from: 17 Jan 2015 09:25 GMT +0000

Booted last: 17 Jan 2015 08:18 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-29-lowlatency #39-Ubuntu SMP PREEMPT Tue Dec 16 21:12:19 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 003: ID 0763:2027 Midiman 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 04f2:b2db Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 004: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 003: ID 1a2c:0021 China Resource Semico Co., Ltd Keyboard
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                236379  0 
mac80211              664996  1 iwldvm
iwlwifi               183507  1 iwldvm
wmi                    19193  0 
cfg80211              506569  3 iwlwifi,mac80211,iwldvm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.32  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fe1a:5902/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173629365 (173.6 MB)  TX bytes:11685469 (11.6 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
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
    3DS Use Guest :  Infra, <MAC '3DS Use Guest ' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2
    119CA:           Infra, <MAC '119CA' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    TALKTALK-EB0AD0: Infra, <MAC 'TALKTALK-EB0AD0' [AC5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SKY684E9:        Infra, <MAC 'SKY684E9' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Jungleland:      Infra, <MAC 'Jungleland' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Home:            Infra, <MAC 'Home' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    superhub2g:     Infra, <MAC 'superhub2g' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.32
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/KewPublic]] (600 root)
[connection] id=KewPublic | type=802-11-wireless
[802-11-wireless] ssid=KewPublic | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/superhub2g]] (600 root)
[connection] id=superhub2g | type=802-11-wireless
[802-11-wireless] ssid=superhub2g | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Kew]] (600 root)
[connection] id=Kew | type=802-11-wireless
[802-11-wireless] ssid=Kew | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KewVisitor]] (600 root)
[connection] id=KewVisitor | type=802-11-wireless
[802-11-wireless] ssid=KewVisitor | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CSLmembers]] (600 root)
[connection] id=CSLmembers | type=802-11-wireless
[802-11-wireless] ssid=CSLmembers | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM019265-5G]] (600 root)
[connection] id=VM019265-5G | type=802-11-wireless
[802-11-wireless] ssid=VM019265-5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Kew-Visitors]] (600 root)
[connection] id=Kew-Visitors | type=802-11-wireless
[802-11-wireless] ssid=Kew-Visitors | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
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
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'superhub2g' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"superhub2g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057731b2433
                    Extra: Last beacon: 14ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '3DS Use Guest ' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"3DS Use Guest "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=64000057731b4978
                    Extra: Last beacon: 14ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SKY684E9' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SKY684E9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007991556d57
                    Extra: Last beacon: 14ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Jungleland' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Jungleland"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000031e6690d304
                    Extra: Last beacon: 14ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'TALKTALK-EB0AD0' [AC5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-EB0AD0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ba899f7567
                    Extra: Last beacon: 14ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

2F00

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     092C5F7885F1C7B9B99605B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:36:64:ED:7A:9C:F0:4F:3E:A3:0A:31:20:56:58:5E:88:66:DF:1C
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B3A65EB1DAE59CB6B5FD971
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:36:64:ED:7A:9C:F0:4F:3E:A3:0A:31:20:56:58:5E:88:66:DF:1C
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     D335B9FC08B25C4ADA0BD33
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:36:64:ED:7A:9C:F0:4F:3E:A3:0A:31:20:56:58:5E:88:66:DF:1C
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-29-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-29-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:36:64:ED:7A:9C:F0:4F:3E:A3:0A:31:20:56:58:5E:88:66:DF:1C
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
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0085 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 3369.337883] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3369.344795] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 3369.428381] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3372.245774] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3372.252644] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 3372.334518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3373.215892] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3373.222798] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 3373.305717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3374.237354] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3374.244331] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 3374.328820] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3375.392939] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3375.394358] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3375.398041] wlan0: authenticated
[ 3375.398060] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3380.397802] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3380.401395] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3380.401416] wlan0: aborting authentication with <MAC 'superhub2g' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3383.146728] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3383.149226] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3383.151368] wlan0: authenticated
[ 3383.151404] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3388.153381] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3388.156071] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3388.156093] wlan0: aborting authentication with <MAC 'superhub2g' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3420.428347] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[ 3420.435242] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 3420.516422] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3423.183002] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3423.186827] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3423.188919] wlan0: authenticated
[ 3423.189013] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3426.240463] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3426.243020] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3426.245181] wlan0: authenticated
[ 3426.245343] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3429.692759] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3429.695331] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3429.697565] wlan0: authenticated
[ 3429.697764] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3433.594542] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3433.596882] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3433.599026] wlan0: authenticated
[ 3433.599162] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3449.131033] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3449.133463] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3449.135630] wlan0: authenticated
[ 3449.135761] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3462.040760] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3462.042379] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3462.045891] wlan0: authenticated
[ 3462.046000] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3474.948076] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3474.950888] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3474.953038] wlan0: authenticated
[ 3474.953163] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3487.819064] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3487.821725] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3487.823888] wlan0: authenticated
[ 3487.823980] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3500.765599] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3500.767934] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3500.770177] wlan0: authenticated
[ 3500.770323] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3513.749347] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3513.752286] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3513.856410] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 2/3)
[ 3513.858578] wlan0: authenticated
[ 3513.858720] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3525.950481] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3525.953114] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3525.955292] wlan0: authenticated
[ 3525.955541] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>
[ 3538.837949] wlan0: authenticate with <MAC 'superhub2g' [AC1]>
[ 3538.840569] wlan0: send auth to <MAC 'superhub2g' [AC1]> (try 1/3)
[ 3538.842734] wlan0: authenticated
[ 3538.842874] wlan0: waiting for beacon from <MAC 'superhub2g' [AC1]>

########## wireless info END ############


```

---

### Post by oli480 on 2015-01-21
This is still an issue, help please :(

Wifi never works, or is very unstable when it does...

The routers are displayed, so I connect to either the 2g or 5g band. It connects and displays the wireless icon, but doesn't successfully pull web pages. Then, usually after a few seconds, wpa_supplicant crashes (says system program problem detected) and network manager says "device not ready" or "disconnected" with no networks displayed. 

My system config is the same as in the post above

---

### Post by chili555 on 2015-01-21
> **oli480 said:**
> This is still an issue, help please :(

Wifi never works, or is very unstable when it does...

The routers are displayed, so I connect to either the 2g or 5g band. It connects and displays the wireless icon, but doesn't successfully pull web pages. Then, usually after a few seconds, wpa_supplicant crashes (says system program problem detected) and network manager says "device not ready" or "disconnected" with no networks displayed. 

My system config is the same as in the post aboveCan you confirm that you've already taken the steps I outlined in post #3?

---

### Post by oli480 on 2015-01-21
Yeah all of them, set REGDOMAIN, IPv6 to "ignore", adjusted router settings...

---

### Post by chili555 on 2015-01-21
> **oli480 said:**
> Yeah all of them, set REGDOMAIN, IPv6 to "ignore", adjusted router settings...I suggest a driver parameter:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
reboot
```Any improvements?

---

### Post by oli480 on 2015-01-21
> **chili555 said:**
> I suggest a driver parameter:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
reboot
```Any improvements?

Ah just started up the PC with these settings and it's working wirelessly straight away! :) I'll test it for a while and see if this fix lasts, then update with [solved]. 

Thanks!

FYI here's my new iwlwifi.conf with the new settings added - ```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8

```

---

### Post by oli480 on 2015-01-26
Hi there

The above settings worked like a charm for 24 hours, then the laptop reverted back to the authentication loop / saying "device not ready" or "wireless networks unavailable"... :(

Could something be getting regularly reset to a default value? Any more ideas?

---

### Post by chili555 on 2015-01-26
Could this be a router issue? Is the performance changed; either for better or worse, if you power-cycle the router?

---

### Post by oli480 on 2015-01-28
Damn, I thought I'd fixed it - removed the other iwlwifi drivers from /lib/firmware, as I thought it might be getting confused. I removed - 

```
iwlwifi-6000-4.ucode  
iwlwifi-6000g2a-6.ucode  
iwlwifi-6000g2b-6.ucode
```

Leaving only the correct 6000 driver - 

```
iwlwifi-6000g2a-5.ucode
```

Worked great after a reboot, and for a few days, but now we're back to the way it was...

> **chili555 said:**
> Could this be a router issue? Is the performance changed; either for better or worse, if you power-cycle the router?

Sometimes it connects more easily, yes, but that doesn't explain Network Manager saying "device not ready" or "disconnected" with no networks visible? If a power cycle gets the laptop to connect, it is only briefly. After a few seconds, it is dropped to "disconnected". 

All other devices on this network have very reliable wireless connections. I know I'm in range, when it works I can even connect to the 5g band.

I really appreciate your help, but I'm getting a bit frustrated.... Is there any way I can make diagnosing this easier? Would screenshots of newtork manager help?

---

### Post by chili555 on 2015-01-28
> Is there any way I can make diagnosing this easier? Would screenshots of newtork manager help?No. We understand that a disconnect has occurred and that NM has notified you. That part is trivial. Knowing *WHY* the disconnect occurred and then fixing it is hard.

After the disconnect, please run:```
cat /var/log/syslog | grep -e iwl -e 80211 | tail -n50  > wifi.txt
```Find the file wifi.txt in your user directory and post it here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)> removed the other iwlwifi drivers from /lib/firmware, as I thought it might be getting confused. Only two or three times in my years of experience have I seen the firmware version as a fixable issue and, even then, not ever on your exact device:> Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)I am not surprised that your effort was unproductive.

---

### Post by oli480 on 2015-01-28
> **chili555 said:**
> After the disconnect, please run:```
cat   /var/log/syslog | grep -e iwl -e 80211 | tail -n50  >   wifi.txt
```Find the file wifi.txt in your user directory and post  it  here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Thanks for the quick reply, here's the results of leaving it trying to connect for a while - 

[http://paste.ubuntu.com/9926329/](http://paste.ubuntu.com/9926329/)

Seems to just loop between two these two  - 
```
Jan 28 23:38:26 t430 kernel: [53258.256511] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 28 23:38:32 t430 kernel: [53263.871063] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
```
I  saw this LTR disabled thing before - what could it mean? This is when I  try and connect to the 5g portion of the router, but I get the same  output for others too.

---

### Post by chili555 on 2015-01-28
I suspect, based on this post, that it has to do with power management: [https://patchwork.ozlabs.org/patch/409301/](https://patchwork.ozlabs.org/patch/409301/)> The LTR is the handshake between the device and the root
complex about the latency allowed when the bus exits power
save. This configuration was missing and this led to high
latency in the link power up. The end user could experience
high latency in the network because of this.I would ordinarily suggest that we disable power saving to see if it helps. However, 'disable' is the default:```
$modinfo iwlwifi 
<snip>
parm:           power_save:enable WiFi power management ([COLOR="#FF0000"]default: disable[/COLOR]) (bool)
<snip>
```You can confirm:```
iwconfig
```From my machine, for example:```
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx
          Bit Rate=57.8 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR="#FF0000"]off[/COLOR]
          Link Quality=55/70  Signal level=-55 dBm  

```I frankly see nothing wrong and potentially fixable.> This is when I try and connect to the 5g portion of the router, How, exactly? Does it have its own SSID?

---

### Post by oli480 on 2015-01-29
You are right, power saving was off. 

> **chili555 said:**
> Does it have its own SSID?

It's one of these [http://www.expertreviews.co.uk/networks/wireless-routers/52755/virgin-media-new-super-hub-review](http://www.expertreviews.co.uk/networks/wireless-routers/52755/virgin-media-new-super-hub-review). Basically broadcasts a "SSID-2g" and "SSID-5g" signal at the same time. You can also set up an additional two wireless networks alongside these. Sounds great in theory but...

Here's another attempt with slightly different results, if that helps - 

```
Jan 29 08:10:52 t430 kernel: [ 1469.126162] cfg80211: World regulatory domain updated:
Jan 29 08:10:52 t430 kernel: [ 1469.126165] cfg80211:  DFS Master region: unset
Jan 29 08:10:52 t430 kernel: [ 1469.126167] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 29 08:10:52 t430 kernel: [ 1469.126169] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.126171] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.126172] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.126173] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.126175] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.126187] cfg80211: Calling CRDA for country: GB
Jan 29 08:10:52 t430 kernel: [ 1469.128708] cfg80211: Regulatory domain changed to country: GB
Jan 29 08:10:52 t430 kernel: [ 1469.128712] cfg80211:  DFS Master region: unset
Jan 29 08:10:52 t430 kernel: [ 1469.128713] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 29 08:10:52 t430 kernel: [ 1469.128715] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.128716] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 08:10:52 t430 kernel: [ 1469.128718] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 29 08:10:52 t430 kernel: [ 1469.128719] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 29 08:10:52 t430 kernel: [ 1469.128720] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 29 08:10:55 t430 kernel: [ 1471.913000] cfg80211: Calling CRDA for country: GB
Jan 29 08:10:55 t430 kernel: [ 1471.915264] cfg80211: Regulatory domain changed to country: GB
Jan 29 08:10:55 t430 kernel: [ 1471.915268] cfg80211:  DFS Master region: unset
Jan 29 08:10:55 t430 kernel: [ 1471.915269] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 29 08:10:55 t430 kernel: [ 1471.915271] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 08:10:55 t430 kernel: [ 1471.915273] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 08:10:55 t430 kernel: [ 1471.915274] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 29 08:10:55 t430 kernel: [ 1471.915275] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 29 08:10:55 t430 kernel: [ 1471.915277] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.524706] cfg80211: Calling CRDA to update world regulatory domain
Jan 29 08:11:45 t430 kernel: [ 1521.527308] cfg80211: World regulatory domain updated:
Jan 29 08:11:45 t430 kernel: [ 1521.527312] cfg80211:  DFS Master region: unset
Jan 29 08:11:45 t430 kernel: [ 1521.527314] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 29 08:11:45 t430 kernel: [ 1521.527316] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.527318] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.527319] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.527320] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.527322] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.527334] cfg80211: Calling CRDA for country: GB
Jan 29 08:11:45 t430 kernel: [ 1521.529840] cfg80211: Regulatory domain changed to country: GB
Jan 29 08:11:45 t430 kernel: [ 1521.529844] cfg80211:  DFS Master region: unset
Jan 29 08:11:45 t430 kernel: [ 1521.529845] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 29 08:11:45 t430 kernel: [ 1521.529847] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.529849] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.529850] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 29 08:11:45 t430 kernel: [ 1521.529851] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 29 08:11:45 t430 kernel: [ 1521.529853] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 29 08:11:45 t430 kernel: [ 1521.530610] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 08:11:45 t430 kernel: [ 1521.537768] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 08:11:45 t430 kernel: [ 1521.807913] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 08:11:45 t430 kernel: [ 1521.814803] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 08:11:47 t430 kernel: [ 1524.205723] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 08:11:47 t430 kernel: [ 1524.212616] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
```

---

### Post by chili555 on 2015-01-29
As much as I hate to even consider it, and because we are very low on other available options, I suggest we amend the iwlwifi.conf file:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the very last line to:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close the text editor. Reboot.

---

### Post by oli480 on 2015-01-29
> **chili555 said:**
> As much as I hate to even consider it, and because we are very low on other available options, I suggest we amend the iwlwifi.conf file:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the very last line to:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close the text editor. Reboot.

That command completely disabled wifi altogether, so I thought I'd go back to stock - comment out the modprobe "options" line, put the firmware files back, follow the modprobe commands [here]("https://wiki.debian.org/iwlwifi"), rebooted, and...this post is being written over wifi! :cool: 

We'll see how it goes, seems stable for now... although the 2G portion of the signal is invisible, which indicates to me everything's not rosy behind the scenes... 

What syslog says - 

```
Jan 29 14:46:34 t430 kernel: [   19.608807] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 29 14:46:34 t430 kernel: [   19.608808] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 29 14:46:36 t430 NetworkManager[864]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)
Jan 29 14:46:36 t430 NetworkManager[864]: <info> (wlan0): using nl80211 for WiFi device control
Jan 29 14:46:36 t430 NetworkManager[864]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Jan 29 14:46:36 t430 kernel: [   23.626795] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:46:36 t430 kernel: [   23.634052] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:46:36 t430 kernel: [   23.897590] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:46:36 t430 kernel: [   23.904429] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:46:46 t430 kernel: [   33.059008] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:46:46 t430 kernel: [   33.065858] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:46:46 t430 kernel: [   33.869224] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:46:46 t430 kernel: [   33.876071] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:47:28 t430 kernel: [   75.073888] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:47:28 t430 kernel: [   75.080744] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:47:28 t430 kernel: [   75.316274] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:47:28 t430 kernel: [   75.323112] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:47:36 t430 kernel: [   83.153456] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:47:36 t430 kernel: [   83.160469] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:47:37 t430 kernel: [   84.287386] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:47:37 t430 kernel: [   84.294285] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:15 t430 NetworkManager[864]: <error> [1422542895.880211] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Jan 29 14:48:20 t430 kernel: [  127.895378] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:20 t430 kernel: [  127.902258] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:21 t430 kernel: [  128.037604] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:21 t430 kernel: [  128.044626] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:21 t430 kernel: [  128.666723] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:21 t430 kernel: [  128.673850] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:21 t430 kernel: [  128.823049] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:21 t430 kernel: [  128.830675] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:22 t430 kernel: [  129.699284] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:22 t430 kernel: [  129.706263] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:22 t430 kernel: [  129.856734] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:22 t430 kernel: [  129.865890] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:59 t430 kernel: [  166.237975] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:59 t430 kernel: [  166.244936] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:59 t430 kernel: [  166.350876] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:59 t430 kernel: [  166.357933] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:48:59 t430 kernel: [  166.511733] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jan 29 14:48:59 t430 kernel: [  166.519025] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Jan 29 14:50:49 t430 kernel: [  276.799056] cfg80211: Calling CRDA for country: GB
Jan 29 14:50:49 t430 kernel: [  276.801294] cfg80211: Regulatory domain changed to country: GB
Jan 29 14:50:49 t430 kernel: [  276.801297] cfg80211:  DFS Master region: unset
Jan 29 14:50:49 t430 kernel: [  276.801298] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 29 14:50:49 t430 kernel: [  276.801300] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 14:50:49 t430 kernel: [  276.801302] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 29 14:50:49 t430 kernel: [  276.801303] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 29 14:50:49 t430 kernel: [  276.801304] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 29 14:50:49 t430 kernel: [  276.801306] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 29 14:54:46 t430 wpa_supplicant[4436]: nl80211: send_and_recv->nl_recvmsgs failed: -33


```

---

### Post by oli480 on 2015-01-31
Back to "normal" now, wireless drivers refuse to authenticate properly, or just not connecting. 

I get the impression we've tried all the easy options... any advice on next steps? Reinstall Ubuntu? Switch to Debian (which worked once I installed the drivers)? Scrap the router? Get a new laptop? :p

I read there's a tool that lets you run Windows wifi drivers under Linux - is that worth a shot?

---

### Post by chili555 on 2015-01-31
> I get the impression we've tried all the easy options... any advice on next steps?Yes. I suggest we now proceed to the hard options. 

Please confirm that you have implemented every step I recommended in post #3.

I recommend we try the version of iwlwifi and its associated suite backported from kernel version 3.18. Download this to your desktop [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz) Right click and select 'extract here.' Then

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.18-1
make defconfig-iwlwifi
make
sudo make install
```Reboot and give me your report. I will probably have one additional step.

---

### Post by oli480 on 2015-02-01
> **chili555 said:**
> Please confirm that you have implemented every step I recommended in post #3. Yep, just checked and they're all still set. > **chili555 said:**
> I recommend we try the version of iwlwifi and its associated suite backported from kernel version 3.18. Download this to your desktop [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz) Right click and select 'extract here.' Then  ```
sudo apt-get update sudo apt-get install linux-headers-generic build-essential cd ~/Desktop/backports-3.18-1 make defconfig-iwlwifi make sudo make install
```Reboot and give me your report. I will probably have one additional step.  Done this, and at first no wireless networks showed at all("disconnected"), then after a minute or so the 2G portion only appeared. Now it either connects and keeps asking me for credentials, or successfully connects then drops whenever I try and load a web page.

---

### Post by oli480 on 2015-02-03
Oh and in case by report you wanted the wireless debugging output, here it is - 

[http://paste.ubuntu.com/10039726/](http://paste.ubuntu.com/10039726/)

This output shows I'm connected, but as soon as I try to load a page it breaks connection and turns to - 

[http://paste.ubuntu.com/10039808/](http://paste.ubuntu.com/10039808/)

---

### Post by oli480 on 2015-02-07
Bump.. still without wifi :(

---

