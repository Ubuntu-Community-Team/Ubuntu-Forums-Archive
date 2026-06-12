---
title: "Intel AC7265 Can't Authenticate T-Mobile Hotspot Wifi"
date: 2015-12-28
forum: Networking &amp; Wireless
---

### Post by djg9282 on 2015-12-28
I just bought a new Intel NUC5i3RYH for my dad to replace his old Windows XP machine. I just installed Ubuntu 15.10 64bit on it, but I cannot connect to my Mobile hotspot so I can download software updates. I currently only have the hotspot as an option for Internet. I do not have a regular router with an Ethernet connection. I know the mobile hotspot works because I use it all the time with my old laptop, a Gateway MT6840 with an Intel PRO/Wireless 3945ABG. I would love to switch him off of Windows, but if this is not resolved then that will be impossible.

I can see the wireless network as an option in the menu. The problem is that it won't connect. It keeps on bringing up the same screen to type in the Wifi password. Eventually it gives up and just displays "Disconnected." Hopefully you can point me in a direction to get this to work.

---

### Post by jeremy31 on 2015-12-28
Is the hotspot using WEP or TKIP encryption?  Wireless N mode only?

---

### Post by djg9282 on 2015-12-28
It is using WPA2 Personal according to the information I have here regarding T-Mobile and my Blackberry device. Unfortunately, I cannot see the information on the mode it is using. To be honest, I have been using Ubuntu for over 5 years, but I guess because I used older devices...things just worked. I hardly ever needed to ask for help regarding problems. This is the first device that is so much newer (and still not mine), but that is giving me complications and headaches. We can do whatever diagnostics you would like, but I will have to go back and forth between computers to post my response.

---

### Post by jeremy31 on 2015-12-28
I would try this first ```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```
Reboot and then check ```
iwlist scan | egrep -i 'ssid|cipher'
```
Look through the last commands results for the hotspots SSID and see if the group and/or pairwise cipher has TKIP listed

---

### Post by djg9282 on 2015-12-28
I did the first command and rebooted.

I then put in the second command and this is the output:

```
$ iwlist scan | egrep -i 'ssid|cipher'
enp0s25   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                    ESSID:"T-Mobile BlackBerry 6788"
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
```

---

### Post by jeremy31 on 2015-12-28
Will Ubuntu connect to the hotspot now?

---

### Post by djg9282 on 2015-12-28
No. It continues to act like it is connecting after I put in the password and then it will come right back to the password screen after about 20 seconds of trying to authenticate.

---

### Post by jeremy31 on 2015-12-28
Run the wireless script from the sticky post "Before posting in networking and wireless" and post the result

---

### Post by weatherman2 on 2015-12-28
Temporary turn off the security of your hotspot (so no password) and then try it.  You should have this option; my Android 5.1 phone does.  (Little "downarrow" to the right of "WPA-PSK").  At least that will tell you if you can connect without security.

---

### Post by djg9282 on 2015-12-28
Here is the results from running the script:

```

########## wireless info START ##########

Report from: 29 Dec 2015 03:17 EST -0500

Booted last: 29 Dec 2015 00:00 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-V [8086:15a3] (rev 03)
    Subsystem: Intel Corporation Device [8086:2057]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:9010]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 007: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 002: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
snd_pcm               102400  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:aa100000-aa120000 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp0s25   no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       645     1  0 02:14 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-16-generic
GENERAL.FIRMWARE-VERSION:               25.30.13.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5b109bb5-4ac5-4444-be96-2e4bed52f3fb | T-Mobile BlackBerry 6788

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.5-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                      BSSID              MODE    CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
T-Mobile BlackBerry 6788  <MAC 'T-Mobile BlackBerry 6788' [AC1]>  Infra   6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2      no        
thermostat-51-76-A0       <MAC 'thermostat-51-76-A0' [AN2]>  Ad-Hoc  11    2462 MHz  54 Mbit/s  24      &#9602;___  --        no        

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

[[/etc/NetworkManager/system-connections/T-Mobile BlackBerry 6788]] (600 root)
[connection] id=T-Mobile BlackBerry 6788 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=T-Mobile BlackBerry 6788
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone]] (600 root)
[connection] id=iPhone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=iPhone
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s25   no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

enp0s25   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'T-Mobile BlackBerry 6788' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"T-Mobile BlackBerry 6788"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000fff98b8f
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D59CBA6E05CEA656524E14B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-IWL3160_UCODE_API_OK.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     75057B888CB98F986AD50C3
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/iwlopt.conf]
options iwlwifi 11n_disable=8

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 1044.539287] wlp2s0: authenticate with <MAC 'T-Mobile BlackBerry 6788' [AC1]>
[ 1044.541777] wlp2s0: send auth to <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1044.542880] wlp2s0: authenticated
[ 1044.543045] wlp2s0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1044.545179] wlp2s0: associate with <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1044.547184] wlp2s0: RX AssocResp from <MAC 'T-Mobile BlackBerry 6788' [AC1]> (capab=0x431 status=12 aid=0)
[ 1044.547188] wlp2s0: <MAC 'T-Mobile BlackBerry 6788' [AC1]> denied association (code=12)
[ 1105.269466] wlp2s0: authenticate with <MAC 'T-Mobile BlackBerry 6788' [AC1]>
[ 1105.271864] wlp2s0: send auth to <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1105.272924] wlp2s0: authenticated
[ 1105.273074] wlp2s0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1105.276544] wlp2s0: associate with <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1105.278619] wlp2s0: RX AssocResp from <MAC 'T-Mobile BlackBerry 6788' [AC1]> (capab=0x431 status=12 aid=0)
[ 1105.278629] wlp2s0: <MAC 'T-Mobile BlackBerry 6788' [AC1]> denied association (code=12)
[ 1116.083367] wlp2s0: authenticate with <MAC 'T-Mobile BlackBerry 6788' [AC1]>
[ 1116.085726] wlp2s0: send auth to <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1116.086772] wlp2s0: authenticated
[ 1116.086942] wlp2s0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1116.090243] wlp2s0: associate with <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1116.092297] wlp2s0: RX AssocResp from <MAC 'T-Mobile BlackBerry 6788' [AC1]> (capab=0x431 status=12 aid=0)
[ 1116.092308] wlp2s0: <MAC 'T-Mobile BlackBerry 6788' [AC1]> denied association (code=12)
[ 1135.846676] wlp2s0: authenticate with <MAC 'T-Mobile BlackBerry 6788' [AC1]>
[ 1135.849125] wlp2s0: send auth to <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1135.850227] wlp2s0: authenticated
[ 1135.850389] wlp2s0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1135.852232] wlp2s0: associate with <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1135.854266] wlp2s0: RX AssocResp from <MAC 'T-Mobile BlackBerry 6788' [AC1]> (capab=0x431 status=12 aid=0)
[ 1135.854269] wlp2s0: <MAC 'T-Mobile BlackBerry 6788' [AC1]> denied association (code=12)
[ 1146.660999] wlp2s0: authenticate with <MAC 'T-Mobile BlackBerry 6788' [AC1]>
[ 1146.664224] wlp2s0: send auth to <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1146.665316] wlp2s0: authenticated
[ 1146.665980] wlp2s0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1146.669843] wlp2s0: associate with <MAC 'T-Mobile BlackBerry 6788' [AC1]> (try 1/3)
[ 1146.671900] wlp2s0: RX AssocResp from <MAC 'T-Mobile BlackBerry 6788' [AC1]> (capab=0x431 status=12 aid=0)
[ 1146.671915] wlp2s0: <MAC 'T-Mobile BlackBerry 6788' [AC1]> denied association (code=12)
[ 1157.597115] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

########## wireless info END ############


```

weatherman2: concerning your request. Blackberry does not allow me to drop the WPA2 security or even change it. If I erase the password, it will not accept changes and I can never have an active hotspot. I did try connecting to an open "cable" wifi that my regular computer connects to, but this wireless refuses to connect to that as well.

---

### Post by weatherman2 on 2015-12-28
I'm using an Intel 7260 in Ubuntu 12.04, but I had to build the latest iwlwifi driver using a backport.  My driver version is a little newer than yours, so you could try this...or you might get it automatically if you do all of your updates and get a newer kernel.  How to do updates without WiFi?  You could try plugging in an ethernet cable temporarily if that's a possibility.

---

### Post by jeremy31 on 2015-12-28
I would file a bug report starting at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)  and see if they can find the issue

---

### Post by djg9282 on 2015-12-29
So I assume you don't see anything in the output that looks "off." I downloaded the latest snapshot of Ubuntu 16.04 and I'm going to run a live USB and see if it improves the problem. Otherwise, I'll go to a relative and hookup to an ethernet connection. If this doesn't work with Ubuntu 16.04, I really don't think the updates will work, but I will give it a try.

Another alternative...if I download a new kernel from the ppa like Kernel 4.3.3 and install, will I have to do anything different to get it to install a new firmware?

---

### Post by djg9282 on 2015-12-29
Could this be my issue? Although I'm having a hard time figuring out what it all means and where this "config" file is located...[http://patchwork.ozlabs.org/patch/465485/](http://patchwork.ozlabs.org/patch/465485/)

I was brought to the above link after reading through this: [https://bugzilla.kernel.org/show_bug.cgi?id=96471](https://bugzilla.kernel.org/show_bug.cgi?id=96471)

---

### Post by jeremy31 on 2015-12-29
That might be the issue, post ```
dmesg | grep -i wmm
```

We should set the country code also ```
sudo iw reg set US
gksudo gedit /etc/default/crda
```

The last line needs to be ```
REGDOMAIN=US
```
Save, exit gedit and reboot
The US country code is based on your script results, if it is not correct check /ust/share/zoneinfo/zone.tab for your country code

---

### Post by djg9282 on 2015-12-29
I am now on my WiFi hotspot with the computer in question. Let me tell you what I did. 

First, I installed the latest stable kernel from Ubuntu's mainline kernel ppa by following instructions here: [http://linuxg.net/install-kernel-4-3-on-ubuntu/](http://linuxg.net/install-kernel-4-3-on-ubuntu/)
Two, I downloaded the latest firmware and put them into the proper directory. [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi) The kernel automatically chose firmware 16 upon reboot. It then connected immediately.

Thanks for all your help into looking into this.

---

### Post by neil-jerram on 2016-11-11
> **djg9282 said:**
> I am now on my WiFi hotspot with the computer in question. Let me tell you what I did. 

First, I installed the latest stable kernel from Ubuntu's mainline kernel ppa by following instructions here: [http://linuxg.net/install-kernel-4-3-on-ubuntu/](http://linuxg.net/install-kernel-4-3-on-ubuntu/)
Two, I downloaded the latest firmware and put them into the proper directory. [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi) The kernel automatically chose firmware 16 upon reboot. It then connected immediately.

Thanks for all your help into looking into this.

I'm happy to report that installing the latest firmware from [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi) has also solved the problem (or a very similar one) for me.

Particular details for my case:
[LIST]
[*]The hotspot is provided by my Blackberry Classic phone.  I had previously observed that my Debian testing laptop could connect to this hotspot, but my Ubuntu Xenial laptop could not.
[*]I already had kernel 4.4 in my Ubuntu Xenial, so did not need any kernel upgrade step (unlike djg's case above).
[*]My chipset is Intel 7260, so the download I needed was [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-16.242414.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-16.242414.0.tgz).
[*]The file that needs installing, from that tarball, is iwlwifi-7260-16.ucode.  There was already a file with this name in /lib/firmware, but I used md5sum to see that it was different from the one in the tarball, and then replaced it with the one in the tarball.
[/LIST]

---

