---
title: "No WiFi After Recent Update on v14.04LTS"
date: 2016-06-18
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2016-06-18
OK - Now same problem on my Personal Laptop. Network Mgr shows IP Address, but have No Connectability.

Here is the printout of Wireless Info Script  to determine type of Network Hardware, etc.

```


########## wireless info START ##########

Report from: 18 Jun 2016 13:54 EDT -0400

Booted last: 18 Jun 2016 13:44 EDT -0400

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-73-generic #95~14.04.1-Ubuntu SMP Thu Jun 9 08:00:04 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xfce (from ~/.dmrc)

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30dc]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4236]
    Subsystem: Intel Corporation Device [8086:1011]
    Kernel driver in use: iwlwifi


##### PCMCIA card info ##################

PRODID_1="RICOH
"
PRODID_2="Bay8Controller
"
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=254

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                236379  0 
mac80211              660855  1 iwldvm
hp_wmi                 14017  0 
sparse_keymap          13948  1 hp_wmi
iwlwifi               183508  1 iwldvm
cfg80211              506619  3 iwlwifi,mac80211,iwldvm
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:d8400000-d8420000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.20.52  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1246 (1.2 KB)  TX bytes:10659 (10.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"FBIvan7"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'FBIvan7' [AC1]>   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.20.1    0.0.0.0         UG    0      0        0 wlan0
192.168.20.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1062     1  0 13:44 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [FBIvan7] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *FBIvan7:        Infra, <MAC 'FBIvan7' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2

  IPv4 Settings:
    Address:         192.168.20.52
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.20.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

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

[[/etc/NetworkManager/system-connections/ATT064]] (600 root)
[connection] id=ATT064 | type=802-11-wireless
[802-11-wireless] ssid=ATT064 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FBIvan7]] (600 root)
[connection] id=FBIvan7 | type=802-11-wireless
[802-11-wireless] ssid=FBIvan7 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################

Region: America/New_York (based on set time zone)

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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FBIvan7' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"FBIvan7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000497835fbc
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT954j687' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ATT954j687"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001311046eaab
                    Extra: Last beacon: 11872ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-9565' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HOME-9565"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013110248199
                    Extra: Last beacon: 6340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013110248a54
                    Extra: Last beacon: 6340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.16.0-73-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     22AB09C9D64E5F7F2B23C2E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-73-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F5:19:27:C1:C3:6B:82:36:E3:EE:CE:BB:EE:CB:E4:A3:48:DA:67:CD
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-73-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     563074BC9E04A4D9CE8255D
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-73-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F5:19:27:C1:C3:6B:82:36:E3:EE:CE:BB:EE:CB:E4:A3:48:DA:67:CD
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-73-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     BD5AA14C2C51A4A5ABF425E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-73-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F5:19:27:C1:C3:6B:82:36:E3:EE:CE:BB:EE:CB:E4:A3:48:DA:67:CD
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-73-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     824E0EB9924EE6A387D5395
depends:        
intree:         Y
vermagic:       3.16.0-73-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F5:19:27:C1:C3:6B:82:36:E3:EE:CE:BB:EE:CB:E4:A3:48:DA:67:CD
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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10f5 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4236 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   25.593537] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   25.768139] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.827565] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[   25.827797] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   25.828968] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
[   25.963145] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   25.963578] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
[   25.993193] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.037309] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   26.037759] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
[   26.171316] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   26.171755] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
[   26.201100] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.588291] wlan0: authenticate with <MAC 'FBIvan7' [AC1]>
[   32.593693] wlan0: send auth to <MAC 'FBIvan7' [AC1]> (try 1/3)
[   32.596817] wlan0: authenticated
[   32.596955] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   32.596959] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   32.600179] wlan0: associate with <MAC 'FBIvan7' [AC1]> (try 1/3)
[   32.602750] wlan0: RX AssocResp from <MAC 'FBIvan7' [AC1]> (capab=0x411 status=0 aid=1)
[   32.610214] wlan0: associated
[   32.610250] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.669563] wlan0: deauthenticating from <MAC 'FBIvan7' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   32.673152] wlan0: authenticate with <MAC 'FBIvan7' [AC1]>
[   32.674466] wlan0: send auth to <MAC 'FBIvan7' [AC1]> (try 1/3)
[   32.677152] wlan0: authenticated
[   32.677247] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   32.677250] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   32.680126] wlan0: associate with <MAC 'FBIvan7' [AC1]> (try 1/3)
[   32.687585] wlan0: RX AssocResp from <MAC 'FBIvan7' [AC1]> (capab=0x411 status=0 aid=1)
[   32.691672] wlan0: associated

########## wireless info END ############


```

I see a couple of odd things, but not sure, and don't know what to do about it.

Here is the result of ;

```

steve-o@SRRelite:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:26:55:f4:76:18
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:d8400000-d841ffff memory:d8424000-d8424fff ioport:80e0(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:68:9d:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-73-generic firmware=8.83.5.1 build 33692 ip=192.168.20.52 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:d8100000-d8101fff

```

I was afraid this was going to happen!
Any suggestions?

Thanks!

---

### Post by praseodym on 2016-06-19
Try disabling the queue of the driver:

```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi-wd.conf
```
Reboot

---

### Post by Rick St. George on 2016-06-19
Nope ... Didn't work. Whatever they did in the last update corrupted my wireless config.
Every other device gets connected, including this laptop under Win7.

Any other suggestions please how to recover the use of my laptop under Xubuntu v14.04?
Thanks!

---

### Post by Rick St. George on 2016-06-20
I notice under resolv.conf it is blank. When I look at the file, it reads "DO NOT CHANGE THE CONTENTS - IT WILL BE OVERWRITTEN".
Apparently by another file. What exactly is going on here? Anyone have a clue?
Read a "solved fix" where they changed it from 127.0.0.1 to 8.8.8.8 and it worked. But how can you change it?

For anyone interested in this issue, visit this page;
[http://unix.stackexchange.com/questions/128220/how-do-i-set-my-dns-when-resolv-conf-is-being-overwritten](http://unix.stackexchange.com/questions/128220/how-do-i-set-my-dns-when-resolv-conf-is-being-overwritten)

---

### Post by Rick St. George on 2016-06-20
Follow this line of Logic ... RESULTS OF: (just to check)

```

steve-o@SRRelite:~$ sudo iw reg get
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

steve-o@SRRelite:~$ sudo tail -n 200 /var/log/syslog
Jun 20 11:06:57 SRRelite kernel: [ 1774.822858] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
Jun 20 11:06:57 SRRelite kernel: [ 1774.823096] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jun 20 11:06:57 SRRelite kernel: [ 1774.823533] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
Jun 20 11:06:57 SRRelite wpa_supplicant[1123]: rfkill: WLAN unblocked
Jun 20 11:06:57 SRRelite NetworkManager[1107]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2401
Jun 20 11:06:57 SRRelite kernel: [ 1774.959935] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jun 20 11:06:57 SRRelite kernel: [ 1774.960400] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
Jun 20 11:06:57 SRRelite avahi-daemon[842]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.20.53.
Jun 20 11:06:57 SRRelite avahi-daemon[842]: New relevant interface wlan0.IPv4 for mDNS.
Jun 20 11:06:57 SRRelite avahi-daemon[842]: Registering new address record for 192.168.20.53 on wlan0.IPv4.
Jun 20 11:06:57 SRRelite NetworkManager[1107]: <info> (wlan0): cleaning up...
Jun 20 11:06:57 SRRelite NetworkManager[1107]: <info> (wlan0): taking down device.
Jun 20 11:06:57 SRRelite kernel: [ 1774.994250] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 20 11:06:57 SRRelite avahi-daemon[842]: Withdrawing address record for 192.168.20.53 on wlan0.
Jun 20 11:06:57 SRRelite avahi-daemon[842]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.20.53.
Jun 20 11:06:57 SRRelite avahi-daemon[842]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 20 11:06:57 SRRelite NetworkManager[1107]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 20 11:06:57 SRRelite dbus[727]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 20 11:06:57 SRRelite NetworkManager[1107]: <info> exiting (success)
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> NetworkManager (version 0.9.8.8) is starting...
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> WEXT support is enabled
Jun 20 11:06:57 SRRelite dbus[727]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> DNS: loaded plugin dnsmasq
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: init!
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: update_system_hostname
Jun 20 11:06:57 SRRelite NetworkManager[2552]:       interface-parser: parsing file /etc/network/interfaces
Jun 20 11:06:57 SRRelite NetworkManager[2552]:       interface-parser: finished parsing file /etc/network/interfaces
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPluginIfupdown: management mode: unmanaged
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: end _init.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ofono: init!
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ofono: end _init.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> Loaded plugin (null): (null)
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    Ifupdown: get unmanaged devices count: 0
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: (40501008) ... get_connections.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ifupdown: (40501008) ... get_connections (managed=false): return empty list.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile: parsing ATT064 ... 
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile:     read connection 'ATT064'
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile: parsing Wired connection 1 ... 
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile:     read connection 'Wired connection 1'
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile: parsing FBIvan7 ... 
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile:     read connection 'FBIvan7'
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile: parsing xfinitywifi ... 
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    keyfile:     read connection 'xfinitywifi'
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ofono: (738214096) ... get_connections.
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    SCPlugin-Ofono: (738214096) connections count: 0
Jun 20 11:06:57 SRRelite NetworkManager[2552]:    Ifupdown: get unmanaged devices count: 0
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver iwlwifi)
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> Networking is enabled by state file
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <warn> failed to allocate link cache: (-12) Object not found
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): carrier is OFF
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): bringing up device.
Jun 20 11:06:57 SRRelite kernel: [ 1775.197831] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
Jun 20 11:06:57 SRRelite kernel: [ 1775.274551] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): preparing device.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): using nl80211 for WiFi device control
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): bringing up device.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 20 11:06:57 SRRelite wpa_supplicant[1123]: rfkill: WLAN hard blocked
Jun 20 11:06:57 SRRelite wpa_supplicant[1123]: Could not set interface wlan0 flags (UP): Operation not possible due to RF-kill
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> WiFi now disabled by radio killswitch
Jun 20 11:06:57 SRRelite kernel: [ 1775.376213] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jun 20 11:06:57 SRRelite kernel: [ 1775.376322] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> urfkill disappeared from the bus
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> ModemManager available in the bus
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0) supports 5 scan SSIDs
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <warn> Trying to remove a non-existant call id.
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: ready -> disabled
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> (wlan0) supports 5 scan SSIDs
Jun 20 11:06:57 SRRelite wpa_supplicant[1123]: rfkill: WLAN unblocked
Jun 20 11:06:57 SRRelite kernel: [ 1775.430658] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
Jun 20 11:06:57 SRRelite kernel: [ 1775.430956] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jun 20 11:06:57 SRRelite kernel: [ 1775.431392] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
Jun 20 11:06:57 SRRelite NetworkManager[2552]: <info> WiFi now enabled by radio killswitch
Jun 20 11:06:57 SRRelite kernel: [ 1775.568206] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jun 20 11:06:57 SRRelite kernel: [ 1775.568660] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
Jun 20 11:06:57 SRRelite kernel: [ 1775.598396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 20 11:06:57 SRRelite kernel: [ 1775.619087] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jun 20 11:06:57 SRRelite kernel: [ 1775.619554] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
Jun 20 11:06:58 SRRelite kernel: [ 1775.755890] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Jun 20 11:06:58 SRRelite kernel: [ 1775.756352] iwlwifi 0000:03:00.0: Radio type=0x0-0x2-0x0
Jun 20 11:06:58 SRRelite kernel: [ 1775.786399] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 20 11:06:58 SRRelite NetworkManager[2552]: <info> (wlan0) supports 5 scan SSIDs
Jun 20 11:06:58 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 20 11:06:58 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 20 11:06:58 SRRelite NetworkManager[2552]: <warn> Trying to remove a non-existant call id.
Jun 20 11:06:58 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun 20 11:06:58 SRRelite NetworkManager[2552]: <info> (wlan0) supports 5 scan SSIDs
Jun 20 11:06:58 SRRelite wpa_supplicant[1123]: wlan0: Reject scan trigger since one is already pending
Jun 20 11:06:58 SRRelite wpa_supplicant[1123]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Auto-activating connection 'FBIvan7'.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) starting connection 'FBIvan7'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> NetworkManager state is now CONNECTING
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): preparing device.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0/wireless): connection 'FBIvan7' has security, and secrets exist.  No new secrets needed.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Config: added 'ssid' value 'FBIvan7'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Config: added 'scan_ssid' value '1'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Config: added 'psk' value '<omitted>'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Config: set interface ap_scan to 1
Jun 20 11:07:00 SRRelite wpa_supplicant[1123]: wlan0: SME: Trying to authenticate with 00:14:bf:0a:ff:e5 (SSID='FBIvan7' freq=2442 MHz)
Jun 20 11:07:00 SRRelite kernel: [ 1778.404224] wlan0: authenticate with 00:14:bf:0a:ff:e5
Jun 20 11:07:00 SRRelite kernel: [ 1778.406813] wlan0: send auth to 00:14:bf:0a:ff:e5 (try 1/3)
Jun 20 11:07:00 SRRelite wpa_supplicant[1123]: wlan0: Trying to associate with 00:14:bf:0a:ff:e5 (SSID='FBIvan7' freq=2442 MHz)
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: inactive -> associating
Jun 20 11:07:00 SRRelite kernel: [ 1778.408594] wlan0: authenticated
Jun 20 11:07:00 SRRelite kernel: [ 1778.408690] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Jun 20 11:07:00 SRRelite kernel: [ 1778.408693] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Jun 20 11:07:00 SRRelite kernel: [ 1778.412056] wlan0: associate with 00:14:bf:0a:ff:e5 (try 1/3)
Jun 20 11:07:00 SRRelite kernel: [ 1778.414475] wlan0: RX AssocResp from 00:14:bf:0a:ff:e5 (capab=0x431 status=0 aid=2)
Jun 20 11:07:00 SRRelite wpa_supplicant[1123]: wlan0: Associated with 00:14:bf:0a:ff:e5
Jun 20 11:07:00 SRRelite kernel: [ 1778.420833] wlan0: associated
Jun 20 11:07:00 SRRelite kernel: [ 1778.420871] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jun 20 11:07:00 SRRelite wpa_supplicant[1123]: wlan0: WPA: Key negotiation completed with 00:14:bf:0a:ff:e5 [PTK=CCMP GTK=CCMP]
Jun 20 11:07:00 SRRelite wpa_supplicant[1123]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:14:bf:0a:ff:e5 completed [id=0 id_str=]
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'FBIvan7'.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> dhclient started with pid 2559
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 11:07:00 SRRelite dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jun 20 11:07:00 SRRelite dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jun 20 11:07:00 SRRelite dhclient: All rights reserved.
Jun 20 11:07:00 SRRelite dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 20 11:07:00 SRRelite dhclient: 
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 20 11:07:00 SRRelite dhclient: Listening on LPF/wlan0/00:21:6a:68:9d:66
Jun 20 11:07:00 SRRelite dhclient: Sending on   LPF/wlan0/00:21:6a:68:9d:66
Jun 20 11:07:00 SRRelite dhclient: Sending on   Socket/fallback
Jun 20 11:07:00 SRRelite dhclient: DHCPREQUEST of 192.168.20.53 on wlan0 to 255.255.255.255 port 67 (xid=0xcb73a5c)
Jun 20 11:07:00 SRRelite dhclient: DHCPACK of 192.168.20.53 from 192.168.20.1
Jun 20 11:07:00 SRRelite dhclient: bound to 192.168.20.53 -- renewal in 33993 seconds.
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   address 192.168.20.53
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   prefix 24 (255.255.255.0)
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   gateway 192.168.20.1
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   nameserver '64.6.65.6'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   nameserver '209.244.0.4'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   nameserver '23.253.163.53'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info>   domain name 'hsd1.fl.comcast.net.'
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 20 11:07:00 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 20 11:07:00 SRRelite avahi-daemon[842]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.20.53.
Jun 20 11:07:00 SRRelite avahi-daemon[842]: New relevant interface wlan0.IPv4 for mDNS.
Jun 20 11:07:00 SRRelite avahi-daemon[842]: Registering new address record for 192.168.20.53 on wlan0.IPv4.
Jun 20 11:07:01 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun 20 11:07:01 SRRelite NetworkManager[2552]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 20 11:07:01 SRRelite NetworkManager[2552]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 20 11:07:01 SRRelite NetworkManager[2552]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun 20 11:07:01 SRRelite NetworkManager[2552]: <info> Policy set 'FBIvan7' (wlan0) as default for IPv4 routing and DNS.
Jun 20 11:07:01 SRRelite NetworkManager[2552]: <info> Activation (wlan0) successful, device activated.
Jun 20 11:07:01 SRRelite ntpdate[2605]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jun 20 11:07:01 SRRelite ntpdate[2605]: no servers can be used, exiting
Jun 20 11:07:02 SRRelite avahi-daemon[842]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::221:6aff:fe68:9d66.
Jun 20 11:07:02 SRRelite avahi-daemon[842]: New relevant interface wlan0.IPv6 for mDNS.
Jun 20 11:07:02 SRRelite avahi-daemon[842]: Registering new address record for fe80::221:6aff:fe68:9d66 on wlan0.*.
Jun 20 11:07:07 SRRelite NetworkManager[2552]: <info> WiFi hardware radio set enabled
Jun 20 11:07:21 SRRelite wpa_supplicant[1123]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 20 11:09:01 SRRelite CRON[2684]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Jun 20 11:09:07 SRRelite wpa_supplicant[1123]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jun 20 11:09:13 SRRelite wpa_supplicant[1123]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jun 20 11:10:30 SRRelite wpa_supplicant[1123]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 20 11:10:36 SRRelite wpa_supplicant[1123]: nl80211: send_and_recv->nl_recvmsgs failed: -33

```


Notice: 5 lines down "cancelled DHCP transaction", then further down 
"taking down device", then following it reports a BUG which dates back to 2008 at this address. 
[http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)
Next it attempts IPv6 which have "ignore" selected in Network Mgr.

Notice: During this time, I changed the DNS Servers in my Router, and notice these two lines above;
> 
Jun 20 11:07:01 SRRelite ntpdate[2605]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jun 20 11:07:01 SRRelite ntpdate[2605]: no servers can be used, exiting


===============================

This may have solved the problem; 

1. Disconnect and Disable Wireless in Network Mgr.

2. Opened Network Mgr / EDIT, Selected WiFi connection / EDIT / IPv4 Settings ... 
   Selected Automatic (DHCP) and 

3. Next Additional DNS servers: added a DNS server
   although probably wasn't necessary, as the following made a huge difference;

4. Checked "Require IPv4 addressing for this connection ..."

5. then Clicked the "Routes" button, UNCHECKED 
   "ignore automatically obtained routes", also make sure 
   "use this connection only for resources.." is unchecked.

6. Enable Wireless in Network Mgr. 

Wireless works!

For some reason "Routes" is Checked by default ... which ignores the routes!

Go figure!?!?!?

Case solved.  Holy $%&*@ Batman! I did it ;-)

---

### Post by 07kaczor on 2016-07-16
just now it happened to me, i update 14.04 at SONY Intel® Core™ i3-3217U CPU @ 1.80GHz × 4  64bit.  right now i can connect with the wire. ethernet after i unplug, its dimmed.

---

