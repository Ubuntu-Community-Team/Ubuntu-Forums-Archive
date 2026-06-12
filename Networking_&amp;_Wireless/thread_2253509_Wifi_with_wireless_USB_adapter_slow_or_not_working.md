---
title: "Wifi with wireless USB adapter slow or not working at all"
date: 2014-11-20
forum: Networking &amp; Wireless
---

### Post by ConcernedPie on 2014-11-20
I recently bought a wifi adapter (Edimax EW-7612UAn V2) for my desktop because ethernet is not an option.  
I plugged in the adapter and I was able to connect to wifi. But it was really slow (I tried pointing it in several directions) or not working at all. But it is constantly connected to wifi. So why is it nog working properly? Am I doing something wrong? 

The adapter did come with a CD-ROM with the drivers I guess. Do I need to install this? And if so how do I do this? When I put the CD-ROM in the computer I only see the ZIP files, I can't find one I have to open. 

I hope I gave enough information, I'm new to ubuntu.;)

---

### Post by jeremy31 on 2014-11-20
> **ConcernedPie said:**
> I recently bought a wifi adapter (Edimax EW-7612UAn V2) for my desktop because ethernet is not an option.  
I plugged in the adapter and I was able to connect to wifi. But it was really slow (I tried pointing it in several directions) or not working at all. But it is constantly connected to wifi. So why is it nog working properly? Am I doing something wrong? 

The adapter did come with a CD-ROM with the drivers I guess. Do I need to install this? And if so how do I do this? When I put the CD-ROM in the computer I only see the ZIP files, I can't find one I have to open. 

I hope I gave enough information, I'm new to ubuntu.;)

The easiest way to get the needed info posted is to read the sticky post "before posting in networking and wireless" to find out how to run the wireless script and post the results.  Hopefully we can make your Ubuntu experience better

---

### Post by ConcernedPie on 2014-11-20
oops sorry,  this is what I got:
```



########## wireless info START ##########

Report from: 20 Nov 2014 16:27 CET +0100

Booted last: 20 Nov 2014 13:44 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7721]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 13fe:3600 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 1058:10a8 Western Digital Technologies, Inc. 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 7392:7822 Edimax Technology Co., Ltd 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

8: phy8: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

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
          inet addr:192.168.1.83  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76da:38ff:fe09:fc2a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:635973 (635.9 KB)  TX bytes:232263 (232.2 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HG655D-13E851"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'HG655D-13E851' [AN3]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HG655D-13E851] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Ziggo7DC0A:      Infra, <MAC 'Ziggo7DC0A' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Ziggo:           Infra, <MAC 'Ziggo' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    *HG655D-13E851:  Infra, <MAC 'HG655D-13E851' [AN3]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 76 WPA2
    VGV75195307E8:   Infra, <MAC 'VGV75195307E8' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Ziggo378D4:      Infra, <MAC 'Ziggo378D4' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2

  IPv4 Settings:
    Address:         192.168.1.83
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

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

[[/etc/NetworkManager/system-connections/HG655D-13E851]] (600 root)
[connection] id=HG655D-13E851 | type=802-11-wireless
[802-11-wireless] ssid=HG655D-13E851 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Amsterdam (based on set time zone)

country CA:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)

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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     7B1675B5BB89B5DD8E7EBAC
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 8247.933999] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8290.435503] wlan0: deauthenticating from <MAC 'HG655D-13E851' [AN3]> by local choice (reason=3)
[ 8315.062694] rtl8192cu: Chip version 0x11
[ 8315.532680] rtl8192cu: MAC address: <MAC 'wlan0' [IF]>
[ 8315.532687] rtl8192cu: Board Type 0
[ 8315.533515] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 8315.533569] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 8315.533894] ieee80211 phy8: Selected rate control algorithm 'rtl_rc'
[ 8315.535553] rtlwifi: wireless switch is on
[ 8315.555919] rtl8192cu: MAC auto ON okay!
[ 8315.759955] rtl8192cu: Tx queue select: 0x05
[ 8316.551997] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 8318.290236] wlan0: authenticate with <MAC 'HG655D-13E851' [AN3]>
[ 8318.347625] wlan0: send auth to <MAC 'HG655D-13E851' [AN3]> (try 1/3)
[ 8318.351939] wlan0: authenticated
[ 8318.353696] wlan0: associate with <MAC 'HG655D-13E851' [AN3]> (try 1/3)
[ 8318.386094] wlan0: RX AssocResp from <MAC 'HG655D-13E851' [AN3]> (capab=0x431 status=0 aid=2)
[ 8318.386159] wlan0: associated
[ 8318.386170] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8318.709427] wlan0: deauthenticating from <MAC 'HG655D-13E851' [AN3]> by local choice (reason=2)
[ 8318.756190] wlan0: authenticate with <MAC 'HG655D-13E851' [AN3]>
[ 8318.784034] wlan0: send auth to <MAC 'HG655D-13E851' [AN3]> (try 1/3)
[ 8318.787024] wlan0: authenticated
[ 8318.789688] wlan0: associate with <MAC 'HG655D-13E851' [AN3]> (try 1/3)
[ 8318.809527] wlan0: RX AssocResp from <MAC 'HG655D-13E851' [AN3]> (capab=0x431 status=0 aid=2)
[ 8318.809581] wlan0: associated
[ 9198.640191] wlan0: AP <MAC 'HG655D-13E851' [AN3]> changed bandwidth, new config is 2422 MHz, width 2 (2432/0 MHz)
[ 9782.678150] wlan0: AP <MAC 'HG655D-13E851' [AN3]> changed bandwidth, new config is 2422 MHz, width 1 (2422/0 MHz)

########## wireless info END ############


```

---

