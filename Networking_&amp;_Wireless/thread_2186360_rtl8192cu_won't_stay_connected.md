---
title: "rtl8192cu won't stay connected"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by Eugene King on 2013-11-06
With the 3.8 kernel and 12.04 my wna1000m wifi adapter with rtl8192cu driver will stay connected to a network but internet drops out. pulling the adapter and installing it will get me internet along with the network connection only to loose it again.

---

### Post by varunendra on 2013-11-07
> **Eugene King said:**
> With the 3.8 kernel and 12.04 my wna1000m wifi adapter with rtl8192cu driver will stay connected to a network but internet drops out. pulling the adapter and installing it will get me internet along with the network connection only to loose it again.
While the adapter is plugged in and working, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Bucky Ball on 2013-11-07
***Post moved to own thread.***

Please do not hijack threads. Thanks.

---

### Post by kurt18947 on 2013-11-07
I had a similar situation with an rtl8192cu adapter and the 'baked-in' driver.  Realtek has released a new driver which may or may not help your situation.  I'm using 13.10 and have settled on a 'cleaned up' version of the old Realtek driver found here:

[pvaret/rtl8192cu-fixes · GitHub]("https://github.com/pvaret/rtl8192cu-fixes")

I'm not sure if that will work on 12.04 or not.  There is one peculiarity I see using the tweaked driver, I haven't tried the new Realtek driver.  If you remove the wifi adapter, it will cause a kernel panic.  The only recovery I know is a reboot and you'd lose anything you haven't saved.

---

### Post by Eugene King on 2013-11-07
This 12.04 is installed on a USB stick

I origonally used a USB cable to tether with my iPhone 5 but IOS7 seems to have screwed up the trust Ubuntu and won't mount my Phone

Edit: this immage is of the PC I'm using at work..........I would really like to get my USB tether fixed but this seems my only option for now.


```

*************** info trace ***************

***** uname -a *****

Linux vaio-VPCEB46FX 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82578DM Gigabit Network Connection [8086:10ef] (rev 05)
    Subsystem: Dell OptiPlex 980 [1028:02da]
    Kernel driver in use: e1000e

***** lsusb *****

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 413c:1005 Dell Computer Corp. Multimedia Pro Keyboard Hub
Bus 002 Device 004: ID 0461:4d51 Primax Electronics, Ltd 0Y357C PMX-MMOCZUL (B) [Dell Laser Mouse]
Bus 002 Device 005: ID 0781:5575 SanDisk Corp. 
Bus 002 Device 010: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 007: ID 413c:2011 Dell Computer Corp. Multimedia Pro Keyboard

***** PCMCIA Card Info *****


***** iwconfig *****

wlan1     IEEE 802.11bgn  ESSID:"Me"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


***** rfkill *****

3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192cu              72751  0 
rtl8192c_common        49561  1 rtl8192cu
rtlwifi                81225  1 rtl8192cu
mac80211              630977  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              525326  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan1  [Me] ----------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CDA:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    iOffice:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    hsyguest:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87
    *Me:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2

  IPv4 Settings:
    Address:         172.20.10.4
    Prefix:          28 (255.255.255.240)
    Gateway:         172.20.10.1

    DNS:             172.20.10.1


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Me"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003119494b
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00024D65
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030101
                    IE: Unknown: 200100
                    IE: Unknown: 23021000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A20001AFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD0A0017F206010103010000
                    IE: Unknown: DD0D0017F20602010634C0597B994D
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F202010184000364000027A4000041435E0061322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s
                    Bit Rates:54 Mb/s
                    Mode:Master
                    Extra:tsf=000000923ece60d6
                    Extra: Last beacon: 728ms ago
                    IE: Unknown: 000100
                    IE: Unknown: 01080C12961824304860
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B05010013C267
                    IE: Unknown: 2A0103
                    IE: Unknown: 32016C
                    IE: Unknown: 851E06008F000F00FF0359007573707765737432356C6170000000000100003A
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0072322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961408
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"hsyguest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s
                    Bit Rates:54 Mb/s
                    Mode:Master
                    Extra:tsf=000000923ece4db5
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 00086873796775657374
                    IE: Unknown: 01080C12961824304860
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B05010013C267
                    IE: Unknown: 2A0103
                    IE: Unknown: 2D1A2C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32016C
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0072322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961408
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"iOffice"
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s
                    Bit Rates:54 Mb/s
                    Mode:Master
                    Extra:tsf=000000923ecfb808
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0007694F6666696365
                    IE: Unknown: 01080C12961824304860
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32016C
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961409


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     B60B278C1942CBFF27FC8A0
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.8.0-32-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E6FCDEDFF185E90DD643BE4
depends:        mac80211
intree:         Y
vermagic:       3.8.0-32-generic SMP mod_unload modversions 

filename:       /lib/modules/3.8.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-32-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   11.433136] rtl8192cu: Chip version 0x10
[   11.515500] rtl8192cu: MAC address: <MAC address removed>
[   11.515504] rtl8192cu: Board Type 0
[   11.515746] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   11.515779] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   11.605667] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.606095] rtlwifi: wireless switch is on
[   13.291372] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.291628] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.294959] rtl8192cu: MAC auto ON okay!
[   13.327822] rtl8192cu: Tx queue select: 0x05
[   13.696211] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.696418] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  167.310320] wlan1: authenticate with <MAC address removed>
[  167.333598] wlan1: direct probe to <MAC address removed> (try 1/3)
[  167.537337] wlan1: direct probe to <MAC address removed> (try 2/3)
[  167.740956] wlan1: direct probe to <MAC address removed> (try 3/3)
[  167.944637] wlan1: authentication with <MAC address removed> timed out
[  172.328736] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  350.560561] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  350.560571] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x83040000
[  350.560578] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  350.560585] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[  353.663271] rtl8192cu: Chip version 0x10
[  353.745857] rtl8192cu: MAC address: <MAC address removed>
[  353.745863] rtl8192cu: Board Type 0
[  353.746102] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  353.746140] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  353.746369] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  353.746979] rtlwifi: wireless switch is on
[  353.772559] rtl8192cu: MAC auto ON okay!
[  353.805292] rtl8192cu: Tx queue select: 0x05
[  354.168078] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  354.168580] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  406.589825] wlan1: authenticate with <MAC address removed>
[  406.613206] wlan1: send auth to <MAC address removed> (try 1/3)
[  406.628298] wlan1: authenticated
[  406.629119] wlan1: associate with <MAC address removed> (try 1/3)
[  406.644274] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  406.644317] wlan1: associated
[  406.644349] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  427.582714] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  431.087477] wlan1: authenticate with <MAC address removed>
[  431.110817] wlan1: send auth to <MAC address removed> (try 1/3)
[  431.129870] wlan1: authenticated
[  431.130928] wlan1: associate with <MAC address removed> (try 1/3)
[  431.146163] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  431.146207] wlan1: associated
[  451.533064] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  455.043779] wlan1: authenticate with <MAC address removed>
[  455.067017] wlan1: send auth to <MAC address removed> (try 1/3)
[  455.075843] wlan1: authenticated
[  455.079179] wlan1: associate with <MAC address removed> (try 1/3)
[  455.086269] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  455.086313] wlan1: associated
[  475.558055] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  479.004403] wlan1: authenticate with <MAC address removed>
[  479.027715] wlan1: send auth to <MAC address removed> (try 1/3)
[  479.059944] wlan1: authenticated
[  479.063821] wlan1: associate with <MAC address removed> (try 1/3)
[  479.096071] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  479.096114] wlan1: associated
[  499.460764] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  505.200420] wlan1: authenticate with <MAC address removed>
[  505.223689] wlan1: send auth to <MAC address removed> (try 1/3)
[  505.240506] wlan1: authenticated
[  505.243762] wlan1: associate with <MAC address removed> (try 1/3)
[  505.274616] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  505.274670] wlan1: associated
[  525.424029] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  531.142456] wlan1: authenticate with <MAC address removed>
[  531.165861] wlan1: send auth to <MAC address removed> (try 1/3)
[  531.167682] wlan1: authenticated
[  531.169941] wlan1: associate with <MAC address removed> (try 1/3)
[  531.204193] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  531.204238] wlan1: associated
[  579.030847] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  581.622330] rtl8192cu: Chip version 0x10
[  581.704681] rtl8192cu: MAC address: <MAC address removed>
[  581.704688] rtl8192cu: Board Type 0
[  581.704927] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  581.704977] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  581.705201] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[  581.705690] rtlwifi: wireless switch is on
[  581.726422] rtl8192cu: MAC auto ON okay!
[  581.759124] rtl8192cu: Tx queue select: 0x05
[  582.122291] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  582.122750] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  584.339226] wlan1: authenticate with <MAC address removed>
[  584.362534] wlan1: send auth to <MAC address removed> (try 1/3)
[  584.420592] wlan1: authenticated
[  584.422429] wlan1: associate with <MAC address removed> (try 1/3)
[  584.424834] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  584.424878] wlan1: associated
[  584.424889] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  785.011795] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  787.092063] rtl8192cu: Chip version 0x10
[  787.176409] rtl8192cu: MAC address: <MAC address removed>
[  787.176416] rtl8192cu: Board Type 0
[  787.176638] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  787.176678] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  787.176958] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[  787.177518] rtlwifi: wireless switch is on
[  787.206588] rtl8192cu: MAC auto ON okay!
[  787.239441] rtl8192cu: Tx queue select: 0x05
[  787.600748] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  787.601268] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  789.804851] wlan1: authenticate with <MAC address removed>
[  789.828125] wlan1: send auth to <MAC address removed> (try 1/3)
[  789.833571] wlan1: authenticated
[  789.836250] wlan1: associate with <MAC address removed> (try 1/3)
[  789.848720] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  789.848766] wlan1: associated
[  789.848788] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

****************** done ******************

```

---

### Post by Eugene King on 2013-11-07
So, I went to brake for 20min or so and came back, woke up the system and opened firefox. It took a few moments but it connected and I still had internet. Looking at the connection speed I see nothing speed wise like I had wired. I tried speednet but without a flashplayer in firefox No deal. May be I'll load Crome and try that.........

Trying to post the above my connection stalled out and I had to pull and reinsert the WIFI adapter to get internet. Showed me connected to my hotspot the entire time.

---

### Post by kurt18947 on 2013-11-08
> **Eugene King said:**
> So, I went to brake for 20min or so and came back, woke up the system and opened firefox. It took a few moments but it connected and I still had internet. Looking at the connection speed I see nothing speed wise like I had wired. I tried speednet but without a flashplayer in firefox No deal. May be I'll load Crome and try that.........

Trying to post the above my connection stalled out and I had to pull and reinsert the WIFI adapter to get internet. Showed me connected to my hotspot the entire time.

Flash installer won't install? It should, won't be the latest but I haven't seen a problem with flash 11.2.x  yet.  There may be issues with flash based games, I don't have any experience there.  As far as the wifi adapter, yes those are the symptoms I saw.  I showed a network connection but not an internet connection.  I found simply turning wifi off then on via the network manager app/icon in the upper right hand corner restored internet connectivity, no need to unplug/replug.   The driver from Realtek doesn't have that issue and is also faster.  The adapter on this machine showed 72 mb./sec using the 'baked-in' driver, 300 mb./sec using the tweaked Realtek driver without the 5 ghz. channel enabled.

---

### Post by varunendra on 2013-11-08
@ Eugene King,

It seems there is only one thing you can try with your driver, rest of the settings/stats already look pretty solid to me. Please try -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=Y
```
Does it help stability? This is a temporary change that will be lost at next boot. If it helps, we can make it permanent. If it doesn't, please try what kurt18947 suggested. He has a good first hand experience with this driver.

@ kurt18947,

Is your chip exactly the same? That is - **[noparse][0846:9041][/noparse]**

---

### Post by Eugene King on 2013-11-08
> **kurt18947 said:**
> Flash installer won't install? It should, won't be the latest but I haven't seen a problem with flash 11.2.x  yet.  There may be issues with flash based games, I don't have any experience there.  As far as the wifi adapter, yes those are the symptoms I saw.  I showed a network connection but not an internet connection.  I found simply turning wifi off then on via the network manager app/icon in the upper right hand corner restored internet connectivity, no need to unplug/replug.   The driver from Realtek doesn't have that issue and is also faster.  The adapter on this machine showed 72 mb./sec using the 'baked-in' driver, 300 mb./sec using the tweaked Realtek driver without the 5 ghz. channel enabled.

I have not gone to Adobe to get it. Just looked for it under add ons.................Have to look

In on of my previous reloads of my USB stick to try and figure what happened/is different I tried loading the realtec driver from their down load and eventually found a thread on how to run the script but it failed. 

Hopefully I have no brakedowns tonight and can get somewhere with this USB micro Adapter. I almost smashed it last night tring to load software it would stall and kill the install.

---

### Post by Eugene King on 2013-11-08
> **varunendra said:**
> @ Eugene King,

It seems there is only one thing you can try with your driver, rest of the settings/stats already look pretty solid to me. Please try -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=Y
```
Does it help stability? This is a temporary change that will be lost at next boot. If it helps, we can make it permanent. If it doesn't, please try what kurt18947 suggested. He has a good first hand experience with this driver.

@ kurt18947,

Is your chip exactly the same? That is - **[noparse][0846:9041][/noparse]**

I preformed the reset. we will see what happens. Thanks for all the help so far! My USB tethering with my iPhone 5 is another issue.......

and I'll look into the GitHub fix

---

### Post by Eugene King on 2013-11-08
> **varunendra said:**
> @ Eugene King,

It seems there is only one thing you can try with your driver, rest of the settings/stats already look pretty solid to me. Please try -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=Y
```
Does it help stability? This is a temporary change that will be lost at next boot. If it helps, we can make it permanent. If it doesn't, please try what kurt18947 suggested. He has a good first hand experience with this driver.

@ kurt18947,

Is your chip exactly the same? That is - **[noparse][0846:9041][/noparse]**

So I preformed the reset and composed my reply. and it stalled trying to post it. and completely lost the message in the process.

I will look into the tweeked driver 

Thanks for all the help so far. It me much easier to just USB tether with my thumb drive but noooooApple once again has to screw things up to have things on their terms.....

---

### Post by Eugene King on 2013-11-08
It looks like that fix is burried in a 3.2.0.56 kernel. I'm going through the motions now but my connection stalled a bunch of times just doing the first command. Yea........

---

### Post by Eugene King on 2013-11-08
I am typing this reply from my iPhone. I lost my blue light in the wifi adapter like there is no longer a driver for it. 

I cant ant seem to recover from it. I tried booting on a previous kernal (3.7.0) and still no blue light.

everything seemed to go well in terminal mode. I just copied and paste into term.

---

### Post by varunendra on 2013-11-09
Anytime you feel clueless, the "wireless_script" report may help getting some clues. I'm standing by for the moment. Shall jump in as soon as I have enough time and have something useful to add. For now, I hope kurt18947 would join us soon.

---

### Post by praseodym on 2013-11-09
Install the patched driver according to this (13.04):

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

### Post by Eugene King on 2013-11-11
> **praseodym said:**
> Install the patched driver according to this (13.04):

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

I followed the patch driver install from a earlier post link just cutting and pasting.......

The above link is in german.....

I did edit the blacklist for the driver and rem'd it out and now have my crappy wifi adapter back.........

I'll see if I can pick out what to do in the above of follow the other link again

---

### Post by Eugene King on 2013-11-11
Here is what happened during install.....I'm just cutting and pasting the commands.

Below is a error


```
ERROR (dkms apport): binary package for rtl8192cu: 3.4.4.4749 not found
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/rtl8192cu/3.4.4.4749/build/make.log for more information.
vaio@vaio-VPCEB46FX:~$ sudo depmod -a && sudo update-initramfs -u 
```

---

### Post by Eugene King on 2013-11-11
so I found and did this.....[https://github.com/tylerx/rtl8192cu-dkms/blob/master/README.md](https://github.com/tylerx/rtl8192cu-dkms/blob/master/README.md)

```
vaio@vaio-VPCEB46FX:/usr/src$ sudo git clone https://github.com/tylerx/rtl8192cu-dkms.git rtl8192cu-3.4.4.4749.20121105
Cloning into 'rtl8192cu-3.4.4.4749.20121105'...
remote: Counting objects: 213, done.
remote: Compressing objects: 100% (153/153), done.
remote: Total 213 (delta 59), reused 209 (delta 58)
Receiving objects: 100% (213/213), 1.05 MiB | 363 KiB/s, done.
Resolving deltas: 100% (59/59), done.
vaio@vaio-VPCEB46FX:/usr/src$ sudo dkms add rtl8192cu/3.4.4.4749.20121105

Creating symlink /var/lib/dkms/rtl8192cu/3.4.4.4749.20121105/source ->
                 /usr/src/rtl8192cu-3.4.4.4749.20121105

DKMS: add completed.
vaio@vaio-VPCEB46FX:/usr/src$ sudo dkms build rtl8192cu/3.4.4.4749.20121105

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.8.0-29-generic -C /lib/modules/3.8.0-29-generic/build M=/var/lib/dkms/rtl8192cu/3.4.4.4749.20121105/build..........
cleaning build area....

DKMS: build completed.
vaio@vaio-VPCEB46FX:/usr/src$ sudo dkms install rtl8192cu/3.4.4.4749.20121105

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-29-generic/updates/dkms/

depmod.......

DKMS: install completed.
vaio@vaio-VPCEB46FX:/usr/src$ 

```

Time for a reboot

---

### Post by Eugene King on 2013-11-11
Well I survived the reboot......and it was a instant reconnect to my hotspot from my iPhone5

Will the internet connection last? Only time will tell.

I guessing the reason I would loose my WiFi adapter was because the install failed and blacklisting the driver in the next step turned it off. 

I'm going for brake. I'll leave everything connect, up and running and see what happins when I get back.

---

### Post by hamishmb on 2013-11-11
The github fix works well in Ubuntu 13.10, but Realtek recently updated their driver, and it now works with kernel versions up to 3.9 (how hard can it be to keep it up to date!), Precise uses 3.2, so it should be okay.

---

### Post by Eugene King on 2013-11-11
> **hamishmb said:**
> The github fix works well in Ubuntu 13.10, but Realtek recently updated their driver, and it now works with kernel versions up to 3.9 (how hard can it be to keep it up to date!), Precise uses 3.2, so it should be okay.

I just got back from brake and did nothing but open up firefox..........after a few seconds it opened and I'm still connect to the internet. 

I tried the driver from realtek and couldn't figure out how to run the script...when I did get it to run it said something happened and failed the install......sad thing for me was that I kingd of remember them even giving the commands and it was cut and paste. 

The link I posted for kernel 3.8 I had to split up the change directery command and then do the sudo command my terminal didn't like having it change directry and then prefore the sudo stuff.

If this doesn't give me problems next work stretch I'll call it solved.......

---

### Post by Eugene King on 2013-11-15
I am not going to call it solved but it did improve by 50%.........

---

### Post by praseodym on 2013-11-16
Check now
```

ifconfig -a
iwconfig
cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
dmesg | grep 8192
```

---

