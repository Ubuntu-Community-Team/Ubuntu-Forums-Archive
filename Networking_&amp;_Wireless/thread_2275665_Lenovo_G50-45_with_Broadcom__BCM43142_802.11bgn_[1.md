---
title: "Lenovo G50-45 with Broadcom  BCM43142 802.11b/g/n [14e4:4365] (rev 01):"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by dreusser on 2015-04-27
I'm running Ubuntu on a Lenovo G50-45. 
1) The wireless usually works fine. 
2) Sometimes, the connection is really slow if the signal is a bit weak. I would need further directions to provide more information on this issue.
3) Sometimes the wl driver produces an error (wl_event_handle Tainted: P) and the network is not available or very slow. 

Output from the wireless-script after a driver error:

```


########## wireless info START ##########

Report from: 27 Apr 2015 21:09 CEST +0200

Booted last: 27 Apr 2015 20:55 CEST +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0621]
    Kernel driver in use: wl

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 105b:e065  
Bus 002 Device 003: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367819  0 
cfg80211              484040  1 wl
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

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
          inet6 addr: fe80::271:ccff:fea2:7989/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1411 errors:0 dropped:0 overruns:0 frame:27450
          TX packets:1688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1173991 (1.1 MB)  TX bytes:210763 (210.7 KB)
          Interrupt:32 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### NetworkManager info ###############

NetworkManager Tool

State: connecting

- Device: wlan0  [EasyBox-25C245] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLAN-FB9538:     Infra, <MAC 'WLAN-FB9538' [AN1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA2
    HP-Print-B4-Officejet Pro 8600: Infra, <MAC 'HP-Print-B4-Officejet Pro 8600' [AN2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA2
    FritzBox!:       Infra, <MAC 'FritzBox!' [AN3]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA2
    DSLWLANModem200: Infra, <MAC 'DSLWLANModem200' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    WLAN-JSY5HP:     Infra, <MAC 'WLAN-JSY5HP' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    WLAN-35AE35:     Infra, <MAC 'WLAN-35AE35' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    HP-Print-80-Officejet Pro 8600: Infra, <MAC 'HP-Print-80-Officejet Pro 8600' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    WLAN-1D2D39:     Infra, <MAC 'WLAN-1D2D39' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    FRITZ!Box 7362 SL: Infra, <MAC 'FRITZ!Box 7362 SL' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    EasyBox-45DE56:  Infra, <MAC 'EasyBox-45DE56' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    DIRECT-Xw-BRAVIA:Infra, <MAC 'DIRECT-Xw-BRAVIA' [AC2]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 39 WPA2
    EasyBox-25C245:  Infra, <MAC 'EasyBox-25C245' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2

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

[[/etc/NetworkManager/system-connections/EasyBox-25C245]] (600 root)
[connection] id=EasyBox-25C245 | type=802-11-wireless
[802-11-wireless] ssid=EasyBox-25C245 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'EasyBox-25C245' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-25C245"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'DIRECT-Xw-BRAVIA' [AC2]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-Xw-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-49-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     DF2576C38AD45205B3556DD
depends:        cfg80211
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

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

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

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
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  664.075028] CPU: 0 PID: 858 Comm: wl_event_handle Tainted: P        WC OX 3.13.0-49-generic #83-Ubuntu
[  664.075169]  [<ffffffffa060c77b>] wl_notify_roaming_status+0xcb/0x150 [wl]
[  664.075218]  [<ffffffffa060b3b2>] wl_event_handler+0x62/0x220 [wl]
[  736.066294] CPU: 0 PID: 858 Comm: wl_event_handle Tainted: P        WC OX 3.13.0-49-generic #83-Ubuntu
[  736.066490]  [<ffffffffa060c77b>] wl_notify_roaming_status+0xcb/0x150 [wl]
[  736.066559]  [<ffffffffa060b3b2>] wl_event_handler+0x62/0x220 [wl]
[  835.427687] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

---

