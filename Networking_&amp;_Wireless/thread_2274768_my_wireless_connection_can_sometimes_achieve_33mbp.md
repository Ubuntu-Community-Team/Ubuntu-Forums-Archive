---
title: "my wireless connection can sometimes achieve 33mbps but always drops to +or- 1mbps"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by ortermagic on 2015-04-22
I have been getting very bad wlan speeds can someone please scrutinise the following script for errors 
 
```

########## wireless info START ##########

Report from: 22 Apr 2015 10:07 BST +0100

Booted last: 22 Apr 2015 08:03 BST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-36-generic #48-Ubuntu SMP Tue Apr 14 20:08:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Device [7470:3468]
    Kernel driver in use: r8169

04:06.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:2093]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 040b:2014 Weltrend Semiconductor 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 045e:0779 Microsoft Corp. LifeCam HD-3000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 04e8:6865 Samsung Electronics Co., Ltd GT-I9300 Phone [Galaxy S III] (PTP mode)
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::32b5:c2ff:fe02:21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1774283 (1.7 MB)  TX bytes:120572 (120.5 KB)

wlan2     Link encap:Ethernet  HWaddr <MAC 'wlan2' [IF]>  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea94:f6ff:fedd:41e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7033280 (7.0 MB)  TX bytes:1977440 (1.9 MB)

##### iwconfig ##########################

eth1      no wireless extensions.

lo        no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:"BTHub3-SM58"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'BTHub3-SM58' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:46   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan2

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan2  [BTHub3-SM58] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan2' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DIRECT-8I[TV]BTHub3-SM58: Infra, <MAC 'DIRECT-8I[TV]BTHub3-SM58' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2
    uk-house:        Infra, <MAC 'uk-house' [AN2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 30 WPA2
    BTWiFi-with-FON: Infra, <MAC 'BTWiFi-with-FON' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82
    *BTHub3-SM58:    Infra, <MAC 'BTHub3-SM58' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.75
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: eth1  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.73
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

no-auto-default=<MAC 'eth1' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/BTHub3-SM58]] (600 root)
[connection] id=BTHub3-SM58 | type=802-11-wireless
[802-11-wireless] ssid=BTHub3-SM58 | bssid=<MAC 'BTHub3-SM58' [AC1]> | mac-address=<MAC 'wlan2' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-8I[TV]BTHub3-SM58]] (600 root)

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

eth1      no frequency information.

lo        no frequency information.

wlan2     13 channels in total; available frequencies :
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

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth1      Interface doesn't support scanning.

wlan2     Scan completed :
          Cell 01 - Address: <MAC 'BTHub3-SM58' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-SM58"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000da45cbc3
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTWiFi-with-FON' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000da41ba2a
                    Extra: Last beacon: 28ms ago
          Cell 03 - Address: <MAC 'DIRECT-8I[TV]BTHub3-SM58' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-8I[TV]BTHub3-SM58"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000220de47b0
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknlo        Interface doesn't support scanning.

own: 4A0E14000A002C01C800140005001900
          Cell 04 - Address: <MAC 'TALKTALK-00138A' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-00138A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008afe60b863
                    Extra: Last beacon: 28ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:11:63:87:7F:6D:EB:C1:40:F8:DB:A7:EF:C1:EB:8C:33:61:50:3F
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:11:63:87:7F:6D:EB:C1:40:F8:DB:A7:EF:C1:EB:8C:33:61:50:3F
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:11:63:87:7F:6D:EB:C1:40:F8:DB:A7:EF:C1:EB:8C:33:61:50:3F
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:11:63:87:7F:6D:EB:C1:40:F8:DB:A7:EF:C1:EB:8C:33:61:50:3F
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     05170C37AC7B7A82211E896
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:11:63:87:7F:6D:EB:C1:40:F8:DB:A7:EF:C1:EB:8C:33:61:50:3F
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        3C:11:63:87:7F:6D:EB:C1:40:F8:DB:A7:EF:C1:EB:8C:33:61:50:3F
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
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

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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
# PCI device 0x168c:0x002d (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x168c:0x0029 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[ 4568.598860] r8169 0000:02:00.0 eth1: link down (repeated 2 times)
[ 4568.598919] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 4568.620976] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 4569.454692] wlan2: authenticate with <MAC 'BTHub3-SM58' [AC1]>
[ 4569.462276] wlan2: send auth to <MAC 'BTHub3-SM58' [AC1]> (try 1/3)
[ 4569.464021] wlan2: authenticated
[ 4569.466270] wlan2: associate with <MAC 'BTHub3-SM58' [AC1]> (try 1/3)
[ 4569.468868] wlan2: RX AssocResp from <MAC 'BTHub3-SM58' [AC1]> (capab=0x411 status=0 aid=2)
[ 4569.468928] wlan2: associated
[ 4569.468950] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 4570.264952] r8169 0000:02:00.0 eth1: link up
[ 4570.264962] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

########## wireless info END ############

```

I get +79mbps using ethernet on this desktop pc.

---

### Post by jeremy31 on 2015-04-22
First thing I would do is change the wifi router encryption setting to WPA2-AES or WPA2 only

---

### Post by ortermagic on 2015-04-22
[INDENT]         Hi Jeremy,
Unfortunately in the network connections edit box I get the following choices 

none
WEP40/128-bit key(HEX orASCII)
WEP128-bit Passphrase
leap
dynamic WEP (802.1x)
WPA&WPA2 Personal
WPA&WPA2 Enterprise


and on the bthomehub configuration help page (see attatchment)
I get the following choices
WPA&WPA2
WPA2 only
WPA only
WEP (64/40 bits)
or none     
[/INDENT]
                                                                                                        [ATTACH=CONFIG]261464[/ATTACH]
 Which should I change? if I change the bt form it does not seem to affect the network connection edit

---

### Post by jeremy31 on 2015-04-22
You should be able to leave the setting in Network Manager alone but change the bthomehub to WPA2 only

---

### Post by ortermagic on 2015-04-23
Thanks for helping Jeremy, I have applied the change you suggested but it has not made much difference, I am currently getting +- 20mbps on wlan and +- 75 mbps on eth0 which isn't too bad, at the moment I think my router may be at fault.
I will keep this question open for the moment, and come back if there is any more deterioration in signal.

---

