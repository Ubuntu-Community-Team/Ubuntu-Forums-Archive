---
title: "After upgrade to 14.04 system connects to wi-fi but it doesn't browse"
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by marga2 on 2015-04-06
Hi,
I've upgrade to 14.04 and it looks like connected to a wi-fi network and also to ethernet network but it doesn´t browse any page, not with firefox, not with chrome. 

A network wireless testing fails with the following error message: **[“Fontconfig warning: ignoring C.UTF-8: not a valid language tag]("http://askubuntu.com/questions/312122/fontconfig-warning-ignoring-c-utf-8-not-a-valid-language-tag")"**


And the following is the information displayed in the wireless-info file, do you have any idea of what is happening and how to solve it?

Thanks
```

########## wireless info START ##########


Report from: 06 Apr 2015 19:54 CEST +0200


Booted last: 06 Apr 2015 17:12 CEST +0200


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description: Ubuntu 14.04.2 LTS
Release: 14.04
Codename: trusty


##### kernel ############################


Linux 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
Subsystem: Lenovo Device [17aa:21f3]
Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 004: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 003 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 002: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 003 Device 005: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
Soft blocked: yes
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no


##### lsmod #############################


iwldvm 232285 0 
mac80211 630669 1 iwldvm
iwlwifi 169932 1 iwldvm
cfg80211 484040 3 iwlwifi,mac80211,iwldvm
wmi 19177 0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0 Link encap:Ethernet HWaddr <MAC 'eth0' [IF]> 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:85832 errors:0 dropped:0 overruns:0 frame:0
TX packets:1085 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:7488454 (7.4 MB) TX bytes:174538 (174.5 KB)
Interrupt:20 Memory:f2500000-f2520000 


wlan0 Link encap:Ethernet HWaddr <MAC 'wlan0' [IF]> 
inet addr:192.168.0.137 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::863a:4bff:fe06:5550/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3047 errors:0 dropped:0 overruns:0 frame:0
TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1043518 (1.0 MB) TX bytes:78287 (78.2 KB)


##### iwconfig ##########################


eth0 no wireless extensions.


lo no wireless extensions.


wlan0 IEEE 802.11abgn ESSID:"OCEANOGRAFIA2" 
Mode:Managed Frequency:2.462 GHz Access Point: <MAC 'OCEANOGRAFIA2' [AC1]> 
Bit Rate=72.2 Mb/s Tx-Power=15 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=56/70 Signal level=-54 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:1382 Missed beacon:0


##### route #############################


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.0.1 0.0.0.0 UG 0 0 0 wlan0
192.168.0.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan0


##### resolv.conf #######################


nameserver 127.0.0.1
search agrocampus-ouest.fr


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0 [OCEANOGRAFIA2] -----------------------------------------------
Type: 802.11 WiFi
Driver: iwlwifi
State: connected
Default: yes
HW Address: <MAC 'wlan0' [IF]>


Capabilities:
Speed: 72 Mb/s


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Points (* = current AP)
A-106 AirLink: Infra, <MAC 'A-106 AirLink' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
Laura Prieto's Network: Infra, <MAC 'Laura Prieto's Network' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
red tep105rbe: Infra, <MAC 'red tep105rbe' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
RNM306: Infra, <MAC 'RNM306' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
*OCEANOGRAFIA2: Infra, <MAC 'OCEANOGRAFIA2' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA2
OCEANOGRAFIA3: Infra, <MAC 'OCEANOGRAFIA3' [AC7]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2


IPv4 Settings:
Address: 192.168.0.137
Prefix: 24 (255.255.255.0)
Gateway: 192.168.0.1


DNS: 150.214.4.35
DNS: 150.214.5.83


- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: e1000e
State: unavailable
Default: no
HW Address: <MAC 'eth0' [IF]>


Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s


Wired Properties
Carrier: off


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


[[/etc/NetworkManager/system-connections/OCEANOGRAFIA2]] (600 root)
[connection] id=OCEANOGRAFIA2 | type=802-11-wireless
[802-11-wireless] ssid=OCEANOGRAFIA2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Madrid (based on set time zone)


country CN:
(2402 - 2482 @ 40), (N/A, 20)
(5735 - 5835 @ 40), (N/A, 30)
(57240 - 59400 @ 2160), (N/A, 28)
(59400 - 63720 @ 2160), (N/A, 44)
(63720 - 65880 @ 2160), (N/A, 28)


##### iwlist channels ###################


eth0 no frequency information.


lo no frequency information.


wlan0 18 channels in total; available frequencies :
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
Channel 149 : 5.745 GHz
Channel 153 : 5.765 GHz
Channel 157 : 5.785 GHz
Channel 161 : 5.805 GHz
Channel 165 : 5.825 GHz
Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


5 APs on Frequency:2.412 GHz (Channel 1)
1 APs on Frequency:2.417 GHz (Channel 2)
1 APs on Frequency:2.437 GHz (Channel 6)
3 APs on Frequency:2.462 GHz (Channel 11)


eth0 Interface doesn't support scanning.


lo Interface doesn't support scanning.


wlan0 Scan completed :
Cell 01 - Address: <MAC 'OCEANOGRAFIA2' [AC1]>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=57/70 Signal level=-53 dBm 
Encryption key:on
ESSID:"OCEANOGRAFIA2"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000288b816f49e
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 02 - Address: <MAC 'ucAir' [AC2]>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=24/70 Signal level=-86 dBm 
Encryption key:on
ESSID:"ucAir"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001b4328c94a
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : 802.1x
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : 802.1x
Cell 03 - Address: <MAC 'ucAirPublica' [AC3]>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=26/70 Signal level=-84 dBm 
Encryption key:on
ESSID:"ucAirPublica"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001b4329a207
Extra: Last beacon: 2044ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Cell 04 - Address: <MAC 'eduroam' [AC4]>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=25/70 Signal level=-85 dBm 
Encryption key:on
ESSID:"eduroam"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001b43295267
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : 802.1x
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : 802.1x
Cell 05 - Address: <MAC 'Laura Prieto's Network' [AC5]>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=35/70 Signal level=-75 dBm 
Encryption key:on
ESSID:"Laura Prieto's Network"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000e1756a6442
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 06 - Address: <MAC 'Red Wi-Fi de GABRIEL' [AC6]>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=25/70 Signal level=-85 dBm 
Encryption key:on
ESSID:"Red Wi-Fi de GABRIEL"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000805cf658e
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 07 - Address: <MAC 'OCEANOGRAFIA3' [AC7]>
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=36/70 Signal level=-74 dBm 
Encryption key:on
ESSID:"OCEANOGRAFIA3"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000004327a419936
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 08 - Address: <MAC 'RNM306' [AC8]>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=27/70 Signal level=-83 dBm 
Encryption key:off
ESSID:"RNM306"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000056da7e3acb9
Extra: Last beacon: 64ms ago
Cell 09 - Address: <MAC 'A-106 AirLink' [AC9]>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=67/70 Signal level=-43 dBm 
Encryption key:on
ESSID:"A-106 AirLink"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000038b8550ec61
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 10 - Address: <MAC 'red tep105rbe' [AC10]>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=28/70 Signal level=-82 dBm 
Encryption key:on
ESSID:"red tep105rbe"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000a76815b07
Extra: Last beacon: 64ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename: /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license: GPL
author: Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version: in-tree:
description: Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion: 496F157C6045EF8314B48BC
depends: iwlwifi,mac80211,cfg80211
intree: Y
vermagic: 3.13.0-48-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo: sha512


[mac80211]
filename: /lib/modules/3.13.0-48-generic/kernel/net/mac80211/mac80211.ko
license: GPL
description: IEEE 802.11 subsystem
srcversion: B8DF1ECC076C2FCEAC70533
depends: cfg80211
intree: Y
vermagic: 3.13.0-48-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo: sha512
parm: max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm: max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm: beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm: probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm: ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename: /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license: GPL
author: Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version: in-tree:
description: Intel(R) Wireless WiFi driver for Linux
firmware: iwlwifi-100-5.ucode
firmware: iwlwifi-1000-5.ucode
firmware: iwlwifi-135-6.ucode
firmware: iwlwifi-105-6.ucode
firmware: iwlwifi-2030-6.ucode
firmware: iwlwifi-2000-6.ucode
firmware: iwlwifi-5150-2.ucode
firmware: iwlwifi-5000-5.ucode
firmware: iwlwifi-6000g2b-6.ucode
firmware: iwlwifi-6000g2a-5.ucode
firmware: iwlwifi-6050-5.ucode
firmware: iwlwifi-6000-4.ucode
firmware: iwlwifi-7265-7.ucode
firmware: iwlwifi-3160-7.ucode
firmware: iwlwifi-7260-7.ucode
srcversion: B81BA270CF5925E724426BD
depends: cfg80211
intree: Y
vermagic: 3.13.0-48-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo: sha512
parm: swcrypto:using crypto in software (default 0 [hardware]) (int)
parm: 11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm: amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm: fw_restart:restart firmware in case of error (default true) (bool)
parm: antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm: wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm: nvm_file:NVM file name (charp)
parm: bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm: led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm: power_save:enable WiFi power management (default: disable) (bool)
parm: power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename: /lib/modules/3.13.0-48-generic/kernel/net/wireless/cfg80211.ko
description: wireless configuration support
license: GPL
author: Johannes Berg
srcversion: 5C139B156678DB83EDA757D
depends: 
intree: Y
vermagic: 3.13.0-48-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: 4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo: sha512
parm: ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm: cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x148f:0x3070 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #############################


[ 6157.740540] wlan0: authenticated
[ 6157.740768] wlan0: waiting for beacon from <MAC 'RNM306' [AC8]>
[ 6157.819623] wlan0: associate with <MAC 'RNM306' [AC8]> (try 1/3)
[ 6157.824462] wlan0: RX AssocResp from <MAC 'RNM306' [AC8]> (capab=0x401 status=0 aid=2)
[ 6157.826627] wlan0: associated
[ 6159.217560] wlan0: deauthenticating from <MAC 'RNM306' [AC8]> by local choice (reason=3)
[ 6162.341366] wlan0: authenticate with <MAC 'OCEANOGRAFIA2' [AC1]>
[ 6162.348996] wlan0: send auth to <MAC 'OCEANOGRAFIA2' [AC1]> (try 1/3)
[ 6162.351606] wlan0: authenticated
[ 6162.352801] wlan0: associate with <MAC 'OCEANOGRAFIA2' [AC1]> (try 1/3)
[ 6162.358866] wlan0: RX AssocResp from <MAC 'OCEANOGRAFIA2' [AC1]> (capab=0x411 status=0 aid=2)
[ 6162.361511] wlan0: associated
[ 6162.670854] wlan0: deauthenticating from <MAC 'OCEANOGRAFIA2' [AC1]> by local choice (reason=2)
[ 6162.677895] wlan0: authenticate with <MAC 'OCEANOGRAFIA2' [AC1]>
[ 6162.680106] wlan0: send auth to <MAC 'OCEANOGRAFIA2' [AC1]> (try 1/3)
[ 6162.682701] wlan0: authenticated
[ 6162.685046] wlan0: associate with <MAC 'OCEANOGRAFIA2' [AC1]> (try 1/3)
[ 6162.688993] wlan0: RX AssocResp from <MAC 'OCEANOGRAFIA2' [AC1]> (capab=0x411 status=0 aid=2)
[ 6162.691216] wlan0: associated


########## wireless info END ##########

```

---

### Post by praseodym on 2015-04-06
Hi,

deactivate IPv6 in the network profile

---

### Post by marga2 on 2015-04-07
It doesn't work, not with wireless, not with wired connection

---

### Post by marga2 on 2015-04-07
I've solved the problem for wireless and wired connection editing the /etc/network/interfaces file. I added the following lines:
```
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp 
```

and then I typed in the Konsole
 ```
sudo /etc/init.d/networking restart

```

Thanks for your help!

---

