---
title: "Belkin N600 DB Wi-Fi USB Adapter not working in 14.04 LTS"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by evan17 on 2014-08-13
Hey all... I have been trying to get a **Belkin N600 Dual-Band Wi-Fi USB Adapter** functioning in Ubuntu 14.04 LTS for the last few days without any luck. So far I have tried:


[LIST]
[*]Using ndiswrapper/ndisgtk to install various Windows drivers from the disk that came with it as well as some Belkin Windows drivers from the web 
[*]Following these instructions: [http://www.brianzier.com/getting-the-belkin-n600-db-to-work-on-ubuntu](http://www.brianzier.com/getting-the-belkin-n600-db-to-work-on-ubuntu) 
[/LIST]

...as well as finding obscure semi-relevant stuff in the forums here but nothing seems to be working. I can get to the point where **ndiswrapper -l** says:

> netrtwlanu : driver installed
    device (050D:110A) present

...and the device shows up when I check **lsusb**:

> Bus 003 Device 007: ID 050d:110a Belkin Components 

...however it does not show up as a network device anywhere, for instance when I check **ifconfig** or or do a **sudo lshw -c Network -sanitize**. All I see in these instances is "eth0" which is my internal ethernet and "lo" which is the Local Loopback. Also, the usb device never shows any lights or indication that it is active or doing anything at all.

When I run "**dmesg | grep -e ndis -e wlan**" I see the following errors:

> 
[  510.146312] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[  510.146328] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[  510.146338] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  510.146352] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  510.146375] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  510.146385] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  510.146394] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  510.146408] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  510.146417] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  510.146426] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  510.146438] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  510.146451] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  510.146460] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  510.146469] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  510.146481] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  510.146490] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  510.146500] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  510.146509] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetOptionalHandlers'
[  510.146518] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  510.146527] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  510.146536] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  510.146545] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  510.146558] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  510.146568] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  510.146577] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIdleNotificationConfirm'
[  510.146586] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIdleNotificationComplete'
[  510.146595] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  510.146605] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  510.146614] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  510.146623] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  510.146640] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExAllocatePool'
[  510.146658] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[  510.146666] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[  510.146723] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  510.146731] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  510.146738] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  510.146746] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  510.146750] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlanu'
[  510.147654] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlanu; check system log for messages from 'loadndisdriver'


This is a Lenovo Thinkpad T440p. My internal network card is a Realtek 8192EE chipset which from what I understand does not have any linux drivers which is why I was attempting to use the usb dongle instead for wifi. I'm not super experienced with Ubuntu and Linux so I've kind of exhausted my own knowledge at this point, any help would be super appreciated. Below is the results of my wireless script. Thanks!

```

########## wireless info START ##########

Report from: 13 Aug 2014 10:15 EDT -0400

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
    Subsystem: Lenovo ThinkPad T440p [17aa:220e]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 138a:0017 Validity Sensors, Inc. 
Bus 003 Device 007: ID 050d:110a Belkin Components 
Bus 003 Device 006: ID 04f2:b39a Chicony Electronics Co., Ltd 
Bus 003 Device 005: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ndiswrapper           283985  0 
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ad2:44ff:fe30:fc83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106610923 (106.6 MB)  TX bytes:3407946 (3.4 MB)
          Interrupt:20 Memory:f0600000-f0620000 

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Home Wired] ---------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

no-auto-default=<MAC addr eth0>,

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos #####

[ndiswrapper]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #####

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules #####

lp
rtc

##### blacklists #####

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
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

##### udev rules #####

# PCI device 0x8086:0x153a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

[    0.787036] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.947631] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    5.981739] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   10.464472] type=1400 audit(1407938326.196:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=395 comm="apparmor_parser"
[   10.465024] type=1400 audit(1407938326.200:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=395 comm="apparmor_parser"
[   69.204159] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   99.819264] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   99.963101] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   99.963117] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   99.963127] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   99.963141] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   99.963164] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   99.963174] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   99.963183] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   99.963198] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   99.963207] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   99.963216] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   99.963228] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   99.963241] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   99.963250] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   99.963259] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   99.963271] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   99.963281] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   99.963290] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   99.963299] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetOptionalHandlers'
[   99.963308] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   99.963317] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   99.963326] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   99.963335] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   99.963349] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   99.963358] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   99.963367] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIdleNotificationConfirm'
[   99.963376] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIdleNotificationComplete'
[   99.963386] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   99.963395] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   99.963405] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   99.963414] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   99.963430] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExAllocatePool'
[   99.963448] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[   99.963456] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[   99.963514] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   99.963522] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   99.963529] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   99.963536] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   99.963540] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlanu'
[   99.964489] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlanu; check system log for messages from 'loadndisdriver'
[  510.146312] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[  510.146328] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[  510.146338] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  510.146352] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  510.146375] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  510.146385] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  510.146394] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  510.146408] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  510.146417] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  510.146426] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  510.146438] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  510.146451] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  510.146460] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  510.146469] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  510.146481] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  510.146490] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  510.146500] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  510.146509] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetOptionalHandlers'
[  510.146518] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  510.146527] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  510.146536] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  510.146545] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  510.146558] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  510.146568] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  510.146577] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIdleNotificationConfirm'
[  510.146586] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIdleNotificationComplete'
[  510.146595] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  510.146605] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  510.146614] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  510.146623] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  510.146640] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExAllocatePool'
[  510.146658] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[  510.146666] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[  510.146723] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  510.146731] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  510.146738] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  510.146746] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  510.146750] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlanu'
[  510.147654] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlanu; check system log for messages from 'loadndisdriver'

########## wireless info END ############
```

---

### Post by varunendra on 2014-08-14
Hi evan17, Welcome to the forums! :)

Native Linux drivers exist for both your internal card and the USB dongle, just not in the kernel that is installed by default. To try them, you must get rid of ndiswrapper first -
```
sudo modprobe -rv ndiswrapper
sudo apt-get purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper
```

As per the comments in the following bug report, the driver for your internal card exists in kernel 3.16, but you can install it on your current kernel from github (just tried on a Live session of 14.04, compiled fine, can't say about performance though) : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239578)
Pay special attention to **comments #156 and #158** by Larry Finger, based on which, the installation instructions would be (assuming you have a working Internet connection via cable or other means) -
```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
```
..probably followed by a reboot.

For your external USB adapter, in case the above one doesn't work well (or at all) and you need the USB adapter, try the suggestions in this thread (post no. 6 onwards) : [http://ubuntuforums.org/showthread.php?p=12713971](http://ubuntuforums.org/showthread.php?p=12713971)

Please let us know how it goes.

---

### Post by tayj10 on 2014-10-02
I am also having issues getting the same adapter to work on Xubuntu 14.04. I've tried installing as suggested here to no avail. I've also tried Larry's specific rtl8192du drivers from  [FONT=Ubuntu Mono]https://github.com/lwfinger/rtl8192du.git[/FONT] However, I'm having issues compiling. Here is the output when I try to run make:

```
zubu@ZUBU:~/rtl8192du$ make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
zubu@ZUBU:~/rtl8192du$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-32-generic/build M=/home/zubu/rtl8192du  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/zubu/rtl8192du/core/rtw_cmd.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_security.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_debug.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_io.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_ioctl_set.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_ieee80211.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_mlme.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_mlme_ext.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_wlan_util.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_pwrctrl.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_rf.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_recv.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_sta_mgt.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_ap.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_xmit.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_p2p.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_sreset.o
  CC [M]  /home/zubu/rtl8192du/core/rtw_efuse.o
  CC [M]  /home/zubu/rtl8192du/hal/hal_intf.o
  CC [M]  /home/zubu/rtl8192du/hal/hal_com.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_hal_init.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_phycfg.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_rf6052.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_dm.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_rxdesc.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_cmd.o
  CC [M]  /home/zubu/rtl8192du/hal/usb_halinit.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192du_led.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192du_xmit.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192du_recv.o
  CC [M]  /home/zubu/rtl8192du/hal/Hal8192DUHWImg.o
  CC [M]  /home/zubu/rtl8192du/hal/usb_ops_linux.o
  CC [M]  /home/zubu/rtl8192du/hal/rtl8192d_xmit.o
  CC [M]  /home/zubu/rtl8192du/os_dep/osdep_service.o
  CC [M]  /home/zubu/rtl8192du/os_dep/os_intfs.o
/home/zubu/rtl8192du/os_dep/os_intfs.c:874:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/zubu/rtl8192du/os_dep/os_intfs.c:874:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
  CC [M]  /home/zubu/rtl8192du/os_dep/usb_intf.o
  CC [M]  /home/zubu/rtl8192du/os_dep/usb_ops_linux.o
  CC [M]  /home/zubu/rtl8192du/os_dep/ioctl_linux.o
  CC [M]  /home/zubu/rtl8192du/os_dep/xmit_linux.o
  CC [M]  /home/zubu/rtl8192du/os_dep/mlme_linux.o
  CC [M]  /home/zubu/rtl8192du/os_dep/recv_linux.o
  CC [M]  /home/zubu/rtl8192du/os_dep/ioctl_cfg80211.o
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: ‘struct cfg80211_mgmt_tx_params’ declared inside parameter list [enabled by default]
     u64 *cookie)
     ^
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c: In function ‘cfg80211_rtw_mgmt_tx’:
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
  size_t len = params->len;
                     ^
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
  struct ieee80211_channel *chan = params->chan;
                                         ^
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
  const u8 *buf = params->buf;
                        ^
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c: At top level:
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
  .mgmt_tx = cfg80211_rtw_mgmt_tx,
  ^
/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) [enabled by default]
make[2]: *** [/home/zubu/rtl8192du/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/zubu/rtl8192du] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [modules] Error 2

```

Any ideas?

---

### Post by varunendra on 2014-10-02
Hello tayj10, Welcome to the forums!

I finally stole some time to experiment with the driver, and indeed it fails to compile! I don't know C programming, so couldn't debug the errors, nor could find any references or patches to correct the errors.

However, I happen to have an old version of the driver that gives more warnings, but no errors. I have just uploaded it to my dropbox account. Please download it from this link and try it instead of the latest one : [https://dl.dropbox.com/s/at2cwezmq64mfew/rtl8192du-master-old.zip](https://dl.dropbox.com/s/at2cwezmq64mfew/rtl8192du-master-old.zip)

I believe I had downloaded this one from the same link where you got the newer version from. At least it builds fine, can't say about performance. Please try yourself and let us know. I hope whatever bug is causing the make error in the newer one will get fixed soon.

---

### Post by tayj10 on 2014-10-17
Hey,

I finally got a chance to give it another go. That version compiled and installed without issue. Thank you very much for the help!

---

