---
title: "poor wifi with atheros ar9485 on hp 15 notebook running 14.04"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by Dermot Doyle on 2015-01-09
Hi All,
After the terribly expensive and frustrating mistake of buying a refurbished macbook pro (two new motherboards in 4 months, crap software etc) I am happily back in the arms of Ubuntu, which I used for 10 years or so and only have one slight problem. I have googled this and found a fair bit of info, but it either wasn't my exact problem or I didn't understand the answers. I wiped windows 8 off a new HP 15 Notebook and installed 14.04 from a CD with no problems. After about a month I have noticed the wifi struggles to connect to my domestic wifi when my Nexus 7 tablet has no problems. The signal is a bit weak downstairs, but I would be surprised if the laptop's capabilities were not as good as the Nexus. Sometimes rebooting will work, but mainly the only thing I can do is take it closer to the router, reboot, and then when it is connected go back downstairs and it will continue to work, usually uninterrupted. My wifi network always shows up and the icon shows it is trying to connect, but it just fails to and says I am offline. 
```

########## wireless info START ##########

Report from: 09 Jan 2015 10:21 GMT +0000

Booted last: 09 Jan 2015 09:43 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]
	Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:2213]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:c342 Suyin Corp. 
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
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

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::aeb5:7dff:fe15:cc83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13815935 (13.8 MB)  TX bytes:3460848 (3.4 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'dlink' [AC1]>   
          Bit Rate=45 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:7   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

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

  Wired Properties
    Carrier:         off

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           81 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    VM526227-2G:     Infra, <MAC 'VM526227-2G' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTHub5-H9MW_EXT: Infra, <MAC 'BTHub5-H9MW_EXT' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    *dlink:          Infra, <MAC 'dlink' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    SKY80872:        Infra, <MAC 'SKY80872' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    cd_EXT:          Infra, <MAC 'cd_EXT' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA
    SKY95A63:        Infra, <MAC 'SKY95A63' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    TALKTALK-34BF64: Infra, <MAC 'TALKTALK-34BF64' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    SKYB20F2:        Infra, <MAC 'SKYB20F2' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    BTHub5-H9MW:     Infra, <MAC 'BTHub5-H9MW' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    TP-LINK_7635A2:  Infra, <MAC 'TP-LINK_7635A2' [AC8]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17

  IPv4 Settings:
    Address:         192.168.0.103
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

[[/etc/NetworkManager/system-connections/FREE WIFI B]] (600 root)
[connection] id=FREE WIFI B | type=802-11-wireless
[802-11-wireless] ssid=FREE WIFI B | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BTHub5-2CFP]] (600 root)
[connection] id=BTHub5-2CFP | type=802-11-wireless
[802-11-wireless] ssid=BTHub5-2CFP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/My Broadband-c91a]] (600 root)
[connection] id=My Broadband-c91a | type=802-11-wireless
[802-11-wireless] ssid=My Broadband-c91a | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'dlink' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002795fb5170
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTHub5-H9MW_EXT' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-H9MW_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000756444d82d
                    Extra: Last beacon: 3240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000756445b396
                    Extra: Last beacon: 52ms ago
          Cell 04 - Address: <MAC 'BTHub5-H9MW' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-H9MW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007564447182
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BTWifi-X' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000075644564e9
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'SKY80872' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"SKY80872"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002807a70ab
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VM526227-2G' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"VM526227-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d211ed3ac0
                    Extra: Last beacon: 52ms ago
          Cell 08 - Address: <MAC 'TP-LINK_7635A2' [AC8]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_7635A2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     ADAEAFEC0FFEB04BC97E45D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
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

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   16.402190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   18.602502] wlan0: authenticate with <MAC 'dlink' [AC1]>
[   18.629709] wlan0: send auth to <MAC 'dlink' [AC1]> (try 1/3)
[   18.633274] wlan0: authenticated
[   18.633752] wlan0: associate with <MAC 'dlink' [AC1]> (try 1/3)
[   18.637526] wlan0: RX AssocResp from <MAC 'dlink' [AC1]> (capab=0xc31 status=0 aid=1)
[   18.637583] wlan0: associated
[   18.637596] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.641519] ath: EEPROM regdomain: 0x833a
[   18.641525] ath: EEPROM indicates we should expect a country code
[   18.641528] ath: doing EEPROM country->regdmn map search
[   18.641530] ath: country maps to regdmn code: 0x37
[   18.641532] ath: Country alpha2 being used: GB
[   18.641534] ath: Regpair used: 0x37
[   18.641536] ath: regdomain 0x833a dynamically updated by country IE
[   18.669792] wlan0: deauthenticating from <MAC 'dlink' [AC1]> by local choice (reason=2)
[   18.679635] wlan0: authenticate with <MAC 'dlink' [AC1]>
[   18.697435] wlan0: send auth to <MAC 'dlink' [AC1]> (try 1/3)
[   18.700239] wlan0: authenticated
[   18.701839] wlan0: associate with <MAC 'dlink' [AC1]> (try 1/3)
[   18.705546] wlan0: RX AssocResp from <MAC 'dlink' [AC1]> (capab=0xc31 status=0 aid=1)
[   18.705602] wlan0: associated
[   18.708973] ath: EEPROM regdomain: 0x833a
[   18.708978] ath: EEPROM indicates we should expect a country code
[   18.708981] ath: doing EEPROM country->regdmn map search
[   18.708983] ath: country maps to regdmn code: 0x37
[   18.708985] ath: Country alpha2 being used: GB
[   18.708986] ath: Regpair used: 0x37
[   18.708989] ath: regdomain 0x833a dynamically updated by country IE

########## wireless info END ############

```

Thanks for any help

---

