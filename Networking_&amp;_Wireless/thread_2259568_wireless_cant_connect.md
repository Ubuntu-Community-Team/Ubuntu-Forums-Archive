---
title: "wireless cant connect"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by dewster77 on 2015-01-05
hi.. Im running Zorin on an Acer Aspire 5610Z and cant get my wireless to connect..Plz help me!

```

########## wireless info START ##########

Report from: 05 Jan 2015 09:21 CST -0600

Booted last: 05 Jan 2015 08:42 CST -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Zorin
Description:    Zorin OS 9
Release:    9
Codename:    trusty

##### kernel ############################

Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Zorin Desktop

##### lspci #############################

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel driver in use: b43-pci-bridge

06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Kernel driver in use: b44

##### lsusb #############################

Bus 001 Device 002: ID 5986:0100 Acer, Inc Orbicam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ssb_hcd                12749  0 
ssb                    51854  2 b44,ssb_hcd
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe28:160b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:745612 (745.6 KB)  TX bytes:84875 (84.8 KB)
          Interrupt:21 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.80
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ssb_hcd]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:74:D8:78:9C:AA:5E:CB:12:DD:D1:AA:C2:15:E1:2C:62:FC:AC:A5
sig_hashalgo:   sha512

[ssb]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:74:D8:78:9C:AA:5E:CB:12:DD:D1:AA:C2:15:E1:2C:62:FC:AC:A5
sig_hashalgo:   sha512

##### module parameters #################

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[  108.800236] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  108.800250] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[  341.984152] b44 ssb1:0 eth0: Link is down
[  468.984278] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  468.984291] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[  927.984158] b44 ssb1:0 eth0: Link is down
[  929.338670] b44 ssb1:0 eth0: powering down PHY (repeated 2 times)
[  943.984294] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[  943.984309] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 1171.258510] b44 ssb1:0 eth0: powering down PHY
[ 1329.316158] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[ 1329.316178] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[ 1329.316190] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[ 1329.316203] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[ 1329.356329] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[ 1329.376716] b44 ssb2:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC 'eth0' [IF]>
[ 1332.984269] b44 ssb2:0 eth0: Link is up at 100 Mbps, full duplex
[ 1332.984282] b44 ssb2:0 eth0: Flow control is off for TX and off for RX
[ 1561.531665] b44 ssb2:0 eth0: powering down PHY
[ 1640.584164] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[ 1640.584183] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[ 1640.584195] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[ 1640.584208] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[ 1640.624295] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[ 1640.646645] b44 ssb3:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC 'eth0' [IF]>
[ 1643.996266] b44 ssb3:0 eth0: Link is up at 100 Mbps, full duplex
[ 1643.996280] b44 ssb3:0 eth0: Flow control is off for TX and off for RX

########## wireless info END ############ 
```

---

### Post by chili555 on 2015-01-05
I suggest you read the sticky at the top. [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by dewster77 on 2015-01-05
do I need to reboot to get this to work> I am able to turn my wireless off and on but its not showing any available wireless

---

### Post by chili555 on 2015-01-05
Please reboot with the ethernet detached and see if it works. If not, show us the wirelss_script once more.

---

