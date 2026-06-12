---
title: "XPS 13 - WiFi connects to router but no internet"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by $teve on 2014-12-07
Hi,

I've just done a fresh install of 14.10 Ubuntu-Gnome, coming from 14.04 UG, and now I'm having problems with WiFi:

I see signal bars in the corner, and it appears that I'm connected to my router, however I cannot access the internet or my routers settings for that matter.

Strangely the problem only seems to occur when I have a USB drive attached.

Here are the outputs of iwconfig:
```
wlan0     IEEE 802.11abgn  ESSID:"steve.net"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: EC:1A:59:17:EA:BF   
          Bit Rate=2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:276   Missed beacon:0

lo        no wireless extensions.

```

Any help will be greatly appreciated

---

### Post by praseodym on 2014-12-07
Deactivate the power management
```

sudo iwconfig wlan0 power off
```
If it is not enough, please run the wireless script from the sticky thread and show the outputs here in code-tags (# button)

---

### Post by $teve on 2014-12-08
> **praseodym said:**
> Deactivate the power management
```

sudo iwconfig wlan0 power off
```
If it is not enough, please run the wireless script from the sticky thread and show the outputs here in code-tags (# button)

Thanks for the reply!

The code you pasted didn't do anything so here is the output of the script. I ran it when the internet was working.... Should i also post the output when it won't work?
```

########## wireless info START ##########

Report from: 09 Dec 2014 00:58 GST +0400

Booted last: 08 Dec 2014 22:03 GST +0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, intel_pstate=enable, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 005: ID 0bda:5604 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 06cb:0af8 Synaptics, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18227  0 
dcdbas                 14928  1 dell_laptop
iwlmvm                217988  0 
mac80211              660592  1 iwlmvm
iwlwifi               182909  1 iwlmvm
cfg80211              510218  3 iwlwifi,mac80211,iwlmvm
wmi                    19193  1 dell_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::7e7a:91ff:fe7b:718b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40412205 (40.4 MB)  TX bytes:5082569 (5.0 MB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"steve.net"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'steve.net' [AC1]>   
          Bit Rate=5.5 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:325   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search steve.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [steve.net] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *steve.net:      Infra, <MAC 'steve.net' [AC1]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2

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

[[/etc/NetworkManager/system-connections/82Diner]] (600 root)
[connection] id=82Diner | type=802-11-wireless
[802-11-wireless] ssid=82Diner | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/steve.net]] (600 root)
[connection] id=steve.net | type=802-11-wireless
[802-11-wireless] ssid=steve.net | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Fast]] (600 root)
[connection] id=Fast | type=802-11-wireless
[802-11-wireless] ssid=Fast | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Dubai (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), NO-IR
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), NO-IR
	(5735 - 5835 @ 40), (3, 20), NO-IR

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
          Current Frequency:2.432 GHz (Channel 5)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'steve.net' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"steve.net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001318ea90cf
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.16.0-25-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     745EC36274968E8B9763DF1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.16.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     47858A8653B88C1F785045F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.16.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        57:84:EB:68:67:A4:54:0D:81:00:54:86:B7:55:38:28:88:8A:60:E0
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
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

coretemp

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

##### rc.local ##########################

rfkill block bluetooth
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 2135.448616] iwlwifi 0000:02:00.0: no hotplug settings from platform (repeated 2 times)
[ 2135.468942] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[ 2135.484003] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2142.695648] wlan0: authenticate with <MAC 'steve.net' [AC1]>
[ 2142.698235] wlan0: send auth to <MAC 'steve.net' [AC1]> (try 1/3)
[ 2142.700054] wlan0: authenticated
[ 2142.701996] wlan0: associate with <MAC 'steve.net' [AC1]> (try 1/3)
[ 2142.726462] wlan0: RX AssocResp from <MAC 'steve.net' [AC1]> (capab=0x431 status=0 aid=4)
[ 2142.727137] wlan0: associated
[ 2142.727160] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2142.784909] wlan0: deauthenticating from <MAC 'steve.net' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 2142.799403] wlan0: authenticate with <MAC 'steve.net' [AC1]>
[ 2142.801844] wlan0: send auth to <MAC 'steve.net' [AC1]> (try 1/3)
[ 2142.805317] wlan0: authenticated
[ 2142.805934] wlan0: associate with <MAC 'steve.net' [AC1]> (try 1/3)
[ 2142.823189] wlan0: RX AssocResp from <MAC 'steve.net' [AC1]> (capab=0x431 status=0 aid=4)
[ 2142.823927] wlan0: associated

########## wireless info END ############

```

---

