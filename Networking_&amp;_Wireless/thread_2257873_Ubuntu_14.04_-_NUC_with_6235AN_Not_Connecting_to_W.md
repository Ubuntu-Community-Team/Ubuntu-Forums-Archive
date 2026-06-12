---
title: "Ubuntu 14.04 - NUC with 6235AN Not Connecting to Wireless"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by phil55 on 2014-12-23
Hi All,

I am fairly new to Ubuntu and have been trolling through many posts to try and resolve this issue, but to no avail. I understand that there is a common problem with the 6235AN adapter.

_**Problem**_

- I can view wireless networks, sometimes, but all have a very weak signal, even if the NUC is placed alongside the AP. 
- If I manage to connect to an SSID, there is no communication whatsoever via wireless.
- I have tried diabling N capability via the*** iwlwifi.conf***, but no luck there either* (tested both **11n_disable=1 **and **11n_disable=8**)*

Any assistance would be greatly appreciated.

Thanks!
Phil

---

### Post by praseodym on 2014-12-23
Please run the wireless scrip from the sticky thread and show the outputs

---

### Post by phil55 on 2014-12-24
Hi Bud, thank you for the reply.
Apologies, I did not see the sticky note initially... Please see the output from the wireless script below:

```


########## wireless info START ##########


Report from: 24 Dec 2014 10:03 SAST +0200


Booted last: 24 Dec 2014 09:49 SAST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)
    Subsystem: Intel Corporation Device [8086:2054]
    Kernel driver in use: e1000e


02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:07da Intel Corp. 
Bus 002 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::c23f:d5ff:fe68:812b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8227747 (8.2 MB)  TX bytes:26709698 (26.7 MB)
          Interrupt:20 Memory:f7d00000-f7d20000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::8200:bff:fe2a:f035/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270 (270.0 B)  TX bytes:310 (310.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.254.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search tcmnetwork.net


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
    tcm-guest-wireless: Infra, <MAC 'tcm-guest-wireless' [AN1]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 24
    tcm-grp-wireless:Infra, <MAC 'tcm-grp-wireless' [AN2]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 24 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.1.114
    Prefix:          23 (255.255.254.0)
    Gateway:         192.168.1.2


    DNS:             192.168.1.8
    DNS:             192.168.9.3


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


[[/etc/NetworkManager/system-connections/Xperia Z1 Compact_d79f]] (600 root)
[connection] id=Xperia Z1 Compact_d79f | type=802-11-wireless
[802-11-wireless] ssid=Xperia Z1 Compact_d79f | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/tcm-grp-wireless]] (600 root)
[connection] id=tcm-grp-wireless | type=802-11-wireless
[802-11-wireless] ssid=tcm-grp-wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Africa/Johannesburg (based on set time zone)


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


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
# PCI device 0x8086:0x1559 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x088e (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    6.838100] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[    6.844879] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[    7.115989] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[    7.123942] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[    7.205556] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   33.108344] wlan0: authenticate with <MAC 'tcm-grp-wireless' [AN2]>
[   33.112751] wlan0: send auth to <MAC 'tcm-grp-wireless' [AN2]> (try 1/3)
[   33.124736] wlan0: send auth to <MAC 'tcm-grp-wireless' [AN2]> (try 2/3)
[   33.133759] wlan0: send auth to <MAC 'tcm-grp-wireless' [AN2]> (try 3/3)
[   33.142496] wlan0: authentication with <MAC 'tcm-grp-wireless' [AN2]> timed out
[   36.365905] wlan0: authenticate with <MAC 'tcm-grp-wireless' [AN2]>
[   36.369104] wlan0: direct probe to <MAC 'tcm-grp-wireless' [AN2]> (try 1/3)
[   36.572941] wlan0: direct probe to <MAC 'tcm-grp-wireless' [AN2]> (try 2/3)
[   36.777092] wlan0: direct probe to <MAC 'tcm-grp-wireless' [AN2]> (try 3/3)
[   36.981343] wlan0: authentication with <MAC 'tcm-grp-wireless' [AN2]> timed out
[  445.539271] wlan0: authenticate with <MAC 'tcm-grp-wireless' [AN2]>
[  445.542378] wlan0: send auth to <MAC 'tcm-grp-wireless' [AN2]> (try 1/3)
[  445.575835] wlan0: send auth to <MAC 'tcm-grp-wireless' [AN2]> (try 2/3)
[  445.579604] wlan0: authenticated
[  445.582595] wlan0: associate with <MAC 'tcm-grp-wireless' [AN2]> (try 1/3)
[  445.592522] wlan0: associate with <MAC 'tcm-grp-wireless' [AN2]> (try 2/3)
[  445.603390] wlan0: RX AssocResp from <MAC 'tcm-grp-wireless' [AN2]> (capab=0x1411 status=0 aid=7)
[  445.620695] wlan0: associated
[  445.620734] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  448.532998] wlan0: deauthenticated from <MAC 'tcm-grp-wireless' [AN2]> (Reason: 3)


########## wireless info END ############



```

---

### Post by praseodym on 2014-12-24
Deactivate the N-mode of the driver and the queue:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot.

---

