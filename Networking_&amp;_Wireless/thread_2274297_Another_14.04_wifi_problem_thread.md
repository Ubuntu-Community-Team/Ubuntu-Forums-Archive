---
title: "Another 14.04 wifi problem thread"
date: 2015-04-19
forum: Networking &amp; Wireless
---

### Post by matteovalentinuzzi on 2015-04-19
[COLOR=#111111][FONT=Ubuntu]I'm having a wifi issue on my laptop that I have no idea how to solve.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My laptop runs in dual-boot Windows 8.1/Ubuntu 14.04: whenever I'm using windows, all the connections run with no problem; on ubuntu, instead, wifi connections work for a couple minutes after start-up, and then they stop working until I reboot. Wired connections work fine.
I read on a question on askubuntu.com that the issue might be related to the power management, but turning it on/off doesn't change anything. Can anyone help me?
Below is the result of the wireless script:
[/FONT][/COLOR]```



########## wireless info START ##########


Report from: 14 Apr 2015 19:04 CEST +0200


Booted last: 14 Apr 2015 19:01 CEST +0200


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


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630669  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
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
          inet addr:10.188.92.98  Bcast:10.188.255.255  Mask:255.255.0.0
          inet6 addr: fe80::9ead:97ff:fe37:9443/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2029470 (2.0 MB)  TX bytes:515449 (515.4 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Wifirst-B Mirabeau"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'Wifirst-B Mirabeau' [AN27]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.188.0.1      0.0.0.0         UG    0      0        0 wlan0
10.188.0.0      0.0.0.0         255.255.0.0     U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Wifirst-B Mirabeau] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Livebox-716f:    Infra, <MAC 'Livebox-716f' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    Freebox-661AF0:  Infra, <MAC 'Freebox-661AF0' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA
    HP-Print-38-ENVY 4500 series: Infra, <MAC 'HP-Print-38-ENVY 4500 series' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA2
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    Livebox-1E3C:    Infra, <MAC 'Livebox-1E3C' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    freebox_CEIBPC:  Infra, <MAC 'freebox_CEIBPC' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    Freebox-9E1DAA:  Infra, <MAC 'Freebox-9E1DAA' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2
    SFR_2150:        Infra, <MAC 'SFR_2150' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    Bbox-CEBC22:     Infra, <MAC 'Bbox-CEBC22' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    SFR_5418:        Infra, <MAC 'SFR_5418' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AN12]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 50 WPA Enterprise
    Livebox-4E18:    Infra, <MAC 'Livebox-4E18' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    angelo26:        Infra, <MAC 'angelo26' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    freebox_Leonardo:Infra, <MAC 'freebox_Leonardo:Infra, <MAC address>, Freq 2472 MHz, Rate 54 Mb/s, Strength 47 WPA' [AN16]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 47 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA Enterprise
    Livebox-06b0:    Infra, <MAC 'Livebox-06b0' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    dlink:           Infra, <MAC 'dlink' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84
    FreeWifi:        Infra, <MAC 'FreeWifi' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    FreeWifi:        Infra, <MAC 'FreeWifi' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    FreeWifi:        Infra, <MAC 'FreeWifi' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    FreeWifi:        Infra, <MAC 'FreeWifi' [AN24]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 50
    Bouygues Telecom Wi-Fi: Infra, <MAC 'Bouygues Telecom Wi-Fi' [AN25]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AN26]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    *Wifirst-B Mirabeau: Infra, <MAC 'Wifirst-B Mirabeau' [AN27]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 36
    Paulo-aime-les-moules-frites: Infra, <MAC 'Paulo-aime-les-moules-frites' [AN28]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA
    NEUF_4E24:       Infra, <MAC 'NEUF_4E24' [AN29]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 10 WPA
    Bbox-2D2FD015:   Infra, <MAC 'Bbox-2D2FD015' [AN30]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN31]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AN32]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30
    FreeWifi:        Infra, <MAC 'FreeWifi' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10
    Bouygues Telecom Wi-Fi: Infra, <MAC 'Bouygues Telecom Wi-Fi' [AN34]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AN35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    Wifirst-B Mirabeau: Infra, <MAC 'Wifirst-B Mirabeau' [AN36]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 52
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AN37]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    SFR_4928:        Infra, <MAC 'SFR_4928' [AN38]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    NEUF_BED0:       Infra, <MAC 'NEUF_BED0' [AN39]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN40]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    freebox_Lele:    Infra, <MAC 'freebox_Lele' [AN41]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2


  IPv4 Settings:
    Address:         10.188.92.98
    Prefix:          16 (255.255.0.0)
    Gateway:         10.188.0.1


    DNS:             10.188.0.1


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


[[/etc/NetworkManager/system-connections/TNCAPC45CC0]] (600 root)
[connection] id=TNCAPC45CC0 | type=802-11-wireless
[802-11-wireless] ssid=TNCAPC45CC0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wifirst-B Mirabeau]] (600 root)
[connection] id=Wifirst-B Mirabeau | type=802-11-wireless
[802-11-wireless] ssid=Wifirst-B Mirabeau | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Wifirst*B Mirabeau]] (600 root)


[[/etc/NetworkManager/system-connections/InfostradaWiFi-BED554]] (600 root)
[connection] id=InfostradaWiFi-BED554 | type=802-11-wireless
[802-11-wireless] ssid=InfostradaWiFi-BED554 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wifirst-B Mirabeau]] (600 root)
[connection] id=Wifirst-B Mirabeau | type=802-11-wireless
[802-11-wireless] ssid=Wifirst-B Mirabeau | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6F:CA:28:7C:25:73:D0:9C:A3:2C:19:80:C0:D7:63:77:7A:63:D4:F5
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


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


[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


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


[/etc/modprobe.d/rt18723be.conf]
option rt18723be fwlps=0 swlps=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   17.182623] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   17.571055] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   17.571265] rtlwifi: wireless switch is on
[   26.036043] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   70.691290] wlan0: authenticate with <MAC 'Wifirst-B Mirabeau' [AN27]>
[   70.701448] wlan0: send auth to <MAC 'Wifirst-B Mirabeau' [AN27]> (try 1/3)
[   70.702530] wlan0: authenticated
[   70.703019] rtl8723be 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   70.703022] rtl8723be 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   70.706420] wlan0: associate with <MAC 'Wifirst-B Mirabeau' [AN27]> (try 1/3)
[   70.708647] wlan0: RX AssocResp from <MAC 'Wifirst-B Mirabeau' [AN27]> (capab=0x421 status=0 aid=4)
[   70.708774] wlan0: associated
[   70.708801] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-04-19
See [http://ubuntuforums.org/showthread.php?t=2273794&p=13265679#post13265679](http://ubuntuforums.org/showthread.php?t=2273794&p=13265679#post13265679)
You made a typo when you attempted the echo options

---

