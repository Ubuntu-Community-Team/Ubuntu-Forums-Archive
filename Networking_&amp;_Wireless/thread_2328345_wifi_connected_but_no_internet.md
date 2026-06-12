---
title: "wifi connected but no internet"
date: 2016-06-20
forum: Networking &amp; Wireless
---

### Post by daedalus.AI on 2016-06-20
After updating to 16.04 I'm once again having troubles with my wifi: I'm connected to my wifi at home but most of the times I have no internet access.

I did update my machine with:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

After a restart it worked for a while until the next time I booted up my machine.

Had those troubles before with 15.04 and if I recall correctly it did fix it for the most part with 11n_disable = 1.
Tried it now but to no avail.

Wireless-info output:
```

########## wireless info START ##########

Report from: 20 Jun 2016 09:24 CEST +0200

Booted last: 20 Jun 2016 09:21 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xfce

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:02d2 Acer, Inc 
Bus 003 Device 003: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                237568  0 
mac80211              708608  1 iwldvm
iwlwifi               188416  1 iwldvm
cfg80211              524288  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:586641 (586.6 KB)  TX bytes:77168 (77.1 KB)
          Interrupt:20 Memory:f2500000-f2520000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18863 (18.8 KB)  TX bytes:23938 (23.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"daedalus"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'daedalus' [AN16]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search localdomain

##### network managers ##################

Installed:

    NetworkManager

Running:

root       890     1  0 09:21 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [daedalus] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    EasyBox-4FA440:  Infra, <MAC 'EasyBox-4FA440' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Gastzugang:      Infra, <MAC 'Gastzugang' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    WLAN-225062:     Infra, <MAC 'WLAN-225062' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Blumenwiese:     Infra, <MAC 'Blumenwiese' [AN4]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    EasyBox-4FA440:  Infra, <MAC 'EasyBox-4FA440' [AN5]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Gastzugang:      Infra, <MAC 'Gastzugang' [AN6]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Landungsboot:    Infra, <MAC 'Landungsboot' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Mutterschiff:    Infra, <MAC 'Mutterschiff' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    EasyBox-597672:  Infra, <MAC 'EasyBox-597672' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    G-SBNET:         Infra, <MAC 'G-SBNET' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    KabelBox-2F14:   Infra, <MAC 'KabelBox-2F14' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    FRITZ!Box 7490:  Infra, <MAC 'FRITZ!Box 7490' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Tau'ri:          Infra, <MAC 'Tau'ri' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    FRITZ!Box 7312:  Infra, <MAC 'FRITZ!Box 7312' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    KabelBox-2F14:   Infra, <MAC 'KabelBox-2F14' [AN15]>, Freq 5560 MHz, Rate 54 Mb/s, Strength 25 WPA2
    *daedalus:       Infra, <MAC 'daedalus' [AN16]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 80 WPA2
    FRITZ!Box Fon WLAN 7112: Infra, <MAC 'FRITZ!Box Fon WLAN 7112' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    KabelBox-7B09:   Infra, <MAC 'KabelBox-7B09' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    FRITZ!Box 7490:  Infra, <MAC 'FRITZ!Box 7490' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    kyrill:          Infra, <MAC 'kyrill' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    EasyBox2016:     Infra, <MAC 'EasyBox2016' [AN21]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Kiefer:          Infra, <MAC 'Kiefer' [AN22]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ZYXEL-062:       Infra, <MAC 'ZYXEL-062' [AN23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
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

[[/etc/NetworkManager/system-connections/daedalus]] (600 root)
[connection] id=daedalus | type=802-11-wireless | permissions=user:daedalus:;
[802-11-wireless] ssid=daedalus | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     E3CBEE01463DF37AB9C5AB1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     19A5C735A79087003D53D6A
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
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
filename:       /lib/modules/3.19.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0085 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    3.590143] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.372165] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.374005] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.380770] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    4.652215] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.659015] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    4.737822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.072582] wlan0: authenticate with <MAC 'daedalus' [AN16]>
[   16.075337] wlan0: send auth to <MAC 'daedalus' [AN16]> (try 1/3)
[   16.076730] wlan0: authenticated
[   16.079638] wlan0: associate with <MAC 'daedalus' [AN16]> (try 1/3)
[   16.081855] wlan0: RX AssocResp from <MAC 'daedalus' [AN16]> (capab=0x411 status=0 aid=1)
[   16.101198] wlan0: associated
[   16.101238] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   81.025148] wlan0: deauthenticated from <MAC 'daedalus' [AN16]> (Reason: 3=DEAUTH_LEAVING)
[   84.291759] wlan0: authenticate with <MAC 'daedalus' [AN16]>
[   84.293951] wlan0: send auth to <MAC 'daedalus' [AN16]> (try 1/3)
[   84.295400] wlan0: authenticated
[   84.296375] wlan0: associate with <MAC 'daedalus' [AN16]> (try 1/3)
[   84.298544] wlan0: RX AssocResp from <MAC 'daedalus' [AN16]> (capab=0x411 status=0 aid=1)
[   84.320739] wlan0: associated
[  101.421667] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[  101.421678] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[  101.421726] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  102.180660] wlan0: deauthenticated from <MAC 'daedalus' [AN16]> (Reason: 3=DEAUTH_LEAVING)
[  105.501901] wlan0: authenticate with <MAC 'daedalus' [AN16]>
[  105.504061] wlan0: send auth to <MAC 'daedalus' [AN16]> (try 1/3)
[  105.505584] wlan0: authenticated
[  105.506307] wlan0: associate with <MAC 'daedalus' [AN16]> (try 1/3)
[  105.508450] wlan0: RX AssocResp from <MAC 'daedalus' [AN16]> (capab=0x411 status=0 aid=1)
[  105.531474] wlan0: associated

########## wireless info END ############


```

---

### Post by praseodym on 2016-06-20
Try disabling the queue of the driver:

```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi-wd.conf
```
Reboot

---

### Post by Rick St. George on 2016-06-21
If praseodym's idea doesn't work, check this out (it worked for me).
For some reason "Routes" gets Checked by default, after an update ... which ignores the routes!
This may be what is happening to you, and others, who show an IP Address ... meaning you're connected but nothing connects.

1. Disconnect and Disable Wireless in Network Mgr.

2. Open Network Mgr / EDIT, Selected WiFi connection / EDIT / IPv4 Settings ... 
    Selected Automatic (DHCP) 

3. Next Additional DNS servers: added a DNS server, select from here;
    [http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm](http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm)
   
4. Checked "Require IPv4 addressing for this connection ..."

5. then Click the "Routes" button, UNCHECKED "ignore automatically obtained routes",
   also make sure "use this connection only for resources.." is unchecked.

6. Disable / Ignore IPv6 (for security reasons), then Save & Close

7. Choose "Enable Wireless" in Network Mgr.

---

### Post by daedalus.AI on 2016-06-22
> **praseodym said:**
> Try disabling the queue of the driver:

```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi-wd.conf
```
Reboot

Sadly that didn't do anything: even after rebooting wifi connected but no internet access.

---

### Post by daedalus.AI on 2016-06-22
> **Rick St. George said:**
> If praseodym's idea doesn't work, check this out (it worked for me).
For some reason "Routes" gets Checked by default, after an update ... which ignores the routes!
This may be what is happening to you, and others, who show an IP Address ... meaning you're connected but nothing connects.

1. Disconnect and Disable Wireless in Network Mgr.

2. Open Network Mgr / EDIT, Selected WiFi connection / EDIT / IPv4 Settings ... 
    Selected Automatic (DHCP) 

3. Next Additional DNS servers: added a DNS server, select from here;
    [http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm](http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm)
   
4. Checked "Require IPv4 addressing for this connection ..."

5. then Click the "Routes" button, UNCHECKED "ignore automatically obtained routes",
   also make sure "use this connection only for resources.." is unchecked.

6. Disable / Ignore IPv6 (for security reasons), then Save & Close

7. Choose "Enable Wireless" in Network Mgr.

It worked immediately after I've finished your steps - but after a restart my problem still persists and even a few more tries of your steps nothing changed.

---

