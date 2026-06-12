---
title: "won't download large files"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by bandito40 on 2015-08-02
I have a Tp-Link AC750 router.  I am having problems downloading large files over wifi. Lan no problems. Windows and wifi no problems. It happens with Chromiun, Firefox, wget, apt-get, curl but not with torrents.  Effects flavours 14.04 LTS 64/32 bit and ChromOS. Files larger than 70 megs tested so far.  Basically the download starts, runs great and then at an undetermined point the download slows, slows some more, and then stops, hangs and then exits. I also did all firmware updates on router.

---

### Post by praseodym on 2015-08-02
Please run the wireless-script from the sticky thread and show the outputs

---

### Post by bandito40 on 2015-08-02
Sorry about that.  Should have looked for the sticky first. Here are the results:

```

########## wireless info START ##########

Report from: 02 Aug 2015 16:02 CDT -0500

Booted last: 02 Aug 2015 15:49 CDT -0500

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e052]
	Kernel driver in use: ath9k

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0742]
	Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 003: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:d251 Suyin Corp. 
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
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

ath9k                 162133  0 
ath9k_common           25638  1 ath9k
ath9k_hw              460416  2 ath9k_common,ath9k
ath                    29397  3 ath9k_common,ath9k,ath9k_hw
mac80211              697212  1 ath9k
ath3k                  13381  0 
bluetooth             486890  23 bnep,ath3k,btusb,rfcomm
cfg80211              520257  4 ath,ath9k_common,ath9k,mac80211

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
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:266960165 (266.9 MB)  TX bytes:18455061 (18.4 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"bandito 5"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'bandito 5' [AN8]>   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:29   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       884     1  0 15:49 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [bandito 5] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DIRECT-roku-664: Infra, <MAC 'DIRECT-roku-664' [AN1]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 72 WPA2
    bandito 2.4:     Infra, <MAC 'bandito 2.4' [AN2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 82 WPA2
    dlink:           Infra, <MAC 'dlink' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    BELL279:         Infra, <MAC 'BELL279' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Cisco63679:      Infra, <MAC 'Cisco63679' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    NGOInternet:     Infra, <MAC 'NGOInternet' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Amped | Wireless- Yousufy: Infra, <MAC 'Amped | Wireless- Yousufy' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    *bandito 5:      Infra, <MAC 'bandito 5' [AN8]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 74 WPA2
    BELL183:         Infra, <MAC 'BELL183' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    BELL845:         Infra, <MAC 'BELL845' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    BELL172:         Infra, <MAC 'BELL172' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Linksys05913:    Infra, <MAC 'Linksys05913' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BELL372:         Infra, <MAC 'BELL372' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    BELL530:         Infra, <MAC 'BELL530' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    BELL061:         Infra, <MAC 'BELL061' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2

  IPv4 Settings:
    Address:         192.168.0.101
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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/bandito 2.4]] (600 root)
[connection] id=bandito 2.4 | type=802-11-wireless
[802-11-wireless] ssid=bandito 2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bandito 5]] (600 root)
[connection] id=bandito 5 | type=802-11-wireless
[802-11-wireless] ssid=bandito 5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Rainy_River (based on set time zone)

country CA:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)

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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:5.22 GHz (Channel 44)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1F848CE7E08483BA640F837
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     D4379726579A4DE1FB7783F
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     330867CC8B48F5E7B4C8088
depends:        ath
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0D7DE85EF15890F115735E2
depends:        cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.18.3-031803-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F2E189013C3BA380B28AA09
depends:        cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath3k]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     5192CF4B9470D212792430F
depends:        bluetooth
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.18.3-031803-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

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
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.169791] ath: phy0: ASPM enabled: 0x43
[   11.169794] ath: EEPROM regdomain: 0x6c
[   11.169795] ath: EEPROM indicates we should expect a direct regpair map
[   11.169798] ath: Country alpha2 being used: 00
[   11.169799] ath: Regpair used: 0x6c
[   21.763091] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.535191] wlan0: authenticate with <MAC 'bandito 5' [AN8]>
[   26.546102] wlan0: direct probe to <MAC 'bandito 5' [AN8]> (try 1/3)
[   26.749226] wlan0: send auth to <MAC 'bandito 5' [AN8]> (try 2/3)
[   26.750141] wlan0: authenticated
[   26.753220] wlan0: associate with <MAC 'bandito 5' [AN8]> (try 1/3)
[   26.754735] wlan0: RX AssocResp from <MAC 'bandito 5' [AN8]> (capab=0x11 status=0 aid=1)
[   26.754859] wlan0: associated
[   26.754905] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.781690] ath: EEPROM regdomain: 0x807c
[   26.781697] ath: EEPROM indicates we should expect a country code
[   26.781700] ath: doing EEPROM country->regdmn map search
[   26.781703] ath: country maps to regdmn code: 0x3a
[   26.781706] ath: Country alpha2 being used: CA
[   26.781708] ath: Regpair used: 0x3a
[   26.781711] ath: regdomain 0x807c dynamically updated by country IE

########## wireless info END ############


```

---

### Post by praseodym on 2015-08-02
Try deactivating IPv6 in the NM settings. Additionally, deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by bandito40 on 2015-08-03
Thanks you.  Seams to have solved the problem on two laptops running 14.04.

---

