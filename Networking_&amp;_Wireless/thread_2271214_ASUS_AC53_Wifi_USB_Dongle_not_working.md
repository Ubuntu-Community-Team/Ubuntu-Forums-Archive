---
title: "ASUS AC53 Wifi USB Dongle not working"
date: 2015-03-28
forum: Networking &amp; Wireless
---

### Post by Simo_Hayha on 2015-03-28
Hi!

I can't get Asus AC53 wifi USB to work after 10 hours researching on the web. I managed to install 2 drivers from Asus using "ndiswrapper". Those drivers are:

[COLOR=#444444][FONT=UbuntuRegular]bcmwlhigh5.inf
[/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular]bcmwlhigh6.inf

but still without results. Please find attached the results of the wireless script:

[/FONT][/COLOR]```
[FONT=Ubuntu Mono]########## wireless info START ##########[/FONT]

Report from: 28 Mar 2015 11:14 GMT +0000

Booted last: 28 Mar 2015 09:46 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:   trusty

##### kernel ############################

Linux 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64     x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 005: ID 0b05:17e5 ASUSTek Computer, Inc. 
Bus 010 Device 004: ID 05a4:9881 Ortek Technology, Inc. IR receiver [VRC-1100 Vista MCE Remote Control]
Bus 010 Device 002: ID 1532:001c Razer USA, Ltd RZ01-0036 Optical Gaming Mouse [Abyssus]
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:3832 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              494362  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.222  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe73:9272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190838402 (190.8 MB)  TX bytes:17069807 (17.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.222
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

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        25:26:EE:FE:32:C9:58:B4:CD:85:CA:5F:BF:EB:ED:A1:75:D1:B2:18
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz     band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################
 [FONT=Ubuntu Mono]########## wireless info END ############[/FONT]
```

[COLOR=#444444][FONT=UbuntuRegular]I  really appreciate any help you can give me.
[/FONT][/COLOR]

---

### Post by chili555 on 2015-03-28
Does ndiswrapper load as expected?```
 sudo modprobe ndiswrapper
``` Please run and post: ```
ndiswrapper -l
``` and also: ```
dmesg | grep ndis
```Thanks.

---

### Post by Simo_Hayha on 2015-03-28
Hi, thanks for your replu. This is what I got:

```
~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0B05:17E5) present
bcmwlhigh6 : driver installed
    device (0B05:17E5) present
John@John-desktop2:~$ dmesg | grep ndis
[   10.621484] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   10.622258] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.226131] ndiswrapper: driver bcmwlhigh5 (ASUS,02/28/2013, 6.30.145.30) loaded
[   12.232190] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fa9000, 32000, 8
[   12.232196] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fb0d00, 32000, 9
[   12.232198] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fb8a00, 32000, 9
[   12.232200] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fc0700, 32000, 9
[   12.232204] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fc8400, 32000, 9
[   12.232206] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fd0100, 32000, 8
[   12.232209] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fd7e00, 32000, 9
[   12.232210] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fdfb00, 32000, 9
[   12.232212] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fe7800, 32000, 9
[   12.232214] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012fef500, 32000, 9
[   12.232216] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012ff7200, 32000, 8
[   12.232218] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012ffef00, 32000, 9
[   12.232220] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013006c00, 32000, 9
[   12.232222] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001300e900, 32000, 9
[   12.232224] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013016600, 32000, 9
[   12.232226] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001301e300, 32000, 8
[   12.232227] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013026000, 32000, 8
[   12.232229] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001302dd00, 32000, 9
[   12.232231] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013035a00, 32000, 9
[   12.232233] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001303d700, 32000, 9
[   12.232235] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013045400, 32000, 9
[   12.232237] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001304d100, 32000, 8
[   12.232238] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013054e00, 32000, 9
[   12.232240] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001305cb00, 32000, 9
[   12.232242] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013064800, 32000, 9
[   12.232244] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001306c500, 32000, 9
[   12.232246] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013074200, 32000, 8
[   12.232247] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001307bf00, 32000, 9
[   12.232249] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013083c00, 32000, 9
[   12.232251] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001308b900, 32000, 9
[   12.232254] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013093600, 32000, 9
[   12.232256] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001309b300, 32000, 8
[   12.232257] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130a3000, 32000, 8
[   12.232259] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130aad00, 32000, 9
[   12.232261] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130b2a00, 32000, 9
[   12.232263] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130ba700, 32000, 9
[   12.232264] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130c2400, 32000, 9
[   12.232266] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130ca100, 32000, 8
[   12.232268] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130d1e00, 32000, 9
[   12.232270] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130d9b00, 32000, 9
[   12.232271] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130e1800, 32000, 9
[   12.232273] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130e9500, 32000, 9
[   12.232275] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130f1200, 32000, 8
[   12.232277] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130f8f00, 32000, 9
[   12.232279] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013100c00, 32000, 9
[   12.232281] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013108900, 32000, 9
[   12.232283] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013110600, 32000, 9
[   12.232285] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013118300, 32000, 8
[   12.232287] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013120000, 32000, 8
[   12.232288] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013127d00, 32000, 9
[   34.799001] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   34.799008] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   34.799014] ndiswrapper (mp_halt:254): device ffff8800b8b128c0 is not initialized - not halting
[   34.799016] ndiswrapper: device eth%d removed
[   34.799175] ndiswrapper: probe of 10-4:1.0 failed with error -22
[   34.799220] usbcore: registered new interface driver ndiswrapper


```

---

### Post by chili555 on 2015-03-28
> bcmwlhigh5 : driver installed
    device (0B05:17E5) present
bcmwlhigh6 : driver installed
    device (0B05:17E5) presentI think you need one or the other but not both. I suspect it is 6, since you have a 64-bit system. I suggest you remove 5 and reboot.```
sudo ndiswrapper -e bcmwlhigh5
```After a reboot, let us see:```
dmesg | grep ndis
```

---

### Post by Simo_Hayha on 2015-03-28
after reboot, I got this:

```
John@John-desktop2:~$ dmesg | grep ndis
[   10.970307] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   10.971015] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.473777] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   12.473785] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   12.473789] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   12.473792] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   12.473796] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   12.473799] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   12.473802] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   12.473805] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   12.473808] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   12.473811] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   12.473815] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   12.473819] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   12.473822] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   12.473825] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   12.473829] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   12.473832] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   12.473835] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   12.473837] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   12.473840] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   12.473843] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   12.473846] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   12.473850] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   12.473854] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   12.473856] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   12.473863] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   12.473866] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   12.473869] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   12.473872] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   12.473875] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   12.473884] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   12.473886] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   12.473888] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   12.473891] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   12.473892] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[   12.474423] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[   12.474477] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2015-03-28
Where did you get the files? I downloaded and extracted the driver files from Asus and I see:```
bcmh43xx64.cat  bcmwlhigh564.sys  bcmwlhigh5.sys
bcmh43xx.cat    bcmwlhigh5.inf    MfgDriver

```In other words, no bcmwlhigh6.inf.

---

### Post by Simo_Hayha on 2015-03-28
When I downloaded the drivers, there were multiple folders, I got the "[COLOR=#444444][FONT=UbuntuRegular]bcmwlhigh5.inf" from the XP folder and "[COLOR=#444444][FONT=UbuntuRegular]bcmwlhigh6.inf" from Win7 folder. There is also a AMD64 folder but inside there is only a .exe that doesn't contain a .inf

I am very new at all this so I may have missed something.

I removed [COLOR=#444444][FONT=UbuntuRegular]"bcmwlhigh6.inf" and installed back "[COLOR=#444444][FONT=UbuntuRegular]bcmwlhigh5.inf".
```
bcmwlhigh5 : driver installed
    device (0B05:17E5) present


```

Rebooted and used:

[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]```
dmesg | grep ndis
```[COLOR=#444444][FONT=UbuntuRegular][COLOR=#444444][FONT=UbuntuRegular]
[/FONT][/COLOR][/FONT][/COLOR]
This is what I got this time:

```
john@john-desktop2:~$ dmesg | grep ndis
[   10.680002] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   10.680842] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   12.076454] ndiswrapper: driver bcmwlhigh5 (ASUS,02/28/2013, 6.30.145.30) loaded
[   12.082165] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013021000, 32000, 8
[   12.082170] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013028d00, 32000, 9
[   12.082173] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013030a00, 32000, 9
[   12.082175] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013038700, 32000, 9
[   12.082177] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013040400, 32000, 9
[   12.082179] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013048100, 32000, 8
[   12.082181] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001304fe00, 32000, 9
[   12.082183] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013057b00, 32000, 9
[   12.082184] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001305f800, 32000, 9
[   12.082186] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013067500, 32000, 9
[   12.082188] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001306f200, 32000, 8
[   12.082190] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013076f00, 32000, 9
[   12.082193] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001307ec00, 32000, 9
[   12.082195] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013086900, 32000, 9
[   12.082196] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001308e600, 32000, 9
[   12.082198] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013096300, 32000, 8
[   12.082201] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001309e000, 32000, 8
[   12.082203] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130a5d00, 32000, 9
[   12.082204] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130ada00, 32000, 9
[   12.082206] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130b5700, 32000, 9
[   12.082208] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130bd400, 32000, 9
[   12.082209] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130c5100, 32000, 8
[   12.082211] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130cce00, 32000, 9
[   12.082213] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130d4b00, 32000, 9
[   12.082215] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130dc800, 32000, 9
[   12.082217] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130e4500, 32000, 9
[   12.082218] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130ec200, 32000, 8
[   12.082220] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130f3f00, 32000, 9
[   12.082222] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900130fbc00, 32000, 9
[   12.082224] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013103900, 32000, 9
[   12.082225] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001310b600, 32000, 9
[   12.082227] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013113300, 32000, 8
[   12.082229] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001311b000, 32000, 8
[   12.082230] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013122d00, 32000, 9
[   12.082232] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001312aa00, 32000, 9
[   12.082234] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013132700, 32000, 9
[   12.082236] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001313a400, 32000, 9
[   12.082237] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013142100, 32000, 8
[   12.082239] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013149e00, 32000, 9
[   12.082241] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013151b00, 32000, 9
[   12.082242] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013159800, 32000, 9
[   12.082245] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013161500, 32000, 9
[   12.082246] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013169200, 32000, 8
[   12.082248] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013170f00, 32000, 9
[   12.082250] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013178c00, 32000, 9
[   12.082251] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013180900, 32000, 9
[   12.082253] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013188600, 32000, 9
[   12.082257] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013190300, 32000, 8
[   12.082258] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90013198000, 32000, 8
[   12.082260] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001319fd00, 32000, 9
[   34.643105] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   34.643112] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   34.643118] ndiswrapper (mp_halt:254): device ffff8800b20968c0 is not initialized - not halting
[   34.643120] ndiswrapper: device eth%d removed
[   34.643279] ndiswrapper: probe of 10-4:1.0 failed with error -22
[   34.643322] usbcore: registered new interface driver ndiswrapper


```

I really appreciate your patience

---

### Post by chili555 on 2015-03-28
ndiswrapper does require XP driver files, so we need the bcmwlhigh5 and not 6. We are disappointed, of course, to see the errors.

Is the 64-bit .sys file in the same folder as bcmwlhigh5.inf? I believe it is bcmwlhigh5[COLOR="#FF0000"]64[/COLOR].sys. I think ndiswrapper is supposed to grab the appropriate .sys file when you load the .inf.

What does this tell us?```
ls /etc/ndiswrapper/bcmwlhigh5/
```> I am very new at all this so I may have missed something.No worries.This is pretty esoteric stuff. There are not many on this forum who know much about ndiswrapper, .inf and .sys files, etc. I only know barely enough!

---

### Post by Simo_Hayha on 2015-03-29
Thanks for keep helping me!

Yes. What I got this time was:

```
john@john-desktop2:~$ ls /etc/ndiswrapper/bcmwlhigh5/
0B05:17C9.F.conf  0B05:17E5.F.conf  bcmwlhigh564.sys  bcmwlhigh5.inf


```

---

### Post by Simo_Hayha on 2015-03-31
Hi chili555, any idea what to do next?

Many thanks

---

