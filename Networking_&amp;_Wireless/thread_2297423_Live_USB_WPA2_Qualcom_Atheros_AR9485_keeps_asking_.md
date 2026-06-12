---
title: "Live USB WPA2 Qualcom Atheros AR9485 keeps asking for password"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by peter206 on 2015-10-03
Hello guys. Still not giving up to Ubuntu. :-)

I finally managed to run the wireless script by connecting to neighbouring unsecured WiFi. Now the problem is that Ubuntu will not connect to my (ESSID "PeroWiFi") secured or unsecured wifi connection. I am running Ubuntu on Live USB, AMD 64 PC with Qualcom Atheros AR9485 internal card supported by Ubuntu.  I beg you for help. 


Here is the script output while it was connected on the unsecured wifi.

```
########## wireless info START ##########

Report from: 03 Oct 2015 18:32 UTC +0000


Booted last: 03 Oct 2015 18:21 UTC +0000


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: file=/cdrom/preseed/ubuntu.seed, cdrom-detect/try-usb=true, noprompt, floppy.allowed_drive_mask=0, ignore_uuid, boot=casper, quiet, splash, --


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:3118]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 008 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID abcd:1234 Unknown 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211


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
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128353 (128.3 KB)  TX bytes:56373 (56.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Kastelic"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Kastelic' [AC1]>   
          Bit Rate=6.5 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:2   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2110     1  0 18:21 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Kastelic] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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
    PeroWiFi:        Infra, <MAC 'PeroWiFi' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    *Kastelic:       Infra, <MAC 'Kastelic' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 33


  IPv4 Settings:
    Address:         192.168.1.11
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


[[/etc/NetworkManager/system-connections/Kastelic]] (600 root)
[connection] id=Kastelic | type=802-11-wireless
[802-11-wireless] ssid=Kastelic | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Etc/UTC (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Kastelic' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"Kastelic"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039c03567a8
                    Extra: Last beacon: 116ms ago
          Cell 02 - Address: <MAC 'PeroWiFi' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"PeroWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000059e440e2
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     CBEA66963CF96C070BE11E6
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B23264F074A7D27F8B691A2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


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
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  625.504535] wlan0: authenticate with <MAC 'Kastelic' [AC1]>
[  625.525184] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 1/3)
[  626.410859] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 2/3)
[  626.530045] wlan0: authenticated
[  626.558850] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 1/3)
[  627.398072] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 2/3)
[  628.397212] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 3/3)
[  628.560229] wlan0: RX AssocResp from <MAC 'Kastelic' [AC1]> (capab=0x401 status=0 aid=1)
[  628.560319] wlan0: associated
[  631.770723] wlan0: authenticate with <MAC 'Kastelic' [AC1]>
[  631.791304] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 1/3)
[  632.405448] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 2/3)
[  632.796228] wlan0: authenticated
[  632.824920] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 1/3)
[  633.380438] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 2/3)
[  634.403569] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 3/3)
[  634.826275] wlan0: RX AssocResp from <MAC 'Kastelic' [AC1]> (capab=0x401 status=0 aid=1)
[  634.826364] wlan0: associated
[  636.680677] wlan0: deauthenticating from <MAC 'Kastelic' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  641.325321] wlan0: authenticate with <MAC 'Kastelic' [AC1]>
[  641.346389] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 1/3)
[  642.351110] wlan0: authenticated
[  642.391851] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 1/3)
[  643.383137] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 2/3)
[  644.393096] wlan0: RX AssocResp from <MAC 'Kastelic' [AC1]> (capab=0x401 status=0 aid=1)
[  644.393183] wlan0: associated
[  644.393925] wlan0: deauthenticating from <MAC 'Kastelic' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  644.601376] wlan0: authenticate with <MAC 'Kastelic' [AC1]>
[  644.615405] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 1/3)
[  645.851943] wlan0: authenticated
[  645.896645] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 1/3)
[  647.379126] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 2/3)
[  647.897947] wlan0: RX AssocResp from <MAC 'Kastelic' [AC1]> (capab=0x401 status=0 aid=1)
[  647.898038] wlan0: associated
[  650.732497] wlan0: authenticate with <MAC 'Kastelic' [AC1]>
[  650.753384] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 1/3)
[  651.375631] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 2/3)
[  651.758263] wlan0: authenticated
[  651.787169] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 1/3)
[  652.386682] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 2/3)
[  653.361766] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 3/3)
[  653.788440] wlan0: RX AssocResp from <MAC 'Kastelic' [AC1]> (capab=0x401 status=0 aid=1)
[  653.788530] wlan0: associated
[  714.457153] wlan0: authenticate with <MAC 'Kastelic' [AC1]>
[  714.477667] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 1/3)
[  715.291607] wlan0: send auth to <MAC 'Kastelic' [AC1]> (try 2/3)
[  715.482420] wlan0: authenticated
[  715.511286] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 1/3)
[  716.290562] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 2/3)
[  717.301722] wlan0: associate with <MAC 'Kastelic' [AC1]> (try 3/3)
[  717.512631] wlan0: RX AssocResp from <MAC 'Kastelic' [AC1]> (capab=0x401 status=0 aid=1)
[  717.512720] wlan0: associated


########## wireless info END ############
```

---

### Post by peter206 on 2015-10-04
Bump & update. 

I have installed Ubuntu along side windows but sill can't connect to my wifi. Can please somebody check the script output and help me with this?

---

### Post by jeremy31 on 2015-10-04
I would change the wifi encryption on the wifi router to WPA2 only, it may be called WPA2-AES or WPA2-PSK.  Right now you have mixed mode with TKIP and that caused issues with my AR9485

---

### Post by peter206 on 2015-10-04
> **jeremy31 said:**
> I would change the wifi encryption on the wifi router to WPA2 only, it may be called WPA2-AES or WPA2-PSK.  Right now you have mixed mode with TKIP and that caused issues with my AR9485


The problem is that Ubuntu will not connect even without any encryption. :-(


P.S. It will connect perfectly to ad-hoc settings but not to infrastructure. But even then without internet access.

---

### Post by jeremy31 on 2015-10-04
You can go into Network Manager and change the IPv6 setting to ignore

---

### Post by peter206 on 2015-10-04
> **jeremy31 said:**
> You can go into Network Manager and change the IPv6 setting to ignore


Already tried that. I noticed that /etc/network/interfaces is empty. Should network manager write something in there for wlan0?

---

### Post by jeremy31 on 2015-10-04
This command may help if that is happening ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure resolvconf
```[/FONT][/COLOR]

---

### Post by peter206 on 2015-10-04
> **jeremy31 said:**
> This command may help if that is happening ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure resolvconf[/FONT][/COLOR]
```


Unfortunately this is not working. Except from the standard "auto lo" and "iface lo inet loopback" the "interfaces" file is empty. No sign of wlan0. Shouldnt network manager store some connection info here or it stores somewhere else?

---

### Post by jeremy31 on 2015-10-04
The interfaces should work the way it is.  Connection info is usually in /etc/NetworkManager/system-connections/  You will have to use root to view the files as they contain passwords an other info.  You could run the wifi script again

---

### Post by peter206 on 2015-10-05
This has to be some really nasty bug. Ubuntu will find everything, recognise all my cards, all wifis, even my broadband settings but it will not connect. With no proper manual or (community) solution I am declering defeat. Maybe in 10 years linux will finaly fix drivers first and only after that made yet another damn GUI. Very disapointing and frustrating.

---

### Post by kurt18947 on 2015-10-05
Which version of Ubuntu are you running? For newish hardware, if you haven't done so, I'd at least try a live install of the latest version of *buntu, currently 15.10 Ubuntu, Xubuntu etc. See if the latest kernel/modules work better.  Something else you could try would be to enable backports though I guess that could cause its own issues. Driver support is - or at least should be - up to the hardware manufacturers. I thought Atheros was pretty good with their linux support.

I have a situation right now with a Thinkpad T410 w/ an Intel 6200 wifi chip. It's pretty slow when connecting to my Linksys router running DD-WRT, like 26 mb./sec. slow. I can plug in a Realtek RTL-8192SU based USB adapter and it connects at 150 mb./sec. no changes to the router. I can take this notebook elsewhere and connect at 100 mb./sec.+. using the Intel wifi so it doesn't seem to be a hardware failing. Some wifi adapters seem to 'not like' some wifi router/access points and love others. I have no idea why but it seems to be the case.

Edit: Another thing you could check would be go into "network connections" and see if there are multiple connections to the same access point. I've had this in the past and it's caused problems. I usually delete them all and establish one connection.

---

### Post by peter206 on 2015-10-06
Can somebody points me where and how EXACTLY does network manager STORES my wifi and password info? It seems like Ubuntu is not ABLE to store and use that info. Can I do it manually trough CLI? Where and which files should I check?

---

### Post by jeremy31 on 2015-10-06
You should be able to see file with ```
ls /etc/NetworkManager/system-connections
```
And check the info with ```
gksudo gedit /etc/NetworkManager/system-connections/YOURCONNECTION
```

The info looks like this
```
[connection]id=CONNECTION NAME
uuid=SOME NUMBER
type=802-11-wireless


[802-11-wireless]
ssid=NETWORK NAME
mode=infrastructure
mac-address=MACADDRESS
security=802-11-wireless-security


[802-11-wireless-security]
key-mgmt=wpa-psk
psk=PASSWORD


[ipv4]
method=auto


[ipv6]
method=ignore
```

---

### Post by cpatrick08 on 2015-10-07
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9kfix.conf > /dev/null  Then reboot   [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/251594](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/251594)

---

