---
title: "Can't Connect to WIFI, related to &quot;sudo connmanctl&quot;?"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by webmanoffesto on 2016-09-14
I'm not able to connect to WiFi from my Asus K55A laptop (not from Ubuntu 16.04 Gnome LTS and not from a Lubuntu live disk).

I recently tried to connect to a Lego Mindstorms robot and ran
robot@ev3dev:~$ sudo connmanctl
as described on 
[http://www.ev3dev.org/docs/tutorials/setting-up-wifi-using-the-command-line/](http://www.ev3dev.org/docs/tutorials/setting-up-wifi-using-the-command-line/)

But I don't know if that's related.

The output of a WiFi analysis script is below. Maybe the below will help you to tell me what the problem is. Thanks

```


mmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmm

########## wireless info START ##########

2016.09.14..10.45

Report from: 14 Sep 2016 14:37 UTC +0000

Booted last: 14 Sep 2016 00:00 UTC +0000

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

file=/cdrom/preseed/lubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, ---

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave AR9485 Wireless Network Adapter [1a3b:2c97]
    Kernel driver in use: ath9k

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:1457]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
ath3k                  20480  0
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
bluetooth             520192  5 ath3k,btbcm,btrtl,btusb,btintel
wmi                    20480  1 asus_wmi
video                  40960  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0f2  no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9485 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e1268d34-c877-41fe-a971-0ef4a8c14189 | ZGQLM

GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
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

SSID   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ZGQLM  <MAC 'ZGQLM' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
--     <MAC '--' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/ZGQLM]] (600 root)
[connection] id=ZGQLM | type=wifi | permissions=user:lubuntu:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ZGQLM
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

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

enp3s0f2  no frequency information.

wlp2s0    14 channels in total; available frequencies :
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

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

lo        Interface doesn't support scanning.

enp3s0f2  Interface doesn't support scanning.

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'ZGQLM' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ZGQLM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000114e0487e2
                    Extra: Last beacon: 576ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FiOS-X3LAR_EXT' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"FiOS-X3LAR_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b60f16c0bb
                    Extra: Last beacon: 908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   86.554125] ath: phy0: Disable PLL PowerSave
[   86.562692] ath: phy0: ASPM enabled: 0x43
[   86.562695] ath: EEPROM regdomain: 0x60
[   86.562696] ath: EEPROM indicates we should expect a direct regpair map
[   86.562697] ath: Country alpha2 being used: 00
[   86.562698] ath: Regpair used: 0x60
[   87.295347] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   92.054299] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[40593.553118] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)

########## wireless info END ############



```

---

### Post by webmanoffesto on 2016-09-18
I just ran "sudo apt-get install network-manager" while on wired ethernet internet. That installed fine (second time?), I didn't get a message about removing connman. Then I unplugged the ethernet cable. That put me on WiFi and I successfully pinged Google. Great. But for some reason I am still unable to surf the web in Firefox or Chromium. This doesn't make sense. What do you recommend?

---

### Post by wildmanne39 on 2016-09-18
Let's start with you setting your network settings in network manager to match the screenshots then if it does not connect reboot router and after it comes back up run the wireless script again and tell us what network you are trying to connect too.

---

### Post by webmanoffesto on 2016-09-18
> **Wild Man said:**
> Let's start with you setting your network settings in network manager to match the screenshots 
What screenshots?

---

### Post by wildmanne39 on 2016-09-18
Sorry they did not show up I will try again.

---

### Post by webmanoffesto on 2016-09-18
My screens look a little different than yours. 
---
In the IPv4 screen (like below)
I entered Server: 8.8.8.8
and added another server 8.8.4.4
Screenshot: [http://i1232.photobucket.com/albums/ff365/webmanoffesto/WiFi..IPV4..Cropped..800W..Server.8.8.8.8..v01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/WiFi..IPV4..Cropped..800W..Server.8.8.8.8..v01.png)

[FONT=gotham]

[/FONT]And the output of the WiFi Network analysis script came out as
```



########## wireless info START ##########


Report from: 18 Sep 2016 21:55 EDT -0400


Booted last: 18 Sep 2016 00:00 EDT -0400


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave AR9485 Wireless Network Adapter [1a3b:2c97]
    Kernel driver in use: ath9k


03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:1457]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
ath3k                  20480  0
bluetooth             520192  10 bnep,ath3k,btbcm,btrtl,btusb,btintel
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  1 asus_wmi
video                  40960  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28903 (28.9 KB)  TX bytes:8680 (8.6 KB)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8b2b:4264:c7f5:3d89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1355535 (1.3 MB)  TX bytes:184819 (184.8 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0f2  no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:"ZGQLM"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'ZGQLM' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:120   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9485 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ZGQLM
GENERAL.CON-UUID:                       07cfe33c-6b09-42e3-af75-19199e89afce
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{12}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   07cfe33c-6b09-42e3-af75-19199e89afce | ZGQLM
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = Toms-AsusK55A
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       expiry = 1474332498
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.5
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::8b2b:4264:c7f5:3d89/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8411-1_0.0.3 06/18/12
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
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


SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
ZGQLM           <MAC 'ZGQLM' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  91      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 
FiOS-X3LAR_EXT  <MAC 'FiOS-X3LAR_EXT' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2      no        


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


[[/etc/NetworkManager/system-connections/Artisan's Asylum]] (600 root)
[connection] id=Artisan's Asylum | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Artisan's Asylum
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_1519]] (600 root)
[connection] id=ES_1519 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_1519
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DIRECT-JZM2020 Series]] (600 root)
[connection] id=DIRECT-JZM2020 Series | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=DIRECT-JZM2020 Series
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/wegmans]] (600 root)
[connection] id=wegmans | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=wegmans
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_8286]] (600 root)
[connection] id=ES_8286 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_8286
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_1219]] (600 root)
[connection] id=ES_1219 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_1219
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Library]] (600 root)
[connection] id=Library | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Library
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_8393]] (600 root)
[connection] id=ES_8393 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_8393
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_4423]] (600 root)
[connection] id=ES_4423 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_4423
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_6514]] (600 root)
[connection] id=ES_6514 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_6514
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Lahey Public WiFi]] (600 root)
[connection] id=Lahey Public WiFi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Lahey Public WiFi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_4880]] (600 root)
[connection] id=ES_4880 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_4880
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_7760]] (600 root)
[connection] id=ES_7760 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_7760
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_1826]] (600 root)
[connection] id=ES_1826 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_1826
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_9807]] (600 root)
[connection] id=ES_9807 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_9807
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_6488]] (600 root)
[connection] id=ES_6488 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_6488
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_3831]] (600 root)
[connection] id=ES_3831 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_3831
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_4637]] (600 root)
[connection] id=ES_4637 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_4637
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_3795]] (600 root)
[connection] id=ES_3795 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_3795
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_8749]] (600 root)
[connection] id=ES_8749 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_8749
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_5247]] (600 root)
[connection] id=ES_5247 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_5247
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_6672]] (600 root)
[connection] id=ES_6672 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_6672
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ZGQLM]] (600 root)
[connection] id=ZGQLM | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ZGQLM
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_8747]] (600 root)
[connection] id=ES_8747 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_8747
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UMassLowell]] (600 root)
[connection] id=UMassLowell | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=UMassLowell
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_5976]] (600 root)
[connection] id=ES_5976 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_5976
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_8817]] (600 root)
[connection] id=ES_8817 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_8817
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_2488]] (600 root)
[connection] id=ES_2488 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_2488
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_2198]] (600 root)
[connection] id=ES_2198 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_2198
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_9066]] (600 root)
[connection] id=ES_9066 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_9066
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_1386]] (600 root)
[connection] id=ES_1386 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_1386
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_5846]] (600 root)
[connection] id=ES_5846 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_5846
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MCCBasic]] (600 root)
[connection] id=MCCBasic | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=MCCBasic
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_9808]] (600 root)
[connection] id=ES_9808 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_9808
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/woburnguest]] (600 root)
[connection] id=woburnguest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=woburnguest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_1732]] (600 root)
[connection] id=ES_1732 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_1732
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_4670]] (600 root)
[connection] id=ES_4670 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_4670
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_2870]] (600 root)
[connection] id=ES_2870 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_2870
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_3124]] (600 root)
[connection] id=ES_3124 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_3124
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_6060]] (600 root)
[connection] id=ES_6060 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_6060
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ES_5739]] (600 root)
[connection] id=ES_5739 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=ES_5739
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp3s0f2  no frequency information.


wlp2s0    11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.462 GHz (Channel 11)


lo        Interface doesn't support scanning.


enp3s0f2  Interface doesn't support scanning.


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'ZGQLM' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"ZGQLM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f43ee1849
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     2B85DCB887D9376A61652DD
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[ath9k]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     323EDC06388A3D0920FD7FC
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[ 4813.524883] wlp2s0: authenticate with <MAC 'ZGQLM' [AC1]>
[ 4813.543426] wlp2s0: send auth to <MAC 'ZGQLM' [AC1]> (try 1/3)
[ 4813.545591] wlp2s0: authenticated
[ 4813.548576] wlp2s0: associate with <MAC 'ZGQLM' [AC1]> (try 1/3)
[ 4813.552189] wlp2s0: RX AssocResp from <MAC 'ZGQLM' [AC1]> (capab=0x431 status=0 aid=3)
[ 4813.552300] wlp2s0: associated
[ 4813.594197] ath: EEPROM regdomain: 0x8348
[ 4813.594200] ath: EEPROM indicates we should expect a country code
[ 4813.594202] ath: doing EEPROM country->regdmn map search
[ 4813.594203] ath: country maps to regdmn code: 0x3a
[ 4813.594205] ath: Country alpha2 being used: US
[ 4813.594206] ath: Regpair used: 0x3a
[ 4813.594208] ath: regdomain 0x8348 dynamically updated by country IE
[ 4824.455997] wlp2s0: deauthenticating from <MAC 'ZGQLM' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4825.456740] wlp2s0: authenticate with <MAC 'ZGQLM' [AC1]>
[ 4825.478928] wlp2s0: send auth to <MAC 'ZGQLM' [AC1]> (try 1/3)
[ 4825.480863] wlp2s0: authenticated
[ 4825.483963] wlp2s0: associate with <MAC 'ZGQLM' [AC1]> (try 1/3)
[ 4825.487577] wlp2s0: RX AssocResp from <MAC 'ZGQLM' [AC1]> (capab=0x431 status=0 aid=3)
[ 4825.487698] wlp2s0: associated
[ 4825.522901] ath: EEPROM regdomain: 0x8348
[ 4825.522904] ath: EEPROM indicates we should expect a country code
[ 4825.522905] ath: doing EEPROM country->regdmn map search
[ 4825.522907] ath: country maps to regdmn code: 0x3a
[ 4825.522908] ath: Country alpha2 being used: US
[ 4825.522909] ath: Regpair used: 0x3a
[ 4825.522910] ath: regdomain 0x8348 dynamically updated by country IE
[ 6447.357598] wlp2s0: deauthenticating from <MAC 'ZGQLM' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6448.336855] wlp2s0: authenticate with <MAC 'ZGQLM' [AC1]>
[ 6448.358804] wlp2s0: send auth to <MAC 'ZGQLM' [AC1]> (try 1/3)
[ 6448.360750] wlp2s0: authenticated
[ 6448.364453] wlp2s0: associate with <MAC 'ZGQLM' [AC1]> (try 1/3)
[ 6448.368163] wlp2s0: RX AssocResp from <MAC 'ZGQLM' [AC1]> (capab=0x431 status=0 aid=3)
[ 6448.368275] wlp2s0: associated
[ 6448.389226] ath: EEPROM regdomain: 0x8348
[ 6448.389230] ath: EEPROM indicates we should expect a country code
[ 6448.389232] ath: doing EEPROM country->regdmn map search
[ 6448.389233] ath: country maps to regdmn code: 0x3a
[ 6448.389235] ath: Country alpha2 being used: US
[ 6448.389236] ath: Regpair used: 0x3a
[ 6448.389238] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############



```



[FONT=gotham][FONT=&amp] ---

[/FONT][/FONT]A couple more screenshots
[http://i1232.photobucket.com/albums/ff365/webmanoffesto/WiFi..IPV4..Cropped..800W..v01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/WiFi..IPV4..Cropped..800W..v01.png)
[http://i1232.photobucket.com/albums/ff365/webmanoffesto/WiFi..IPV6..n02..Cropped..800W..v01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/WiFi..IPV6..n02..Cropped..800W..v01.png)

Ubuntu Forums won't let me attach these images because it thinks they are bigger than 1024W, which they are not.
[FONT=gotham]
[/FONT]

---

### Post by webmanoffesto on 2016-09-19
I am now able to surf the net on wired ethernet and on WiFi!
In file /etc/resolvconf/resolv.conf.d/base I added the following entries:
nameserver 8.8.8.8
nameserver 8.8.4.4


I'm thrilled that I was FINALLY able to resolve this problem without resorting to reinstall.

---

### Post by wildmanne39 on 2016-09-19
Glad it worked!
Enjoy!

---

