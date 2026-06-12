---
title: "Ubuntu 13.10 Beaglebone Black RT8192CU not working"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by Nathan_Wolfe on 2014-04-02
Ok I am new to Linux and have spent the better part of two days trying to get this to work.

Result of 
```
lsusb
```

Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
ifconfig
```

shows eth0 and lo but nothing for wireless.


```



########## wireless info START ##########






##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux ubuntu-armhf 3.8.13-bone30 #1 SMP Thu Nov 14 06:23:24 UTC 2013 armv7l armv7l armv7l GNU/Linux

##### lspci #####

##### lsusb #####

Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)

# loopback network interface

auto lo

iface lo inet loopback

# primary network interface

auto eth0

iface eth0 inet dhcp

#hwaddress ether <MAC address removed>

##### iwconfig #####

##### route #####

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0


##### resolv.conf #####

nameserver 192.168.11.1

##### nm-tool #####

##### NetworkManager.state #####

##### NetworkManager.conf #####

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

rtl8192cu              87088  0 
rtlwifi                76713  1 rtl8192cu
rtl8192c_common        59537  1 rtl8192cu
mac80211              494585  3 rtlwifi,rtl8192c_common,rtl8192cu
cfg80211              421293  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.8.13-30/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     121073B066033BC0F990E22
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
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
vermagic:       3.8.13-bone30 SMP mod_unload modversions ARMv7 p2v8 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
filename:       /lib/modules/3.8.13-bone30/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BA0AC747DDF6CF6A0206365
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.13-bone30 SMP mod_unload modversions ARMv7 p2v8 

filename:       /lib/modules/3.8.13-bone30/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192common-.ko
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
vermagic:       3.8.13-bone30 SMP mod_unload modversions ARMv7 p2v8 


##### modules #####

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
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb

##### udev rules #####

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    1.562733] bone-capemgr bone_capemgr.9: slot #0: Requesting firmware 'DMCC Mk.06-Mk06.dtbo' for board-name 'DMCC (Dual Motor Control Cape)', version 'Mk06'
[   14.364641] bone-capemgr bone_capemgr.9: failed to load firmware 'DMCC Mk.06-Mk06.dtbo'
[   14.382656] bone-capemgr bone_capemgr.9: slot #5: Requesting firmware 'cape-boneblack-hdmi-00A0.dtbo' for board-name 'Bone-Black-HDMI', version '00A0'
[   14.384381] bone-capemgr bone_capemgr.9: slot #4: Requesting firmware 'cape-bone-2g-emmc1.dtbo' for board-name 'Bone-LT-eMMC-2G', version '00A0'
[   14.581248] bone-capemgr bone_capemgr.9: slot #6: Requesting firmware 'cape-boneblack-hdmin-00A0.dtbo' for board-name 'Bone-Black-HDMIN', version '00A0'
[   15.896656] rtl8192cu 1-1:1.0: usb_probe_interface
[   15.896686] rtl8192cu 1-1:1.0: usb_probe_interface - got id
[   15.903153] rtl8192cu: Chip version 0x11
[   16.970364] rtl8192cu: MAC address: <MAC address removed>
[   16.970402] rtl8192cu: Board Type 0
[   16.970513] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   16.973550] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   16.991235] rtlwifi:rtl_fw_cb():<0-0> Firmware is too big!


########## wireless info END ############

```

I have been through so many fixes that I have found online that I can't keep straight what I have done at this point. I flashed a new image on a sdcard and am ready to do as suggested. 
As I said I am new to linux so don't assume that I know how to do anything. 

Thanks

---

