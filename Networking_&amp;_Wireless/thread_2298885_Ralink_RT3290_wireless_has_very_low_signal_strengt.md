---
title: "Ralink RT3290 wireless has very low signal strength on 14.04"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by pawanthegunner on 2015-10-14
I am having issues with the Wi-Fi connectivity on my HP Probook 4440s with a Ralink card. The wireless speeds are very slow compared to Windows. And the signal strength is never over 50% whereas it is around 80% for Windows. I have tried a few solutions for RT cards, but none seem to work. Any help? Here is the output from the wireless script: 

```

########## wireless info START ##########

Report from: 14 Oct 2015 18:36 IST +0530

Booted last: 14 Oct 2015 18:20 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:17f3]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c29 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              630728  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19177  1 hp_wmi

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

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.87.3.65  Bcast:10.87.3.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2818226 (2.8 MB)  TX bytes:764596 (764.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ION@15th-Block"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ION@15th-Block' [AN10]>   
          Bit Rate=19.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:25   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.87.0.1       0.0.0.0         UG    0      0        0 wlan0
10.87.0.0       0.0.0.0         255.255.252.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1077     1  0 18:20 ?        00:00:00 NetworkManager

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

- Device: wlan0  [ION@15th-Block 1] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           19 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Photon Max Wi-Fi_FF93: Infra, <MAC 'Photon Max Wi-Fi_FF93' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA2
    ION@16th-Block:  Infra, <MAC 'ION@16th-Block' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    ION@15th-Block:  Infra, <MAC 'ION@15th-Block' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    ION@15th-Block:  Infra, <MAC 'ION@15th-Block' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    ION@17th-Block:  Infra, <MAC 'ION@17th-Block' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10
    ION@15th-Block:  Infra, <MAC 'ION@15th-Block' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    Connectify-YAS:  Infra, <MAC 'Connectify-YAS' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    ION@15th-Block:  Infra, <MAC 'ION@15th-Block' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    Skywalking twerp:Infra, <MAC 'Skywalking twerp:Infra, <MAC address>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    *ION@15th-Block: Infra, <MAC 'ION@15th-Block' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42

  IPv4 Settings:
    Address:         10.87.3.65
    Prefix:          22 (255.255.252.0)
    Gateway:         10.87.0.1

    DNS:             1.186.15.110
    DNS:             1.186.15.106
    DNS:             1.186.47.2

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

[[/etc/NetworkManager/system-connections/XT1033 3697]] (600 root)
[connection] id=XT1033 3697 | type=802-11-wireless
[802-11-wireless] ssid=XT1033 3697 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sony Xperia tipo_4a15]] (600 root)
[connection] id=Sony Xperia tipo_4a15 | type=802-11-wireless
[802-11-wireless] ssid=Sony Xperia tipo_4a15 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ION@15th-Block 1]] (600 root)
[connection] id=ION@15th-Block 1 | type=802-11-wireless
[802-11-wireless] ssid=ION@15th-Block | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Connectify1111000]] (600 root)
[connection] id=Connectify1111000 | type=802-11-wireless
[802-11-wireless] ssid=Connectify1111000 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ION@MIT-Library]] (600 root)
[connection] id=ION@MIT-Library | type=802-11-wireless
[802-11-wireless] ssid=ION@MIT-Library | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ION@MIT-NLH]] (600 root)
[connection] id=ION@MIT-NLH | type=802-11-wireless
[802-11-wireless] ssid=ION@MIT-NLH | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ION@15th-Block]] (600 root)
[connection] id=ION@15th-Block | type=802-11-wireless
[802-11-wireless] ssid=ION@15th-Block | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ION@16th-Block]] (600 root)
[connection] id=ION@16th-Block | type=802-11-wireless
[802-11-wireless] ssid=ION@16th-Block | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

virbr0    no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C88E1E4BD840C950F493E4
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A6B5D01725492005F5918FA
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1B9A9CB4CAAB78DFE7974EA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8D081A0C2EE28771C5194E1
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/ralink-bt.conf]
install rtbth /sbin/modprobe --ignore-install rtbth; mknod /dev/rtbth c 192 0; /usr/bin/rtbt &

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   58.588585] wlan0: direct probe to <MAC 'ION@15th-Block' [AN10]> (try 2/3)
[   58.792747] wlan0: direct probe to <MAC 'ION@15th-Block' [AN10]> (try 3/3)
[   58.996848] wlan0: authentication with <MAC 'ION@15th-Block' [AN10]> timed out
[   59.241534] wlan0: authenticate with <MAC 'ION@15th-Block' [AN4]>
[   59.257148] wlan0: send auth to <MAC 'ION@15th-Block' [AN4]> (try 1/3)
[   59.262590] wlan0: authenticated
[   59.265138] wlan0: associate with <MAC 'ION@15th-Block' [AN4]> (try 1/3)
[   59.270845] wlan0: RX AssocResp from <MAC 'ION@15th-Block' [AN4]> (capab=0x401 status=0 aid=8)
[   59.270957] wlan0: associated
[   59.281082] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'ION@15th-Block' [AN4]>
[   64.960819] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=88.247.125.60 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=62404 DF PROTO=TCP SPT=2150 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[   67.657730] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=88.247.125.60 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=62405 DF PROTO=TCP SPT=2150 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[   73.663914] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=88.247.125.60 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=62406 DF PROTO=TCP SPT=2150 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[   79.899305] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43266 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[   79.901769] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43267 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[   82.216447] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=23.217.239.139 DST=10.87.3.65 LEN=1500 TOS=0x08 PREC=0x00 TTL=52 ID=30263 DF PROTO=TCP SPT=443 DPT=35745 WINDOW=972 RES=0x00 ACK URGP=0 
[  104.807023] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43268 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  104.821138] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43269 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  106.809134] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=173.255.112.173 DST=10.87.3.65 LEN=98 TOS=0x00 PREC=0x00 TTL=42 ID=58354 DF PROTO=TCP SPT=443 DPT=50395 WINDOW=251 RES=0x00 ACK PSH URGP=0 
[  113.256811] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=104.148.44.191 DST=10.87.3.65 LEN=40 TOS=0x00 PREC=0x00 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  129.549365] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43271 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  154.087799] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43273 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  178.566464] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43275 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  178.569374] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43274 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  202.621557] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43276 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  226.824185] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43279 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  252.391265] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=119.116.36.6 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=30520 DF PROTO=TCP SPT=45016 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[  255.393367] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=119.116.36.6 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=30521 DF PROTO=TCP SPT=45016 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[  350.430382] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43288 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  350.497643] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43289 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  375.323638] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43290 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  375.432397] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43291 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  467.943690] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=173.255.112.173 DST=10.87.3.65 LEN=98 TOS=0x00 PREC=0x00 TTL=42 ID=58357 DF PROTO=TCP SPT=443 DPT=50395 WINDOW=251 RES=0x00 ACK PSH URGP=0 
[  588.322657] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=173.255.112.173 DST=10.87.3.65 LEN=98 TOS=0x00 PREC=0x00 TTL=42 ID=58358 DF PROTO=TCP SPT=443 DPT=50395 WINDOW=251 RES=0x00 ACK PSH URGP=0 
[  604.723287] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=23.207.129.109 DST=10.87.3.65 LEN=83 TOS=0x00 PREC=0x00 TTL=59 ID=36111 DF PROTO=TCP SPT=443 DPT=58587 WINDOW=962 RES=0x00 ACK PSH URGP=0 
[  629.512667] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=222.186.190.37 DST=10.87.3.65 LEN=40 TOS=0x00 PREC=0x00 TTL=110 ID=256 PROTO=TCP SPT=332 DPT=5900 WINDOW=16384 RES=0x00 SYN URGP=0 
[  762.756798] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=61.147.103.96 DST=10.87.3.65 LEN=40 TOS=0x00 PREC=0x00 TTL=103 ID=256 PROTO=TCP SPT=6000 DPT=1433 WINDOW=16384 RES=0x00 SYN URGP=0 
[  821.313183] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=183.248.74.73 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=48 ID=51779 DF PROTO=TCP SPT=40315 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[  824.306530] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=183.248.74.73 DST=10.87.3.65 LEN=60 TOS=0x00 PREC=0x00 TTL=48 ID=51780 DF PROTO=TCP SPT=40315 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[  842.663852] wlan0: authenticate with <MAC 'ION@15th-Block' [AN3]>
[  842.671157] wlan0: direct probe to <MAC 'ION@15th-Block' [AN3]> (try 1/3)
[  842.875193] wlan0: direct probe to <MAC 'ION@15th-Block' [AN3]> (try 2/3)
[  843.079340] wlan0: direct probe to <MAC 'ION@15th-Block' [AN3]> (try 3/3)
[  843.283430] wlan0: authentication with <MAC 'ION@15th-Block' [AN3]> timed out
[  843.464511] wlan0: authenticate with <MAC 'ION@15th-Block' [AN6]>
[  843.479726] wlan0: direct probe to <MAC 'ION@15th-Block' [AN6]> (try 1/3)
[  843.683668] wlan0: direct probe to <MAC 'ION@15th-Block' [AN6]> (try 2/3)
[  843.887812] wlan0: direct probe to <MAC 'ION@15th-Block' [AN6]> (try 3/3)
[  844.092006] wlan0: authentication with <MAC 'ION@15th-Block' [AN6]> timed out
[  844.236626] wlan0: authenticate with <MAC 'ION@15th-Block' [AN8]>
[  844.244201] wlan0: direct probe to <MAC 'ION@15th-Block' [AN8]> (try 1/3)
[  844.448169] wlan0: direct probe to <MAC 'ION@15th-Block' [AN8]> (try 2/3)
[  844.652332] wlan0: direct probe to <MAC 'ION@15th-Block' [AN8]> (try 3/3)
[  844.856462] wlan0: authentication with <MAC 'ION@15th-Block' [AN8]> timed out
[  846.029980] wlan0: authenticate with <MAC 'ION@15th-Block' [AN10]>
[  846.045343] wlan0: send auth to <MAC 'ION@15th-Block' [AN10]> (try 1/3)
[  846.056343] wlan0: authenticated
[  846.057212] wlan0: associate with <MAC 'ION@15th-Block' [AN10]> (try 1/3)
[  846.062487] wlan0: RX AssocResp from <MAC 'ION@15th-Block' [AN10]> (capab=0x401 status=0 aid=7)
[  846.062594] wlan0: associated
[  846.235237] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'ION@15th-Block' [AN10]>
[  857.486634] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43192 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  857.487001] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43193 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  882.608547] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43192 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  907.955536] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43193 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  907.956270] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43192 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  926.310507] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:74:e5:43:36:ac:1f:08:00 SRC=10.87.3.241 DST=10.87.3.65 LEN=29 TOS=0x00 PREC=0x00 TTL=128 ID=7693 PROTO=UDP SPT=62068 DPT=7 LEN=9 
[  933.343732] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=77.111.195.158 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43193 PROTO=UDP SPT=27015 DPT=1900 LEN=98 
[  933.344328] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:00:24:14:58:da:c7:08:00 SRC=193.107.36.36 DST=10.87.3.65 LEN=118 TOS=0x08 PREC=0x20 TTL=241 ID=43192 PROTO=UDP SPT=80 DPT=1900 LEN=98 
[  934.460013] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:74:e5:43:36:ac:1f:08:00 SRC=10.87.3.241 DST=10.87.3.65 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=8052 DF PROTO=TCP SPT=51013 DPT=2987 WINDOW=8192 RES=0x00 SYN URGP=0 
[  934.565090] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:74:e5:43:36:ac:1f:08:00 SRC=10.87.3.241 DST=10.87.3.65 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=8162 DF PROTO=TCP SPT=51013 DPT=2987 WINDOW=8192 RES=0x00 SYN URGP=0 
[  938.355907] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:74:e5:43:36:ac:1f:08:00 SRC=10.87.3.241 DST=10.87.3.65 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=8216 DF PROTO=TCP SPT=51013 DPT=2987 WINDOW=65535 RES=0x00 SYN URGP=0 

########## wireless info END ############


```

---

### Post by michi1983 on 2015-10-14
Hm, only thing I can say is that Linux is a little more sensitive when it comes to wifi handling.
I would put the focus first on setting the wifi up correctly than on driver issues.
This includes that I would only want to use WPA2-PSK AES encryption, no TKIP and then I would use a free wifi scanner like [this one]("http://ubuntuhandbook.org/index.php/2013/08/linssid-wifi-scanner-for-ubuntu-linux-mint/") and see if my wifi has a 4-channel distance to nearby wifis.

---

