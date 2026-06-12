---
title: "Ubuntu 14.10 won't connect to Android Hotspot"
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by xmbwd on 2015-01-01
I have an Android running a hotspot that I know works, because I can connect to it from a Mac, a PC, and another Android.  But my Asus laptop running 14.10 -- which works fine with my home WiFi -- simply won't connect to it.  And it acts weird when I try.  

The symptoms:

[LIST=1]
[*]I select the wireless icon in the menu bar and select "AndroidAP" (I've tried this with and without the Android hotspot being encrypted)
[*]The wifi icon changes from full "bars" to just one or two (even though the signal is directly next to it)
[*]The wifi icon then (a) stops working as a drop down (that is, when I select the icon, nothing appears below it) and then (b) disappears
[*]When I open Settings>Network>Wireless, the "AndroidAP" is selected (has a check mark next to it), but it does not work.  There is no network connection.
[*]Unlike my home network, when I select the "AndroidAP" netowork's ">" button, the "Disconnect" button is greyed out
[/LIST]

Below are the results from the wireless script.  I don't really understand this issue -- as the Asus wireless (actually, a usb dongle) seems to work fine with all other routers.  And the AndroidAP "router" works with all other platforms.  

Any ideas?

```

########## wireless info START ##########

Report from: 01 Jan 2015 11:02 PST -0800

Booted last: 01 Jan 2015 10:48 PST -0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi_osi=, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4160]

##### lsusb #############################

Bus 001 Device 008: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 022: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 006: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              510218  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
asus_nb_wmi            16990  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19193  1 asus_wmi
video                  20128  2 i915,asus_wmi

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

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:10.0.1.50  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fef5:1af0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4655 errors:0 dropped:22 overruns:0 frame:0
          TX packets:3329 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3888305 (3.8 MB)  TX bytes:737797 (737.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"dd_wrt"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'dd_wrt' [AC1]>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=94/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.2        0.0.0.0         UG    0      0        0 wlan1
10.0.1.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan1  [dd_wrt 1] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    dd_wrt:          Infra, <MAC 'dd_wrt' [AC2]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 59 WPA2
    dd_wrt_Guest:    Infra, <MAC 'dd_wrt_Guest' [AC3]>, Freq 2432 MHz, Rate 16 Mb/s, Strength 55 WPA2
    dd_wrt:          Infra, <MAC 'dd_wrt' [AC4]>, Freq 2432 MHz, Rate 16 Mb/s, Strength 54 WPA2
    AndroidAP:       Infra, <MAC 'AndroidAP' [AN4]>, Freq 2437 MHz, Rate 8 Mb/s, Strength 47 WPA2
    *dd_wrt:         Infra, <MAC 'dd_wrt' [AC1]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA2
    i beg to difference: Infra, <MAC 'i beg to difference' [AN6]>, Freq 2457 MHz, Rate 44 Mb/s, Strength 43 WPA WPA2

  IPv4 Settings:
    Address:         10.0.1.50
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.2

    DNS:             10.0.1.2

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

[[/etc/NetworkManager/system-connections/Amped_Rep_5.0GHz]] (600 root)
[connection] id=Amped_Rep_5.0GHz | type=802-11-wireless
[802-11-wireless] ssid=Amped_Rep_5.0GHz | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Jason's work iphone]] (600 root)
[connection] id=Jason's work iphone | type=802-11-wireless
[802-11-wireless] ssid=Jason's work iphone | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KaiserGuest]] (600 root)
[connection] id=KaiserGuest | type=802-11-wireless
[802-11-wireless] ssid=KaiserGuest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dd_wrt 2]] (600 root)
[connection] id=dd_wrt 2 | type=802-11-wireless
[802-11-wireless] ssid=dd_wrt | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/G2 2]] (600 root)
[connection] id=G2 2 | type=802-11-wireless
[802-11-wireless] ssid=G2 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/IBI-Guest]] (600 root)
[connection] id=IBI-Guest | type=802-11-wireless
[802-11-wireless] ssid=IBI-Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/i beg to difference]] (600 root)
[connection] id=i beg to difference | type=802-11-wireless
[802-11-wireless] ssid=i beg to difference | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KaiserGuest 1]] (600 root)
[connection] id=KaiserGuest 1 | type=802-11-wireless
[802-11-wireless] ssid=KaiserGuest | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/APLTV]] (600 root)
[connection] id=APLTV | type=802-11-wireless
[802-11-wireless] ssid=APLTV | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Life Rocks]] (600 root)
[connection] id=Life Rocks | type=802-11-wireless
[802-11-wireless] ssid=Life Rocks | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ipad-rmueller]] (600 root)
[connection] id=ipad-rmueller | type=802-11-wireless
[802-11-wireless] ssid=ipad-rmueller | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LG G2]] (600 root)
[connection] id=LG G2 | type=802-11-wireless
[802-11-wireless] ssid=LG G2 | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/AVE 2500]] (600 root)
[connection] id=AVE 2500 | type=802-11-wireless
[802-11-wireless] ssid=AVE 2500 | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Kimpton]] (600 root)
[connection] id=Kimpton | type=802-11-wireless
[802-11-wireless] ssid=Kimpton | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/G2 3]] (600 root)
[connection] id=G2 3 | type=802-11-wireless
[802-11-wireless] ssid=G2 | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/i beg to difference 1]] (600 root)
[connection] id=i beg to difference 1 | type=802-11-wireless
[802-11-wireless] ssid=i beg to difference | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/G2]] (600 root)
[connection] id=G2 | type=802-11-wireless
[802-11-wireless] ssid=G2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE940]] (600 root)
[connection] id=2WIRE940 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE940 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AmtrakConnect]] (600 root)
[connection] id=AmtrakConnect | type=802-11-wireless
[802-11-wireless] ssid=AmtrakConnect | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/G2 1]] (600 root)
[connection] id=G2 1 | type=802-11-wireless
[802-11-wireless] ssid=G2 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BAPC-guest]] (600 root)
[connection] id=BAPC-guest | type=802-11-wireless
[802-11-wireless] ssid=BAPC-guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dd_wrt_Guest]] (600 root)
[connection] id=dd_wrt_Guest | type=802-11-wireless
[802-11-wireless] ssid=dd_wrt_Guest | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/G2 Access]] (600 root)
[connection] id=G2 Access | type=802-11-wireless
[802-11-wireless] ssid=G2 Access | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LG-LS980_000]] (600 root)
[connection] id=LG-LS980_000 | type=802-11-wireless
[802-11-wireless] ssid=LG-LS980_000 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Phoenix Park Hotel]] (600 root)
[connection] id=Phoenix Park Hotel | type=802-11-wireless
[802-11-wireless] ssid=Phoenix Park Hotel | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dd_wrt 1]] (600 root)
[connection] id=dd_wrt 1 | type=802-11-wireless
[802-11-wireless] ssid=dd_wrt | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CCQA4]] (600 root)
[connection] id=CCQA4 | type=802-11-wireless
[802-11-wireless] ssid=CCQA4 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FoxFi47]] (600 root)
[connection] id=FoxFi47 | type=802-11-wireless
[802-11-wireless] ssid=FoxFi47 | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dd_wrt_Guest 1]] (600 root)
[connection] id=dd_wrt_Guest 1 | type=802-11-wireless
[802-11-wireless] ssid=dd_wrt_Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/G2_8580]] (600 root)
[connection] id=G2_8580 | type=802-11-wireless
[802-11-wireless] ssid=G2_8580 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dd_wrt]] (600 root)
[connection] id=dd_wrt | type=802-11-wireless
[802-11-wireless] ssid=dd_wrt | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     11 channels in total; available frequencies :
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
          Current Frequency:2.432 GHz (Channel 5)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.432 GHz (Channel 5)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'dd_wrt' [AC1]>
                    ESSID:"dd_wrt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=94/100  
          Cell 02 - Address: <MAC 'dd_wrt' [AC2]>
                    ESSID:"dd_wrt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=60/100  
          Cell 03 - Address: <MAC 'dd_wrt_Guest' [AC3]>
                    ESSID:"dd_wrt_Guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=47/100  
          Cell 04 - Address: <MAC 'dd_wrt' [AC4]>
                    ESSID:"dd_wrt"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=72/100  Signal level=47/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist iwlwifi

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

sleep 25s
sudo echo 0 > /sys/class/leds/asus::kbd_backlight/brightness
echo 0 | sudo tee /sys/class/leds/asus::kbd_backlight/brightness

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[   36.509486] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[   38.207580] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-01-01
What is wrong with the Intel 7260 that you are trying a USB wifi?

---

### Post by xmbwd on 2015-01-01
The internal card did not pick up signals as well.  It worked, but just wasn't as strong.

---

### Post by xmbwd on 2015-01-03
Just to be clear, the internal card worked for wifi, with a weaker signal.  But like the USB, it did not connect to the Android hotspot.  So the problem is indepent of wireless card.

---

### Post by xmbwd on 2015-01-18
I think (am inferring) that the problem is that my Android is broadcasting a Wireless N signal -- and I still can't get my computer to connect to wireless n.  I'm going to post that question elsewhere. . . . .

---

### Post by xmbwd on 2015-01-23
So it ***was*** the Wireless N problem -- that is, my Android was only sending out a Wireless N signal, and my laptop was not set up to receive Wireless N.  I followed the solution [here]("http://askubuntu.com/questions/575160/ubuntu-14-10-cant-connect-to-wireless-n-signals"), and now **both** Wireless N and the Android's hotspot work.  [B][I]

However....[/I][/B]my network manager keeps crashing....and I need to unplug my USB Edimax dongle to get it to reconnect to networks after suspend.  This is a new issue after the Wireless N fix, so I will have to try to research and fix it.

---

