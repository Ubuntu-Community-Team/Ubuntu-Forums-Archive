---
title: "WiFi for HP 17-y020ca under Ubuntu 16.04 always either disabled or “not ready”"
date: 2016-06-27
forum: Networking &amp; Wireless
---

### Post by Nathaniel_Osgood on 2016-06-27
[COLOR=#111111][FONT=Ubuntu]I recently purchased an HP Notebook 17-y020ca and installed XUbuntu 16.04. This notebook has a Broadcom Corporation BCM43142 wireless card.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This wireless card was not originally detected (but the ethernet card worked fine), and I followed the instructions at:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://askubuntu.com/questions/765584/is-it-possible-to-use-broadcom-bcm43142-wifi-in-ubuntu-16-04](http://askubuntu.com/questions/765584/is-it-possible-to-use-broadcom-bcm43142-wifi-in-ubuntu-16-04)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and now the card appears to be generally detected, and "Enable WiFi" is given as an active (non-greyed-out) option in my Networking menu of the system Panel  in XFCE.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I DO click "Enable WiFi",m this menu often ignores it, but sometimes change the status to indicate that it is enabled via a checkmark next to "Enable WiFi". However, when this happens (i.e., when "Enable WiFi" is checked), one of two things happen further up in the menu. Either it says:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
"Wi-Fi is disabled" 
        or 
"Device not ready"[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I ran the wireless-info.bash script and include below.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I would be truly grateful for any suggestions that anyone could give. I much appreciate your consideration![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]

Sincerely,
 
Nathaniel Osgood

[/FONT][/COLOR]```

########## wireless info START ##########


Report from: 27 Jun 2016 11:59 CST -0600


Booted last: 27 Jun 2016 00:00 CST -0600


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu (from ~/.dmrc)


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    DeviceName: RTL8166 Lan Connection
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:8221]


02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: WLAN Broadcom 43142 bgn 1x1
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]


##### lsusb #############################


Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 05c8:038f Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 0a5c:216d Broadcom Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
hp_wmi                 16384  0
sparse_keymap          16384  2 acer_wmi,hp_wmi
wl                   6365184  0
cfg80211              565248  1 wl
wmi                    20480  2 acer_wmi,hp_wmi
video                  40960  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:634941 (634.9 KB)  TX bytes:364653 (364.6 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:228 


##### iwconfig ##########################


eno1      no wireless extensions.


lo        no wireless extensions.


wlo1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
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


root       793     1  0 11:49 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/eno1
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/wlo1
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
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


##### iw reg get ########################


Region: America/Regina (based on set time zone)


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


eno1      no frequency information.


lo        no frequency information.


wlo1      32 channels in total; available frequencies :
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


wlo1      Interface doesn't support scanning : Network is down


eno1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/4.4.0-21-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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


[   12.989617] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   12.989627] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   13.010399] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.015143] wl: module verification failed: signature and/or required key missing - tainting kernel
[   13.372937] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   14.585653] wl 0000:02:00.0 wlo1: renamed from wlan0
[   15.477355] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   15.483048] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   15.665397] r8169 0000:01:00.0 eno1: link down (repeated 2 times)
[   15.665478] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   17.272949] r8169 0000:01:00.0 eno1: link up
[   17.273002] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[  134.246145] r8169 0000:01:00.0 eno1: link down
[  210.833497] r8169 0000:01:00.0 eno1: link up
[  536.696508] r8169 0000:01:00.0 eno1: link down


########## wireless info END ############



```

---

### Post by Nathaniel_Osgood on 2016-06-27
Thanks to the suggestion of Pilot6 at AskUbuntu ([http://askubuntu.com/questions/792041/wifi-for-hp-17-y020ca-under-ubuntu-16-04-always-either-disabled-or-not-ready](http://askubuntu.com/questions/792041/wifi-for-hp-17-y020ca-under-ubuntu-16-04-always-either-disabled-or-not-ready)), 

I was able to resolve this simply with the following command. 

sudo tee /etc/modprobe.d/blacklist_acer.conf <<< "blacklist acer_wmi"

Thanks so much, Pilot6!

Sincerely,

Nathaniel Osgood

---

