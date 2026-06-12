---
title: "Wifi Realtek rtl8723bu unable to connect to Airport Express - Ubuntu 18.04.2 LTS"
date: 2019-05-09
forum: Networking &amp; Wireless
---

### Post by dutohubohu on 2019-05-09
Hello everyone,

I can't connect my computer to an Apple Airport Express ([1st generation A1264]("https://support.apple.com/kb/SP1?locale=en_US"), up-to-date firmware v7.6.9). The Airport Express is connected to an Arris cable modem SB6121.

The computer is a dual boot Ubuntu 18.04/Windows 10. I installed the rtl8723bu driver found on [Larry Finger Github]("https://github.com/lwfinger/rtl8723bu") and I've never experienced any wifi connection problem until now. Bluetooth works too.

Here is what I can tell:
- Connection to the AE works under W10
- Connection to the AE works under Ubuntu through another computer acting as a hotspot/wifi repeater
- Direct connection to the AE does not work, authentication prompt keeps coming up

The AE SSID is 'Caramba'. Below is the wireless-info output:
```

########## wireless info START ##########
Report from: 09 May 2019 00:17 EDT -0400

Booted last: 09 May 2019 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-47-generic #50-Ubuntu SMP Wed Mar 13 10:44:52 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 093a:733a Pixart Imaging, Inc. 
Bus 001 Device 003: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

cfg80211              622592  1 8723bu

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlx<IF from MAC [IF1]>: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF1]>' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

wlx<IF from MAC [IF1]>  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       860     1  0 00:08 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF1]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8723bu
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/usb1/1-7/1-7:1.2/net/wlx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{21,8}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fbe670f7-0828-4bf6-842c-2853394aec27 | Hotspot
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   620bf623-2e2b-461c-adf3-011cd7812846 | Caramba

SSID              BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Caramba           <MAC 'Caramba' [AC3]>  Infra  6     2437 MHz  130 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       no             
CO2               <MAC 'CO2' [AC4]>  Infra  6     2437 MHz  130 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no             
ATT4Keu9s2        <MAC 'ATT4Keu9s2' [AC7]>  Infra  11    2462 MHz  130 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no             
missroger         <MAC 'missroger' [AC6]>  Infra  11    2462 MHz  130 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
NETGEAR21         <MAC 'NETGEAR21' [AC1]>  Infra  1     2412 MHz  130 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no             
@BTSF             <MAC '@BTSF' [AC5]>  Infra  6     2437 MHz  130 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no             
HOME-F561-2.4     <MAC 'HOME-F561-2.4' [AN7]>  Infra  6     2437 MHz  195 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no             
$29.99 per month  <MAC '$29.99 per month' [AC2]>  Infra  2     2417 MHz  540 Mbit/s  49      &#9602;&#9604;__  WPA2       no             

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Vinology Public Wi-Fi]] (600 root)
[connection] id=Vinology Public Wi-Fi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Vinology Public Wi-Fi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/03ca82]] (600 root)
[connection] id=03ca82 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=03ca82
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone]] (600 root)
[connection] id=iPhone | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=iPhone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FlixBus]] (600 root)
[connection] id=FlixBus | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=FlixBus
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_SNCF_WIFI_INTERCITES]] (600 root)
[connection] id=_SNCF_WIFI_INTERCITES | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=_SNCF_WIFI_INTERCITES
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/lag-public]] (600 root)
[connection] id=lag-public | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=lag-public
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bbox-CC339556]] (600 root)
[connection] id=Bbox-CC339556 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Bbox-CC339556
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wifi Ouibus]] (600 root)
[connection] id=wifi Ouibus | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=wifi Ouibus
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Caramba]] (600 root)
[connection] id=Caramba | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Caramba
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/46EE6E]] (600 root)
[connection] id=46EE6E | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=46EE6E
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ifyouregonnaaskitsthisone]] (600 root)
[connection] id=ifyouregonnaaskitsthisone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=ifyouregonnaaskitsthisone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/freebox_ADF3D3]] (600 root)
[connection] id=freebox_ADF3D3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=freebox_ADF3D3
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SFR-9158]] (600 root)
[connection] id=SFR-9158 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=SFR-9158
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Teaspressa Guest]] (600 root)
[connection] id=Teaspressa Guest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Teaspressa Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ERC COLD BREW ROCKS Secure]] (600 root)
[connection] id=ERC COLD BREW ROCKS Secure | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=ERC COLD BREW ROCKS Secure
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DESKTOP-8FS5E46 1834]] (600 root)
[connection] id=DESKTOP-8FS5E46 1834 | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=DESKTOP-8FS5E46 1834
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ERC COLD BREW ROCKS ]] (600 root)
[connection] id=ERC COLD BREW ROCKS  | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=ERC COLD BREW ROCKS 
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/teabiz]] (600 root)
[connection] id=teabiz | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=teabiz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sweetwaters Downtown]] (600 root)
[connection] id=Sweetwaters Downtown | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Sweetwaters Downtown
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CrazyWisdomNetwork]] (600 root)
[connection] id=CrazyWisdomNetwork | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=CrazyWisdomNetwork
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-A88C]] (600 root)
[connection] id=Livebox-A88C | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=Livebox-A88C
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=raphpc
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PANERA]] (600 root)
[connection] id=PANERA | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF1]>' [IF1]> | mac-address-blacklist= | ssid=PANERA
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlx<IF from MAC [IF1]>  13 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF1]>  Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR21' [AC1]>
                    ESSID:"NETGEAR21"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=64/100  
                    Extra:fm=0003
          Cell 02 - Address: <MAC '$29.99 per month' [AC2]>
                    ESSID:"$29.99 per month"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=11/100  Signal level=46/100  
                    Extra:fm=0001
          Cell 03 - Address: <MAC 'Caramba' [AC3]>
                    ESSID:"Caramba"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=100/100  
                    Extra:fm=0003
          Cell 04 - Address: <MAC 'CO2' [AC4]>
                    ESSID:"CO2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=76/100  
                    Extra:fm=0003
          Cell 05 - Address: <MAC '@BTSF' [AC5]>
                    ESSID:"@BTSF"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=56/100  
                    Extra:fm=0001
          Cell 06 - Address: <MAC 'missroger' [AC6]>
                    ESSID:"missroger"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=70/100  
                    Extra:fm=0003
          Cell 07 - Address: <MAC 'ATT4Keu9s2' [AC7]>
                    ESSID:"ATT4Keu9s2"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=72/100  
                    Extra:fm=0003

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-47-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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
blacklist rtl8xxxu

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  198.010303] RTL871X: rtw_set_802_11_connect(wlx<IF from MAC [IF1]>)  fw_state=0x00000008 (repeated 4 times)
[  220.613669] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF1]>: link is not ready

########## wireless info END ############

```

Do you guys have any idea of where the problem may come from please?

Thanks a lot!

---

### Post by dutohubohu on 2019-05-09
Also here are some logs from dmesg and /var/log/syslog:

An extract from /var/log/syslog:
```
May  9 00:28:11 dutohubohupc kernel: [  138.562465] RTL871X: RTW_ADAPTIVITY_EN_May  9 00:28:11 dutohubohupc kernel: [  138.562471] AUTO, chplan:0x20, Regulation:0,0
May  9 00:28:11 dutohubohupc kernel: [  138.562472] RTL871X: RTW_ADAPTIVITY_MODE_
May  9 00:28:11 dutohubohupc kernel: [  138.562473] NORMAL
May  9 00:28:12 dutohubohupc kernel: [  139.167309] RTL871X: nolinked power save leave
May  9 00:28:14 dutohubohupc kernel: [  141.289109] RTL871X: nolinked power save enter
May  9 00:27:59 dutohubohupc gnome-software[1746]: message repeated 3 times: [ Failed to load snap icon: local snap has no icon]
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5619] device (wlxXXXXXXXXXXXX): Activation: starting connection 'Caramba' (620bf623-2e2b-461c-adf3-011cd7812846)
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5639] audit: op="connection-activate" uuid="620bf623-2e2b-461c-adf3-011cd7812846" name="Caramba" pid=1368 uid=1000 result="success"
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5643] device (wlxXXXXXXXXXXXX): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5646] manager: NetworkManager state is now CONNECTING
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5655] device (wlxXXXXXXXXXXXX): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5659] device (wlxXXXXXXXXXXXX): Activation: (wifi) access point 'Caramba' has security, but secrets are required.
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5659] device (wlxXXXXXXXXXXXX): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5735] device (wlxXXXXXXXXXXXX): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5742] device (wlxXXXXXXXXXXXX): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5746] device (wlxXXXXXXXXXXXX): Activation: (wifi) connection 'Caramba' has security, and secrets exist.  No new secrets needed.
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5747] Config: added 'ssid' value 'Caramba'
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5747] Config: added 'scan_ssid' value '1'
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5747] Config: added 'bgscan' value 'simple:30:-80:86400'
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5748] Config: added 'key_mgmt' value 'WPA-PSK'
May  9 00:28:15 dutohubohupc NetworkManager[835]: <info>  [1557376095.5748] Config: added 'psk' value '<hidden>'
May  9 00:28:15 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: Trying to associate with 00:25:XXXXX:a0:f5 (SSID='Caramba' freq=2437 MHz)
May  9 00:28:15 dutohubohupc gnome-shell[1368]: Object St.Widget (0x5597de46f3d0), has been already deallocated - impossible to access it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: == Stack trace for context 0x5597dc866320 ==
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #0 0x5597dcbf6408 i   resource:///org/gnome/shell/ui/modalDialog.js:93 (0x7f7dfc0f14d8 @ 22)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #1 0x7ffced57d050 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f7dfc0b5de0 @ 71)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #2 0x5597dcbf6350 i   resource:///org/gnome/gjs/modules/_legacy.js:39 (0x7f7dfc0b5b38 @ 215)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #3 0x5597dcbf62c0 i   resource:///org/gnome/shell/ui/status/network.js:781 (0x7f7dd80166f8 @ 409)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #4 0x7ffced57e3c0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f7dfc0b5de0 @ 71)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #5 0x5597dcbf6238 i   resource:///org/gnome/shell/ui/modalDialog.js:168 (0x7f7dfc0f1a28 @ 92)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #6 0x7ffced57efa0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f7dfc0b5de0 @ 71)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #7 0x7ffced57f730 b   self-hosted:914 (0x7f7dfc0f12b8 @ 346)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #8 0x7ffced5806a0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (0x7f7dfc0d2b38 @ 54)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #9 0x7ffced5807f0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:337 (0x7f7dfc0d2bc0 @ 1626)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #10 0x7ffced5808a0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:350 (0x7f7dfc0d2c48 @ 100)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #11 0x5597dcbf61c0 i   resource:///org/gnome/gjs/modules/tweener/tweener.js:365 (0x7f7dfc0d2cd0 @ 10)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #12 0x7ffced581c20 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f7dfc0d2230 @ 386)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #13 0x5597dcbf6130 i   resource:///org/gnome/shell/ui/tweener.js:244 (0x7f7dfc0cf808 @ 159)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #14 0x7ffced582870 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f7dfc0b5de0 @ 71)
May  9 00:28:15 dutohubohupc org.gnome.Shell.desktop[1368]: #15 0x5597dcbf60b0 i   resource:///org/gnome/shell/ui/tweener.js:219 (0x7f7dfc0cf780 @ 15)
May  9 00:28:15 dutohubohupc gnome-shell[1368]: clutter_actor_destroy: assertion 'CLUTTER_IS_ACTOR (self)' failed
May  9 00:28:16 dutohubohupc kernel: [  143.115115] RTL871X: RTW_ADAPTIVITY_EN_
May  9 00:28:16 dutohubohupc kernel: [  143.115121] AUTO, chplan:0x20, Regulation:0,0
May  9 00:28:16 dutohubohupc kernel: [  143.115122] RTL871X: RTW_ADAPTIVITY_MODE_
May  9 00:28:16 dutohubohupc kernel: [  143.115123] NORMAL
May  9 00:28:16 dutohubohupc kernel: [  143.628864] RTL871X: nolinked power save leave
May  9 00:28:16 dutohubohupc kernel: [  143.838300] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
May  9 00:28:16 dutohubohupc NetworkManager[835]: <info>  [1557376096.9754] device (wlxXXXXXXXXXXXX): supplicant interface state: ready -> associating
May  9 00:28:17 dutohubohupc kernel: [  143.865639] RTL871X: start auth
May  9 00:28:17 dutohubohupc kernel: [  143.867089] RTL871X: auth success, start assoc
May  9 00:28:18 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:18 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:18 dutohubohupc NetworkManager[835]: <info>  [1557376098.6102] device (wlxXXXXXXXXXXXX): supplicant interface state: associating -> disconnected
May  9 00:28:18 dutohubohupc NetworkManager[835]: <info>  [1557376098.7148] device (wlxXXXXXXXXXXXX): supplicant interface state: disconnected -> scanning
May  9 00:28:20 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: Trying to associate with 00:25:XXXXX:a0:f5 (SSID='Caramba' freq=2437 MHz)
May  9 00:28:20 dutohubohupc kernel: [  147.183682] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
May  9 00:28:20 dutohubohupc NetworkManager[835]: <info>  [1557376100.3233] device (wlxXXXXXXXXXXXX): supplicant interface state: scanning -> associating
May  9 00:28:20 dutohubohupc kernel: [  147.449641] RTL871X: start auth
May  9 00:28:20 dutohubohupc kernel: [  147.452144] RTL871X: auth success, start assoc
May  9 00:28:22 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:22 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:22 dutohubohupc NetworkManager[835]: <info>  [1557376102.1945] device (wlxXXXXXXXXXXXX): supplicant interface state: associating -> disconnected
May  9 00:28:22 dutohubohupc NetworkManager[835]: <info>  [1557376102.6993] device (wlxXXXXXXXXXXXX): supplicant interface state: disconnected -> scanning
May  9 00:28:23 dutohubohupc systemd[1]: Starting Stop ureadahead data collection...
May  9 00:28:23 dutohubohupc systemd[1]: Started Stop ureadahead data collection.
May  9 00:28:24 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: Trying to associate with 00:25:XXXXX:a0:f5 (SSID='Caramba' freq=2437 MHz)
May  9 00:28:24 dutohubohupc kernel: [  151.070251] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
May  9 00:28:24 dutohubohupc NetworkManager[835]: <info>  [1557376104.2077] device (wlxXXXXXXXXXXXX): supplicant interface state: scanning -> associating
May  9 00:28:24 dutohubohupc kernel: [  151.340819] RTL871X: start auth
May  9 00:28:24 dutohubohupc kernel: [  151.343252] RTL871X: auth success, start assoc
May  9 00:28:26 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:26 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:26 dutohubohupc NetworkManager[835]: <info>  [1557376106.0658] device (wlxXXXXXXXXXXXX): supplicant interface state: associating -> disconnected
May  9 00:28:27 dutohubohupc NetworkManager[835]: <info>  [1557376107.0720] device (wlxXXXXXXXXXXXX): supplicant interface state: disconnected -> scanning
May  9 00:28:28 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: Trying to associate with 00:25:XXXXX:a0:f5 (SSID='Caramba' freq=2437 MHz)
May  9 00:28:28 dutohubohupc kernel: [  155.399419] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
May  9 00:28:28 dutohubohupc NetworkManager[835]: <info>  [1557376108.5410] device (wlxXXXXXXXXXXXX): supplicant interface state: scanning -> associating
May  9 00:28:28 dutohubohupc kernel: [  155.641611] RTL871X: start auth
May  9 00:28:28 dutohubohupc kernel: [  155.643830] RTL871X: auth success, start assoc
May  9 00:28:30 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:30 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Caramba" auth_failures=1 duration=10 reason=CONN_FAILED
May  9 00:28:30 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-ASSOC-REJECT status_code=1
May  9 00:28:30 dutohubohupc NetworkManager[835]: <info>  [1557376110.3856] device (wlxXXXXXXXXXXXX): supplicant interface state: associating -> disconnected
May  9 00:28:34 dutohubohupc kernel: [  161.660997] RTL871X: nolinked power save enter
May  9 00:28:36 dutohubohupc kernel: [  162.919041] RTL871X: RTW_ADAPTIVITY_EN_
May  9 00:28:36 dutohubohupc kernel: [  162.919047] AUTO, chplan:0x20, Regulation:0,0
May  9 00:28:36 dutohubohupc kernel: [  162.919048] RTL871X: RTW_ADAPTIVITY_MODE_
May  9 00:28:36 dutohubohupc kernel: [  162.919049] NORMAL
May  9 00:28:36 dutohubohupc kernel: [  163.432912] RTL871X: nolinked power save leave
May  9 00:28:36 dutohubohupc NetworkManager[835]: <info>  [1557376116.7790] device (wlxXXXXXXXXXXXX): supplicant interface state: disconnected -> scanning
May  9 00:28:38 dutohubohupc kernel: [  165.312626] RTL871X: nolinked power save enter
May  9 00:28:40 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-SSID-REENABLED id=0 ssid="Caramba"
May  9 00:28:40 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: Trying to associate with 00:25:XXXXX:a0:f5 (SSID='Caramba' freq=2437 MHz)
May  9 00:28:41 dutohubohupc kernel: [  167.967196] RTL871X: RTW_ADAPTIVITY_EN_
May  9 00:28:41 dutohubohupc kernel: [  167.967202] AUTO, chplan:0x20, Regulation:0,0
May  9 00:28:41 dutohubohupc kernel: [  167.967203] RTL871X: RTW_ADAPTIVITY_MODE_
May  9 00:28:41 dutohubohupc kernel: [  167.967204] NORMAL
May  9 00:28:41 dutohubohupc NetworkManager[835]: <warn>  [1557376121.1364] device (wlxXXXXXXXXXXXX): Activation: (wifi) association took too long
May  9 00:28:41 dutohubohupc NetworkManager[835]: <info>  [1557376121.1365] device (wlxXXXXXXXXXXXX): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
May  9 00:28:41 dutohubohupc NetworkManager[835]: <warn>  [1557376121.1384] device (wlxXXXXXXXXXXXX): Activation: (wifi) asking for new secrets
May  9 00:28:41 dutohubohupc kernel: [  168.552839] RTL871X: nolinked power save leave
May  9 00:28:41 dutohubohupc kernel: [  168.762395] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
May  9 00:28:41 dutohubohupc NetworkManager[835]: <info>  [1557376121.8992] device (wlxXXXXXXXXXXXX): supplicant interface state: scanning -> associating
May  9 00:28:41 dutohubohupc wpa_supplicant[839]: wlxXXXXXXXXXXXX: CTRL-EVENT-DISCONNECTED bssid=00:25:XXXXX:a0:f5 reason=3 locally_generated=1
May  9 00:28:41 dutohubohupc NetworkManager[835]: <warn>  [1557376121.9073] sup-iface[0x56093b3f6a40,wlxXXXXXXXXXXXX]: connection disconnected (reason -3)
May  9 00:28:41 dutohubohupc NetworkManager[835]: <info>  [1557376121.9076] device (wlxXXXXXXXXXXXX): supplicant interface state: associating -> disconnected
May  9 00:28:43 dutohubohupc NetworkManager[835]: <warn>  [1557376123.4366] device (wlxXXXXXXXXXXXX): User canceled the secrets request.
May  9 00:28:43 dutohubohupc NetworkManager[835]: <info>  [1557376123.4368] device (wlxXXXXXXXXXXXX): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
May  9 00:28:43 dutohubohupc NetworkManager[835]: <info>  [1557376123.4374] manager: NetworkManager state is now DISCONNECTED
May  9 00:28:43 dutohubohupc NetworkManager[835]: <warn>  [1557376123.4383] device (wlxXXXXXXXXXXXX): Activation: failed for connection 'Caramba'
May  9 00:28:43 dutohubohupc NetworkManager[835]: <info>  [1557376123.4399] device (wlxXXXXXXXXXXXX): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
May  9 00:28:43 dutohubohupc kernel: [  170.305567] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
May  9 00:28:43 dutohubohupc gnome-shell[980]: An active wireless connection, in infrastructure mode, involves no access point?
May  9 00:28:43 dutohubohupc gnome-shell[1368]: An active wireless connection, in infrastructure mode, involves no access point?
May  9 00:28:45 dutohubohupc kernel: [  171.989534] RTL871X: nolinked power save enter
May  9 00:28:47 dutohubohupc kernel: [  174.671245] RTL871X: RTW_ADAPTIVITY_EN_
May  9 00:28:47 dutohubohupc kernel: [  174.671251] AUTO, chplan:0x20, Regulation:0,0
May  9 00:28:47 dutohubohupc kernel: [  174.671252] RTL871X: RTW_ADAPTIVITY_MODE_
May  9 00:28:47 dutohubohupc kernel: [  174.671253] NORMAL
```

And an extract from dmesg:
```
[    5.712335] Bluetooth: Core ver 2.22[    5.712365] NET: Registered protocol family 31
[    5.712366] Bluetooth: HCI device and connection manager initialized
[    5.712373] Bluetooth: HCI socket layer initialized
[    5.712376] Bluetooth: L2CAP socket layer initialized
[    5.712383] Bluetooth: SCO socket layer initialized
[    5.713994] Linux video capture interface: v2.00
[    5.722466] usbcore: registered new interface driver btusb
[    5.723717] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[    5.723722] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[    5.728652] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[    5.728659] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[    5.745707] Bluetooth: hci0: rom_version status=0 version=1
[    5.745723] Bluetooth: hci0: cfg_sz 0, total size 22496
[    5.752726] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    5.756754] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    5.770160] uvcvideo: Found UVC 1.00 device VGA Webcam (093a:733a)
[    5.783394] uvcvideo 1-8:1.0: Entity type for entity Extension 4 was not initialized!
[    5.783398] uvcvideo 1-8:1.0: Entity type for entity Processing 3 was not initialized!
[    5.783400] uvcvideo 1-8:1.0: Entity type for entity Camera 1 was not initialized!
[    5.783508] input: VGA Webcam: VGA Webcam as /devices/pci0000:00/0000:00:15.0/usb1/1-8/1-8:1.0/input/input8
[    5.783941] usbcore: registered new interface driver uvcvideo
[    5.783942] USB Video Class driver (1.1.1)
[    5.790598] PKCS#7 signature not signed with a trusted key
[    5.790628] 8723bu: loading out-of-tree module taints kernel.
[    5.791353] 8723bu: module verification failed: signature and/or required key missing - tainting kernel
[    5.794237] RTL871X: module init start
[    5.794241] RTL871X: rtl8723bu v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
[    5.794242] RTL871X: rtl8723bu BT-Coex version = BTCOEX20140507-4E40
[    5.844867] RTL871X: rtw_ndev_init(wlan0)
[    5.846107] usbcore: registered new interface driver rtl8723bu
[    5.846109] RTL871X: module init ret=0
[    5.911199] snd_hda_intel 0000:00:0e.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.911949] idma64 idma64.5: Found Intel integrated DMA 64-bit
[    5.919646] idma64 idma64.6: Found Intel integrated DMA 64-bit
[    5.926199] idma64 idma64.7: Found Intel integrated DMA 64-bit
[    5.932977] idma64 idma64.8: Found Intel integrated DMA 64-bit
[    5.933541] idma64 idma64.9: Found Intel integrated DMA 64-bit
[    5.934677] idma64 idma64.12: Found Intel integrated DMA 64-bit
[    5.935199] idma64 idma64.13: Found Intel integrated DMA 64-bit
[    5.935680] idma64 idma64.14: Found Intel integrated DMA 64-bit
[    5.957990] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC269VC: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    5.957994] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.957997] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[    5.957999] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    5.958000] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    5.958003] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x19
[    5.958005] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[    5.981102] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:0e.0/sound/card0/input9
[    5.981201] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:0e.0/sound/card0/input10
[    5.981281] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0e.0/sound/card0/input11
[    5.981360] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0e.0/sound/card0/input12
[    5.981437] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:0e.0/sound/card0/input13
[    5.981515] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:0e.0/sound/card0/input14
[    5.981588] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:0e.0/sound/card0/input15
[    6.030303] RAPL PMU: API unit is 2^-32 Joules, 4 fixed counters, 655360 ms ovfl timer
[    6.030306] RAPL PMU: hw unit of domain pp0-core 2^-14 Joules
[    6.030306] RAPL PMU: hw unit of domain package 2^-14 Joules
[    6.030307] RAPL PMU: hw unit of domain dram 2^-14 Joules
[    6.030308] RAPL PMU: hw unit of domain pp1-gpu 2^-14 Joules
[    6.063620] SSE version of gcm_enc/dec engaged.
[    6.236835] fbcon: inteldrmfb (fb0) is primary device
[    6.236978] Console: switching to colour frame buffer device 240x67
[    6.237027] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    6.237302] EDAC pnd2: b_cr_tolud_pci=080000001 ret=0
[    6.237346] EDAC pnd2: b_cr_touud_lo_pci=080000000 ret=0
[    6.237388] EDAC pnd2: b_cr_touud_hi_pci=000000001 ret=0
[    6.237429] EDAC pnd2: b_cr_asym_mem_region0_mchbar=000000000 ret=0
[    6.237470] EDAC pnd2: b_cr_asym_mem_region1_mchbar=000000000 ret=0
[    6.237512] EDAC pnd2: b_cr_mot_out_base_mchbar=000000000 ret=0
[    6.237553] EDAC pnd2: b_cr_mot_out_mask_mchbar=000000000 ret=0
[    6.237635] EDAC pnd2: b_cr_slice_channel_hash=80000dbc00000244 ret=0
[    6.237676] EDAC pnd2: b_cr_asym_2way_mem_region_mchbar=000000000 ret=0
[    6.237718] EDAC pnd2: d_cr_drp0=01048c0a1 ret=0
[    6.237760] EDAC pnd2: d_cr_drp0=01048c0a1 ret=0
[    6.237802] EDAC pnd2: d_cr_drp0=01048c0a1 ret=0
[    6.237844] EDAC pnd2: d_cr_drp0=01048c0a1 ret=0
[    6.237845] EDAC pnd2: Unsupported DIMM in channel 0
[    6.237846] EDAC pnd2: Unsupported DIMM in channel 1
[    6.237847] EDAC pnd2: Unsupported DIMM in channel 2
[    6.237848] EDAC pnd2: Unsupported DIMM in channel 3
[    6.237849] EDAC pnd2: Failed to register device with error -22.
[    6.276330] intel_telemetry_core Init
[    6.286128] intel_rapl: Found RAPL domain package
[    6.286132] intel_rapl: Found RAPL domain core
[    6.286134] intel_rapl: Found RAPL domain uncore
[    6.286137] intel_rapl: Found RAPL domain dram
[    6.589461] input: SYNA3602:00 0911:5288 Touchpad as /devices/pci0000:00/0000:00:16.2/i2c_designware.2/i2c-2/i2c-SYNA3602:00/0018:0911:5288.0001/input/input17
[    6.592326] hid-multitouch 0018:0911:5288.0001: input,hidraw0: I2C HID v1.00 Mouse [SYNA3602:00 0911:5288] on i2c-SYNA3602:00
[    6.601106] rtl8723bu 1-7:1.2 wlxXXXXXXXXXXXX: renamed from wlan0
[    6.755601] dw-apb-uart.8: ttyS4 at MMIO 0x82124000 (irq = 4, base_baud = 115200) is a 16550A
[    6.816296] [drm] RC6 on
[    6.884319] dw-apb-uart.9: ttyS5 at MMIO 0x82122000 (irq = 5, base_baud = 115200) is a 16550A
[    7.012372] dw-apb-uart.10: ttyS6 at MMIO 0x80008000 (irq = 6, base_baud = 115200) is a 16550A
[    7.140443] dw-apb-uart.11: ttyS7 at MMIO 0x82120000 (irq = 7, base_baud = 115200) is a 16550A
[    8.624880] audit: type=1400 audit(1557374900.771:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=795 comm="apparmor_parser"
[    8.624889] audit: type=1400 audit(1557374900.771:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=795 comm="apparmor_parser"
[    8.624893] audit: type=1400 audit(1557374900.771:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=795 comm="apparmor_parser"
[    8.625219] audit: type=1400 audit(1557374900.771:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=796 comm="apparmor_parser"
[    8.625783] audit: type=1400 audit(1557374900.771:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=792 comm="apparmor_parser"
[    8.625789] audit: type=1400 audit(1557374900.771:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=792 comm="apparmor_parser"
[    8.625792] audit: type=1400 audit(1557374900.771:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=792 comm="apparmor_parser"
[    8.625796] audit: type=1400 audit(1557374900.771:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=792 comm="apparmor_parser"
[    8.626499] audit: type=1400 audit(1557374900.771:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=797 comm="apparmor_parser"
[    8.627667] audit: type=1400 audit(1557374900.771:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=799 comm="apparmor_parser"
[    8.740042] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.740045] Bluetooth: BNEP filters: protocol multicast
[    8.740052] Bluetooth: BNEP socket layer initialized
[    9.683469] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[   10.354031] RTL871X: RTW_ADAPTIVITY_EN_
[   10.354037] AUTO, chplan:0x20, Regulation:0,0
[   10.354038] RTL871X: RTW_ADAPTIVITY_MODE_
[   10.354039] NORMAL
[   10.922072] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[   11.092722] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[   13.745420] RTL871X: nolinked power save enter
[   14.658484] RTL871X: RTW_ADAPTIVITY_EN_
[   14.658491] AUTO, chplan:0x20, Regulation:0,0
[   14.658492] RTL871X: RTW_ADAPTIVITY_MODE_
[   14.658493] NORMAL
[   15.261401] RTL871X: nolinked power save leave
[   17.382521] RTL871X: nolinked power save enter
[   37.682494] RTL871X: RTW_ADAPTIVITY_EN_
[   37.682500] AUTO, chplan:0x20, Regulation:0,0
[   37.682501] RTL871X: RTW_ADAPTIVITY_MODE_
[   37.682501] NORMAL
[   38.280877] RTL871X: nolinked power save leave
[   40.160922] RTL871X: nolinked power save enter
[   55.138615] Bluetooth: RFCOMM TTY layer initialized
[   55.138631] Bluetooth: RFCOMM socket layer initialized
[   55.138641] Bluetooth: RFCOMM ver 1.11
[   57.820514] rfkill: input handler disabled
[   70.658783] RTL871X: RTW_ADAPTIVITY_EN_
[   70.658789] AUTO, chplan:0x20, Regulation:0,0
[   70.658790] RTL871X: RTW_ADAPTIVITY_MODE_
[   70.658790] NORMAL
[   71.168818] RTL871X: nolinked power save leave
[   73.291306] RTL871X: nolinked power save enter
[  113.675810] RTL871X: RTW_ADAPTIVITY_EN_
[  113.675816] AUTO, chplan:0x20, Regulation:0,0
[  113.675817] RTL871X: RTW_ADAPTIVITY_MODE_
[  113.675818] NORMAL
[  114.189210] RTL871X: nolinked power save leave
[  116.068794] RTL871X: nolinked power save enter
[  166.714411] RTL871X: RTW_ADAPTIVITY_EN_
[  166.714416] AUTO, chplan:0x20, Regulation:0,0
[  166.714417] RTL871X: RTW_ADAPTIVITY_MODE_
[  166.714418] NORMAL
[  167.292814] RTL871X: nolinked power save leave
[  169.385632] RTL871X: nolinked power save enter
[  189.956334] RTL871X: RTW_ADAPTIVITY_EN_
[  189.956339] AUTO, chplan:0x20, Regulation:0,0
[  189.956340] RTL871X: RTW_ADAPTIVITY_MODE_
[  189.956341] NORMAL
[  190.537275] RTL871X: nolinked power save leave
[  192.639817] RTL871X: nolinked power save enter
[  194.012235] RTL871X: RTW_ADAPTIVITY_EN_
[  194.012241] AUTO, chplan:0x20, Regulation:0,0
[  194.012243] RTL871X: RTW_ADAPTIVITY_MODE_
[  194.012243] NORMAL
[  194.633356] RTL871X: nolinked power save leave
[  196.561111] RTL871X: nolinked power save enter
[  197.222334] RTL871X: RTW_ADAPTIVITY_EN_
[  197.222341] AUTO, chplan:0x20, Regulation:0,0
[  197.222342] RTL871X: RTW_ADAPTIVITY_MODE_
[  197.222342] NORMAL
[  197.801412] RTL871X: nolinked power save leave
[  198.010303] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
[  198.049729] RTL871X: start auth
[  198.053569] RTL871X: auth success, start assoc
[  201.321910] RTL871X: nolinked power save enter
[  201.982296] RTL871X: RTW_ADAPTIVITY_EN_
[  201.982301] AUTO, chplan:0x20, Regulation:0,0
[  201.982302] RTL871X: RTW_ADAPTIVITY_MODE_
[  201.982303] NORMAL
[  202.560976] RTL871X: nolinked power save leave
[  202.770702] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
[  202.861790] RTL871X: start auth
[  202.865617] RTL871X: auth success, start assoc
[  206.496840] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
[  206.752821] RTL871X: start auth
[  206.766095] RTL871X: auth success, start assoc
[  211.053165] RTL871X: rtw_set_802_11_connect(wlxXXXXXXXXXXXX)  fw_state=0x00000008
[  211.565803] RTL871X: start auth
[  211.590036] RTL871X: auth success, start assoc
[  217.437055] RTL871X: nolinked power save enter
[  220.613669] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[  221.284132] RTL871X: RTW_ADAPTIVITY_EN_
[  221.284138] AUTO, chplan:0x20, Regulation:0,0
[  221.284139] RTL871X: RTW_ADAPTIVITY_MODE_
[  221.284140] NORMAL
```

Thanks

---

