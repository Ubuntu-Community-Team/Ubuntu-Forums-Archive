---
title: "Hp RT5390 Ralink random disconnects."
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by Santiago_Alcala on 2015-05-17
Hello community, I'm getting tired of this. My issue is easy, I get random disconnects and sometimes slow connection with this computer.
I have linux in another PC and I do not have any problem. 
Here with this laptop, I can use Windows with no problem and using an USB Wifi Card works perfectly..
I'm using Mint now, but i had the same problem with ubuntu.

I do not know what to do, tried a lot of guides and I can't find the solution.

```


########## wireless info START ##########


Report from: 17 May 2015 01:18 ART -0300


Booted last: 17 May 2015 01:11 ART -0300


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    LinuxMint
Description:    Linux Mint 17.1 Rebecca
Release:    17.1
Codename:    rebecca


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


default


##### lspci #############################


01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:166d]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 004: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  3 rt2800pci,rt2800usb,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  7 rt2x00pci,rt2x00usb,rt2800lib,rt2800pci,rt2800usb,rt2800mmio,rt2x00mmio
mac80211              630653  4 rt2x00lib,rt2x00pci,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19177  1 hp_wmi


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
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c218:85ff:fe9d:340f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2198811 (2.1 MB)  TX bytes:586958 (586.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"QueHacemoMingoAhora"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'QueHacemoMingoAhora' [AC1]>   
          Bit Rate=90 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


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


- Device: wlan0  [Auto QueHacemoMingoAhora] ------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
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
    *QueHacemoMingoAhora: Infra, <MAC 'QueHacemoMingoAhora' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 61 WPA2


  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             8.8.8.8
    DNS:             8.8.8.4


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


[[/etc/NetworkManager/system-connections/Auto QueHacemoMingoAhora]] (600 root)
[connection] id=Auto QueHacemoMingoAhora | type=802-11-wireless
[802-11-wireless] ssid=QueHacemoMingoAhora | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Auto FIRPO WiFi]] (600 root)
[connection] id=Auto FIRPO WiFi | type=802-11-wireless
[802-11-wireless] ssid=FIRPO WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto QueHacemoMingoAhora-a7bdba71-36bf-4bf6-b190-40eb8ff479fe]] (600 root)
[connection] id=Auto QueHacemoMingoAhora | type=802-11-wireless
[802-11-wireless] ssid=QueHacemoMingoAhora | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'QueHacemoMingoAhora' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"QueHacemoMingoAhora"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c175f11a
                    Extra: Last beacon: 12860ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     98B048D64D7288E7C870495
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1C7B3D09AA920FB776204BA
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[rt2800pci]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AF1E5AA2D7E623CCBA9A1CD
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AA2C68A3C0E9D5BDA2B36E9
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7A7EEDE3C2270AE56EB54F8
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[rt2x00pci]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     47F0A082BE7F0118126DD77
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[rt2x00mmio]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D5F2B94A767BFCDB29314F2
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9BB2D2E4429AB671216A29
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
nohwcrypt: N


[rt2800pci]
nohwcrypt: Y


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


lp
rtc
rt5290sta


##### modprobe options ##################


[/etc/modprobe.d/asus_nb.conf]
options asus_nb_wmi wapf=4


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


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x5390 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   15.314720] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   15.357396] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   15.479571] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   15.792387] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   15.802125] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   16.178554] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[   18.482660] wlan0: authenticate with <MAC 'QueHacemoMingoAhora' [AC1]>
[   18.498968] wlan0: send auth to <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   18.500390] wlan0: authenticated
[   18.501996] wlan0: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   18.505781] wlan0: RX AssocResp from <MAC 'QueHacemoMingoAhora' [AC1]> (capab=0x431 status=0 aid=5)
[   18.505947] wlan0: associated
[   18.505994] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.574216] wlan0: deauthenticating from <MAC 'QueHacemoMingoAhora' [AC1]> by local choice (reason=2)
[   18.600812] wlan0: authenticate with <MAC 'QueHacemoMingoAhora' [AC1]>
[   18.610547] wlan0: send auth to <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   18.612578] wlan0: authenticated
[   18.614312] wlan0: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   18.619811] wlan0: RX AssocResp from <MAC 'QueHacemoMingoAhora' [AC1]> (capab=0x431 status=0 aid=5)
[   18.619936] wlan0: associated
[   19.034718] wlan1: authenticate with <MAC 'QueHacemoMingoAhora' [AC1]>
[   19.085965] wlan1: send auth to <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   19.087406] wlan1: authenticated
[   19.090555] wlan1: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   19.094612] wlan1: RX AssocResp from <MAC 'QueHacemoMingoAhora' [AC1]> (capab=0x431 status=0 aid=6)
[   19.101902] wlan1: associated
[   19.101999] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   19.111147] wlan1: deauthenticating from <MAC 'QueHacemoMingoAhora' [AC1]> by local choice (reason=2)
[   19.165811] wlan1: authenticate with <MAC 'QueHacemoMingoAhora' [AC1]>
[   19.196193] wlan1: send auth to <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   19.197652] wlan1: authenticated
[   19.198680] wlan1: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   19.202575] wlan1: RX AssocResp from <MAC 'QueHacemoMingoAhora' [AC1]> (capab=0x431 status=0 aid=6)
[   19.209504] wlan1: associated
[   50.419162] ieee80211 phy1: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19
[   52.020704] ieee80211 phy1: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[   52.032732] wlan1: deauthenticating from <MAC 'QueHacemoMingoAhora' [AC1]> by local choice (reason=3)
[   60.836085] wlan0: deauthenticating from <MAC 'QueHacemoMingoAhora' [AC1]> by local choice (reason=3)
[   61.084340] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   64.080014] wlan0: authenticate with <MAC 'QueHacemoMingoAhora' [AC1]>
[   64.095646] wlan0: send auth to <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   64.097119] wlan0: authenticated
[   64.099212] wlan0: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   64.203444] wlan0: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 2/3)
[   64.307645] wlan0: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 3/3)
[   64.411804] wlan0: association with <MAC 'QueHacemoMingoAhora' [AC1]> timed out
[   64.456329] wlan0: authenticate with <MAC 'QueHacemoMingoAhora' [AC1]>
[   64.464273] wlan0: send auth to <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   64.465804] wlan0: authenticated
[   64.467850] wlan0: associate with <MAC 'QueHacemoMingoAhora' [AC1]> (try 1/3)
[   64.477710] wlan0: RX AssocResp from <MAC 'QueHacemoMingoAhora' [AC1]> (capab=0x431 status=0 aid=5)
[   64.477858] wlan0: associated
[   64.477880] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```



There is my wireless info

Thanks! and Forgive me about my english, I'm hispanic.

---

### Post by Santiago_Alcala on 2015-05-18
Up?
Someone? Please!

---

### Post by Vladlenin5000 on 2015-05-18
Hi and welcome.

Do you have your system updated? If not that's the first thing to do:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You probably should do it with an alternative internet connection, wired or with the USB dongle you mentioned. Reboot and test again. If the symptom persists then the often recommended troubleshooting step is to disable "hardware encryption":
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```

The first one remove the driver and the second reloads it with the intended parameter. Do NOT reboot. This is only temporary and won't survive a reboot. Test it thoroughly for several hours. If it improves then it can be made permanent.

---

### Post by Santiago_Alcala on 2015-05-19
I'm still having the same problem...
I prove those two methods and didn't work properly...

I don't know what else to do :(

---

### Post by Santiago_Alcala on 2015-05-22
BUMP, Please!

---

### Post by Vladlenin5000 on 2015-05-22
It seems you need a 'real' doctor (@chili555), not a wannabe like me. :oops:

---

### Post by Hadaka on 2015-05-22
Hi, please COPY and paste one line at a time...
```
sudo modprobe -rf rt2800pci
echo 'options rt2800pci nohwcrypt=1' | sudo tee -a /etc/modprobe.d/rt2800pci.conf
sudo modpobe rt2800pci
sudo iw reg set AR
sudo sed -i 's/^REG.*=$/&AR/' /etc/default/crda
```
boot
test and report back please
thanks

---

