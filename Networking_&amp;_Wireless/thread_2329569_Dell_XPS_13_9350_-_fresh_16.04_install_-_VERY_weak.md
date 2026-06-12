---
title: "Dell XPS 13 9350 - fresh 16.04 install - VERY weak wifi (Intel 3160)"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by rodney-boyd-t on 2016-07-03
New laptop, Dell 13 9350 (2016 edition) touchscreen, wifi connects but very weak connection (must be next to router for it to connect).

Have tried all the suggested things I could find, and rolled most back if they didn't work (none did). Also have updated BIOS to latest too. My Wireless info below. 

On 4.4.0-28-generic kernel

Any and all help appreciated. Thanks.


```


########## wireless info START ##########


Report from: 03 Jul 2016 20:36 AEST +1000


Booted last: 03 Jul 2016 00:00 AEST +1000


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


3a:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0c45:670c Microdia 
Bus 001 Device 004: ID 04f3:20d0 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                311296  0
dell_laptop            20480  0
dell_wmi               16384  0
dcdbas                 16384  1 dell_laptop
sparse_keymap          16384  1 dell_wmi
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915_bpo,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlp58s0   Link encap:Ethernet  HWaddr <MAC 'wlp58s0' [IF1]>  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3791006 (3.7 MB)  TX bytes:1084889 (1.0 MB)


##### iwconfig ##########################


lo        no wireless extensions.


wlp58s0   IEEE 802.11abg  ESSID:"OPTUSVD33688F8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'OPTUSVD33688F8' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=18/70  Signal level=-92 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:327  Invalid misc:981   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlp58s0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlp58s0


##### resolv.conf #######################


nameserver 208.67.220.222
nameserver 208.67.220.220
nameserver 198.142.235.14


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root       684     1  0 20:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp58s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-28-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp58s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:3a:00.0/net/wlp58s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/RR]] (600 root)
[connection] id=RR | type=wifi | permissions=user:rod:;
[wifi] mac-address=<MAC 'wlp58s0' [IF1]> | mac-address-blacklist= | ssid=RR
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OPTUSVD33688F8]] (600 root)
[connection] id=OPTUSVD33688F8 | type=wifi | permissions=user:rod:;
[wifi] mac-address=<MAC 'wlp58s0' [IF1]> | mac-address-blacklist= | ssid=OPTUSVD33688F8
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Australia/Sydney (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


wlp58s0   32 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)


wlp58s0   Scan completed :
          Cell 01 - Address: <MAC 'OPTUSVD33688F8' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"OPTUSVD33688F8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000073b4125b7
                    Extra: Last beacon: 4400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     49DC02934CB3D8C312FF8E1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-28-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/4.4.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y


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
bt_coex_active: N
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1 power_save=0 bt_coex_active=0 swcrypto=0


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[  346.352762] wlp58s0: authenticated
[  346.353906] wlp58s0: associate with <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[  346.357054] wlp58s0: RX AssocResp from <MAC 'OPTUSVD33688F8' [AC1]> (capab=0x411 status=0 aid=6)
[  346.360417] wlp58s0: associated
[  346.360515] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes ready
[ 1012.616600] wlp58s0: deauthenticated from <MAC 'OPTUSVD33688F8' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 1016.152593] wlp58s0: authenticate with <MAC 'OPTUSVD33688F8' [AC1]>
[ 1016.155027] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1016.200351] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 2/3)
[ 1016.238293] wlp58s0: authenticated
[ 1016.240847] wlp58s0: associate with <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1016.257195] wlp58s0: aborting association with <MAC 'OPTUSVD33688F8' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1016.263428] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1016.384071] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1016.384087] wlp58s0: authenticate with <MAC 'OPTUSVD33688F8' [AC1]>
[ 1016.386265] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1016.432961] wlp58s0: aborting authentication with <MAC 'OPTUSVD33688F8' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1016.436389] wlp58s0: authenticate with <MAC 'OPTUSVD33688F8' [AC1]>
[ 1016.437473] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1016.437490] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 2/3)
[ 1016.437497] wlp58s0: aborting authentication with <MAC 'OPTUSVD33688F8' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1020.108826] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1020.234069] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1023.839919] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1023.959130] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1024.122419] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1024.241693] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1026.493637] wlp58s0: authenticate with <MAC 'OPTUSVD33688F8' [AC1]>
[ 1026.496228] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1026.521947] wlp58s0: authenticated
[ 1026.525630] wlp58s0: associate with <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1026.604896] wlp58s0: associate with <MAC 'OPTUSVD33688F8' [AC1]> (try 2/3)
[ 1026.673128] wlp58s0: associate with <MAC 'OPTUSVD33688F8' [AC1]> (try 3/3)
[ 1026.680137] wlp58s0: RX AssocResp from <MAC 'OPTUSVD33688F8' [AC1]> (capab=0x411 status=0 aid=6)
[ 1026.689402] wlp58s0: associated
[ 1026.689547] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes ready
[ 1046.287443] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1046.412338] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1050.103329] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1050.230409] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1053.860640] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1053.983198] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1054.118158] iwlwifi 0000:3a:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[ 1054.244467] IPv6: ADDRCONF(NETDEV_UP): wlp58s0: link is not ready
[ 1056.457329] wlp58s0: authenticate with <MAC 'OPTUSVD33688F8' [AC1]>
[ 1056.459920] wlp58s0: send auth to <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1056.461965] wlp58s0: authenticated
[ 1056.463910] wlp58s0: associate with <MAC 'OPTUSVD33688F8' [AC1]> (try 1/3)
[ 1056.467054] wlp58s0: RX AssocResp from <MAC 'OPTUSVD33688F8' [AC1]> (capab=0x411 status=0 aid=6)
[ 1056.470418] wlp58s0: associated
[ 1056.470551] IPv6: ADDRCONF(NETDEV_CHANGE): wlp58s0: link becomes ready


########## wireless info END ############



```

---

### Post by mmesh on 2016-12-05
Hi Rodney,

Have you been able to solve your problem? I also have great problems with my WiFi connection on XPS 9350 with Intel card and Ubuntu 16.04 and I was hoping that you might have found a solution...

---

### Post by chili555 on 2016-12-05
> **mmesh said:**
> Hi Rodney,

Have you been able to solve your problem? I also have great problems with my WiFi connection on XPS 9350 with Intel card and Ubuntu 16.04 and I was hoping that you might have found a solution...
I suspect that the original poster had a loose or disconnected antenna and that he is long gone.

I suggest that you start your own new question and include the information from the wireless_script mentioned in the sticky.

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

