---
title: "New Laptop Install, WIFI permanently disabled"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by nickTaylor1181 on 2016-08-28
Hi all

I'm trying to set up a new laptop for my folks with Ubuntu 16.04.1 

It's an ACER Aspire ES1 522

I hit a fairly serious issue almost immediately - the trackpad didn't work. I temporarily got around this using a USB mouse... and all seemed to go as planned...

... then when installing software (the first big apt-update) the wifi stopped working, and won't come back.

If I do rfkill list all, it says 'Hard blocked: yes' under wifi... no blocks on anything else.

I've tried going back to Ubuntu 14.04... same thing (neither trackpad or wifi work). Am now back on Ubuntu 16.04... still hard-blocked.



Any help much appreciated.

---

### Post by grahammechanical on 2016-08-28
hard blocked: yes = the WiFi adapter is switched off in hardware. It may be disabled in the BIOS. It may need a keyboard combination to switch it on. If Windows is installed and WiFi is turned off in Windows to save battery power, then the WiFi adapter will be turned off in Ubuntu.

you could try this

```
rfkill unblock wifi
```

If that does not work, on 16.04 we can try this

```
nmcli radio wifi on
```

My machine is a desktop. so, I am unfamiliar with laptops & notebooks. Is it possible that when the battery power level drops to a certain point the motherboard starts switching things like the WiFi adapter to prevent the machine shutting down whilst the OS is still loaded? The process of downloading and installing updates is very CPU intensive I have noticed. It will drain battery power.

Regards

---

### Post by Bucky Ball on 2016-08-28
*Thread moved to **Networking and Wireless**.*

You generally have a key on the laptop with a little wireless icon on it (usually one of the 'F*' keys or one of the number/symbol keys at the top). You may need to *squint hard* to see it as the symbol is often small and dark in colour. 

Hold down the FN (function) key which is just next to the Windows key (Super key) on the left bottom of keyboard then hit the wireless key. That should switch it on if it's off, and vice versa. You'll see the wireless light go on or off, or hopefully! :| :)

Either way, please open a terminal and post the output of these two commands:

```
sudo lshw -C network
iwconfig
```

Use code tags for the output (instructions for how the green link at bottom of this post). Thanks.

* ... and as grahammechanical hints at, best to have the machine plugged in when setting this up to rule out anything to do with dropping battery power. Never heard of the scenario described, but just in case.

---

### Post by nickTaylor1181 on 2016-08-30
Hello - thanks for getting back to me. Sorry for the delay, had to buy a mouse, LOL. Trackpad not working.


Okay - answers in some sort of order:

1)

rfkill unblock wifi

nmcli radio wifi on

don't change anything. 

2)
I've installed 16.04, removed it and installed 14.04, then removed that and gone back to 16.04, all with a power-supply plugged in. 16.04 was working to start with but something broke it, and it's never come back. The fact that this has happened across two different operating systems leads me to suspect something lower-level than OS might be at fault here... but I'm a bit terrified of tinkering with firmware (this isn't my PC, I don't want to brick it), so I've been avoiding that.

3)
There is the usual cryptic, easy-to-hit-by-accident wifi on/off key, but clicking it doesn't appear to change anything.

4) 
Output of 
sudo lshw -C network

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 1c:39:47:9f:5c:19
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:35 ioport:2000(size=256) memory:f0b04000-f0b04fff memory:f0b00000-f0b03fff
  *-network DISABLED
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: c8:ff:28:45:7a:2d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:40 memory:f0a00000-f0a7ffff memory:f0a80000-f0a8ffff

```


5) Output of iwconfig

```

lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


......................

Thanks for your help - it's really appreciated.

---

### Post by Bucky Ball on 2016-08-30
> **nickTaylor1181 said:**
> 

3)
There is the usual cryptic, easy-to-hit-by-accident wifi on/off key, but clicking it doesn't appear to change anything.

That's odd, because

  ```
*-network DISABLED
```

... which would generally indicate a hardware switch and you seem to have the correct driver installed. :-k

It would really help the wireless gurus get to the bottom of this if you could run the wirelessinfo script linked in my signature at the bottom of this post and post the output here. I'm a mere wireless pup scout but I can give help with some obvious and known fixes. :)

* Also, and importantly, please stick with whichever release is working best now you know this is working in both rather than switching between the two. Easier to give support. ;)

---

### Post by chili555 on 2016-08-30
> It would really help the wireless gurus get to the bottom of this Subscribed.

---

### Post by Bucky Ball on 2016-08-30
> **chili555 said:**
> Subscribed.

And here's one now. :)

---

### Post by nickTaylor1181 on 2016-08-31
Yea - I'm kindof surprised that the keyboard wifi on/off isn't the culprit as well. I don't think it is though. It's this little icon under F3 key that looks like radio-waves... clicking it... fn-clicking it... no difference to rfkill's output. I suspect this might be some sort of firmware issue, but I might be wrong.

Anyhoo... the output of wireless-info.txt is:

```



########## wireless info START ##########


Report from: 31 Aug 2016 21:31 NZST +1200


Booted last: 31 Aug 2016 00:00 NZST +1200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:104b]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0642]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b47f Chicony Electronics Co., Ltd 
Bus 001 Device 009: ID 04ca:300b Lite-On Technology Corp. Atheros AR3012 Bluetooth
Bus 001 Device 010: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 13fe:4200 Kingston Technology Company Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
ath3k                  20480  0
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
wmi                    20480  1 acer_wmi
video                  40960  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:off/any  
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


root      2329     1  0 Aug30 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
SMCAP              <MAC 'SMCAP' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
belkin54gastpandc  <MAC 'belkin54gastpandc' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA1       no        
--                 <MAC '--' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  --         no        
Tech_D0017116      <MAC 'Tech_D0017116' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  14      &#9602;___  WPA1 WPA2  no        


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Pacific/Auckland (based on set time zone)


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


lo        no frequency information.


enp1s0    no frequency information.


wlp2s0    13 channels in total; available frequencies :
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


lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'SMCAP' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"SMCAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b66671703
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'belkin54gastpandc' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"belkin54gastpandc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002ddaaf6b177
                    Extra: Last beacon: 808ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     323EDC06388A3D0920FD7FC
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[ath3k]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     2B85DCB887D9376A61652DD
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
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


##### dmesg #############################


[ 1873.035579] ath: phy0: ASPM enabled: 0x42
[ 1873.051759] r8169 0000:01:00.0 enp1s0: link down
[ 1873.566151] usb 1-1.3: device firmware changed
[ 1876.216206] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[ 1876.233564] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[ 1876.244373] r8169 0000:01:00.0 enp1s0: link down
[ 1876.245083] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[ 1876.405565] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)


########## wireless info END ############



```

---

### Post by nickTaylor1181 on 2016-08-31
It's just started working... and I've no idea what I did.

Is it possible that there's some massive delay before the effects of the wifi on/off switch happens?

Sorry - bit embarrassing if that's what it was. I swear I tried it about 20 times tho... any other laptop, this would be my first guess at the culprit.


Anyhoo... thanks for your help everyone. Sorry if I accidentally lead you up the garden path. I must confess to being a bit baffled to be fair.

---

### Post by nickTaylor1181 on 2016-08-31
I logged out and in again, and it's stopped working again

Maybe something's wrong with the keyboard - it looks like there's a trackpad enable/disable button as well, and the trackpad doesn't work either (and the button doesn't have any effect). Clutching at straws here now though.

This is now the output of wireless-info.txt


```



########## wireless info START ##########


Report from: 31 Aug 2016 21:55 NZST +1200


Booted last: 31 Aug 2016 00:00 NZST +1200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:104b]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0642]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b47f Chicony Electronics Co., Ltd 
Bus 001 Device 023: ID 04ca:300b Lite-On Technology Corp. Atheros AR3012 Bluetooth
Bus 001 Device 025: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 001 Device 024: ID 13fe:4200 Kingston Technology Company Inc. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
9: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
ath3k                  20480  0
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
wmi                    20480  1 acer_wmi
video                  40960  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40238089 (40.2 MB)  TX bytes:1363483 (1.3 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2329     1  0 Aug30 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/SMCAP]] (600 root)
[connection] id=SMCAP | type=wifi | permissions=user:tae:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=SMCAP
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Pacific/Auckland (based on set time zone)


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


lo        no frequency information.


enp1s0    no frequency information.


wlp2s0    13 channels in total; available frequencies :
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


lo        Interface doesn't support scanning.


enp1s0    Interface doesn't support scanning.


wlp2s0    Interface doesn't support scanning : Network is down


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     323EDC06388A3D0920FD7FC
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[ath3k]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     2B85DCB887D9376A61652DD
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
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


##### dmesg #############################


[ 3414.498748] usb 1-1.3: device firmware changed
[ 3417.216482] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[ 3417.242244] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[ 3417.256561] r8169 0000:01:00.0 enp1s0: link down
[ 3417.256797] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[ 3417.330391] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 3418.248225] wlp2s0: authenticate with <MAC address>
[ 3418.260121] wlp2s0: send auth to <MAC address> (try 1/3)
[ 3418.262069] wlp2s0: authenticated
[ 3418.262347] ath9k 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 3418.262353] ath9k 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[ 3418.263046] wlp2s0: associate with <MAC address> (try 1/3)
[ 3418.273343] wlp2s0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=5)
[ 3418.273463] wlp2s0: associated
[ 3418.273582] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 3421.223046] wlp2s0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)


########## wireless info END ############



```

---

### Post by chili555 on 2016-08-31
Please run:```
rfkill list all
```Then try both Fn+F3 and run it again:```
rfkill list all
```I think it's all the key combination.

What is the exact model of the laptop? Let's check the manual.

---

### Post by nickTaylor1181 on 2016-09-01
Hiya - every time I change anything I repeatedly do the 'fn+f3' and '[FONT=Ubuntu Mono, monospace][COLOR=#000000]rfkill list all' combo. Hundreds of times by now :) - it's not changing anything.[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]If I log in, for about 1/2 a second it looks as though it's connected to a network... then the "connected" icon disappears, and a message saying "you are now offline" appears.


The  model is Acer Aspire E51-522-476P[/COLOR][/FONT]

---

### Post by chili555 on 2016-09-01
As a temporary experiment, please try:```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
rfkill list all
```Any change?

---

### Post by nickTaylor1181 on 2016-09-01
Hiya

Nope - no change.

I have at least managed to fix the touchpad tho - went into setup and changed it from advanced to basic.

.....

I think I've fixed it though.

.....

Tried booting into network-enabled recovery mode... it gave a load of messages saying it couldn't find "resolve.conf", and basically just kindof hung.

When I googled the error messages, I came up with (among other things), this:

[https://github.com/docker/docker/issues/4861](https://github.com/docker/docker/issues/4861)

Which claims that 

"[COLOR=#333333][FONT=-apple-system]I am running on an Asus X550CC. Overall, a decent machine but it has one caveat: The Wi-Fi hardware is disabled under Linux until you sleep and then resume[/FONT][/COLOR]"

Different model, but this might explain why the wifi suddenly came back to life before... I'd accidentally hit the sleep key which is right next to the wifi key. Couldn't replicate this behaviour deliberately tho :)

then I found this:

[http://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill](http://askubuntu.com/questions/98702/how-to-unblock-something-listed-in-rfkill)

> 
sudo nano /etc/modprobe.d/blacklist.conf


add blacklist acer_wmi as a new line at the bottom of this file.


then reboot.


Which appears to have worked. I've rebooted a couple of times... the fix appears to be permanent.

So I think we're all good now - although I'm not 100% sure what acer_wmi actually is.




Thanks for your help everyone. It is really really appreciated.

---

