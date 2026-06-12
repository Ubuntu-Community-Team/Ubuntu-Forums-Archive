---
title: "Wifi problem on Lubuntu 14.04 - No past solutions worked"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by marco102 on 2015-04-11
Hi, I'm new with Lubuntu. I've installed it on an old Asus A6 series. It works perfectly, except for the WiFi connection.
The problem is that I can't connect to my WiFi. I just can connect wired.
I've already checked some possible solutions in this forum, but nothing seems to work for me.
Please, note that:
- I've already upgraded the system
- I've tryed the "simple-solution" to see if it was an "icon-problem", but entering manually ns-applet I just got another icon about wired connection, not about the wifi connection
- I've checked my wifi card, a Broadcom BCM4318. I've followed the procedure explained here ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)), installing the correct drivers. I just didn't the last passage, about switching between drivers.

Here are my wireless-info:

```

########## wireless info START ##########

Report from: 11 Apr 2015 14:19 CEST +0200

Booted last: 11 Apr 2015 14:04 CEST +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #45~14.04.1-Ubuntu SMP Tue Mar 24 11:13:52 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, acpi=force, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: ASUSTeK Computer Inc. L8400B or L3C/S notebook [1043:1045]
    Kernel driver in use: 8139too

02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: ASUSTeK Computer Inc. A6U notebook embedded card [1043:120f]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 002: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

##### lsmod #############################

wl                   6144840  1 
cfg80211              418839  1 wl

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe33:40e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18512113 (18.5 MB)  TX bytes:2843425 (2.8 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/Netgear]] (600 root)
[connection] id=Netgear | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        87:39:A8:87:A4:1D:D0:55:86:D0:6C:96:CA:93:91:C1:4D:16:D2:EB
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   20.075246] wl driver 6.30.223.248 (r487574) failed with code 21
[   20.076008] EIP is at wdev_priv.part.9+0x3/0x5 [wl]
[   20.076008]  [<f964ca93>] wl_free_if.isra.15+0x23/0xa0 [wl]
[   20.076008]  [<f964d2c8>] wl_free+0x78/0x220 [wl]
[   20.076008]  [<f964d7e1>] wl_pci_probe+0x371/0x730 [wl]
[   20.076008]  [<f86c7073>] wl_module_init+0x73/0x1000 [wl]
[   20.076008] EIP: [<f96552c2>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f49dfbac

########## wireless info END ############


```

I really don't know what to do. Please, help me.

---

### Post by jeremy31 on 2015-04-11
Since you have the Broadcom proprietary driver installed, you need to remove it
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-dkms broadcom-sta-common
```

And install the firmware for the open source b43 module
```
sudo apt-get install firmware-b43-installer
```

Reboot and if the wifi isn't working then, post the new results from the wireless script

---

### Post by marco102 on 2015-04-12
After a reboot, now it works! Thank you jeremy31. :p
Just for informational purpose, why did I need to remove the Broadcom proprietary driver?

---

### Post by jeremy31 on 2015-04-12
The Broadcom proprietary driver blacklists the needed modules and could interfere

---

### Post by marco102 on 2015-04-12
Ok, I got it. Thank you for the extra explanation!

---

