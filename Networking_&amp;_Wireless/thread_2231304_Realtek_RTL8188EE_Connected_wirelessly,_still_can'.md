---
title: "Realtek RTL8188EE: Connected wirelessly, still can't access Internet"
date: 2014-06-24
forum: Networking &amp; Wireless
---

### Post by princee2 on 2014-06-24
I have installed Ubuntu 14.04 LTS for on a USB. 
Before installation, in the "Try Ubuntu" mode, I checked if things were working using USB-based booting. Wifi and other applications worked properly. 


After installation, computer is showing that wifi is connected but internet is not working. I have checked with my iPad and friend's PC, and everything is fine.

Operating system - Ubuntu 14.04

I'm using the USB to boot, but the computer I am using is an HP Pavilion.

I know above details are not enough, please let me know what all other details are needed and how to get them.

---

### Post by mörgæs on 2014-06-24
It's all explained in the sticky notes.

---

### Post by princee2 on 2014-06-24
Here is my info:

```
########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux tachyon 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:1982]
	Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 0bda:571c Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 005 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #####

rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi

##### iw reg get #####

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"2WIRE790"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 192.168.1.254
nameserver 127.0.1.1
search attlocal.net

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [2WIRE790] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    C4 Downstairs:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    C4 Network:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Fortress of Solitude: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2
    *2WIRE790:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    2WIRE392:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    bryant2049:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    2WIRE332:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.90
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             8.8.8.8
    DNS:             8.8.4.4

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

No way to aquire root rights found.

##### iwlist channel #####

wlan0     11 channels in total; available frequencies :
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

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     1B8E36556B30AA35325F55D
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   30.414753] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   30.414798] rtl8188ee 0000:02:00.0: irq 48 for MSI/MSI-X
[   34.296007] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   34.296277] rtlwifi: wireless switch is on
[   36.190072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.190414] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.495655] wlan0: authenticate with <MAC address removed>
[   39.508764] wlan0: send auth to <MAC address removed> (try 1/3)
[   39.511129] wlan0: authenticated
[   39.511391] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   39.511395] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   39.512736] wlan0: associate with <MAC address removed> (try 1/3)
[   39.515936] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[   39.516056] wlan0: associated
[   39.516095] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.572308] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[   39.593327] wlan0: authenticate with <MAC address removed>
[   39.593427] wlan0: send auth to <MAC address removed> (try 1/3)
[   39.594712] wlan0: authenticated
[   39.594934] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   39.594940] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   39.596850] wlan0: associate with <MAC address removed> (try 1/3)
[   39.598653] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[   39.598763] wlan0: associated
[ 1714.647473] wlan0: Connection to AP <MAC address removed> lost
[ 1715.994110] wlan0: authenticate with <MAC address removed>
[ 1716.003902] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1716.006107] wlan0: authenticated
[ 1716.006455] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1716.006461] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1716.009251] wlan0: associate with <MAC address removed> (try 1/3)
[ 1716.014795] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1716.014914] wlan0: associated
[ 1725.182513] wlan0: Connection to AP <MAC address removed> lost
[ 1726.509307] wlan0: authenticate with <MAC address removed>
[ 1726.518945] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1726.521224] wlan0: authenticated
[ 1726.521550] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1726.521554] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1726.524271] wlan0: associate with <MAC address removed> (try 1/3)
[ 1726.540814] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1726.540935] wlan0: associated
[ 1745.724193] wlan0: Connection to AP <MAC address removed> lost
[ 1747.050638] wlan0: authenticate with <MAC address removed>
[ 1747.060009] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1747.061387] wlan0: authenticated
[ 1747.061564] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1747.061568] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1747.061758] wlan0: associate with <MAC address removed> (try 1/3)
[ 1747.063505] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1747.063629] wlan0: associated
[ 1888.587716] wlan0: Connection to AP <MAC address removed> lost
[ 1889.914250] wlan0: authenticate with <MAC address removed>
[ 1889.923798] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1889.932033] wlan0: authenticated
[ 1889.932492] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1889.932497] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1889.933477] wlan0: associate with <MAC address removed> (try 1/3)
[ 1889.935365] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1889.935483] wlan0: associated
[ 1995.595388] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2007.520752] wlan0: authenticate with <MAC address removed>
[ 2007.530258] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2007.533222] wlan0: authenticated
[ 2007.533429] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2007.533433] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2007.535855] wlan0: associate with <MAC address removed> (try 1/3)
[ 2007.537820] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 2007.537945] wlan0: associated
[ 2027.351012] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2144.184126] wlan0: authenticate with <MAC address removed>
[ 2144.193643] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2144.195471] wlan0: authenticated
[ 2144.196269] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2144.196275] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2144.199373] wlan0: associate with <MAC address removed> (try 1/3)
[ 2144.204781] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 2144.204899] wlan0: associated
[ 4862.599193] wlan0: Connection to AP <MAC address removed> lost
[ 4863.946025] wlan0: authenticate with <MAC address removed>
[ 4863.955642] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4863.963161] wlan0: authenticated
[ 4863.963438] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4863.963442] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4863.965011] wlan0: associate with <MAC address removed> (try 1/3)
[ 4863.967021] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 4863.967146] wlan0: associated
[ 4907.116947] wlan0: Connection to AP <MAC address removed> lost
[ 4908.467648] wlan0: authenticate with <MAC address removed>
[ 4908.477383] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4908.479620] wlan0: authenticated
[ 4908.479878] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4908.479886] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4908.482762] wlan0: associate with <MAC address removed> (try 1/3)
[ 4908.488897] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 4908.489012] wlan0: associated
[ 5077.975131] wlan0: Connection to AP <MAC address removed> lost
[ 5079.321900] wlan0: authenticate with <MAC address removed>
[ 5079.331300] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5079.333769] wlan0: authenticated
[ 5079.334038] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5079.334042] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5079.336895] wlan0: associate with <MAC address removed> (try 1/3)
[ 5079.339593] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 5079.339711] wlan0: associated
[ 5232.886662] wlan0: Connection to AP <MAC address removed> lost
[ 5234.213500] wlan0: authenticate with <MAC address removed>
[ 5234.222833] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5234.226075] wlan0: authenticated
[ 5234.226363] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5234.226367] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5234.228367] wlan0: associate with <MAC address removed> (try 1/3)
[ 5234.231343] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 5234.231458] wlan0: associated
[ 5271.424410] wlan0: Connection to AP <MAC address removed> lost
[ 5272.770949] wlan0: authenticate with <MAC address removed>
[ 5272.780516] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5272.781861] wlan0: authenticated
[ 5272.782418] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5272.782426] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5272.786177] wlan0: associate with <MAC address removed> (try 1/3)
[ 5272.790479] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 5272.790595] wlan0: associated
[ 5422.333262] wlan0: Connection to AP <MAC address removed> lost
[ 5423.680366] wlan0: authenticate with <MAC address removed>
[ 5423.689713] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5423.693436] wlan0: authenticated
[ 5423.693698] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5423.693706] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5423.694997] wlan0: associate with <MAC address removed> (try 1/3)
[ 5423.702867] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 5423.702987] wlan0: associated
[ 5456.932209] wlan0: Connection to AP <MAC address removed> lost
[ 5458.275150] wlan0: authenticate with <MAC address removed>
[ 5458.284416] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5458.289537] wlan0: authenticated
[ 5458.289835] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5458.289839] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5458.290099] wlan0: associate with <MAC address removed> (try 1/3)
[ 5458.292313] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[ 5458.292438] wlan0: associated

########## wireless info END ############

```

---

### Post by wildmanne39 on 2014-06-24
This driver can be a pain to get to work properly, please try:
```
sudo modprobe -r rtl8188ee
sudo modprobe rtl8188ee swenc=1
```
do not reboot until you are done testing this setting, it will be lost when you do, but if it helps we can make it permanent.

Also this > disabling VHT as WMM/QoS is not supported by the APis in the dmesg file, you need to set your routers encryption to wpa2 (AES) only, not mixed mode and not (TKIP) if possible that will help, plus channel 1 or 11 usually work best.
Thanks

---

### Post by princee2 on 2014-06-25
Thanks for replying, however I can't connect at all now.

It was already set to WPA2. 

When I wanted to change the channel to 1 or 11, I noticed that I had to change the Mode to ad-hoc and then set "Band" to a non-automatic status. Which do I change to, A or B/G ?

---

