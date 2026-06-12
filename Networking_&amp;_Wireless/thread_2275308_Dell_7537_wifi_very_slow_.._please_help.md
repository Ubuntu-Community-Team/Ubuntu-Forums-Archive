---
title: "Dell 7537 wifi very slow .. please help"
date: 2015-04-25
forum: Networking &amp; Wireless
---

### Post by dragan4 on 2015-04-25
greeting friends


Plaese you to help the new Ubuntu user ...


A month ago I bought a Dell 7537 and decided to finally get to the 14.04 Ununtu system'm


But there begin my problems namely my dell 7537 laptop runs very slow on wifi internet in the house that I have an older computer works without problems on the same wifi and the speed is 15MB while the new does not come 0.5mb and keeps breaking conection.


I tried to find some solution here in the forum but not succes.  I try have worked as it says here, but without success [http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/) ....


Yesterday I bought a Tenda USB adapter W311M because I read somewhere that this laptop there is a problem with the driver for the wifi card but with this new USB adapter is the same that is even worse is falling out from the net :(


Does anybody can send me some advice what could I do.




Thank you very much

---

### Post by wildmanne39 on 2015-04-25
Unplug your usb adaptor and reboot computer then run the wireless script in my signature and copy and paste output here by clicking new reply then above the window you click on # and put the information in between the 2 code boxes ```

```
Thanks

---

### Post by dragan4 on 2015-04-25
Thanks ... here is my script 


```


########## wireless info START ##########


Report from: 25 Apr 2015 16:14 CEST +0200


Booted last: 25 Apr 2015 10:24 CEST +0200


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4460]
	Kernel driver in use: iwlwifi


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: Dell Device [1028:05f9]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 04f3:0206 Elan Microelectronics Corp. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 0c45:6705 Microdia 
Bus 002 Device 003: ID 04f2:0408 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwlmvm                189813  0 
mac80211              630669  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 dell_wmi


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
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae7b:a1ff:fe0c:17a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:394705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419358055 (419.3 MB)  TX bytes:54972804 (54.9 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"Maric"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'Maric' [AN1]>   
          Bit Rate=12 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:279   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


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


- Device: wlan0  [Maric 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           12 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Maric:          Infra, <MAC 'Maric' [AN1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/maric adsl]] (600 root)
[connection] id=maric adsl | type=802-11-wireless
[802-11-wireless] ssid=maric adsl | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Maric 2]] (600 root)
[connection] id=Maric 2 | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Maric 1]] (600 root)
[connection] id=Maric 1 | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/TP-LINK_AF81B3]] (600 root)
[connection] id=TP-LINK_AF81B3 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_AF81B3 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Maric]] (600 root)
[connection] id=Maric | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/HG530]] (600 root)
[connection] id=HG530 | type=802-11-wireless
[802-11-wireless] ssid=HG530 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Nikolic]] (600 root)
[connection] id=Nikolic | type=802-11-wireless
[802-11-wireless] ssid=Nikolic | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Belgrade (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     412FF07DA992AAD938A30BE
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
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
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
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
options iwlwifi 11n_disable=1 wd_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[11940.346414] wlan0: authenticate with <MAC 'Maric' [AN1]>
[11940.348050] wlan0: send auth to <MAC 'Maric' [AN1]> (try 1/3)
[11940.349186] wlan0: authenticated
[11940.349300] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[11940.350072] wlan0: associate with <MAC 'Maric' [AN1]> (try 1/3)
[11940.351811] wlan0: RX AssocResp from <MAC 'Maric' [AN1]> (capab=0x411 status=0 aid=2)
[11940.352535] wlan0: associated
[11940.352566] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14506.481152] wlan0: deauthenticated from <MAC 'Maric' [AN1]> (Reason: 6)
[14506.554152] wlan0: authenticate with <MAC 'Maric' [AN1]>
[14506.555764] wlan0: send auth to <MAC 'Maric' [AN1]> (try 1/3)
[14506.559267] wlan0: authenticated
[14506.559525] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[14506.560073] wlan0: associate with <MAC 'Maric' [AN1]> (try 1/3)
[14506.564504] wlan0: RX AssocResp from <MAC 'Maric' [AN1]> (capab=0x411 status=0 aid=2)
[14506.565777] wlan0: associated
[14514.317885] wlan0: deauthenticated from <MAC 'Maric' [AN1]> (Reason: 6)
[14530.025749] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14554.223390] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[14554.235606] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14561.503755] wlan0: authenticate with <MAC 'Maric' [AN1]>
[14561.505534] wlan0: send auth to <MAC 'Maric' [AN1]> (try 1/3)
[14561.507216] wlan0: authenticated
[14561.507452] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[14561.508235] wlan0: associate with <MAC 'Maric' [AN1]> (try 1/3)
[14561.515147] wlan0: RX AssocResp from <MAC 'Maric' [AN1]> (capab=0x411 status=0 aid=2)
[14561.516044] wlan0: associated
[14561.516088] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14562.254714] wlan0: deauthenticating from <MAC 'Maric' [AN1]> by local choice (reason=2)
[14562.257634] wlan0: authenticate with <MAC 'Maric' [AN1]>
[14562.259262] wlan0: send auth to <MAC 'Maric' [AN1]> (try 1/3)
[14562.263925] wlan0: authenticated
[14562.264123] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[14562.267927] wlan0: associate with <MAC 'Maric' [AN1]> (try 1/3)
[14562.269694] wlan0: RX AssocResp from <MAC 'Maric' [AN1]> (capab=0x411 status=0 aid=2)
[14562.270317] wlan0: associated
[17095.263343] wlan0: deauthenticated from <MAC 'Maric' [AN1]> (Reason: 6)
[17099.040160] wlan0: authenticate with <MAC 'Maric' [AN1]>
[17099.041835] wlan0: send auth to <MAC 'Maric' [AN1]> (try 1/3)
[17099.042997] wlan0: authenticated
[17099.043188] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[17099.043473] wlan0: associate with <MAC 'Maric' [AN1]> (try 1/3)
[17099.045273] wlan0: RX AssocResp from <MAC 'Maric' [AN1]> (capab=0x411 status=0 aid=2)
[17099.046208] wlan0: associated
[20671.194673] wlan0: deauthenticating from <MAC 'Maric' [AN1]> by local choice (reason=3)
[20677.294141] wlan0: authenticate with <MAC 'Maric' [AN1]>
[20677.295213] wlan0: send auth to <MAC 'Maric' [AN1]> (try 1/3)
[20677.296302] wlan0: authenticated
[20677.296369] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[20677.298722] wlan0: associate with <MAC 'Maric' [AN1]> (try 1/3)
[20677.300465] wlan0: RX AssocResp from <MAC 'Maric' [AN1]> (capab=0x411 status=0 aid=2)
[20677.301154] wlan0: associated


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-04-25
Hi, looks like you have set some driver parameters please change:
```
options iwlwifi 11n_disable=1 wd_disable=1
```
To:
```
options iwlwifi 11n_disable=8
```
save and close your editor.
Go into your router and try channel 1, 6 or 11
also change > disabling HT/VHT due to WEP/TKIP
in router to use > WPA2-AES instead of TKIP
then save the configuration and close router page.

Go into network manager and remove all connections then reboot computer and let network manager find your connection.
If that does not help please do:
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless

```
Thanks

---

### Post by dragan4 on 2015-04-26
Thank you very much for your reply and for your time ...


can you explain a little what I need to do with this

> [COLOR=#000000]*disabling HT/VHT due to WEP/TKIP*[/COLOR]

I think this needs to change something in the router but do not know exactly how the name of this option on the router?


Thank you very much

---

### Post by wildmanne39 on 2015-04-26
In your router setting you will see encryption or security settings change the settings to just wpa2 (AES) (CCMP) only not TKIP. That should get rid of the message that you asked about it is in the error message of the info you posted and make it connect faster.

---

### Post by dragan4 on 2015-04-28
Hi 

Thank you very much for your reply .... I've made all the changes as you write but still no results :(




here I did this once wirless script to you check if I did well ...


Any help really means a lot to me :)



```


########## wireless info START ##########


Report from: 28 Apr 2015 11:35 CEST +0200


Booted last: 28 Apr 2015 10:36 CEST +0200


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4460]
    Kernel driver in use: iwlwifi


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Dell Device [1028:05f9]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 04f3:0206 Elan Microelectronics Corp. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 0c45:6705 Microdia 
Bus 002 Device 003: ID 04f2:0408 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwlmvm                189813  0 
mac80211              630669  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 dell_wmi


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
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae7b:a1ff:fe0c:17a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:217991621 (217.9 MB)  TX bytes:31776934 (31.7 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Maric"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Maric' [AC1]>   
          Bit Rate=43.3 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


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


- Device: wlan0  [Maric 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           39 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Maric:          Infra, <MAC 'Maric' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 51 WPA2


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Maric 2]] (600 root)
[connection] id=Maric 2 | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Maric 1]] (600 root)
[connection] id=Maric 1 | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Maric]] (600 root)
[connection] id=Maric | type=802-11-wireless
[802-11-wireless] ssid=Maric | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Belgrade (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Maric' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Maric"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d9aa08326
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     412FF07DA992AAD938A30BE
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
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
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
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
options iwlwifi 11n_disable=8


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 2797.553154] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 3)
[ 2801.347266] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 2801.348885] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 2801.350037] wlan0: authenticated
[ 2801.350586] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 2801.352841] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 2801.353701] wlan0: associated
[ 2803.487707] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 3)
[ 2807.268715] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 2807.270350] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 2807.271852] wlan0: authenticated
[ 2807.272452] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 2807.275550] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 2807.276231] wlan0: associated
[ 2942.880777] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 3)
[ 2946.674745] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 2946.676615] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 2946.677835] wlan0: authenticated
[ 2946.682074] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 2946.684666] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=2)
[ 2946.685442] wlan0: associated
[ 3207.792228] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 3)
[ 3211.595341] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 3211.597082] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 3211.722074] wlan0: authenticated
[ 3211.726293] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 3212.036707] wlan0: associate with <MAC 'Maric' [AC1]> (try 2/3)
[ 3212.124868] wlan0: associate with <MAC 'Maric' [AC1]> (try 3/3)
[ 3212.191891] wlan0: association with <MAC 'Maric' [AC1]> timed out
[ 3223.048323] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3225.860690] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 3225.861562] wlan0: direct probe to <MAC 'Maric' [AC1]> (try 1/3)
[ 3226.065895] wlan0: send auth to <MAC 'Maric' [AC1]> (try 2/3)
[ 3226.067963] wlan0: authenticated
[ 3226.069071] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 3226.229021] wlan0: associate with <MAC 'Maric' [AC1]> (try 2/3)
[ 3226.241736] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=1)
[ 3226.242487] wlan0: associated
[ 3226.242535] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3442.523546] wlan0: deauthenticated from <MAC 'Maric' [AC1]> (Reason: 6)
[ 3442.593820] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 3442.595644] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 3442.718980] wlan0: authenticated
[ 3442.721147] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 3442.825178] wlan0: associate with <MAC 'Maric' [AC1]> (try 2/3)
[ 3442.929105] wlan0: associate with <MAC 'Maric' [AC1]> (try 3/3)
[ 3443.033007] wlan0: association with <MAC 'Maric' [AC1]> timed out
[ 3447.204062] wlan0: authenticate with <MAC 'Maric' [AC1]>
[ 3447.205886] wlan0: send auth to <MAC 'Maric' [AC1]> (try 1/3)
[ 3447.207067] wlan0: authenticated
[ 3447.207673] wlan0: associate with <MAC 'Maric' [AC1]> (try 1/3)
[ 3447.209799] wlan0: RX AssocResp from <MAC 'Maric' [AC1]> (capab=0x411 status=0 aid=1)
[ 3447.210566] wlan0: associated


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-04-28
Let's try a few more things, change this:
```
802.11abgn
```
To
```
802.11abg
```
in the router.
Try channel 1,6,or 11 in your router, take it off auto.

If your router is capable of N speeds, you will probably be better off with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz.
then save configuration.

Also in network manager go into wireless settings and change your settings to match the screenshots.

The power management setting did not stick to let's try to turn it off another way.
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.

You do know that you need to shutdown your computer and remove your usb adaptor and unload the drivers for it, and also disconnect your wired connection for your internal card to work properly?

Also what country are you in the 00 listed looks like the U.S. but other information says Europe/Belgrade.
Thanks

---

### Post by dragan4 on 2015-04-29
[QUOTE=Wild Man;13274655]Let's try a few more things, change this:
```
802.11abgn
```
To
```
802.11abg
```


Sorry I do not understand how this I could change it if only to change in file wireless-info.txt file located in the folder Home or?

thanks

---

### Post by wildmanne39 on 2015-04-29
Let's try a few more things, change this:
```
802.11abgn
```
To
```
802.11abg
```


Sorry I do not understand how this I could change it if only to change in file wireless-info.txt file located in the folder Home or?

thanks[/QUOTE]The settings are in your router.
Thanks

---

### Post by dragan4 on 2015-04-29
Thanks very much ...

currently work good hope that it will work  ....


really thank you very much for your help and time you lose to solve my problems

---

### Post by wildmanne39 on 2015-04-29
Glad it is working!
Enjoy!

---

