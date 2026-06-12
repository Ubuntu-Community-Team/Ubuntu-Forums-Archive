---
title: "Lenovo Yoga 2, rtl8723be - connection lost"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by svenmeier on 2015-01-03
My Yoga 2 loses wifi connection after half an hour up to one hour stable connection with my router:

```


########## wireless info START ##########

Report from: 03 Jan 2015 15:40 CET +0100

Booted last: 03 Jan 2015 15:23 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.18.0-031800-generic #201412071935 SMP Mon Dec 8 00:36:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 5986:054a Acer, Inc 
Bus 001 Device 003: ID 04f3:0303 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723be             143324  0 
btcoexist             183652  1 rtl8723be
rtl_pci                39724  1 rtl8723be
rtlwifi               125094  3 btcoexist,rtl_pci,rtl8723be
mac80211              697159  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              520257  2 mac80211,rtlwifi
snd_soc_rt5640         93325  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          207780  1 snd_soc_rt5640
snd_pcm               106273  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
ideapad_laptop         18524  0 
sparse_keymap          13890  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

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

##### nm-tool ###########################

NetworkManager Tool

State: connecting

- Device: wlan0  [MyNetwork] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MyOtherNetwork:         Infra, <MAC 'MyOtherNetwork' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    MyNetwork:     Infra, <MAC 'MyNetwork' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA2

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

[[/etc/NetworkManager/system-connections/MyOtherNetwork]] (600 root)
[connection] id=MyOtherNetwork | type=802-11-wireless
[802-11-wireless] ssid=MyOtherNetwork | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/MyNetwork]] (600 root)
[connection] id=MyNetwork | type=802-11-wireless
[802-11-wireless] ssid=MyNetwork | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), NO-IR
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), NO-IR
	(5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

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

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.18.0-031800-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     8AC1F759DF32597E60363CC
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)

parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.18.0-031800-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     732219E08E5DA01496FCDAB
depends:        mac80211,rtlwifi
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.18.0-031800-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     DAE391EDBAC96158E9B47AD
depends:        mac80211,cfg80211
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.18.0-031800-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     7EEF5988245D414BA91F27D
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:96:8A:58:35:65:9D:60:E5:47:16:91:47:93:FC:20:5E:B5:9E:C0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.18.0-031800-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.0-031800-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:96:8A:58:35:65:9D:60:E5:47:16:91:47:93:FC:20:5E:B5:9E:C0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
swenc: Y
swlps: N

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

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N swlps=N ips=N msi=Y swenc=Y

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  702.299091] wlan0: direct probe to <MAC 'MyNetwork' [AN2]> (try 1/3)
[  702.502890] wlan0: direct probe to <MAC 'MyNetwork' [AN2]> (try 2/3)
[  702.706973] wlan0: direct probe to <MAC 'MyNetwork' [AN2]> (try 3/3)
[  702.911059] wlan0: authentication with <MAC 'MyNetwork' [AN2]> timed out
[  714.604448] wlan0: authenticate with <MAC 'MyNetwork' [AN2]>
[  714.624219] wlan0: send auth to <MAC 'MyNetwork' [AN2]> (try 1/3)
[  714.658127] wlan0: authenticated
[  714.658342] rtl8723be 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  714.658348] rtl8723be 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  714.659952] wlan0: associate with <MAC 'MyNetwork' [AN2]> (try 1/3)
[  714.763988] wlan0: associate with <MAC 'MyNetwork' [AN2]> (try 2/3)
[  714.868032] wlan0: associate with <MAC 'MyNetwork' [AN2]> (try 3/3)
[  714.972063] wlan0: association with <MAC 'MyNetwork' [AN2]> timed out
[  729.242489] wlan0: authenticate with <MAC 'MyNetwork' [AN2]>
[  729.262310] wlan0: send auth to <MAC 'MyNetwork' [AN2]> (try 1/3)
[  729.264181] wlan0: authenticated
[  729.264386] rtl8723be 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  729.264391] rtl8723be 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  729.265996] wlan0: associate with <MAC 'MyNetwork' [AN2]> (try 1/3)
[  729.268381] wlan0: RX AssocResp from <MAC 'MyNetwork' [AN2]> (capab=0x431 status=0 aid=1)
[  729.268545] wlan0: associated
[  870.304086] wlan0: deauthenticating from <MAC 'MyNetwork' [AN2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  875.941571] wlan0: authenticate with <MAC 'MyOtherNetwork' [AN1]>
[  878.360293] wlan0: direct probe to <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[  878.562243] wlan0: direct probe to <MAC 'MyOtherNetwork' [AN1]> (try 2/3)
[  878.766399] wlan0: direct probe to <MAC 'MyOtherNetwork' [AN1]> (try 3/3)
[  878.970484] wlan0: authentication with <MAC 'MyOtherNetwork' [AN1]> timed out
[  880.127255] wlan0: authenticate with <MAC 'MyOtherNetwork' [AN1]>
[  880.147125] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[  880.250938] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 2/3)
[  880.354979] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 3/3)
[  880.459023] wlan0: authentication with <MAC 'MyOtherNetwork' [AN1]> timed out
[  881.812070] wlan0: authenticate with <MAC 'MyOtherNetwork' [AN1]>
[  881.831901] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[  881.935703] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 2/3)
[  882.039737] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 3/3)
[  882.143781] wlan0: authentication with <MAC 'MyOtherNetwork' [AN1]> timed out
[  883.996929] wlan0: authenticate with <MAC 'MyOtherNetwork' [AN1]>
[  884.016800] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[  884.120624] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 2/3)
[  884.224649] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 3/3)
[  884.328693] wlan0: authentication with <MAC 'MyOtherNetwork' [AN1]> timed out
[  896.022037] wlan0: authenticate with <MAC 'MyOtherNetwork' [AN1]>
[  896.041769] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[  896.056123] wlan0: authenticated
[  896.057544] wlan0: associate with <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[  896.074451] wlan0: RX AssocResp from <MAC 'MyOtherNetwork' [AN1]> (capab=0x431 status=0 aid=3)
[  896.074626] wlan0: associated
[ 1016.620625] wlan0: disassociated from <MAC 'MyOtherNetwork' [AN1]> (Reason: 2)
[ 1017.583390] wlan0: authenticate with <MAC 'MyOtherNetwork' [AN1]>
[ 1017.603157] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 1/3)
[ 1017.707001] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 2/3)
[ 1017.811044] wlan0: send auth to <MAC 'MyOtherNetwork' [AN1]> (try 3/3)
[ 1017.915085] wlan0: authentication with <MAC 'MyOtherNetwork' [AN1]> timed out
[ 1031.051667] rtl8723be: unknown parameter 'msi' ignored
[ 1031.065953] Using firmware rtlwifi/rtl8723befw.bin
[ 1031.067086] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1031.067434] rtlwifi: wireless switch is on
[ 1031.672964] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1041.752720] wlan0: authenticate with <MAC 'MyNetwork' [AN2]>
[ 1041.752731] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[ 1041.762838] wlan0: send auth to <MAC 'MyNetwork' [AN2]> (try 1/3)
[ 1041.765271] wlan0: authenticated
[ 1046.770110] wlan0: aborting authentication with <MAC 'MyNetwork' [AN2]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

As suggested in several other threads here on the forum and on launchpad I've tried:
- updating the kernel to 3.18
- using latest driver from [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)
- several driver options (options rtl8723be fwlps=N swlps=N ips=N msi=Y swenc=Y), e.g.
-- disable power save
-- enable msi
-- enable/disable swenc
- disable IPv6
- restrict authentication to WPA2 on the router

Regretfully the problem persists. Once the connection is lost, nothing helps to regain connection to the router. Wifi works flawlessly on dual boot Windows 8.1.

Any ideas on how to go one with this problem? Perhaps someone can spot a problem in my wireless info?

Thanks
Sven

---

### Post by jeremy31 on 2015-01-03
I see this ```
[COLOR=#000000][FONT=Ubuntu Mono]capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
```
So entering this in terminal might help if you are in Germany ```
sudo iw reg set DE
``` and the msi option isn't valid for your driver[/FONT][/COLOR]

---

### Post by svenmeier on 2015-01-07
Hi,

I've tried setting the regulatory domain as you suggested, but it didn't improve the connection stability :(.

Thanks
Sven

---

