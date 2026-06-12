---
title: "Wifi is good in windows bad in linux"
date: 2015-07-13
forum: Networking &amp; Wireless
---

### Post by aqhebad on 2015-07-13
hi everyone
I have installed lubuntu in my laptop
the problem is my wifi is sucks in linux(it works slowly, have low signal, unstable, sometimes have high latency jump)
but it's works great in windows
I already tried update the linux to latest version i do upgrade and dist-upgrade
but the problem still exist
I have run varunendra wireless script 
```
[COLOR=#000000]########## wireless info START ##########[/COLOR]
Report from: 13 Jul 2015 15:41 WIB +0700

Booted last: 13 Jul 2015 15:08 WIB +0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14b7]
    Kernel driver in use: r8169

07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. Device [105b:e054]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 002 Device 002: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rt2800pci              13630  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              652777  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              494362  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19193  1 asus_wmi
video                  20128  1 asus_wmi

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
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::864b:f5ff:fe2a:4b92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23089670 (23.0 MB)  TX bytes:5568665 (5.5 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Buncis's Mansion"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Buncis's Mansion' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:41  Invalid misc:16   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.15    0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       676     1  0 15:08 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Buncis's Mansion] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    net25:           Infra, <MAC 'net25' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA2
    *Buncis's Mansion: Infra, <MAC 'Buncis's Mansion' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 53 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.15

    DNS:             8.8.8.8
    DNS:             202.134.0.155
    DNS:             203.130.196.155
    DNS:             8.8.4.4
    DNS:             203.130.196.5
    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/net25]] (600 root)
[connection] id=net25 | type=802-11-wireless
[802-11-wireless] ssid=net25 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Buncis's Mansion]] (600 root)
[connection] id=Buncis's Mansion | type=802-11-wireless
[802-11-wireless] ssid=Buncis's Mansion | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Buncis's Mansion' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Buncis's Mansion"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003783a8c71
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E643C8F6A545F357EEB41AF
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4F1D9212CBFF4F4BE09171A
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     EDDCA794C9E4C3981037918
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7856EF56F97508465F566A2
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     71EFA3CA86D02D0528C49EE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x5390 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1379.083292] wlan0: authenticate with <MAC 'Buncis's Mansion' [AC1]>
[ 1379.097658] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1379.115587] wlan0: authenticated
[ 1379.117184] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1380.052839] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 2/3)
[ 1380.164840] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 3/3)
[ 1380.276722] wlan0: association with <MAC 'Buncis's Mansion' [AC1]> timed out
[ 1381.846808] wlan0: authenticate with <MAC 'Buncis's Mansion' [AC1]>
[ 1381.860602] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1381.862429] wlan0: authenticated
[ 1381.864266] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1381.968223] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 2/3)
[ 1382.072151] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 3/3)
[ 1382.176221] wlan0: association with <MAC 'Buncis's Mansion' [AC1]> timed out
[ 1384.259896] wlan0: authenticate with <MAC 'net25' [AN1]>
[ 1384.271854] wlan0: send auth to <MAC 'net25' [AN1]> (try 1/3)
[ 1384.277255] wlan0: authenticated
[ 1384.277803] rt2800pci 0000:07:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1384.277815] rt2800pci 0000:07:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1384.279379] wlan0: associate with <MAC 'net25' [AN1]> (try 1/3)
[ 1384.284470] wlan0: RX AssocResp from <MAC 'net25' [AN1]> (capab=0x411 status=0 aid=4)
[ 1384.284712] wlan0: associated
[ 1576.911104] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1577.071126] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1577.231236] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1577.599225] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1577.759281] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1577.919270] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1578.079279] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1578.511355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1578.671336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1578.831396] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1578.991417] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1617.708652] wlan0: deauthenticating from <MAC 'net25' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1619.454883] wlan0: authenticate with <MAC 'Buncis's Mansion' [AC1]>
[ 1619.470117] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1619.573559] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 2/3)
[ 1619.575807] wlan0: authenticated
[ 1619.577611] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1619.681591] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 2/3)
[ 1619.785522] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 3/3)
[ 1619.889612] wlan0: association with <MAC 'Buncis's Mansion' [AC1]> timed out
[ 1621.066552] wlan0: authenticate with <MAC 'Buncis's Mansion' [AC1]>
[ 1621.081801] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1621.085866] wlan0: authenticated
[ 1621.089504] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1621.193422] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 2/3)
[ 1621.297533] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 3/3)
[ 1621.401506] wlan0: association with <MAC 'Buncis's Mansion' [AC1]> timed out
[ 1622.970685] wlan0: authenticate with <MAC 'Buncis's Mansion' [AC1]>
[ 1622.985659] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1623.089337] wlan0: send auth to <MAC 'Buncis's Mansion' [AC1]> (try 2/3)
[ 1623.094303] wlan0: authenticated
[ 1623.097652] wlan0: associate with <MAC 'Buncis's Mansion' [AC1]> (try 1/3)
[ 1623.101956] wlan0: RX AssocResp from <MAC 'Buncis's Mansion' [AC1]> (capab=0x431 status=0 aid=3)
[ 1623.102187] wlan0: associated
[ 1641.723449] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 10 times)
[ 1936.973906] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1937.133981] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[ 1937.293989] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[ 1938.046189] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush (repeated 4 times)
 [COLOR=#000000]########## wireless info END ############[/COLOR]
```

here is the paste bin [http://paste.ubuntu.com/11871424/](http://paste.ubuntu.com/11871424/)

---

### Post by praseodym on 2015-07-14
Change the encryption mode to pure WPA2-AES (CCMP), not mixed mode WPA/WPA2. Check the router manual.

---

