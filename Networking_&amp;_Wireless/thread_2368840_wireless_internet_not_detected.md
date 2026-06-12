---
title: "wireless internet not detected?"
date: 2017-08-15
forum: Networking &amp; Wireless
---

### Post by Forbees on 2017-08-15
```
 lspci | grep Wireless
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter (rev 01)
```

sometimes when i boot i have no wifi, can't find any signal. what *seems* to fix it is powering down, unplugging the power cable, and wiggling the PCI-E card. #ConfirmationBias.


i just spent the last hour trying to get my wifi up again and it magically "fixed" itself. but what i found out is when the wifi isn't working, ubuntu isn't even detecting my wireless interface

ifconfig doesn't show wlan0
iwconfig doesn't show wlan0
ifconfig wlan0 up says "no such device"

i spent $60 on this NIC, i'm open to having to buy a different one since i this one seems to have some known issues with ubuntu(bought it in a pinch and it was my only option at the time) but i'm having a hard time finding a NIC that actually supports wireless AC 5gHz with ubuntu


so.... how do i stop ubuntu from forgetting there's a NIC plugged in? or do i just get a new NIC and what one?

---

### Post by praseodym on 2017-08-16
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by Forbees on 2017-08-16
```

########## wireless info START ##########

Report from: 16 Aug 2017 20:04 EDT -0400

Booted last: 16 Aug 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.10.0-32-generic #36-Ubuntu SMP Tue Aug 8 12:10:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:8505]
	Kernel driver in use: r8169

07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter [10ec:8812] (rev 01)
	Subsystem: TRENDnet RTL8812AE 802.11ac PCIe Wireless Network Adapter [20f4:807e]
	Kernel driver in use: rtl8821ae

##### lsusb #############################

Bus 003 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4088 Creative Technology, Ltd Live! Cam Chat HD [VF0700]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 005 Device 002: ID 0e6f:0214 Logic3 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0d8c:0139 C-Media Electronics, Inc. Multimedia Headset [Gigaware by Ignition L.P.]
Bus 004 Device 003: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 004 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
rtl8821ae             229376  0
btcoexist             167936  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,btcoexist,rtl8821ae
mac80211              782336  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              602112  2 mac80211,rtlwifi
mxm_wmi                16384  0
wmi                    16384  2 asus_wmi,mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 432  bytes 32970 (32.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 432  bytes 32970 (32.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::2e0:4cff:fe88:1200  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 35049  bytes 33411303 (33.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 29007  bytes 5690468 (5.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Mad Scientist"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'Mad Scientist' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:257   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 192.168.1.1
nameserver 127.0.0.53
search wowway.com

##### network managers ##################

Installed:

	Wicd

Running:

	None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Mad Scientist]] (600 root)
[connection] id=Mad Scientist | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Mad Scientist
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Mad Scientist 1]] (600 root)
[connection] id=Mad Scientist 1 | type=wifi | permissions=
[wifi] bssid=<MAC 'Mad Scientist' [AC1]> | mac-address=<MAC address> | mac-address-blacklist= | mtu=1500 | ssid=Mad Scientist
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Detroit (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Mad Scientist' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Mad Scientist"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012754c272d
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WOW!5500' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"WOW!5500"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000021a7438427
                    Extra: Last beacon: 6752ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Hillsonly_EXT' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Hillsonly_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a8727ab1d6
                    Extra: Last beacon: 916ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b0231dbb5
                    Extra: Last beacon: 11496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Mad Scientist 5GHz' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Mad Scientist 5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012756dc32d
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Dwight_House' [AC6]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Dwight_House"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f66bbc183
                    Extra: Last beacon: 12864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'nofreewifi_EXT' [AC7]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"nofreewifi_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000156e3a6a170
                    Extra: Last beacon: 12848ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     6CA5F147BB6BDA3D20D84FF
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.10.0-32-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B833496EC3F52F9539F912E
depends:        mac80211,rtlwifi
vermagic:       4.10.0-32-generic SMP mod_unload 

[rtlwifi]
filename:       /lib/modules/4.10.0-32-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     0BB42E4C7EBEC81FFE99621
depends:        mac80211,cfg80211
vermagic:       4.10.0-32-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.10.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-32-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    5.293621] rtlwifi: loading out-of-tree module taints kernel.
[    5.293670] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[    5.357038] rtl8821ae: Using firmware rtlwifi/rtl8812aefw.bin
[    5.357042] rtl8821ae: Using firmware rtlwifi/rtl8812aefw_wowlan.bin
[    5.379798] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    5.380005] rtlwifi: rtlwifi: wireless switch is on
[    5.515566] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e8.hcd failed with error -2
[    5.515568] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e8.hcd not found
[    6.460590] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   24.240209] wlan0: authenticate with <MAC 'Mad Scientist' [AC1]>
[   24.240934] wlan0: send auth to <MAC 'Mad Scientist' [AC1]> (try 1/3)
[   24.242490] wlan0: authenticated
[   24.243187] wlan0: associate with <MAC 'Mad Scientist' [AC1]> (try 1/3)
[   24.246027] wlan0: RX AssocResp from <MAC 'Mad Scientist' [AC1]> (capab=0x1411 status=0 aid=1)
[   24.246226] wlan0: associated
[   24.246292] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

currently the wireless is working, so idk if that'll affect what's in here

---

### Post by genericvii143 on 2017-08-16
"NetworkManager is not installed (package "network-manager")."  I have a feeling that the problem in in there sound little bit weird.Do a research how the network manager should be set up.

---

### Post by Forbees on 2017-08-17
i uninstalled network manager to start using Wicd instead. gave me a little bit more stability. the problem was there before i did that though.


pretty much i've come to the conclusion that i have to modprobe the drivers and reboot every time wlan0 doesn't want to show up. 

i'm running another thread asking about getting this card to work with anything other than wireless b/g (since N has drops and ubuntu doesn't seem to like 5gHz for AC) and we realized that the realtek [driver]("https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa") pack doesn't actually have my chip in there (RTL8812AE) and i'm using RTL8821AE instead

i feel like this has something to do with it but it wouldn't know what driver to modprobe in for hopes of better reliability . currently other thread is suggesting to cut the losses and get a better supported card

---

### Post by wildmanne39 on 2017-08-17
You said when you cannot connect your wifi card is not even seen by Ubuntu that means there is a hardware issue, even if the driver is not working correctly when you run the command:
```
lspci -nnk | grep -iA2 net
```
your card should always show up.

---

### Post by Forbees on 2017-08-18
i wish it was hardware. windows has no problem with it......


previous theory i had is bunk now. got home from work and had to reboot about 20 times to get the wireless up again, even with modprobe'ing the drivers back in. i guess yesterday it was a fluke that it seemed to work


i can also boot from the live USB i used to install this copy of ubuntu and the wifi "works" (packet drops and slow speeds, common with this card). google'ing told me to disable wireless N on my router for 2.4Ghz, installed the rtl8821ae driver, removed the default network manager and installed Wicd, which seems to get the 2.4Ghz wireless G speeds between 200KB/s and 1.4MB/s and connection stable which lasted for two months before i started having this issue


next time it fails to work i'll see if the code you gave me shows anything. i've also tried using a different PCI-e port and it still happens

---

### Post by wildmanne39 on 2017-08-18
There are some things we can do to help as long as it is not a hardware issue, I do not see your network information in the output it is like your router was turned off or wifi was not enabled in the router at the time.

Let's turn of power management for your wifi:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Your resolve config is not correct it says:
```
resolv.conf #######################

nameserver 192.168.1.1
nameserver 127.0.0.53
search wowway.com

```
It should only have:
```
nameserver 127.0.0.53
```
in that file, if you did not change that and I doubt you did we need to fix it by doing.
```
sudo dpkg-reconfigure resolvconf
```
and then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one, then reboot.

I believe the question you need to answer no too has been removed in 17.04.

wicd has not been maintained in a long time, network manager would be a better choice, you can not  have both installed at the same time.

I would remove the spaces in the network name in the router and set encryption to just wpa2 if you have that option and a fixed channel of 1, 6 or 11.

Do not try to use the 5ghz range while we try to get wifi working.

Which network are you trying to connect too?

Also we need to open the NetworkManager file with your text editor because there is a bug in 17.04 network manager:
  
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot

---

### Post by Forbees on 2017-08-21
nice reply, thanks for the maximum effort :D

 so ```
 lspci -nnk | grep -iA2 net 
``` shows my card whether it's working or not, which throws me off some. but it does support the idea that maybe my problem could be coming from Wicd.. so i'm going to go back to network manager and remove it. 5ghz hasn't been an option, i have another thread trying to figure out why 5ghz cant connect to anything. 

i want to say i already turned off power management but i'll run the code again to be safe

possibly note worthy, my wireless interface shows up as wlps0 when not working and wlan0 when working. all i could find online was that there's a new naming scheme and lots of people have wlps0 with internet working

```
sudo dpkg-reconfigure resolvconf
``` after selecting Yes' to the "Prepare /etc/resolv.conf for dynamic updates?"  gives me next
```
Reboot recommended                                                          
 &#9474;                                                                             
 &#9474; Suppliers of name server information such as local caching name servers     
 &#9474; and interface configurers are expected to supply name server information    
 &#9474; to the resolvconf program. However, although installation of the            
 &#9474; resolvconf package triggers them to supply their information, some of       
 &#9474; them fail to do so.                                                         
 &#9474;                                                                             
 &#9474; This bug would lead to loss of valid name server information on             
 &#9474; installation of the resolvconf package if the following workaround were     
 &#9474; not adopted: resolvconf includes the full contents of the                   
 &#9474; pre-installation /etc/resolv.conf in its database until reboot. This has    
 &#9474; the drawback that name server information is retained even if the           
 &#9474; associated interface is later deconfigured. (This incorrect behavior is
judged to be less harmful than the alternative of losing valid              
 &#9474; information.)                                                               
 &#9474;                                                                             
 &#9474; Until the bug in question is fixed and the workaround removed, the only     
 &#9474; way to ensure that resolvconf has fully correct name server information     
 &#9474; after the resolvconf package has been installed on a running system is      
 &#9474; to reboot the system.                                                       
 &#9474;                       
```


so i'll continue to ```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
``` 
heres the output
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

seems a little short lol... adding the lines in and saved.


so looks like it's time for a reboot. i'll run sudo dpkg-reconfigure resolvconf again since its asking for one... probably something to do with not rebooting after removing wicd and reinstalling network manager 


also the network SSID is Mad Scientist. lets hope this reboot doesn't brick my internet lol

---

### Post by Forbees on 2017-08-21
reboot and the wifi is working right away. first time in two weeks i haven't had to reboot 20 times or w.e. to get online. but i'm not ready to say we're out of the woods yet

sudo dpkg-reconfigure resolvconf still gives me the same reboot recommend message. so sounds like something else isn't right

---

### Post by Forbees on 2017-08-26
4 straight days of no issues. must have been something to do with wicd since a resent update or something along the codes you had me run. speedtest is showing about max for wireless B/G so i'm marking thread solved

---

### Post by wildmanne39 on 2017-08-26
Glad it is working, it is not an update, it is the commands I gave you to run.

---

