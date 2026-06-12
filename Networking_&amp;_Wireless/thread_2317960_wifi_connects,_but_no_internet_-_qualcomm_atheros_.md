---
title: "wifi connects, but no internet - qualcomm atheros ar928x"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by fab4 on 2016-03-21
hello, as mentioned in the title, i cannot get internet access when connected through wifi. ethernet works fine, though. the wifi works also on several android and windows machines in our household. so there is no issue with that.
any help appreciated.
regards fabian

```
########## wireless info START ##########

Report from: 21 Mar 2016 23:13 CET +0100

Booted last: 21 Mar 2016 23:03 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:38:02 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1815]
    Kernel driver in use: sis190

02:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: AzureWave AW-NE771 802.11bgn Wireless Mini PCIe Card [AR9281] [1a3b:1067]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. RTS5116 Card Reader Controller
Bus 001 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 143360  0 
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              729088  1 ath9k
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9391809 (9.3 MB)  TX bytes:1453914 (1.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.67  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2669 errors:0 dropped:1 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:664711 (664.7 KB)  TX bytes:27152 (27.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Kommune Kabel Zwei"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Kommune Kabel Zwei' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=17 dBm   
          [CODE]Retry short limit:7   RTS thr:off   Fragment thr:off
```
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:69   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin

##### network managers ##################

Installed:

    NetworkManager

Running:

root       750     1  0 23:03 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Kommune Kabel Zwei] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    EasyBox-790078:  Infra, <MAC 'EasyBox-790078' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    FRITZ!Box 7490:  Infra, <MAC 'FRITZ!Box 7490' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    EasyBox-B87537:  Infra, <MAC 'EasyBox-B87537' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    FRITZ!Box 7490:  Infra, <MAC 'FRITZ!Box 7490' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    EasyBox-1C6526:  Infra, <MAC 'EasyBox-1C6526' [AN5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Kommune Kabel Zwei: Infra, <MAC 'Kommune Kabel Zwei' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    *Kommune Kabel Zwei: Infra, <MAC 'Kommune Kabel Zwei' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WPA WPA2
    FRITZ!Box 7272:  Infra, <MAC 'FRITZ!Box 7272' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    o2-WLAN32:       Infra, <MAC 'o2-WLAN32' [AN9]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 17 WPA2
    FRITZ!Box 7362 SL: Infra, <MAC 'FRITZ!Box 7362 SL' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2

  IPv4 Settings:
    Address:         192.168.2.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sis190
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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

[[/etc/NetworkManager/system-connections/Kommune Kabel Zwei]] (600 root)
[connection] id=Kommune Kabel Zwei | type=802-11-wireless
[802-11-wireless] ssid=Kommune Kabel Zwei | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Kommune Kabel Zwei' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Kommune Kabel Zwei"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df545ee8a
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FRITZ!Box 7490' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7490"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000066bc9c8
                    Extra: Last beacon: 1712ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Kommune Kabel Zwei' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Kommune Kabel Zwei"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009b9dc1e6b
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'EasyBox-790078' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-790078"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f9d6b26a4
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     681B59FC4C4EB63D7B98108
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
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
minstrel_vht_only: Y
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   17.955638] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.972631] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.981032] wlan0: authenticate with <MAC 'Kommune Kabel Zwei' [AC1]>
[   20.001116] wlan0: send auth to <MAC 'Kommune Kabel Zwei' [AC1]> (try 1/3)
[   20.003842] wlan0: authenticated
[   20.008066] wlan0: associate with <MAC 'Kommune Kabel Zwei' [AC1]> (try 1/3)
[   20.011884] wlan0: RX AssocResp from <MAC 'Kommune Kabel Zwei' [AC1]> (capab=0x411 status=0 aid=6)
[   20.012030] wlan0: associated
[   20.012086] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.016680] ath: EEPROM regdomain: 0x8348
[   20.016684] ath: EEPROM indicates we should expect a country code
[   20.016687] ath: doing EEPROM country->regdmn map search
[   20.016689] ath: country maps to regdmn code: 0x3a
[   20.016691] ath: Country alpha2 being used: US
[   20.016692] ath: Regpair used: 0x3a
[   20.016694] ath: regdomain 0x8348 dynamically updated by country IE
[   20.070423] wlan0: deauthenticating from <MAC 'Kommune Kabel Zwei' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   20.078825] wlan0: authenticate with <MAC 'Kommune Kabel Zwei' [AC1]>
[   20.093012] wlan0: send auth to <MAC 'Kommune Kabel Zwei' [AC1]> (try 1/3)
[   20.094892] wlan0: authenticated
[   20.100046] wlan0: associate with <MAC 'Kommune Kabel Zwei' [AC1]> (try 1/3)
[   20.103818] wlan0: RX AssocResp from <MAC 'Kommune Kabel Zwei' [AC1]> (capab=0x411 status=0 aid=6)
[   20.103921] wlan0: associated
[   20.107647] ath: EEPROM regdomain: 0x8348
[   20.107652] ath: EEPROM indicates we should expect a country code
[   20.107654] ath: doing EEPROM country->regdmn map search
[   20.107656] ath: country maps to regdmn code: 0x3a
[   20.107658] ath: Country alpha2 being used: US
[   20.107660] ath: Regpair used: 0x3a
[   20.107662] ath: regdomain 0x8348 dynamically updated by country IE
[   28.000051] sis190 0000:00:04.0 eth0: mii ext = 0000
[   28.024065] sis190 0000:00:04.0 eth0: mii lpa=41e1 adv=01e1 exp=0007
[   28.024073] sis190 0000:00:04.0 eth0: link on 100 Mbps Full Duplex mode
[   28.024097] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  235.320055] sis190 0000:00:04.0 eth0: auto-negotiating...
[  285.572061] sis190 0000:00:04.0 eth0: mii ext = 0000
[  285.604051] sis190 0000:00:04.0 eth0: mii lpa=41e1 adv=01e1 exp=0007
[  285.604060] sis190 0000:00:04.0 eth0: link on 100 Mbps Full Duplex mode

########## wireless info END ############[/CODE]

---

### Post by BulletsWithGPS on 2016-03-22
Hey. I also have the qualcomm atheros ar928x. And the same problem.

I tried ubuntu some months ago and it was working fine. Now, I have this problem in every distro

---

### Post by jeremy31 on 2016-03-22
Does your network have TKIP enabled and/or spaces in the network name?

---

### Post by zeitgeistnz-aaron on 2016-07-17
Hey there, I also have this problem with the qualcomm atheros ar928x. Any help would much appreciated... I have been trying to solve this on my own for hours!!

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Sony Corporation 88E8040 PCI-E Fast Ethernet Controller [104d:903f]
    Kernel driver in use: sky2

03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Foxconn International, Inc. AR928X Wireless Network Adapter (PCI-Express) [105b:e007]
    Kernel driver in use: ath9k

Cheers

---

### Post by wildmanne39 on 2016-07-18
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by danbosse1 on 2016-07-18
I just had a limited Internet connection problem. Try flushing the ip tables and make sure your firewall is off

```
sudo iptables -F
```

---

### Post by him610 on 2016-07-18
> ##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country US:

If this is still set like this, it may be the source of your nonconnectablity.

If you are in Deutschland, you need to set the correct country code. If you are in the US, you need to set the correct timezone.

---

