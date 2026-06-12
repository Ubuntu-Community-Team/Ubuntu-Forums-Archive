---
title: "Wireless Internet on Ubuntu 15.04 using Asus X205TA"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by terzim on 2015-04-11
Dear readers,

This is my first post on this forum. I ask your kind help to sort out two issues I have with my new laptop. 

[SIZE=4]**[Some background first]**[/SIZE]


[LIST]
[*]I **installed Ubuntu 15.04** on my newly-bought laptop (model: **Asus X205TA**). Removed Windows fully, so it is now a Linux-only machine. 
[*]The successful installation was achieved by following the **instructions of this page**: [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/) with some little tweaks to adapt the boot process to the partitioning of my hard disk. 
[*]Also, I followed the posts' instructions to manipulate the firmware and have my wireless built-in device recognized, **but with no success** (see problem Number 1, below). 
[/LIST]

[SIZE=4]**[The problems]**[/SIZE]


[LIST]
[*][SIZE=3]**NUMBER 1:**[/SIZE] The **laptop built-in wireless device does not work.** It does not show up at all among the list of devices (see results of the "wireless script" below) 
[*]**[SIZE=3]NUMBER 2:[/SIZE]** I purchased a Netgear N300 Wireless Mini USB Adapter to try to overcome problem number 1. It is recognized (plug'n'play) by the computer, and can connect to my internet network. However, **the connection FADES AWAY seconds after** it is successfully established. 
[/LIST]

[SIZE=4]**[The request]**[/SIZE]

- Help me solve either problem number 1 (i.e., built-in wireless device not recognized) or number 2 (i.e., netgear wifi adapter's connection fades away after seconds). 

Below is the output of the script that you produced, which I ran on the system. 

```

########## wireless info START ##########

Report from: 11 Apr 2015 17:07 BST +0100

Booted last: 11 Apr 2015 14:29 BST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-10-generic #10-Ubuntu SMP Mon Mar 23 16:25:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: video=VGA-1:1368x768e, reboot=pci,force

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 007: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 04f2:b483 Chicony Electronics Co., Ltd 
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

rtl8192cu              67761  0 
rtl_usb                18448  1 rtl8192cu
rtl8192c_common        53221  1 rtl8192cu
rtlwifi                73866  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              720010  3 rtl_usb,rtlwifi,rtl8192cu
brcmfmac              276948  0 
brcmutil               15781  1 brcmfmac
cfg80211              539517  3 brcmfmac,mac80211,rtlwifi
asus_nb_wmi            21128  0 
asus_wmi               24131  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19193  1 asus_wmi
video                  20322  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1996426 (1.9 MB)  TX bytes:299895 (299.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        NETGEAR WNA3100M
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 3.19.0-10-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          50 (connecting (configuring))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     SKYE84C0
GENERAL.CON-UUID:                       7d179b65-4810-473a-a671-b3c8acb44e6f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/98
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7d179b65-4810-473a-a671-b3c8acb44e6f | SKYE84C0
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
BTHub3-6X3M      <MAC 'BTHub3-6X3M' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  4       ____  WPA1 WPA2         no        
BTWifi-X         <MAC 'BTWifi-X' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  4       ____  WPA1 WPA2 802.1X  no        
SKY24F68         <MAC 'SKY24F68' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  4       ____  WPA2              no        
BTWifi-with-FON  <MAC 'BTWifi-with-FON' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  7       &#9602;___  --                no        
SKY41212         <MAC 'SKY41212' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  4       ____  WPA1 WPA2         no        
TALKTALK-1D7774  <MAC 'TALKTALK-1D7774' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  4       ____  WPA1 WPA2         no        
SKYE84C0         <MAC 'SKYE84C0' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2              no        

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

[[/etc/NetworkManager/system-connections/SKYE84C0]] (600 root)
[connection] id=SKYE84C0 | type=wifi
[wifi] ssid=SKYE84C0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

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

##### iwlist scan #######################

wlan0     Failed to read scan data : Resource temporarily unavailable

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.19.0-10-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     0773F170E0C9390F9FE7B5D
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.19.0-10-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     24DB546A69CAC1638071366
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.19.0-10-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     134BAE300AAF914967D6C6C
depends:        rtlwifi
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-10-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B418C1F03A19AD383E66CF3
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-10-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[brcmfmac]
filename:       /lib/modules/3.19.0-10-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4354-pcie.txt
firmware:       brcm/brcmfmac4354-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     EF8DB74BE0DC2CF3B4D9D7E
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           firmware_path:string
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)

[brcmutil]
filename:       /lib/modules/3.19.0-10-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.19.0-10-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-10-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        06:37:5D:B6:08:53:4C:1D:80:60:BF:25:63:59:2F:F3:EA:34:BE:B3
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/fcmode: Permission denied
grep: /sys/module/brcmfmac/parameters/firmware_path: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/blacklist-custom.conf]
blacklist brcmfmac  
blacklist brcmutil

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/sdhci.conf]
options sdhci debug_quirks=0x8000

##### rc.local ##########################

echo on > /sys/bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
modprobe brcmfmac 

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   43.560494] rtl8192cu: Chip version 0x11
[   43.597986] rtl8192cu: MAC address: <MAC 'wlan0' [IF]>
[   43.597994] rtl8192cu: Board Type 0
[   43.598100] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   43.598168] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   43.628486] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   43.657201] rtl8192cu: MAC auto ON okay!
[   43.671424] rtl8192cu: Tx queue select: 0x05
[   45.023031] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[   45.036184] wlan0: send auth to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[   45.038628] wlan0: authenticated
[   45.042764] wlan0: associate with <MAC 'SKYE84C0' [AN7]> (try 1/3)
[   45.060728] wlan0: RX AssocResp from <MAC 'SKYE84C0' [AN7]> (capab=0x411 status=0 aid=3)
[   45.069134] wlan0: associated
[  185.754824] wlan0: deauthenticating from <MAC 'SKYE84C0' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  193.130515] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[  193.142896] wlan0: send auth to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[  193.974462] wlan0: send auth to <MAC 'SKYE84C0' [AN7]> (try 2/3)
[  194.950139] wlan0: send auth to <MAC 'SKYE84C0' [AN7]> (try 3/3)
[  195.965023] wlan0: authentication with <MAC 'SKYE84C0' [AN7]> timed out
[  196.852162] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[  196.865151] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[  197.068284] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 2/3)
[  197.272973] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 3/3)
[  197.477342] wlan0: authentication with <MAC 'SKYE84C0' [AN7]> timed out
[  198.759297] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[  198.775449] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[  198.976386] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 2/3)
[  199.180001] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 3/3)
[  199.384728] wlan0: authentication with <MAC 'SKYE84C0' [AN7]> timed out
[  201.170827] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[  201.183734] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[  201.387534] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 2/3)
[  201.591424] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 3/3)
[  201.795446] wlan0: authentication with <MAC 'SKYE84C0' [AN7]> timed out
[  213.354536] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[  213.366798] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[  213.568479] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 2/3)
[  213.772392] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 3/3)
[  213.976255] wlan0: authentication with <MAC 'SKYE84C0' [AN7]> timed out
[  218.608834] wlan0: authenticate with <MAC 'SKYE84C0' [AN7]>
[  218.625744] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 1/3)
[  218.831020] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 2/3)
[  219.037077] wlan0: direct probe to <MAC 'SKYE84C0' [AN7]> (try 3/3)
[  219.237726] wlan0: authentication with <MAC 'SKYE84C0' [AN7]> timed out

########## wireless info END ############


```

In answering my question, please consider that I have no other way of connecting to the internet on that computer (there is no cable port). Also, my Linux knowledge level is "newbie++" so please write detailed instructions. 

Thanks,
Massi

---

### Post by praseodym on 2015-04-11
Hi,

download these files and save them in "Downloads".

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb)

[https://dl.dropboxusercontent.com/u/2902662/rtl8192cu-fixes.tar.gz](https://dl.dropboxusercontent.com/u/2902662/rtl8192cu-fixes.tar.gz)

Extract the tar.gz there. Installation:

```
cd ~/Downloads/
sudo dpkg -i *.deb
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by terzim on 2015-04-11
Thank you sir!

It magically worked and solved problem number 2: the netgear wireless adapter is now working flawlessly. Problem 1 (i.e. wireless built-in device not recognized) is still unsolved so I hope someone can give me a hand with that. 

I needed a working connection to finalise my Ubuntu installation on my new Asus X205TA. I managed to complete the installation and now I have a working system (and boots without issues!). It took more than 2 weeks...

Thanks a lot,
Massi

---

### Post by raviarya on 2015-04-13
Follow (inbuilt wifi and more):

[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)



> **terzim said:**
> Thank you sir!

It magically worked and solved problem number 2: the netgear wireless adapter is now working flawlessly. Problem 1 (i.e. wireless built-in device not recognized) is still unsolved so I hope someone can give me a hand with that. 

I needed a working connection to finalise my Ubuntu installation on my new Asus X205TA. I managed to complete the installation and now I have a working system (and boots without issues!). It took more than 2 weeks...

Thanks a lot,
Massi

---

### Post by terzim on 2015-04-17
Thank you. I am following that thread but I have not yet found a solution to my **built-in wifi issue**. Also, they changed topic in the thread so I was hoping to get a specific solution here. 

Will keep on working on it and post if I find one.

---

### Post by analogdialog on 2015-05-13
The link [http://www.jfwhome.com/2014/03/07/pe...mer-book-t100/](http://www.jfwhome.com/2014/03/07/pe...mer-book-t100/)  is dead, do you happen to have the instructions ? Are you happy with the installation so far ?

---

### Post by Pilot6 on 2015-05-13
Did you try

echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus.conf

and reboot?

---

### Post by terzim on 2015-05-14
gentlemen. Unfortunately I have not tried anymore to make the built-in wi-fi device work. I considered it to be a lost battle and NONE of the instructions around the web worked. 

I am very very happy so far with the external Netgear N300 Wireless Mini USB Adapter which I mentioned in the first post and which worked after I followed the instructions posted by praseodym. 

NOTE: you mention the link in my initial post is dead. 

I recovered a copy from web archive: [http://web.archive.org/web/20150318034615/http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://web.archive.org/web/20150318034615/http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

Please be aware that I needed to follow A LOT of deviations from that guide to make it comply with my partitioning scheme and other bits and pieces. So a lot of time will be required and a good knowledge of the machine.

---

### Post by djdispencer on 2015-06-21
Thank you so much, this resolved the lost wifi issue again (it happens every upgrade actually). I've got a USB-wifi stick (cheepest one from the media market) wich also requires the "Realtek RTL8192cu" - driver.

---

