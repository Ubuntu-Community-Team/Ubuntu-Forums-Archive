---
title: "new incident, same issue: 14.04 inconsistent wifi"
date: 2015-05-18
forum: Networking &amp; Wireless
---

### Post by Malik_Rumi on 2015-05-18
Shortly after reporting my problem solved ([http://ubuntuforums.org/showthread.php?t=2272149](http://ubuntuforums.org/showthread.php?t=2272149)) they came back. After working fine Friday night, Saturday morning my wifi was reporting connected but I was not able to access any web pages. I ran the wireless script (dated 051615). Since I could see that Power Management was on again, and I had been told to turn it off, I ran sudo /sbin/iwconfig wlan0 power off, but it made no difference. I don't understand why Power Management keeps coming back on. Am I really turning it off or is it just a toggle until restart?

Then, Sunday night, after having been powered off for several hours, wifi was suddenly back as if nothing had ever been wrong. But now, Monday morning, not only is it not working, the icon says I am disconnected and my default home ssid is not even listed as one of those available. I am posting this from the Windows side of my dual boot machine. The wifi on Windows has never given me a hint of problems.

So I ran the wireless script again, (dated 051815) in hopes the comparison would be valuable. 

Would these problems be solved with a USB wifi adapter? Does it matter which one I buy?

```


########## wireless info START ##########


Report from: 16 May 2015 17:48 CDT -0500


Booted last: 16 May 2015 17:42 CDT -0500


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 8087:07dc Intel Corp. 
Bus 002 Device 005: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0457:1039 Silicon Integrated Systems Corp. 
Bus 002 Device 002: ID 0c45:6621 Microdia 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                217725  0 
mac80211              652718  1 iwlmvm
dell_wmi_aio           12652  0 
sparse_keymap          13948  1 dell_wmi_aio
iwlwifi               179412  1 iwlmvm
cfg80211              494362  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
wmi                    19193  1 dell_wmi_aio
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  6 snd_soc_rt5640,snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:2:4280:201:8cb9:90a3:f0e7:ba34/64 Scope:Global
          inet6 addr: fe80::ea2a:eaff:fe33:232c/64 Scope:Link
          inet6 addr: 2601:2:4280:201:ea2a:eaff:fe33:232c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:806 (806.0 B)  TX bytes:18736 (18.7 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"HOME-8212"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'HOME-8212' [AN14]>   
          Bit Rate=5.5 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search hsd1.mn.comcast.net


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [HOME-8212] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           5 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Toxsick Waste:   Infra, <MAC 'Toxsick Waste' [AN1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    RTET:            Infra, <MAC 'RTET' [AN2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 59 WPA2
    Chaska Herald:   Infra, <MAC 'Chaska Herald' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    HOME-6D32:       Infra, <MAC 'HOME-6D32' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    HOME-D712:       Infra, <MAC 'HOME-D712' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    LabStation Guest:Infra, <MAC 'LabStation Guest:Infra, <MAC address>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    IDEXXw1:         Infra, <MAC 'IDEXXw1' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Tonia's:         Infra, <MAC 'Tonia's' [AN8]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    linksys:         Infra, <MAC 'linksys' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 85
    chaskanet:       Infra, <MAC 'chaskanet' [AN11]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 74
    chaskanet:       Infra, <MAC 'chaskanet' [AN12]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60
    hpsetup:         Ad-Hoc, <MAC 'hpsetup' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    *HOME-8212:      Infra, <MAC 'HOME-8212' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.76.76
    DNS:             75.75.75.75


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


[[/etc/NetworkManager/system-connections/Angels207]] (600 root)
[connection] id=Angels207 | type=802-11-wireless
[802-11-wireless] ssid=Angels207 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=HOME-8212b | type=802-11-wireless
[802-11-wireless] ssid=HOME-8212
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CarverPublicWIFI]] (600 root)
[connection] id=CarverPublicWIFI | type=802-11-wireless
[802-11-wireless] ssid=CarverPublicWIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WINKHUB-1ABB8F-1377]] (600 root)
[connection] id=WINKHUB-1ABB8F-1377 | type=802-11-wireless
[802-11-wireless] ssid=WINKHUB-1ABB8F-1377 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/HCL_Public]] (600 root)
[connection] id=HCL_Public | type=802-11-wireless
[802-11-wireless] ssid=HCL_Public | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/HOME-8212]] (600 root)
[connection] id=HOME-8212 | type=802-11-wireless
[802-11-wireless] ssid=HOME-8212 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


lo        no frequency information.


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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


wlan0     Interface doesn't support scanning : Input/output error


lo        Interface doesn't support scanning.


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.16.0-37-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     C3CE81DD94553577D83E97E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.16.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     05170C37AC7B7A82211E896
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     93D664267873827B22C4309
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.16.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


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
options iwlwifi 11n-disable=1
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   10.166962] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   18.154241] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   18.170219] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.331280] wlan0: authenticate with <MAC 'HOME-8212' [AN14]>
[   22.334380] wlan0: send auth to <MAC 'HOME-8212' [AN14]> (try 1/3)
[   22.335761] wlan0: authenticated
[   22.337939] wlan0: associate with <MAC 'HOME-8212' [AN14]> (try 1/3)
[   22.346425] wlan0: RX AssocResp from <MAC 'HOME-8212' [AN14]> (capab=0x411 status=0 aid=3)
[   22.348239] wlan0: associated
[   22.348264] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.041906] iwlwifi 0000:02:00.0: Error sending MCAST_FILTER_CMD: enqueue_hcmd failed: -5
[   25.041909] iwlwifi 0000:02:00.0: mcast filter cmd error. ret=-5
[   25.059315] iwlwifi 0000:02:00.0: Error sending MCAST_FILTER_CMD: enqueue_hcmd failed: -5
[   25.059328] iwlwifi 0000:02:00.0: mcast filter cmd error. ret=-5
[   46.605605] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[   46.605612] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[   90.096200] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[   90.096207] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  153.151219] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  153.151231] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  236.215778] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  236.215782] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  339.300990] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  339.301002] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  413.623877] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  413.623881] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5


########## wireless info END ############



```

```


########## wireless info START ##########


Report from: 18 May 2015 05:05 CDT -0500


Booted last: 18 May 2015 04:37 CDT -0500


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev ff)
	Kernel driver in use: iwlwifi


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 8087:07dc Intel Corp. 
Bus 002 Device 005: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0457:1039 Silicon Integrated Systems Corp. 
Bus 002 Device 002: ID 0c45:6621 Microdia 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwlmvm                217725  0 
mac80211              652718  1 iwlmvm
dell_wmi_aio           12652  0 
sparse_keymap          13948  1 dell_wmi_aio
iwlwifi               179412  1 iwlmvm
cfg80211              494362  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  6 snd_soc_rt5640,snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 dell_wmi_aio


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


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


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


[[/etc/NetworkManager/system-connections/Angels207]] (600 root)
[connection] id=Angels207 | type=802-11-wireless
[802-11-wireless] ssid=Angels207 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=HOME-8212b | type=802-11-wireless
[802-11-wireless] ssid=HOME-8212
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CarverPublicWIFI]] (600 root)
[connection] id=CarverPublicWIFI | type=802-11-wireless
[802-11-wireless] ssid=CarverPublicWIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WINKHUB-1ABB8F-1377]] (600 root)
[connection] id=WINKHUB-1ABB8F-1377 | type=802-11-wireless
[802-11-wireless] ssid=WINKHUB-1ABB8F-1377 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/HCL_Public]] (600 root)
[connection] id=HCL_Public | type=802-11-wireless
[802-11-wireless] ssid=HCL_Public | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/HOME-8212]] (600 root)
[connection] id=HOME-8212 | type=802-11-wireless
[802-11-wireless] ssid=HOME-8212 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


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


##### iwlist scan #######################


wlan0     Interface doesn't support scanning : Input/output error


lo        Interface doesn't support scanning.


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.16.0-37-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     C3CE81DD94553577D83E97E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.16.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     05170C37AC7B7A82211E896
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     93D664267873827B22C4309
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.16.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        74:DE:34:06:B3:CB:2F:7F:39:77:33:D7:59:63:19:56:80:CD:9E:D5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


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
options iwlwifi 11n-disable=1
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   20.048157] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   20.064862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.083574] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[   44.083579] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[   77.082360] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[   77.082373] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  120.120844] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  120.120854] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  173.162317] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  173.162328] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  236.215974] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  236.215986] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  299.264515] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  299.264527] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  362.318445] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  362.318457] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  425.365534] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  425.365545] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  488.419806] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  488.419817] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  551.467267] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  551.467277] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  614.521788] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  614.521800] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  677.569211] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  677.569221] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  740.623726] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  740.623738] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  803.671106] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  803.671117] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  866.725603] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  866.725612] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  929.772950] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  929.772961] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[  992.827351] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[  992.827362] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1055.875534] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1055.875544] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1118.929073] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1118.929084] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1181.976489] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1181.976499] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1245.031158] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1245.031168] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1308.078601] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1308.078610] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1371.132989] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1371.132998] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1434.180444] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1434.180454] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1497.232119] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1497.232130] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1560.282548] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1560.282559] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1623.336886] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1623.336898] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1686.384275] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1686.384286] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1728.887562] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1728.887566] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5


########## wireless info END ############

Thanks.

```

---

### Post by chili555 on 2015-05-18
> Would these problems be solved with a USB wifi adapter? Does it matter which one I buy?Of course they'd be solved. However, that's a bit like fixing a flat tire on your car by buying a new car! Before you give up on your Intel, we ought to try everything in our power to fix it.

This is undoubtedly the problem:> [ 1560.282548] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1560.282559] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5
[ 1623.336886] iwlwifi 0000:02:00.0: Error sending SCAN_REQUEST_CMD: enqueue_hcmd failed: -5
[ 1623.336898] iwlwifi 0000:02:00.0: Scan failed! status 0x1 ret -5A Google search strongly suggests it's a firmware bug. The version of the driver you are using calls for:```
firmware:       iwlwifi-7260-[COLOR="#FF0000"]9[/COLOR].ucode
```I have seen a few cases where, even though the driver's modinfo calls for -9 firmware, it will, in a pinch, load -8. Therefore, it is helpful to see what firmware is actually loaded on boot. Please reboot so we have a clean slate and then run and post:```
dmesg | grep firmware
```I suspect we will see that 25.228.[COLOR="#FF0000"]9[/COLOR].0 is loading. If so, then the called-for firmware is present and called. 

Of course, if it calls for -10 and can't find it and, as a fallback, uses -9, we will download and install the -10 firmware.

We might also check to see if the firmware file is corrupted:```
ls -al /lib/firmware | grep 7260
```For the -9 version, I get:```
-rw-r--r--  1 root root [COLOR="#FF0000"] 680508[/COLOR] Dec  1 15:45 iwlwifi-7260-9.ucode
```You might try the live DVD for Ubuntu 15.04 and see if the performance improves. If so, I'd simply install it and be done.

We can backport the later driver from 15.04 with some difficulty, but  let's see what you find before we get out the bigger hammer.

---

### Post by Malik_Rumi on 2015-05-18
I'm no expert, but I don't think I'm supposed to have 3 versions of the firmware, am I?

```

malikarumi@Tetouan2:~$ dmesg | grep firmware[   10.081364] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm

```

```
 
malikarumi@Tetouan2:~$ ls -al /lib/firmware | grep 7260
-rw-r--r--  1 root root  683236 Nov 24 09:42 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  679780 Dec  1 09:16 iwlwifi-7260-8.ucode
-rw-r--r--  1 root root  680508 Dec  1 14:45 iwlwifi-7260-9.ucode

```

Ok, work your magic. Thanks.

---

### Post by chili555 on 2015-05-18
> I'm no expert, but I don't think I'm supposed to have 3 versions of the firmware, am I?Sure. Why not? If you upgrade the driver to a later version that calls for -10, it's already there. You needn't also separately download and install the later firmware.

Did you try a live session for 15.04? Was the wireless working as expected?

---

### Post by Malik_Rumi on 2015-05-19
This is me, reporting to you from my 15.04 live usb. I waited to try this option until I heard back from you. It's only been a couple of minutes, but it did connect quickly and easily to my wifi. I'll play with it a while and see how it goes. HOWEVER...

It seems to have erased my original bootloader. When I rebooted with 14.04, I got a grub2 screen from which I could chose either Windows or Ubuntu. That is gone now, and it always goes to Windows. I would not have thought making a live usb would impact the boot on the HD, but apparently it does if I am reading the community wiki correctly. There is also supposed to be a way to preserve the old bootloader, but none of this info was on the 'how to make and use a live cd' page. 

So I set windows to boot from the usb. Note, as an aside, fwiw, that there were THREE ubuntu options alongside the usb itself, but there was nothing to differentiate b/w the three ubuntus, and clicking on one just got me back to windows anyway. So I tried again, went with the usb, and here I am.

All is not lost as far as the original bootloader being missing is concerned. The file system shows me all my old ubuntu files on the HD, so I can keep working that way - as long as the wifi on 15.04 holds out, at least! I don't know what I would do if I wanted to go back to 14.04, but I'd say that's unlikely. I just hope that when I do install 15.04 I don't have new issues and can keep / get back the dual boot I had before.

---

### Post by chili555 on 2015-05-19
I am very glad the wireless is working as expected and very sorry that the bootloader is not working as expected. That is not a completely unknown occurrence, for whatever reason, so help is available. It is, however, beyond my experience. I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by Malik_Rumi on 2015-05-23
I'm back and I don't want to be.  As suggested, I installed 15.04, however, it is still not a consistently reliable wifi experience.  
 
 
 I put the computer in suspend and when I came back to it this morning there was not only no wifi, my home default SSID wasn't even on the list of available networks. I ran the wireless script again, it is enclosed.  

```


########## wireless info START ##########

Report from: 23 May 2015 09:43 CDT -0500

Booted last: 23 May 2015 04:35 CDT -0500

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:31:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 8087:07dc Intel Corp. 
Bus 001 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0457:1039 Silicon Integrated Systems Corp. 
Bus 001 Device 003: ID 0c45:6621 Microdia 
Bus 001 Device 002: ID 05dc:c75c Lexar Media, Inc. 
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

iwlmvm                278528  0 
dell_wmi_aio           16384  0 
mac80211              724992  1 iwlmvm
sparse_keymap          16384  1 dell_wmi_aio
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
iwlwifi               196608  1 iwlmvm
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  6 snd_soc_rt5640,snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea2a:eaff:fe33:232c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42595 (42.5 KB)  TX bytes:49085 (49.0 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"xfinitywifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'xfinitywifi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-18-generic
GENERAL.FIRMWARE-VERSION:               25.15.12.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     xfinitywifi
GENERAL.CON-UUID:                       7db8da5e-bf72-4183-bef2-d6511d14e540
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7db8da5e-bf72-4183-bef2-d6511d14e540 | xfinitywifi
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   b7ecafee-89f4-4c10-8a3b-ddfbf1db1220 | HOME-8212
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.10/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1432392427
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 300
DHCP4.OPTION[16]:                       ip_address = 192.168.1.10
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 150
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 263
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::ea2a:eaff:fe33:232c/64, gw = ::

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Toxsick Waste     <MAC 'Toxsick Waste' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
--                <MAC '--' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2       no        
RTET              <MAC 'RTET' [AC5]>  Infra  9     2452 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
Tonia's           <MAC 'Tonia's' [AC3]>  Infra  7     2442 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        
chugchug          <MAC 'chugchug' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
LabStation Guest  <MAC 'LabStation Guest' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
Angels207         <MAC 'Angels207' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
SepiaPanda        <MAC 'SepiaPanda' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
chaskanet         <MAC 'chaskanet' [AC4]>  Infra  7     2442 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --         no        
xfinitywifi       <MAC 'xfinitywifi' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  --         no        
chaskanet         <MAC 'chaskanet' [AN11]>  Infra  7     2442 MHz  54 Mbit/s  40      &#9602;&#9604;__  --         no        
xfinitywifi       <MAC 'xfinitywifi' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  --         no        
xfinitywifi       <MAC 'xfinitywifi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         yes     * 
HOME-8212         <MAC 'HOME-8212' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
--                <MAC '--' [AN15]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
HOME-6D32         <MAC 'HOME-6D32' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
--                <MAC '--' [AN17]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
HOME-D712         <MAC 'HOME-D712' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
Chaska Herald     <MAC 'Chaska Herald' [AN19]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1       no        
linksys           <MAC 'linksys' [AN20]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
IDEXXw1           <MAC 'IDEXXw1' [AN21]>  Infra  11    2462 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        
xfinitywifi       <MAC 'xfinitywifi' [AN22]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --         no        
chaskanet         <MAC 'chaskanet' [AN23]>  Infra  10    2457 MHz  54 Mbit/s  34      &#9602;&#9604;__  --         no        

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

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi
[wifi] ssid=xfinitywifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HOME-8212]] (600 root)
[connection] id=HOME-8212 | type=wifi
[wifi] ssid=HOME-8212 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (3, 27), (N/A)
    (5170 - 5250 @ 40), (3, 17), (N/A)
    (5250 - 5330 @ 40), (3, 20), (0 ms), DFS
    (5490 - 5600 @ 40), (3, 20), (0 ms), DFS
    (5650 - 5710 @ 40), (3, 20), (0 ms), DFS
    (5735 - 5835 @ 40), (3, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      5   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'xfinitywifi' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029b15fc364
                    Extra: Last beacon: 8ms ago
          Cell 02 - Address: <MAC 'HOME-8212' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"HOME-8212"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029d058fe4b
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Tonia's' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Tonia's"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000976639101
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'chaskanet' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"chaskanet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005d8dbcc0a1
                    Extra: Last beacon: 56ms ago
          Cell 05 - Address: <MAC 'RTET' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"RTET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000274cadea
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'HOME-D712' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"HOME-D712"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019cd05d8fb6
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Toxsick Waste' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Toxsick Waste"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c9076ab332
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HOME-6D32' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"HOME-6D32"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023fce6255d8
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'xfinitywifi' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c9076ad06d
                    Extra: Last beacon: 56ms ago
          Cell 10 - Address: <MAC 'xfinitywifi' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023fce628037
                    Extra: Last beacon: 56ms ago

00000000

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     64F898655E66F8611F09B6B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     45659D6D4B015B51A3FF148
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     97E94F4448EBBA00BC45455
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    8.163581] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    8.238683] iwlwifi 0000:02:00.0: loaded firmware version 25.15.12.0 op_mode iwlmvm
[    8.502572] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.502729] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    8.753193] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.975272] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   21.453806] wlan0: authenticate with <MAC 'xfinitywifi' [AC1]>
[   21.458790] wlan0: send auth to <MAC 'xfinitywifi' [AC1]> (try 1/3)
[   21.466107] wlan0: authenticated
[   21.469797] wlan0: associate with <MAC 'xfinitywifi' [AC1]> (try 1/3)
[   21.489786] wlan0: RX AssocResp from <MAC 'xfinitywifi' [AC1]> (capab=0x401 status=0 aid=2)
[   21.491407] wlan0: associated

########## wireless info END ############


```


  	 	 	 	   
About an hour later I tried again, and this time the wifi came up correctly and immediately. I ran another wireless script just for comparison.  
  

```


########## wireless info START ##########

Report from: 23 May 2015 10:51 CDT -0500

Booted last: 23 May 2015 04:35 CDT -0500

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:31:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 8087:07dc Intel Corp. 
Bus 001 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 0457:1039 Silicon Integrated Systems Corp. 
Bus 001 Device 003: ID 0c45:6621 Microdia 
Bus 001 Device 002: ID 05dc:c75c Lexar Media, Inc. 
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

iwlmvm                278528  0 
dell_wmi_aio           16384  0 
mac80211              724992  1 iwlmvm
sparse_keymap          16384  1 dell_wmi_aio
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
iwlwifi               196608  1 iwlmvm
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  6 snd_soc_rt5640,snd_soc_core,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  1 dell_wmi_aio

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea2a:eaff:fe33:232c/64 Scope:Link
          inet6 addr: 2601:2:4280:201:ea2a:eaff:fe33:232c/64 Scope:Global
          inet6 addr: 2601:2:4280:201:bc96:af91:4d30:74c0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4636400 (4.6 MB)  TX bytes:827738 (827.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HOME-8212"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'HOME-8212' [AC1]>   
          Bit Rate=243 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    1024   0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.mn.comcast.net

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-18-generic
GENERAL.FIRMWARE-VERSION:               25.15.12.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     HOME-8212
GENERAL.CON-UUID:                       b7ecafee-89f4-4c10-8a3b-ddfbf1db1220
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     243 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7db8da5e-bf72-4183-bef2-d6511d14e540 | xfinitywifi
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   b7ecafee-89f4-4c10-8a3b-ddfbf1db1220 | HOME-8212
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 10.0.0.11/24, gw = 10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.76.76
IP4.DNS[2]:                             75.75.75.75
IP4.DOMAIN[1]:                          hsd1.mn.comcast.net.
DHCP4.OPTION[1]:                        network_number = 10.0.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1433000897
DHCP4.OPTION[9]:                        domain_name = hsd1.mn.comcast.net.
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 10.0.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 604800
DHCP4.OPTION[16]:                       ip_address = 10.0.0.11
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 75.75.76.76 75.75.75.75
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         ip = 2601:2:4280:201:bc96:af91:4d30:74c0/64, gw = fe80::2ac:e0ff:fee2:8211
IP6.ADDRESS[2]:                         ip = 2601:2:4280:201:ea2a:eaff:fe33:232c/64, gw = fe80::2ac:e0ff:fee2:8211
IP6.ADDRESS[3]:                         ip = fe80::ea2a:eaff:fe33:232c/64, gw = fe80::2ac:e0ff:fee2:8211
IP6.ROUTE[1]:                           dst = 2601:2:4280:201::/64, nh = ::, mt = 10
IP6.DNS[1]:                             2001:558:feed::2
IP6.DNS[2]:                             2001:558:feed::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:9f:f5:63:bd:27:5b:e4:5d:54:39:40:38:ff:56:cc:4e
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::2 2001:558:feed::1
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1
DHCP6.OPTION[5]:                        dhcp6_unknown_16 = 0:0:11:8b:0:a:65:52:6f:75:74:65:72:31:2e:30
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:0:ac:e0:e2:82:11

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Toxsick Waste  <MAC 'Toxsick Waste' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
RTET           <MAC 'RTET' [AN2]>  Infra  9     2452 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
xfinitywifi    <MAC 'xfinitywifi' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  --         no        
--             <MAC '--' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
HOME-6D32      <MAC 'HOME-6D32' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
--             <MAC '--' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
Chaska Herald  <MAC 'Chaska Herald' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1       no        
xfinitywifi    <MAC 'xfinitywifi' [AN9]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --         no        
--             <MAC '--' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no        
linksys        <MAC 'linksys' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
xfinitywifi    <MAC 'xfinitywifi' [AN12]>  Infra  11    2462 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --         no        
Tonia's        <MAC 'Tonia's' [AC4]>  Infra  7     2442 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
chaskanet      <MAC 'chaskanet' [AN14]>  Infra  7     2442 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --         no        
Angels207      <MAC 'Angels207' [AN15]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
HOME-8212      <MAC 'HOME-8212' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi
[wifi] ssid=xfinitywifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HOME-8212]] (600 root)
[connection] id=HOME-8212 | type=wifi
[wifi] ssid=HOME-8212 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (3, 27), (N/A)
    (5170 - 5250 @ 40), (3, 17), (N/A)
    (5250 - 5330 @ 40), (3, 20), (0 ms), DFS
    (5490 - 5600 @ 40), (3, 20), (0 ms), DFS
    (5650 - 5710 @ 40), (3, 20), (0 ms), DFS
    (5735 - 5835 @ 40), (3, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HOME-8212' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"HOME-8212"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ab6192d14
                    Extra: Last beacon: 208564ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Chaska Herald' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Chaska Herald"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002a99624df47
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'linksys' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c98ce68a8
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Tonia's' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Tonia's"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a6860299d
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'chaskanet' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"chaskanet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a98b43f987
                    Extra: Last beacon: 3444ms ago
          Cell 06 - Address: <MAC 'HOME-D712' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"HOME-D712"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019dc25a3b32
                    Extra: Last beacon: 52ms ago

F000001000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Toxsick Waste' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Toxsick Waste"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c9f967f0a4
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     64F898655E66F8611F09B6B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     45659D6D4B015B51A3FF148
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     97E94F4448EBBA00BC45455
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   17.975272] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   21.453806] wlan0: authenticate with <MAC 'xfinitywifi' [AN4]>
[   21.458790] wlan0: send auth to <MAC 'xfinitywifi' [AN4]> (try 1/3)
[   21.466107] wlan0: authenticated
[   21.469797] wlan0: associate with <MAC 'xfinitywifi' [AN4]> (try 1/3)
[   21.489786] wlan0: RX AssocResp from <MAC 'xfinitywifi' [AN4]> (capab=0x401 status=0 aid=2)
[   21.491407] wlan0: associated
[  654.240962] wlan0: AP <MAC 'xfinitywifi' [AN4]> changed bandwidth, new config is 2437 MHz, width 2 (2447/0 MHz)
[ 4392.570087] wlan0: deauthenticating from <MAC 'xfinitywifi' [AN4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4395.979935] wlan0: authenticate with <MAC 'HOME-8212' [AC1]>
[ 4395.984503] wlan0: direct probe to <MAC 'HOME-8212' [AC1]> (try 1/3)
[ 4396.187965] wlan0: send auth to <MAC 'HOME-8212' [AC1]> (try 2/3)
[ 4396.189153] wlan0: authenticated
[ 4396.190755] wlan0: associate with <MAC 'HOME-8212' [AC1]> (try 1/3)
[ 4396.207445] wlan0: RX AssocResp from <MAC 'HOME-8212' [AC1]> (capab=0x411 status=0 aid=2)
[ 4396.210097] wlan0: associated

########## wireless info END ############


```  

   I appreciate your thoughts and feedback, but I am starting to think this is a lost cause. Thanks.

---

### Post by jeremy31 on 2015-05-24
It looks like it is having issues with xfinitywifi and it works with HOME-8212 even though the HOME-8212 access point is using TKIP.  If you wish to use xfinitywifi, I would edit the connection in Netwrok Manager and select a BSSID and see if it works better and possibly set IPv6 to ignore

---

