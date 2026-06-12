---
title: "Ubuntu 14.04.3 TLS : no way to connect wifi with iwl3945"
date: 2016-03-26
forum: Networking &amp; Wireless
---

### Post by joelg2 on 2016-03-26
hello,
I have just installed Ubuntu 14.04.3 LTS on an old laptop;
everything was OK except for the WIFI :
I can see the SSIDs around but no way to connect to any of them (WPA, WEP nor open ones) :
actually, I never managed to connect even once via wifi ;
By the way, wired connection works properly

I have run the  2 following updates and reboot the PC : no change
sudo apt-get update 
sudo apt-get dist-upgrade

I have also run the wireless-info script via the following command :
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

[FONT=arial]"iwlist scan" outputs look good, I can see the SSIDs around, but, I noticed sometimes that the outputs simply show "no result";
I also noticed there is no definition about WIFI in /etc/network/interfaces ;

Here is the output of this script :
```


########## wireless info START ##########

Report from: 25 Mar 2016 23:57 CET +0100

Booted last: 25 Mar 2016 23:49 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:33 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation WM3945ABG MOW2 [8086:1001]
    Kernel driver in use: iwl3945

06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Packard Bell B.V. Device [1631:c022]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwl3945                65536  0 
iwlegacy               90112  1 iwl3945
mac80211              618496  2 iwl3945,iwlegacy
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
cfg80211              450560  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2996 errors:1 dropped:1 overruns:1 frame:0
          TX packets:1779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3478298 (3.4 MB)  TX bytes:201254 (201.2 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
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

root       764     1  0 23:49 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    FG44:            Infra, <MAC 'FG44' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    orange:          Infra, <MAC 'orange' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    Livebox-0E18:    Infra, <MAC 'Livebox-0E18' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

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

[[/etc/NetworkManager/system-connections/jgap]] (600 root)
[connection] id=jgap | type=802-11-wireless
[802-11-wireless] ssid=jgap | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FG44]] (600 root)
[connection] id=FG44 | type=802-11-wireless
[802-11-wireless] ssid=FG44 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IBMVISITOR]] (600 root)
[connection] id=IBMVISITOR | type=802-11-wireless
[802-11-wireless] ssid=IBMVISITOR | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Livebox-0E18]] (600 root)
[connection] id=Livebox-0E18 | type=802-11-wireless
[802-11-wireless] ssid=Livebox-0E18 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=802-11-wireless
[802-11-wireless] ssid=FreeWifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/jgap 1]] (600 root)
[connection] id=jgap 1 | type=802-11-wireless
[802-11-wireless] ssid=jgap | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.56 GHz (Channel 112)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FreeWifi' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000919e30160
                    Extra: Last beacon: 2352ms ago
          Cell 02 - Address: <MAC 'FreeWifi_secure' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000919e185ec
                    Extra: Last beacon: 2416ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC 'FG44' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"FG44"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000919e30160
                    Extra: Last beacon: 2384ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'orange' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019c81518180
                    Extra: Last beacon: 3124ms ago
          Cell 05 - Address: <MAC 'Livebox-0E18' [AC5]>
                    Channel:112
                    Frequency:5.56 GHz (Channel 112)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Livebox-0E18"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019c7d39103b
                    Extra: Last beacon: 892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     38AF47414DCF3CBFB173CB3
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FA:68:D8:85:DB:14:4E:77:6E:C3:BA:77:BA:A5:78:33:89:EA:8D:85
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.19.0-56-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     752C696EB47FC8BDCF872BB
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FA:68:D8:85:DB:14:4E:77:6E:C3:BA:77:BA:A5:78:33:89:EA:8D:85
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FA:68:D8:85:DB:14:4E:77:6E:C3:BA:77:BA:A5:78:33:89:EA:8D:85
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-56-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FA:68:D8:85:DB:14:4E:77:6E:C3:BA:77:BA:A5:78:33:89:EA:8D:85
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/iwl3945.conf]
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1

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
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   28.450175] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   28.521932] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.603244] 8139too 0000:06:07.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  116.631549] 8139too 0000:06:07.0 eth0: link down
[  131.468855] wlan0: authenticate with <MAC 'FG44' [AC3]>
[  131.474908] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 1/3)
[  131.676047] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 2/3)
[  131.880086] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 3/3)
[  132.084051] wlan0: authentication with <MAC 'FG44' [AC3]> timed out
[  135.405044] wlan0: authenticate with <MAC 'FG44' [AC3]>
[  135.411981] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 1/3)
[  135.612063] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 2/3)
[  135.816076] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 3/3)
[  136.020059] wlan0: authentication with <MAC 'FG44' [AC3]> timed out
[  139.716747] wlan0: authenticate with <MAC 'FG44' [AC3]>
[  139.718382] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 1/3)
[  139.920105] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 2/3)
[  140.124040] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 3/3)
[  140.328072] wlan0: authentication with <MAC 'FG44' [AC3]> timed out
[  142.032032] iwl3945 0000:03:00.0: Queue 0 stuck for 2500 ms.
[  142.032042] iwl3945 0000:03:00.0: On demand firmware reload
[  142.114705] wlan0: authenticate with <MAC 'FG44' [AC3]>
[  142.114880] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 1/3)
[  142.316046] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 2/3)
[  142.520047] wlan0: direct probe to <MAC 'FG44' [AC3]> (try 3/3)
[  142.724046] wlan0: authentication with <MAC 'FG44' [AC3]> timed out
[  165.349889] 8139too 0000:06:07.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  510.505488] 8139too 0000:06:07.0 eth0: link down

########## wireless info END ############


```

thanks in advance for any feedback

[/FONT]

---

