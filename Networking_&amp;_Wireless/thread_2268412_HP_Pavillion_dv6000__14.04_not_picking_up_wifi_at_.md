---
title: "HP Pavillion dv6000  14.04 not picking up wifi at all"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by GimpTOOTS on 2015-03-08
I have searched the forum for a while now and I can't seem to get my computer to pick up wifi. It is working on a wired connection. I have tryed various things from the forum and I can't get it to read or even pull up that I have wifi. I am new to linux and Ubuntu so this might be a noob thing.  This computer did have windows Vista on it and the wifi worked perfectly. Please help. 




[HTML]########## wireless info START ##########

Report from: 08 Mar 2015 18:00 CDT -0500

Booted last: 08 Mar 2015 17:48 CDT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-31-generic #41~14.04.1-Ubuntu SMP Wed Feb 11 19:30:43 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: wl

05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30bb]
    Kernel driver in use: e100

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wl                   6144840  1 
hp_wmi                 13741  0 
sparse_keymap          13708  1 hp_wmi
cfg80211              418839  1 wl
wmi                    18689  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.16.0.12  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:febf:1cfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4492925 (4.4 MB)  TX bytes:281205 (281.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 eth0
172.16.0.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.16.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.0.1

    DNS:             172.16.0.1

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

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

modinfo: ERROR: Module wl not found.
[wl]

[cfg80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     88153DA7841870E4F2012EE
depends:        
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7B:A2:3B:85:F6:E4:A9:73:F57:C8:69:A0:77:49:26:1D:E0:38:11
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   19.926078] EIP is at wdev_priv.part.9+0x3/0x5 [wl]
[   19.927000]  [<f95cca93>] wl_free_if.isra.15+0x23/0xa0 [wl]
[   19.927113]  [<f95cd2c8>] wl_free+0x78/0x220 [wl]
[   19.927272]  [<f95cd7e1>] wl_pci_probe+0x371/0x730 [wl]
[   19.928005]  [<f82c1073>] wl_module_init+0x73/0x1000 [wl]
[   19.928005] EIP: [<f95d52c2>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f0a15bac

########## wireless info END ############[/HTML]

[ATTACH]260528[/ATTACH]

---

### Post by wildmanne39 on 2015-03-08
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Then:
```
sudo apt-get install firmware-b43-installer
```
Reboot
Thanks

---

### Post by swan2 on 2015-09-23
Had a similar issue with my dv6000 after a clean install of 14.04 LTS.  Network Manager could see the APs but not connect to even an open AP.  I had tried just [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get installing firmware-b43-installer, with no luck.  Purging [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]bcmwl-kernel-source, removing and reinstalling [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]firmware-b43-installer fixed the problem.  Thanks![/FONT][/COLOR]

---

