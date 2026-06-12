---
title: "CAn't install my wireless card on alienware 13"
date: 2016-02-06
forum: Networking &amp; Wireless
---

### Post by ahmedbj2 on 2016-02-06
Hi and thanks for your time
i have an alienware 13 and i can't install my wireless card i followed lot of solutions but didn't solve the problem
here is a description 
```


########## wireless info START ##########

Report from: 06 Feb 2016 12:08 WET +0000

Booted last: 06 Feb 2016 11:54 WET +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1525]

02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 10)
    Subsystem: Dell Device [1028:0683]
    Kernel driver in use: alx

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 006: ID 187c:0527 Alienware Corporation 
Bus 001 Device 005: ID 0c45:6708 Microdia 
Bus 001 Device 004: ID 04f3:0441 Elan Microelectronics Corp. 
Bus 001 Device 008: ID 05ac:12a8 Apple, Inc. 
Bus 001 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

ath3k                  16384  0 
bluetooth             491520  12 bnep,ath3k,btusb,rfcomm
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  1 nouveau
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau

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
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:172.20.10.2  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36954 (36.9 KB)  TX bytes:36139 (36.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    0      0        0 eth1
172.20.10.0     0.0.0.0         255.255.255.240 U     1      0        0 eth1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       728     1  0 11:54 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            ipheth
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.20.10.2
    Prefix:          28 (255.255.255.240)
    Gateway:         172.20.10.1

    DNS:             172.20.10.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
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

##### iw reg get ########################

Region: Africa/Casablanca (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     7EE336E583AE05D4924225A
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0xe091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    3.525903] usb 1-8: Direct firmware load for ar3k/AthrBT_0x00000200.dfu failed with error -2
[    3.533074] ath3k: probe of 1-8:1.0 failed with error -2
[    4.065713] nouveau 0000:03:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[    4.065718] nouveau 0000:03:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[    5.656133] nouveau 0000:03:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[    5.656138] nouveau 0000:03:00.0: Direct firmware load for nouveau/fuc409c failed with error -2

########## wireless info END ############



```
If someone can help

---

### Post by chili555 on 2016-02-06
Did you try this solution? [http://askubuntu.com/questions/661424/ubuntu-14-04-wireless-not-working-no-network-interface-atheros-168c003e-dev](http://askubuntu.com/questions/661424/ubuntu-14-04-wireless-not-working-no-network-interface-atheros-168c003e-dev)

---

