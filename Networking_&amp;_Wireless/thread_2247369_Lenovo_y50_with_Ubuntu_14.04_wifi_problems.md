---
title: "Lenovo y50 with Ubuntu 14.04 wifi problems"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by branimir3 on 2014-10-07
Hello, I have lenovo y50 laptop with dualboot(windows 7/ubuntu 14.04). On windows, my wifi is working fine.
However, I am having some problems on Ubuntu:
[LIST]
[*]Wireless network is inconsistent - works for a while , then stops working
[*]Works fine at first, but stops working after few minutes
[/LIST]

Here is my wireless script log:


```


########## wireless info START ##########


Report from: 07 Oct 2014 18:01 CEST +0200


Booted last: 07 Oct 2014 11:48 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
	Kernel driver in use: iwlwifi


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 174f:14b8 Syntek 
Bus 003 Device 004: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
mxm_wmi                13021  1 nouveau
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19177  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:273680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163360272 (163.3 MB)  TX bytes:57402963 (57.4 MB)


vboxnet0  Link encap:Ethernet  HWaddr <MAC 'vboxnet0' [IF]>  
          inet addr:192.168.56.1  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:16341 (16.3 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ab2:bdff:fec8:a1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1807348 (1.8 MB)  TX bytes:871922 (871.9 KB)


##### iwconfig ##########################


vboxnet0  no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"B.net_11121"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'B.net_11121' [AN7]>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:41   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.56.0    0.0.0.0         255.255.255.0   U     0      0        0 vboxnet0


##### resolv.conf #######################


nameserver 127.0.1.1


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
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off


- Device: wlan0  [B.net_11121] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           12 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Allurea:         Infra, <MAC 'Allurea' [AN1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 72 WPA2
    NTS:             Infra, <MAC 'NTS' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    ISKONOVAC-039ED0:Infra, <MAC 'ISKONOVAC-039ED0' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    B.net_08058:     Infra, <MAC 'B.net_08058' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA
    jagodica:        Infra, <MAC 'jagodica' [AN5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 52 WEP
    FT:              Infra, <MAC 'FT' [AN6]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WEP
    *B.net_11121:    Infra, <MAC 'B.net_11121' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA


  IPv4 Settings:
    Address:         192.168.0.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             83.139.105.2
    DNS:             83.139.104.2


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


[[/etc/NetworkManager/system-connections/Allurea]] (600 root)
[connection] id=Allurea | type=802-11-wireless
[802-11-wireless] ssid=Allurea | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FRITZ!Box 7330]] (600 root)
[connection] id=FRITZ!Box 7330 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7330 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/B.net_11121]] (600 root)
[connection] id=B.net_11121 | type=802-11-wireless
[802-11-wireless] ssid=B.net_11121 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Zagreb (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


vboxnet0  no frequency information.


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


vboxnet0  Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D8BB21196A865641A4A81D0
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
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
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        38:F3:B6:C6:3A:85:AF:FD:FB:BE:0E:53:33:9D:F8:E0:C6:B6:C9:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[29094.311212] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29101.595999] wlan0: authenticate with <MAC 'B.net_11121' [AN7]>
[29101.597768] wlan0: send auth to <MAC 'B.net_11121' [AN7]> (try 1/3)
[29101.600096] wlan0: authenticated
[29101.600466] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29101.602122] wlan0: associate with <MAC 'B.net_11121' [AN7]> (try 1/3)
[29101.605072] wlan0: RX AssocResp from <MAC 'B.net_11121' [AN7]> (capab=0x411 status=0 aid=17)
[29101.605841] wlan0: associated
[29101.605885] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29101.662616] wlan0: deauthenticating from <MAC 'B.net_11121' [AN7]> by local choice (reason=2)
[29101.665120] wlan0: authenticate with <MAC 'B.net_11121' [AN7]>
[29101.666653] wlan0: send auth to <MAC 'B.net_11121' [AN7]> (try 1/3)
[29101.669150] wlan0: authenticated
[29101.669259] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29101.670056] wlan0: associate with <MAC 'B.net_11121' [AN7]> (try 1/3)
[29101.672845] wlan0: RX AssocResp from <MAC 'B.net_11121' [AN7]> (capab=0x411 status=0 aid=17)
[29101.673466] wlan0: associated
[29118.228366] wlan0: deauthenticating from <MAC 'B.net_11121' [AN7]> by local choice (reason=3)
[29121.861416] wlan0: authenticate with <MAC 'B.net_11121' [AN7]>
[29121.863740] wlan0: send auth to <MAC 'B.net_11121' [AN7]> (try 1/3)
[29121.866703] wlan0: authenticated
[29121.866806] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29121.870543] wlan0: associate with <MAC 'B.net_11121' [AN7]> (try 1/3)
[29121.873474] wlan0: RX AssocResp from <MAC 'B.net_11121' [AN7]> (capab=0x411 status=0 aid=17)
[29121.874112] wlan0: associated
[29333.146805] wlan0: deauthenticated from <MAC 'B.net_11121' [AN7]> (Reason: 7)
[29333.224088] wlan0: authenticate with <MAC 'B.net_11121' [AN7]>
[29333.225895] wlan0: send auth to <MAC 'B.net_11121' [AN7]> (try 1/3)
[29333.228075] wlan0: authenticated
[29333.228395] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29333.229710] wlan0: associate with <MAC 'B.net_11121' [AN7]> (try 1/3)
[29333.232582] wlan0: RX AssocResp from <MAC 'B.net_11121' [AN7]> (capab=0x411 status=0 aid=17)
[29333.233477] wlan0: associated
[29453.497024] wlan0: deauthenticated from <MAC 'B.net_11121' [AN7]> (Reason: 7)
[29468.809170] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29617.406342] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[29617.419080] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[29624.692199] wlan0: authenticate with <MAC 'B.net_11121' [AN7]>
[29624.694019] wlan0: send auth to <MAC 'B.net_11121' [AN7]> (try 1/3)
[29624.696212] wlan0: authenticated
[29624.696449] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29624.698588] wlan0: associate with <MAC 'B.net_11121' [AN7]> (try 1/3)
[29624.701558] wlan0: RX AssocResp from <MAC 'B.net_11121' [AN7]> (capab=0x411 status=0 aid=17)
[29624.702414] wlan0: associated
[29624.702464] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[29625.695439] wlan0: deauthenticating from <MAC 'B.net_11121' [AN7]> by local choice (reason=2)
[29625.705288] wlan0: authenticate with <MAC 'B.net_11121' [AN7]>
[29625.706866] wlan0: send auth to <MAC 'B.net_11121' [AN7]> (try 1/3)
[29625.708954] wlan0: authenticated
[29625.709092] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[29625.710770] wlan0: associate with <MAC 'B.net_11121' [AN7]> (try 1/3)
[29625.713633] wlan0: RX AssocResp from <MAC 'B.net_11121' [AN7]> (capab=0x411 status=0 aid=17)
[29625.714443] wlan0: associated


########## wireless info END ############



```

---

### Post by varunendra on 2014-10-08
Welcome to the forums branimir3!

Please try this in a terminal -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
This will append an option in your 'iwlwifi.conf' file that is supposed to enable Tx aggregation on the interface. Let us know if this solves the problem.

---

### Post by branimir3 on 2014-10-13
Sorry but that didn't help too much. Connection is still unstable :/

---

### Post by jeremy31 on 2014-10-13
> **baltic said:**
> [FONT=fixedsys]options iwlwifi 11n_disable=8[/FONT]
This was working on 1030 and other old intel WiFis. 

This has worked on newer cards in 14.04 since the devs decided to fix the problems for some cards was to disable it on all intel cards.  Hopefully they will be able to come up with a quirks list so that it is enabled for cards that don't have issues with it being enabled
Here is one bug report 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)

It does appear tbat TKIP is being used on the access point, can the security be changed to WPA2-AES only?

---

### Post by Scooby-2 on 2014-10-22
> Hello, 
I tried both disabling and enabling wifi and uninstalling wireless driver from windows. None of that helped me. I also noticed everything works fine at my apartment's wifi, on both OS.


If you are saying that WiFi works fine at your apartment, but not at another physical location (e.g. lodge) under both operating systems it means there is nothing wrong with your Y50's hardware or setup, but rather the environment. It may be that there are other wireless networks using the same or adjacent channels in your lodge environment. Ideally, each network should be at least 2 channels apart, i.e. 4 networks should use channels 1, 3, 5 and 7, for example. To see what there is around you, open a terminal and type ```
sudo iwlist scan
```You are looking for the lines starting with the word Frequency, as in > Frequency:2.412 GHz (Channel 1)You may also need to run the command several times and run it with your laptop in different places in the room/building where you are having problems, as a weaker signal may not be picked up every time in every place. You may also want to switch off your own router, in case there is a network nearby using the same channel as you. With yours switched off you should be able to see a weaker signal using your channel.

I have had problems where neighbours have had wireless routers sent by the ISP (where I live there is only one ISP) and they are all set to the same channel. Also, Windows and Linux differ in the way that they cope with crosstalk/interference.

To see just the Frequencies and Channels found for each scan type ```
sudo iwlist scan|grep Frequency
```

---

### Post by wildmanne39 on 2014-10-22
You could just look at the wireless script information, it already has that information listed.
Thanks

---

### Post by jeremy31 on 2014-10-22
> **branimir3 said:**
> Hello, 
I tried both disabling and enabling wifi and uninstalling wireless driver from windows. None of that helped me. I also noticed everything works fine at my apartment's wifi, on both OS.

[FONT=courier new]Do you have control over access point named B.Net_11121 as it is using WPA(TKIP) and seems to causing issues from your wireless script, you can check your dmesg log yourself while connected to B.Net with ```
dmesg | grep TKIP
```

[/FONT]If you can make changes, change it to WPA2-AES

---

### Post by shree-cse on 2014-10-23
Hi all, I'm facing the exact same issue as the OP, please find my wireless script. Please help, I'm new to this


```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Shreelu-Lenovo-Y50-70 3.18.0-031800rc1-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4710HQ CPU @ 2.50GHz
Memory : 7896 MB
Uptime : 09:51:12 up 10 min,  2 users,  load average: 0.18, 0.34, 0.29




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 5986:055e Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"<MAC ID removed>"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 <MAC ID removed>>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN                no            no
3: hci0: Bluetooth                   no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8723be              96097  0 
btcoexist              51822  1 rtl8723be
rtl8723_common         23662  1 rtl8723be
rtl_pci                27417  1 rtl8723be
rtlwifi                74534  2 rtl_pci,rtl8723be
mac80211              697143  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              520257  2 mac80211,rtlwifi
ideapad_laptop         18524  0 
sparse_keymap          13890  1 ideapad_laptop
wmi                    19379  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
ideapad_laptop  (1): no_bt_rfkill=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (6): debug=0 | disable_watchdog=N | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
======================o=============o===========o=============o=========o===========o==============o===========
 eth0                 | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [<BT Device>] | 802.11 WiFi | rtl8723be | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    *<MAC ID removed>: Infra, <MAC C-01 4C:60:DE:FC:49:0D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2


    Address:         10.0.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             10.0.0.1
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


<MAC ID removed>    : ssid=4C:60:DE:FC:49:0D | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
D-Link_DIR-524       : ssid=D-Link_DIR-524 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HTC Portable Hotspot 9BE1 : ssid=HTC Portable Hotspot 9BE1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.217/2.736/3.256/0.522 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.012/0.013/0.015/0.004 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 <MAC ID removed>>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"<MAC ID removed>"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d670e149d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8723be]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     5D113E08097276ABF2EF3C6
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)


[btcoexist]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     0C170EE6883C780D98D7EC3
depends:        


[rtl8723_common]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     251C540A2D3AD38CCA85ED9
depends:        


[rtl_pci]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     DCE642AF51FCBF67FE7DEB6
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     35225554E432897005F9BA7
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/net/mac80211/mac80211.ko
srcversion:     94D2BCBEF47023226C94CB7
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/net/wireless/cfg80211.ko
srcversion:     38480743B72586E8ACD5AEC
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ideapad_laptop]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/platform/x86/ideapad-laptop.ko
srcversion:     671575052EDF181E26050E7
depends:        sparse-keymap
parm:           no_bt_rfkill:No rfkill for bluetooth. (bool)


[wmi]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     2E987FE96F7EBB6BFC7E2B2
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=8
mlx4.conf         : softdep mlx4_core post: mlx4_en
modprobe.conf     : options rtl8192ce ips=1
                    options rtl8192ce fwlps=0
                    options rtl8192ce swenc=1
rtl8188ee.conf    : options rtl8188ee ips=0 fwlps=0


[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.18.0-031800rc1-generic root=UUID=81b4850c-ce00-493c-902e-9200929b5d15 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.030747] Initializing cgroup subsys net_cls
[    0.030752] Initializing cgroup subsys net_prio
[    4.059904] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.060286] audit: initializing netlink subsys (disabled)
[    4.256410] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.754095] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x495f01)
[   11.175439] wmi: Mapper loaded
[   12.662350] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   12.714856] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.715113] rtlwifi: rtlwifi: wireless switch is on
[   16.826302] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.754022] thinkpad_acpi: http://ibm-acpi.sf.net/
[  112.248475] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  114.718585] wlan0: authenticate with <MAC C-01 <MAC ID removed>>
[  114.718597] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  114.741166] wlan0: send auth to <MAC C-01 <MAC ID removed>> (try 1/3)
[  114.744287] wlan0: authenticated
[  114.746166] wlan0: associate with <MAC C-01 <MAC ID removed>> (try 1/3)
[  114.751504] wlan0: RX AssocResp from <MAC C-01 <MAC ID removed>> (capab=0x411 status=0 aid=2)
[  114.752405] wlan0: associated
[  114.752418] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  114.815334] wlan0: deauthenticating from <MAC C-01 <MAC ID removed>> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  114.828495] wlan0: authenticate with <MAC C-01 <MAC ID removed>>
[  114.828498] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  114.840346] wlan0: send auth to <MAC C-01 <MAC ID removed>> (try 1/3)
[  114.845406] wlan0: authenticated
[  114.846213] wlan0: associate with <MAC C-01 <MAC ID removed>> (try 1/3)
[  114.851393] wlan0: RX AssocResp from <MAC C-01 <MAC ID removed>> (capab=0x411 status=0 aid=2)
[  114.851918] wlan0: associated
[  347.930370] wlan0: failed to use reserved channel context, disconnecting (err=-95)
[  348.903615] wlan0: authenticate with <MAC C-01 <MAC ID removed>>
[  348.927513] wlan0: send auth to <MAC C-01 <MAC ID removed>> (try 1/3)
[  348.930511] wlan0: authenticated
[  348.930988] wlan0: associate with <MAC C-01 <MAC ID removed>> (try 1/3)
[  348.936178] wlan0: RX AssocResp from <MAC C-01 <MAC ID removed>> (capab=0x411 status=0 aid=2)
[  348.936708] wlan0: associated
[  356.926413] wlan0: deauthenticated from <MAC C-01 <MAC ID removed>> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  363.536357] wlan0: authenticate with <MAC C-01 <MAC ID removed>>
[  363.559487] wlan0: send auth to <MAC C-01 <MAC ID removed>> (try 1/3)
[  363.562478] wlan0: authenticated
[  363.563738] wlan0: associate with <MAC C-01 <MAC ID removed>> (try 1/3)
[  363.568650] wlan0: RX AssocResp from <MAC C-01 <MAC ID removed>> (capab=0x411 status=0 aid=2)
[  363.569179] wlan0: associated


	======== Done ========

```

---

### Post by shree-cse on 2014-10-23
> **varunendra said:**
> Welcome to the forums branimir3!

Please try this in a terminal -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
This will append an option in your 'iwlwifi.conf' file that is supposed to enable Tx aggregation on the interface. Let us know if this solves the problem.


Tried this, will check if it worked. Connection is stable for now. Normally I've a drop for every 4-5 mins and then I've to reboot, which makes it almost impossible to use ubuntu for Internet.

---

### Post by branimir3 on 2014-10-23
> **Scooby-2 said:**
> If you are saying that WiFi works fine at your apartment, but not at another physical location (e.g. lodge) under both operating systems it means there is nothing wrong with your Y50's hardware or setup, but rather the environment. It may be that there are other wireless networks using the same or adjacent channels in your lodge environment. Ideally, each network should be at least 2 channels apart, i.e. 4 networks should use channels 1, 3, 5 and 7, for example. To see what there is around you, open a terminal and type ```
sudo iwlist scan
```You are looking for the lines starting with the word Frequency, as in You may also need to run the command several times and run it with your laptop in different places in the room/building where you are having problems, as a weaker signal may not be picked up every time in every place. You may also want to switch off your own router, in case there is a network nearby using the same channel as you. With yours switched off you should be able to see a weaker signal using your channel.

I have had problems where neighbours have had wireless routers sent by the ISP (where I live there is only one ISP) and they are all set to the same channel. Also, Windows and Linux differ in the way that they cope with crosstalk/interference.

To see just the Frequencies and Channels found for each scan type ```
sudo iwlist scan|grep Frequency
```


What I wanted to say is that, at my apartment, wireless works fine on both Ubuntu and Windows systems. 
Here at "lodge" wireless works fine on Windows, while I'm having described issues on Ubuntu.

This is the output of 'sudo iwlist scan|grep Frequency' at "lodge"

```
vboxnet0  Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


                    Frequency:2.437 GHz (Channel 6)
                    Frequency:2.412 GHz (Channel 1)
                    Frequency:2.417 GHz (Channel 2)
                    Frequency:2.442 GHz (Channel 7)
                    Frequency:2.442 GHz (Channel 7)
                    Frequency:2.462 GHz (Channel 11)



```

Doesn't seem like there is always a "2 channel gap". 

> **jeremy31 said:**
> [FONT=courier new]Do you have control over access point named B.Net_11121 as it is using WPA(TKIP) and seems to causing issues from your wireless script, you can check your dmesg log yourself while connected to B.Net with ```
dmesg | grep TKIP
```

[/FONT]If you can make changes, change it to WPA2-AES

Is there any other solution without changing my router settings ? This is the output of [FONT=courier new]```
dmesg | grep TKIP
``` and it doesnt look very good to me:

[/FONT]```
[   25.508180] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use[  232.837555] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  524.986897] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1105.459328] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1105.520870] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1125.531355] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1291.084201] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1292.147425] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2106.700467] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2106.783421] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[44489.312138] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[44489.441519] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[68561.542115] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[68561.684941] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[69373.280501] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[73091.032569] iwlwifi 0000:08:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use

```
[FONT=courier new]
After googling the output, I came across the following thread:
[/FONT]http://ubuntuforums.org/archive/index.php/t-2142750.html

Do you guys thing the following code can help? I am a little scared to try it out because I am afraid of my connection becoming unsecure and I don't know how to revert it in case it fails.
[COLOR=#000000][FONT=verdana]```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sudo modprobe -rfv ath5k[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sudo modprobe -v ath5k 
```[/FONT][/COLOR]

---

### Post by jeremy31 on 2014-10-23
If the nohwcrypt option causes problems ```
sudo gedit /etc/modprobe.d/ath5k.conf
```
Place a # in front of options ath5k nohwcrypt and save

---

### Post by branimir3 on 2014-10-23
> **jeremy31 said:**
> If the nohwcrypt option causes problems ```
sudo gedit /etc/modprobe.d/ath5k.conf
```
Place a # in front of options ath5k nohwcrypt and save

Running ```
sudo gedit /etc/modprobe.d/ath5k.conf
``` opens ath5k.conf file which is empty.

---

### Post by jeremy31 on 2014-10-23
> **branimir3 said:**
> Running ```
sudo gedit /etc/modprobe.d/ath5k.conf
``` opens ath5k.conf file which is empty.

Actually the file probably doesn't exist yet, but it will if you run the code ```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
```

---

### Post by Scooby-2 on 2014-10-23
> **Wild Man said:**
> You could just look at the wireless script information, it already has that information listed.
ThanksThe script is excellent  and I agree that it will provide the channel information we need to see. However I think it is easier to see one line output for each detected channel, so their frequencies/channels can be easily compared. I also think it necessary to run the command - or script - multiple times in different locations in the problem environment, as interfering channels, especially if they are on the same frequency or are a little weak, will not necessarily be reported every time the command/script is run.

I was trying to make it easier to interpret by reducing the amount of information presented. But perhaps it would be better still to use the following:```
sudo iwlist scan|egrep 'Frequency|Cell|ESSID'
```which will give something like the following:

[IMG]http://i1244.photobucket.com/albums/gg567/Scooby269/Screenshot_zpsd5b2b56f.png[/IMG]

This clearly shows 3 networks, their respective channels and SSIDs (albeit 2 of them a bit paranoid!). It's easy to see here that two of them are using channel 1 which would cause problems.

---

### Post by jeremy31 on 2014-10-23
> **shree-cse said:**
> Tried this, will check if it worked. Connection is stable for now. Normally I've a drop for every 4-5 mins and then I've to reboot, which makes it almost impossible to use ubuntu for Internet.

It shouldn't have made any difference because the option is specific to the iwlwifi module and you should be using rtl8723be with rtlwifi and a couple others

You should start your own thread and attach the wireless info file

---

### Post by Scooby-2 on 2014-10-23
I maintain that if your laptop works perfectly in one environment but not in another you do not need to do anything to it. Your iwlist scan output shows 3 networks which are using the same or adjacent channels (one on channel 6, two on 7). Poor connectivity is guaranteed for those channels, though you have not stated which is yours. See the modified command I have posted and use the following command:```
[COLOR=#000000][FONT=Ubuntu Mono]sudo iwlist scan|egrep 'Frequency|Cell|ESSID'[/FONT][/COLOR]
```
Please post your output and state which is your SSID.

If you keep changing your system you risk stopping it from working in your apartment. Then you'll be even deeper in the brown stuff.

---

### Post by mark-lamorey on 2014-10-23
Hi branimir -

I had a similar problem with an M73T from lenovo - it also used Realtek
It all became solved by running the below line

[COLOR=#000000]echo "options [/COLOR][COLOR=#417394]rtl8723be[/COLOR][COLOR=#000000] fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

[/COLOR]This line made a file @ /etc/modprobe.d that overides some settings in the driver for rtl8723be
The specific settings keep the wifi from going to sleep and into a power down mode as it does not wake up properly.

However, when I look at your wireless script I see that your wireless is the Intel - I will dig to see if there is something in the community on your drivers.
[iwlmvm]
[mac80211]
[iwlwifi]

---

### Post by mark-lamorey on 2014-10-23
Take a look at this thread - try the modprobe.d entry if the problem sounds similar to yours.

[http://ubuntuforums.org/showthread.php?t=2247245&highlight=iwlmvm+intermittent](http://ubuntuforums.org/showthread.php?t=2247245&highlight=iwlmvm+intermittent)

Although upon more reading if your problem is only at one location, the problem is likely no fundamental to your laptop.

---

### Post by branimir3 on 2014-11-20
Hello, none of the solutions worked for me :/ I tried to change wifi encryption to wpa2/aes as some of you suggested, but then I realized that encryption is already set!

---

