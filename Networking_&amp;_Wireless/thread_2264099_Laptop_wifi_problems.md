---
title: "Laptop wifi problems"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by 1200wd on 2015-02-05
Wifi on my laptop has been working for a year, but after a recent update it started to get slowly and instable. So I tried a few things and reinstalled the network-manager. But now it's totally broken. The hardware list tells me the network controller is unclaimed, but the drivers should be included in the kernel. Upgraded to a new kernel but that didn't help.

```
sudo lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c3500000-c3501fff
```

This is the output of the wireless script:

```

########## wireless info START ##########

Report from: 05 Feb 2015 14:17 CET +0100

Booted last: 05 Feb 2015 14:05 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 1a)
    Subsystem: Intel Corporation Device [8086:0000]

08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)

0e:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:1853]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 004: ID 10f1:1a37 Importek 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

cfg80211              484040  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.251.25  Bcast:192.168.251.255  Mask:255.255.255.0
          inet6 addr: fe80::e611:5bff:fe60:2e36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5463 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3768977 (3.7 MB)  TX bytes:838493 (838.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.251.1   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.251.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### nm-tool ###########################

** (process:30678): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

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

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ASUS_5G]] (600 root)
[connection] id=ASUS_5G | type=802-11-wireless
[802-11-wireless] ssid=ASUS_5G | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UPC WifiSpots]] (600 root)
[ipv6] method=auto
[connection] id=UPC WifiSpots | type=802-11-wireless
[802-11-wireless] ssid=UPC WifiSpots | mac-address=<MAC address>
[802-1x] system-ca-certs=true
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR_EXT]] (600 root)
[connection] id=NETGEAR_EXT | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR_EXT | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ARV75190BCB9C]] (600 root)
[connection] id=ARV75190BCB9C | type=802-11-wireless
[802-11-wireless] ssid=ARV75190BCB9C | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC240645313]] (600 root)
[connection] id=UPC240645313 | type=802-11-wireless
[802-11-wireless] ssid=UPC240645313 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7340]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7340 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7340 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTHub3-XRN8]] (600 root)
[connection] id=BTHub3-XRN8 | type=802-11-wireless
[802-11-wireless] ssid=BTHub3-XRN8 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Amsterdam (based on set time zone)

country NL:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5330 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

loop
lp
rtc
vboxdrv

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
blacklist ehci_hcd

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

sudo rmmod psmouse 2>>/home/lennart/rc.log

rfkill block bluetooth 2>>/home/lennart/rc.log

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.4/0000:0e:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```

Any ideas?

---

### Post by jeremy31 on 2015-02-05
Something caused the module to not load, try ```
sudo modprobe iwlwifi
```

---

### Post by 1200wd on 2015-02-05
Thanks for your answer!

Tried modprobe, but that does not load the module and doesn't give any output also not in verbose mode.

No output in syslog as well. Only this about the cfg80211 module, but I suppose that is correct?

```
Feb  5 18:49:39 archibald kernel: [15558.705799] cfg80211: Calling CRDA to update world regulatory domain
Feb  5 18:49:39 archibald kernel: [15558.748841] Intel(R) Wireless WiFi driver for Linux, in-tree:
Feb  5 18:49:39 archibald kernel: [15558.748844] Copyright(c) 2003-2013 Intel Corporation
Feb  5 18:49:39 archibald kernel: [15558.761721] cfg80211: World regulatory domain updated:
Feb  5 18:49:39 archibald kernel: [15558.761724] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  5 18:49:39 archibald kernel: [15558.761725] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:49:39 archibald kernel: [15558.761727] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:49:39 archibald kernel: [15558.761728] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:49:39 archibald kernel: [15558.761729] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:49:39 archibald kernel: [15558.761730] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

---

### Post by jeremy31 on 2015-02-05
Power down the laptop and after booting do ```
lspci -nnk | grep -iA2
``` and hope it changed from what the script reported

---

### Post by 1200wd on 2015-02-05
That command gives no results, but after rebooting loading the iwlwifi module gives this result:

```
$ sudo modprobe iwlwifi -v
insmod /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
```

However no other logs and no wifi

---

### Post by jeremy31 on 2015-02-05
> **1200wd said:**
> That command gives no results, but after rebooting loading the iwlwifi module gives this result:

```
$ sudo modprobe iwlwifi -v
insmod /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
```

However no other logs and no wifi

I forgot to type the last part but I suspect it hasn't changed ```
lspci -nnk | grep -iA2 net
```

The modprobe command should have loaded iwldvm also, can you get into BIOS and reset to defaults?

---

### Post by 1200wd on 2015-02-05
That seems to have done the trick. The iwlwifi module is loaded again and wifi is working.
Not sure what changed in the BIOS, I'm sure I didn't make changes by hand the last few days.

But anyway thanks very much for your help!

---

### Post by jeremy31 on 2015-02-05
> **1200wd said:**
> That seems to have done the trick. The iwlwifi module is loaded again and wifi is working.
Not sure what changed in the BIOS, I'm sure I didn't make changes by hand the last few days.

But anyway thanks very much for your help!

Something happened with BIOS, not sure what but it prevented Ubuntu from detecting the correct ID for your wifi as the script reported this ```
[COLOR=#000000][FONT=Ubuntu Mono]07:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:422b] (rev 1a)[/FONT][/COLOR]    Subsystem: Intel Corporation Device [8086:0000]
``` and I doubt that subsystem [8086:0000] is correct

---

