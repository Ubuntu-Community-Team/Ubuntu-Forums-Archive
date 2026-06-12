---
title: "Atheros QCA9565 / AR9565"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by Tristan_Alan_Dulla on 2014-05-06
here is the info:



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


##### kernel #####


Linux Tristan 3.5.0-49-generic #74~precise1-Ubuntu SMP Fri May 2 21:32:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell Device [1028:020c]
	Kernel modules: wl
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
	Subsystem: Dell Device [1028:05f3]
	Kernel driver in use: r8169


##### lsusb #####


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 002: ID 0bc2:a003 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 0c45:64af Microdia 
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### lsmod #####


ath3k                  12918  0 
wl                   3074942  0 
cfg80211              208382  1 wl
bluetooth             212001  25 rfcomm,bnep,btusb,ath3k
lib80211               14382  1 wl


##### modinfo #####


filename:       /lib/modules/3.5.0-49-generic/updates/dkms/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0.1
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     FBB03F235485371B207CD8D
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*
depends:        bluetooth
vermagic:       3.5.0-49-generic SMP mod_unload modversions 


filename:       /lib/modules/3.5.0-49-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.5.0-49-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


##### modules #####


lp
rtc
lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   10.061421] wl: module license 'MIXED/Proprietary' taints kernel.


########## wireless info END ############

---

### Post by chili555 on 2014-05-06
First, a Broadcom driver is no help and probably a hindrance; let's remove it:```
sudo apt-get purge bcmwl-kernel-source
```As for the correct driver for your device, please see my answer here: [http://askubuntu.com/questions/461149/wireless-network-card-is-dectected-but-not-working/461177#461177](http://askubuntu.com/questions/461149/wireless-network-card-is-dectected-but-not-working/461177#461177)

---

