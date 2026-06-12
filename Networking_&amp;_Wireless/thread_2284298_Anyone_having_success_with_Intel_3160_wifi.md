---
title: "Anyone having success with Intel 3160 wifi?"
date: 2015-06-28
forum: Networking &amp; Wireless
---

### Post by galatians2 on 2015-06-28
Has anyone managed to get a stable, fast (>60Mbit) connection using Intel 3160 Wifi over medium distances inside a house ?

I have a Lenovo Y50-70 which has an Intel 3160 Wifi M.2 card. I've tried various combinations of kernel version, backports drivers and iwlwifi firmware without much success.

I'm running Ubuntu 14.04.2 LTS with all the packages updated. For every combination of kernel/firmware I've tried most combinations of kernel modules options:

```

options iwlwifi 11n_disable=1/8 bt_coex_active=Y/N swcrypto=1/0
options iwlmvm power_scheme=1

```

I've tried:

**kernel 3.13.0-55-generic with firmware iwlwifi-3160-8.ucode:** 802.11N 2.4Ghz won't connect at all. If I disable 802.11N and use 802.11G it works ok if I'm right next to the access point but is unstable upstairs. If I use 5Ghz then it's reasonably stable and I get around 3Mbit but it slows down to 0.5Mbit often.

**kernel 3.19.0-21 with firmware 3160-ucode-25.17.12.0:** 802.11N 2.4Ghz connects at 2Mbit but stops working without a dmesg error after a few minutes. If I connect to 5Ghz (not sure if it's using 802.11A or N) I get a pretty stable connection at about 20Mbit.

**kernel 4.1 with firmware 3160-ucode-25.30.13.0:** 802.11N 2.4Ghz connects at 2Mbit but stops working without a dmesg error after a few minutes. If I connect to 5Ghz (not sure if it's using 802.11A or N) I get a pretty stable connection at about 20Mbit.

On the 3rd floor of my house (~40 feet away from the router) 2.4Ghz basically doesn't work at all on 802.11G or N. 5Ghz is stable at around 10Mbit. At the same location I've tested with 3 smartphones and 2 other laptops (1 windows, 1 Ubuntu) and they all get 70-150Mbit solid on 2.4Ghz 802.11N so I know it's not a problem with my router. I have people at my house all the time using all kinds of laptops/phones without issue.

This is pretty surprising to me considering this card was released almost 2 years ago and it has an Open Source driver. Is it a hardware design issue or truly just bad drivers? I see many windows users with similar issues for this card and the 7260.

```


########## wireless info START ##########


Report from: 28 Jun 2015 11:26 CDT -0500


Booted last: 28 Jun 2015 10:54 CDT -0500


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 4.1.0-040100-generic #201506220235 SMP Mon Jun 22 06:36:19 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
    Kernel driver in use: iwlwifi


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 174f:14b8 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                307200  0 
mac80211              786432  1 iwlmvm
iwlwifi               217088  1 iwlmvm
cfg80211              589824  3 iwlwifi,mac80211,iwlmvm
mxm_wmi                16384  1 nouveau
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  2 mxm_wmi,nouveau


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
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d27e:35ff:fed4:4f13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44796213 (44.7 MB)  TX bytes:5595050 (5.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"MI8"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: <MAC 'MI8' [AC1]>   
          Bit Rate=27.8 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       839     1  0 10:54 ?        00:00:00 NetworkManager


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


- Device: wlan0  [MI8] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           52 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    MI7:             Infra, <MAC 'MI7' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    *MI8:            Infra, <MAC 'MI8' [AC1]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 57 WPA2


  IPv4 Settings:
    Address:         192.168.1.8
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


no-auto-default=<MAC address>,<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/ThinkBig]] (600 root)
[connection] id=ThinkBig | type=802-11-wireless
[802-11-wireless] ssid=ThinkBig | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/MI7A]] (600 root)
[connection] id=MI7A | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=MI7A | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MI7]] (600 root)
[connection] id=MI7 | type=802-11-wireless
[802-11-wireless] ssid=MI7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR]] (600 root)
[connection] id=NETGEAR | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Green]] (600 root)
[connection] id=Green | type=802-11-wireless
[802-11-wireless] ssid=Green | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MI8]] (600 root)
[connection] id=MI8 | type=802-11-wireless
[802-11-wireless] ssid=MI8 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/arnold]] (600 root)
[connection] id=arnold | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=arnold | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


iw: error while loading shared libraries: libnl.so.1: cannot open shared object file: No such file or directory


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
          Current Frequency:5.785 GHz


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.785 GHz


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MI8' [AC1]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MI8"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d02001f4b7
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MI7' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"MI7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d01ee70887
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.1.0-040100-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4BAA00B1F9481F9B825BC4D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.1.0-040100-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A8:A8:81:C2:00:CA:CF:B3:CA:EA:CF:AF:74:C5:46:9C:22:79:68:73
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.1.0-040100-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5F217E3E605BFE2A9C4566D
depends:        cfg80211
intree:         Y
vermagic:       4.1.0-040100-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A8:A8:81:C2:00:CA:CF:B3:CA:EA:CF:AF:74:C5:46:9C:22:79:68:73
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.1.0-040100-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-IWL3160_UCODE_API_OK.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     B72437DD648288F0DE2EB8E
depends:        cfg80211
intree:         Y
vermagic:       4.1.0-040100-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A8:A8:81:C2:00:CA:CF:B3:CA:EA:CF:AF:74:C5:46:9C:22:79:68:73
sig_hashalgo:   sha512
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
filename:       /lib/modules/4.1.0-040100-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2151DA0D0F0543B97999E87
depends:        
intree:         Y
vermagic:       4.1.0-040100-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A8:A8:81:C2:00:CA:CF:B3:CA:EA:CF:AF:74:C5:46:9C:22:79:68:73
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 1
tfd_q_hang_detect: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
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
swcrypto: 1
uapsd_disable: Y


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
blacklist btusb


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlmvm.conf]
options iwlmvm power_scheme=1


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi bt_coex_active=N swcrypto=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    6.553936] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[    6.684348] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.107795] wlan0: authenticate with <MAC 'MI7' [AC2]>
[   10.109046] wlan0: send auth to <MAC 'MI7' [AC2]> (try 1/3)
[   10.160055] wlan0: authenticated
[   10.162055] wlan0: associate with <MAC 'MI7' [AC2]> (try 1/3)
[   10.201556] wlan0: RX AssocResp from <MAC 'MI7' [AC2]> (capab=0x411 status=0 aid=8)
[   10.202938] wlan0: associated
[   10.202946] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  339.478872] wlan0: deauthenticating from <MAC 'MI7' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  342.773544] wlan0: authenticate with <MAC 'MI8' [AC1]>
[  342.774700] wlan0: send auth to <MAC 'MI8' [AC1]> (try 1/3)
[  342.795230] wlan0: authenticated
[  342.799093] wlan0: associate with <MAC 'MI8' [AC1]> (try 1/3)
[  342.836192] wlan0: RX AssocResp from <MAC 'MI8' [AC1]> (capab=0x411 status=0 aid=1)
[  342.837196] wlan0: associated


########## wireless info END ############

```

Edit: Here's a dmesg error that kernel 4.1 with firmware 13 gives using 802.11N:

```

[ 5265.630343] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 5265.630345] iwlwifi 0000:08:00.0: CSR values:
[ 5265.630347] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 5265.630358] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c89204
[ 5265.630372] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X80000040
[ 5265.630386] iwlwifi 0000:08:00.0:                     CSR_INT: 0X00000000
[ 5265.630399] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 5265.630413] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 5265.630427] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 5265.630438] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 5265.630452] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 5265.630466] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X00000164
[ 5265.630479] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0X00000000
[ 5265.630490] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X80000000
[ 5265.630501] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X803a0000
[ 5265.630515] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X001f0042
[ 5265.630529] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 5265.630540] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 5265.630554] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 5265.630565] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 5265.630578] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000060
[ 5265.630590] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X88447d69
[ 5265.630603] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 5265.630614] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[ 5265.630628] iwlwifi 0000:08:00.0:      CSR_MONITOR_STATUS_REG: 0X5bb7f777
[ 5265.630639] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 5265.630653] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 5265.630654] iwlwifi 0000:08:00.0: FH register values:
[ 5265.630676] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X4492fc00
[ 5265.630690] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X04492fd0
[ 5265.630703] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000a8
[ 5265.630717] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[ 5265.630731] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 5265.630744] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[ 5265.630758] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 5265.630771] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[ 5265.630785] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 5265.630909] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 5265.630911] iwlwifi 0000:08:00.0: Status: 0x00000000, count: 6
[ 5265.630912] iwlwifi 0000:08:00.0: Loaded firmware version: 25.30.13.0
[ 5265.630913] iwlwifi 0000:08:00.0: 0x00000084 | NMI_INTERRUPT_UNKNOWN       
[ 5265.630914] iwlwifi 0000:08:00.0: 0x00800634 | uPc
[ 5265.630915] iwlwifi 0000:08:00.0: 0x00000000 | branchlink1
[ 5265.630916] iwlwifi 0000:08:00.0: 0x00000B2E | branchlink2
[ 5265.630918] iwlwifi 0000:08:00.0: 0x00014734 | interruptlink1
[ 5265.630919] iwlwifi 0000:08:00.0: 0x00019A18 | interruptlink2
[ 5265.630920] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 5265.630921] iwlwifi 0000:08:00.0: 0x00000080 | data2
[ 5265.630922] iwlwifi 0000:08:00.0: 0x07030000 | data3
[ 5265.630923] iwlwifi 0000:08:00.0: 0xFFC1D6F2 | beacon time
[ 5265.630924] iwlwifi 0000:08:00.0: 0xE239F8AB | tsf low
[ 5265.630925] iwlwifi 0000:08:00.0: 0x000001D8 | tsf hi
[ 5265.630926] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 5265.630927] iwlwifi 0000:08:00.0: 0x00B59BBF | time gp2
[ 5265.630928] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 5265.630929] iwlwifi 0000:08:00.0: 0x0004191E | uCode version
[ 5265.630930] iwlwifi 0000:08:00.0: 0x00000164 | hw version
[ 5265.630931] iwlwifi 0000:08:00.0: 0x00C89204 | board version
[ 5265.630932] iwlwifi 0000:08:00.0: 0x0002001C | hcmd
[ 5265.630933] iwlwifi 0000:08:00.0: 0xA402200A | isr0
[ 5265.630934] iwlwifi 0000:08:00.0: 0x01000000 | isr1
[ 5265.630935] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 5265.630936] iwlwifi 0000:08:00.0: 0x0041F8C5 | isr3
[ 5265.630937] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 5265.630938] iwlwifi 0000:08:00.0: 0x00014110 | isr_pref
[ 5265.630939] iwlwifi 0000:08:00.0: 0x00000000 | wait_event
[ 5265.630940] iwlwifi 0000:08:00.0: 0x00000080 | l2p_control
[ 5265.630941] iwlwifi 0000:08:00.0: 0x00012030 | l2p_duration
[ 5265.630942] iwlwifi 0000:08:00.0: 0x0000003F | l2p_mhvalid
[ 5265.630943] iwlwifi 0000:08:00.0: 0x000000CE | l2p_addr_match
[ 5265.630944] iwlwifi 0000:08:00.0: 0x00000005 | lmpm_pmg_sel
[ 5265.630945] iwlwifi 0000:08:00.0: 0x17061509 | timestamp
[ 5265.630946] iwlwifi 0000:08:00.0: 0x0034A8B8 | flow_handler
[ 5265.630948] ieee80211 phy0: Hardware restart was requested
[ 5265.734031] iwlwifi 0000:08:00.0: Failing on timeout while stopping DMA channel 8 [0x07fd0001]
[ 5265.734328] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 5265.734586] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 5265.837792] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 5265.838051] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled

```

---

