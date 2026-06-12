---
title: "Trying to get rtl8821ae working in Ubuntu 14.04"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by petriborg on 2014-12-31
Trying to get rtl8821ae working in Ubuntu 14.04. There appears to be two issues right now A) scanning is not working, it never seems to see any wireless network, B) its switching back and forth from 2.4Ghz to 5Ghz like crazy.

Has anyone gotten this working? Or is this a hopeless case?

Below is the output from the wireless_script floating around.

```


########## wireless info START ##########

Report from: 31 Dec 2014 22:05 EST -0500

Booted last: 24 Dec 2014 12:10 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-28-generic #38-Ubuntu SMP Sat Dec 13 16:13:28 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/petri/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave Device [1a3b:2161]
	Kernel driver in use: rtl8821ae

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13d3:3414 IMC Networks 
Bus 003 Device 003: ID 1267:0214 Logic3 / SpectraVideo plc 
Bus 003 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8821ae             546666  0 
mac80211              652702  1 rtl8821ae
cfg80211              494330  2 mac80211,rtl8821ae
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          196012  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.12  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29791246 (29.7 MB)  TX bytes:3605190 (3.6 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

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

[[/etc/NetworkManager/system-connections/Chainsaw-Wireless]] (600 root)
[connection] id=Chainsaw-Wireless | type=802-11-wireless
[802-11-wireless] ssid=Chainsaw-Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

wlan0     24 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         Ping Yan<ping_yan@realsil.com.cn>
srcversion:     EA439BC895EA5691716AF12
depends:        mac80211,cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:D5:A4:C5:69:75:74:85:F8:8B:F7:E3:3F:43:B2:EC:5E:5C:E1:44
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

[mac80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:D5:A4:C5:69:75:74:85:F8:8B:F7:E3:3F:43:B2:EC:5E:5C:E1:44
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:D5:A4:C5:69:75:74:85:F8:8B:F7:E3:3F:43:B2:EC:5E:5C:E1:44
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8821ae]
fwlps: N
ips: N
swenc: N
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
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[637314.400287] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637315.803781] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637318.158926] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637319.562444] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637344.361453] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637345.764963] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637387.345912] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637388.749421] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637440.326758] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637441.730249] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637503.307986] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637504.711495] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637566.281220] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637567.684712] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637629.262446] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637630.665940] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637692.235680] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637693.639187] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637755.216908] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637756.620401] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637818.190139] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637819.593631] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637881.167370] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637882.570863] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[637944.144600] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[637945.548093] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638007.125830] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638008.529326] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638070.099061] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638071.502554] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638133.080290] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638134.483786] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638196.053521] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638197.457015] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638259.034749] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638260.438258] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638322.007981] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638323.411475] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638384.985212] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638386.388706] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638447.962444] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638449.365947] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638510.943673] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638512.347165] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638573.916904] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638575.320398] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638636.898133] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638638.301642] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638699.871364] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638701.274859] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638762.852594] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638764.256087] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638825.825825] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638827.229318] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638888.807054] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638890.210548] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[638951.780285] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[638953.183779] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639014.761515] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639016.165009] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639077.734747] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639079.138243] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639140.715975] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639142.119486] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639203.689209] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639205.092702] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639266.670436] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639268.073947] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639329.643669] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639331.047162] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639392.624898] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639394.028392] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639455.598130] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639457.001632] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639518.575359] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639519.978853] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639581.552592] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639582.956099] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639644.533818] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639645.937329] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639707.507047] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639708.910544] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639770.488280] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639771.891774] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639833.461513] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639834.865021] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639896.442739] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639897.846236] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[639959.415958] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[639960.819467] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[640022.397202] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[640023.800710] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[640085.370435] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[640086.773928] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[640148.347664] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[640149.751157] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[640211.324894] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[640212.728388] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[640243.629216] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[640245.032717] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G

########## wireless info END ############

```

---

### Post by praseodym on 2015-01-01
Try the module parameters:

```
echo "options rtl8821ae swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
Reboot and change to a fixed channel

---

### Post by petriborg on 2015-01-01
OK I changed that configuration. 

```

##### module parameters #################

[rtl8821ae]
fwlps: N
ips: N
swenc: Y
swlps: N

```

I might not be using the right command, or something, but it seems the channel is set to 8, which is right, but I can't set the ap or scan or anything else.

```

# iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off

lo        no wireless extensions.

```

```

# nmcli d list iface wlan0
GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           802-11-wireless
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        Lynx Point PCI Express Root Port
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 3.16.0-28-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         54:27:1E:65:94:47
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     not connected
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS:
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

```

---

### Post by praseodym on 2015-01-01
Which channel is it? Choose one in the 2,4GHz-band

---

### Post by petriborg on 2015-01-02
Its using channel 8, Frequency:2.447 GHz

---

### Post by castor_fou on 2015-01-03
I have the same kind of issues with same kernel and same driver : [http://ubuntuforums.org/showthread.php?t=2256469](http://ubuntuforums.org/showthread.php?t=2256469)
Don't know how to fix it.

---

### Post by castor_fou on 2015-01-03
Switching to rtlwifi seems to fix it for me.

---

