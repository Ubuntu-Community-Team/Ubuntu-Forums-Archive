---
title: "Alienware 17 fresh install of Ubuntu 14.04.2 can't connect wired or wireleslly"
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by Tony_Martinez on 2015-05-26
I recently installed Ubuntu 14.04.2 on my Alienware 17 laptop, and haven't been able to connect
to the internet through wifi or wired connection. I tried running the scripts posted in the sticky
but they require an internet connection.

I was able to find out the make of the Ethernet and Network Controllers.

Ethernet Controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 10)
Network Controller: Qualcomm Atheros Device 003e (rev 20)

I also tried checking available drivers to install and didn't find any.

This is my result after running the command " lspci -n | egrep '0200|0280' | awk '{print$3}' "

```
 1969:e091
168c:003e
```

---

### Post by Tony_Martinez on 2015-05-29
bump

---

### Post by Tony_Martinez on 2015-05-29
Bump again

---

### Post by Tony_Martinez on 2015-05-29
So I was mistaken, the ethernet does work, so I updated and ran the wireless script.
```

########## wireless info START ##########

Report from: 29 May 2015 17:47 PDT -0700

Booted last: 29 May 2015 17:45 PDT -0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 10)
	Subsystem: Dell Device [1028:0685]
	Kernel driver in use: alx

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
	Subsystem: Bigfoot Networks, Inc. Device [1a56:1525]

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader [10ec:5227] (rev 01)

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 002: ID 187c:0528 Alienware Corporation 
Bus 003 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_wmi               12761  0 
mxm_wmi                13021  1 nouveau
sparse_keymap          13948  1 dell_wmi
ath3k                  13331  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
bluetooth             446409  12 bnep,ath3k,btusb,rfcomm
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  3 dell_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.0.0.199  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:9:7082:17f9::b20d/128 Scope:Global
          inet6 addr: 2601:9:7082:17f9:7520:74f5:17c9:3375/64 Scope:Global
          inet6 addr: fe80::36e6:d7ff:fe31:3a46/64 Scope:Link
          inet6 addr: 2601:9:7082:17f9:36e6:d7ff:fe31:3a46/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4213200 (4.2 MB)  TX bytes:278446 (278.4 KB)
          Interrupt:18 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ca.comcast.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root       860     1  0 17:45 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.199
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

  IPv6 Settings:
    Address:         2601:9:7082:17f9::b20d
    Prefix:          128
    Gateway:         fe80::68ee:96ff:fece:5084

    Address:         2601:9:7082:17f9:7520:74f5:17c9:3375
    Prefix:          64
    Gateway:         fe80::68ee:96ff:fece:5084

    Address:         2601:9:7082:17f9:36e6:d7ff:fe31:3a46
    Prefix:          64
    Gateway:         fe80::68ee:96ff:fece:5084

    Address:         fe80::36e6:d7ff:fe31:3a46
    Prefix:          64
    Gateway:         fe80::68ee:96ff:fece:5084

    Address:         2601:9:7082:17f9::b20d
    Prefix:          128
    Gateway:         ::

    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     8449188E53D477A663A0DBF
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512

##### module parameters #################

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   13.259873] usb 3-9: Direct firmware load failed with error -2
[   13.260315] ath3k: probe of 3-9:1.0 failed with error -12

########## wireless info END ############

```

---

### Post by chili555 on 2015-05-29
> Qualcomm Atheros Device [168c:003e] At this time, there is no support for your device aside from a reputedly unstable, experimental kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

Along about post #115, the arduous process is described. I haven't tried it and can't advise you further. Sorry.

If it were me, I'd buy a cheap USB wireless and wait a couple of months or so until this makes it into the mainline Ubuntu kernel.

---

### Post by Tony_Martinez on 2015-05-30
I was afraid that was the case. Thank you for your help.

However, I messed up my windows bootloader when I was trying to remove Ubuntu using EasyBCD.
I made another post about it here [http://ubuntuforums.org/showthread.php?t=2280342](http://ubuntuforums.org/showthread.php?t=2280342)

Any help would be appreciated.

EDIT: NEVERMIND

---

