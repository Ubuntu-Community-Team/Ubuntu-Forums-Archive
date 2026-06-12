---
title: "Trusty: Unstable wifi ATH5k - fails &quot;REASON=4&quot;"
date: 2015-05-24
forum: Networking &amp; Wireless
---

### Post by izziere on 2015-05-24
Hi all.  I have a variant of this common problem.

My wifi is up and down like a ***** ********.  All updates are in place and I have gone through my friend Goole at length and tried a few things it suggested.  The wifi disconnects regularly, which is not good for a wireless server!

The following is just one example of many entries to syslog:

```

May 24 14:51:25 #SERVER# kernel: [ 1008.040323] cfg80211: Calling CRDA to update world regulatory domain
May 24 14:51:25 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-DISCONNECTED bssid=nn:nn:a5:a2:de:95 reason=4 locally_generated=1
May 24 14:51:25 #SERVER# kernel: [ 1008.103177] cfg80211: World regulatory domain updated:
May 24 14:51:25 #SERVER# kernel: [ 1008.103184] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 24 14:51:25 #SERVER# kernel: [ 1008.103199] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 24 14:51:25 #SERVER# kernel: [ 1008.103209] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 24 14:51:25 #SERVER# kernel: [ 1008.103218] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 24 14:51:25 #SERVER# kernel: [ 1008.103226] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 24 14:51:25 #SERVER# kernel: [ 1008.103235] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 24 14:51:25 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 24 14:51:26 #SERVER# wpa_supplicant[1588]: wlan0: SME: Trying to authenticate with nn:nn:a5:a2:de:95 (SSID='#HIDDEN#' freq=2437 MHz)
May 24 14:51:27 #SERVER# kernel: [ 1009.556403] wlan0: authenticate with nn:nn:a5:a2:de:95
May 24 14:51:27 #SERVER# kernel: [ 1009.562125] wlan0: send auth to nn:nn:a5:a2:de:95 (try 1/3)
May 24 14:51:27 #SERVER# kernel: [ 1009.637329] wlan0: send auth to nn:nn:a5:a2:de:95 (try 2/3)
May 24 14:51:27 #SERVER# kernel: [ 1009.648626] wlan0: send auth to nn:nn:a5:a2:de:95 (try 3/3)
May 24 14:51:27 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="#HIDDEN#" auth_failures=1 duration=10
May 24 14:51:27 #SERVER# kernel: [ 1009.704705] wlan0: authentication with nn:nn:a5:a2:de:95 timed out
May 24 14:51:32 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 24 14:52:29 #SERVER# wpa_supplicant[1588]: message repeated 9 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
May 24 14:52:31 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="#HIDDEN#"
May 24 14:52:31 #SERVER# wpa_supplicant[1588]: wlan0: SME: Trying to authenticate with nn:nn:a5:a2:de:95 (SSID='#HIDDEN#' freq=2437 MHz)
May 24 14:52:31 #SERVER# kernel: [ 1073.644919] wlan0: authenticate with nn:nn:a5:a2:de:95
May 24 14:52:31 #SERVER# kernel: [ 1073.653101] wlan0: send auth to nn:nn:a5:a2:de:95 (try 1/3)
May 24 14:52:31 #SERVER# wpa_supplicant[1588]: wlan0: Trying to associate with nn:nn:a5:a2:de:95 (SSID='#HIDDEN#' freq=2437 MHz)
May 24 14:52:31 #SERVER# kernel: [ 1073.711644] wlan0: authenticated
May 24 14:52:31 #SERVER# kernel: [ 1073.716426] wlan0: associate with nn:nn:a5:a2:de:95 (try 1/3)
May 24 14:52:31 #SERVER# kernel: [ 1073.772007] wlan0: associate with nn:nn:a5:a2:de:95 (try 2/3)
May 24 14:52:31 #SERVER# kernel: [ 1073.816703] wlan0: associate with nn:nn:a5:a2:de:95 (try 3/3)
May 24 14:52:31 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="#HIDDEN#" auth_failures=2 duration=20
May 24 14:52:31 #SERVER# kernel: [ 1073.845040] wlan0: association with nn:nn:a5:a2:de:95 timed out
May 24 14:52:41 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 24 14:52:53 #SERVER# wpa_supplicant[1588]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
May 24 14:52:55 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="#HIDDEN#"
May 24 14:52:55 #SERVER# wpa_supplicant[1588]: wlan0: SME: Trying to authenticate with nn:nn:a5:a2:de:95 (SSID='#HIDDEN#' freq=2437 MHz)
May 24 14:52:55 #SERVER# wpa_supplicant[1588]: wlan0: Trying to associate with nn:nn:a5:a2:de:95 (SSID='#HIDDEN#' freq=2437 MHz)
May 24 14:52:55 #SERVER# kernel: [ 1097.924986] wlan0: authenticate with nn:nn:a5:a2:de:95
May 24 14:52:55 #SERVER# kernel: [ 1097.938028] wlan0: send auth to nn:nn:a5:a2:de:95 (try 1/3)
May 24 14:52:55 #SERVER# kernel: [ 1097.939799] wlan0: authenticated
May 24 14:52:55 #SERVER# kernel: [ 1097.944245] wlan0: associate with nn:nn:a5:a2:de:95 (try 1/3)
May 24 14:52:55 #SERVER# wpa_supplicant[1588]: wlan0: Associated with nn:nn:a5:a2:de:95
May 24 14:52:55 #SERVER# kernel: [ 1097.989240] wlan0: RX AssocResp from nn:nn:a5:a2:de:95 (capab=0x11 status=0 aid=3)
May 24 14:52:55 #SERVER# kernel: [ 1097.991039] wlan0: associated
May 24 14:52:55 #SERVER# wpa_supplicant[1588]: wlan0: WPA: Key negotiation completed with nn:nn:a5:a2:de:95 [PTK=CCMP GTK=TKIP]
May 24 14:52:55 #SERVER# wpa_supplicant[1588]: wlan0: CTRL-EVENT-CONNECTED - Connection to nn:nn:a5:a2:de:95 completed [id=0 id_str=]

```

My wireless-info file shows the following (looks like it was in disconnected mode when I ran the script - as it spends more time disconnected than connected, this is not a surprise):

```



########## wireless info START ##########

Report from: 24 May 2015 14:39 BST +0100

Booted last: 24 May 2015 14:35 BST +0100

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:28 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/####/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:0e.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 05)
	Subsystem: Compaq Computer Corporation NC3120 Fast Ethernet NIC [0e11:b01e]
	Kernel driver in use: e100

00:10.0 Ethernet controller [0200]: Qualcomm Atheros AR2417 Wireless Network Adapter [AR5007G 802.11bg] [168c:001d] (rev 01)
	Subsystem: Belkin F5D7000 v8000 Wireless G Desktop Card [1799:720b]
	Kernel driver in use: ath5k

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 179: rfkill: command not found

##### lsmod #############################

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546118  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
	address 192.168.#.#
	network 192.168.#.#
	netmask 255.255.255.0
	broadcast 192.168.#.#
	gateway 192.168.#.#
	dns-nameservers #####
	wpa-ssid #HIDDEN#
	wpa-psk  ########

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.#.#  Bcast:192.168.#.#  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fef5:fd03/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43882 (43.8 KB)  TX bytes:25151 (25.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.#.#   0.0.0.0         UG    0      0        0 wlan0
192.168.#.#     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver ##

##### network managers ##################

Installed:

	None found.

Running:

	None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '#HIDDEN#' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"#HIDDEN#"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002f87be67
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath5k]
filename:       /lib/modules/3.13.0-53-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     4AD5C4F9BD3EBE694FAA65C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        79:A8:AA:31:2E:38:81:B7:C6:CA:23:E4:59:A5:5B:C7:86:5F:41:9F
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-53-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        79:A8:AA:31:2E:38:81:B7:C6:CA:23:E4:59:A5:5B:C7:86:5F:41:9F
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BF4F6788BCD3848D1F2F4BF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        79:A8:AA:31:2E:38:81:B7:C6:CA:23:E4:59:A5:5B:C7:86:5F:41:9F
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     22618C9A8AD682CBE73FFF2
depends:        
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        79:A8:AA:31:2E:38:81:B7:C6:CA:23:E4:59:A5:5B:C7:86:5F:41:9F
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N

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

loop
lp

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

/usr/local/bin/noip2
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:0e.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:10.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   56.621024] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[   56.637988] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[   56.653723] wlan0: authenticated
[   56.656730] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[   56.688329] wlan0: RX AssocResp from <MAC '#HIDDEN#' [AC1]> (capab=0x11 status=0 aid=3)
[   56.690128] wlan0: associated
[   56.690196] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  123.576536] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  123.585745] wlan0: direct probe to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  123.788133] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 2/3)
[  123.789759] wlan0: authenticated
[  123.793006] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  123.797243] wlan0: RX AssocResp from <MAC '#HIDDEN#' [AC1]> (capab=0x11 status=0 aid=3)
[  123.799175] wlan0: associated
[  145.436537] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  145.445888] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  145.558776] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 2/3)
[  145.590902] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 3/3)
[  145.618157] wlan0: authentication with <MAC '#HIDDEN#' [AC1]> timed out
[  147.524583] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  147.534026] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  147.572274] wlan0: authenticated
[  147.576236] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  147.579462] wlan0: RX AssocResp from <MAC '#HIDDEN#' [AC1]> (capab=0x11 status=0 aid=3)
[  147.581303] wlan0: associated
[  164.260617] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  164.266793] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  164.333787] wlan0: authenticated
[  164.336645] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  164.456130] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 2/3)
[  164.604135] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 3/3)
[  164.724123] wlan0: association with <MAC '#HIDDEN#' [AC1]> timed out
[  203.187301] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  203.194063] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  203.283564] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 2/3)
[  203.295090] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 3/3)
[  203.313800] wlan0: authenticated
[  203.316693] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  203.456129] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 2/3)
[  203.560126] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 3/3)
[  203.607001] wlan0: association with <MAC '#HIDDEN#' [AC1]> timed out
[  259.635497] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  259.642093] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  259.657584] wlan0: authenticated
[  259.660637] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  259.692847] wlan0: RX AssocResp from <MAC '#HIDDEN#' [AC1]> (capab=0x11 status=0 aid=3)
[  259.694625] wlan0: associated
[  269.350744] wlan0: authenticate with <MAC '#HIDDEN#' [AC1]>
[  269.357148] wlan0: send auth to <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  269.401708] wlan0: authenticated
[  269.404646] wlan0: associate with <MAC '#HIDDEN#' [AC1]> (try 1/3)
[  269.407365] wlan0: RX AssocResp from <MAC '#HIDDEN#' [AC1]> (capab=0x11 status=0 aid=3)
[  269.410009] wlan0: associated

########## wireless info END ############

```

Does anyone have any ideas they could share please?

Many thanks.

---

### Post by jeremy31 on 2015-05-24
Have you tried changing the encryption on the wifi router to WPA2-AES or WPA2 only as you seem to be using TKIP and that causes issues

---

### Post by izziere on 2015-05-24
> **jeremy31 said:**
> Have you tried changing the encryption on the wifi router to WPA2-AES or WPA2 only as you seem to be using TKIP and that causes issues

Hi Jeremy and thanks for the quick reply.  Yep done that and it didn't work.  Left it now on WPA2-PSK (AES) to reduce number of potential problems.  For avoidance of doubt, done the whole ifdown and ifup thing and rebooted following the router change.

It might be a conincidence but it gets worse when there is heavy network traffic.

---

### Post by jeremy31 on 2015-05-24
You could also try ```
echo "options ath5k nohwcrypt=Y" | sudo tee -a /etc/modprobe.d/ath5k.conf
``` and ```
sudo iw reg set GB
```
Reboot

---

### Post by izziere on 2015-05-24
Appears to have been solved - many thanks!

Stupidly I tried variants of both those, but individually.  The problems seem to have been caused by both, so having both fixes in place has worked.

---

