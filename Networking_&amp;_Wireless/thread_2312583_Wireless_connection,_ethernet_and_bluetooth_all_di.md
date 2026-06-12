---
title: "Wireless connection, ethernet and bluetooth all disabled after update"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by lukas15 on 2016-02-05
Hello everyone

After I updated yesterday my wireless connection, as well as the ethernet connection as bluetooth stopped working (network via USB tethering also doesn't work). It now says "No network devices available". When running Ubuntu on a Live USB, the networking works fine.

I have already tried a few things like installing the b43 as described in [this link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") under "b43 - No internet access", but that doesn't work. When I run the modprobe commands it says
```
modprobe: FATAL: Module b43 not found.
```

I have also tried reinstalling the bcmwl-kernel-source, like described in the 9th post of [this link]("http://ubuntuforums.org/showthread.php?t=2259382") (when purging the bcmwl-kernel-source package it said it was not installed yet), but to no avail.

Can anyone help me? I have added the output of the wireless-info script at the bottom of my post. I don't really know what to take away from it, but on thing that caught my eye is that the rfkill doesn't even give any output ... Any help would be very appreciated.

```

########## wireless info START ##########

Report from: 05 Feb 2016 15:14 CET +0100

Booted last: 05 Feb 2016 14:28 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

0a:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]

0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1818]

##### lsusb #############################

Bus 002 Device 004: ID 8087:07da Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:c334 Suyin Corp. 
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0781:556b SanDisk Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1109     1  0 14:28 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

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

[[/etc/NetworkManager/system-connections/PROXIMUS_FON]] (600 root)
[connection] id=PROXIMUS_FON | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=PROXIMUS_FON | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HITRON-8F70]] (600 root)
[connection] id=HITRON-8F70 | type=802-11-wireless
[802-11-wireless] ssid=HITRON-8F70 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Garage]] (600 root)
[connection] id=Garage | type=802-11-wireless
[802-11-wireless] ssid=Garage | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/verhuisnet]] (600 root)
[connection] id=verhuisnet | type=802-11-wireless
[802-11-wireless] ssid=verhuisnet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/huisnet]] (600 root)
[connection] id=huisnet | type=802-11-wireless
[802-11-wireless] ssid=huisnet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-2.4-9BC7]] (600 root)
[connection] id=WiFi-2.4-9BC7 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-2.4-9BC7 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NUMERICABLE-0E70]] (600 root)
[connection] id=NUMERICABLE-0E70 | type=802-11-wireless
[802-11-wireless] ssid=NUMERICABLE-0E70 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BRU-hotspot]] (600 root)
[connection] id=BRU-hotspot | type=802-11-wireless
[802-11-wireless] ssid=BRU-hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WiFi-2.4-09BB]] (600 root)
[connection] id=WiFi-2.4-09BB | type=802-11-wireless
[802-11-wireless] ssid=WiFi-2.4-09BB | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Telekom]] (600 root)
[connection] id=Telekom | type=802-11-wireless
[802-11-wireless] ssid=Telekom | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WT]] (600 root)
[connection] id=WT | type=802-11-wireless
[802-11-wireless] ssid=WT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GWGVM2]] (600 root)
[connection] id=GWGVM2 | type=802-11-wireless
[802-11-wireless] ssid=GWGVM2 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/belkin.b81]] (600 root)
[connection] id=belkin.b81 | type=802-11-wireless
[802-11-wireless] ssid=belkin.b81 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

[ -x /usr/bin/numlockx ] && numlockx on

[ -x /usr/bin/numlockx ] && numlockx on

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:0b:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.3/0000:0a:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1464.494514] wl: Unknown symbol wiphy_register (err 0)
[ 1464.494519] wl: Unknown symbol wiphy_new (err 0)
[ 1464.494542] wl: Unknown symbol lib80211_get_crypto_ops (err 0)
[ 1464.494574] wl: Unknown symbol wiphy_unregister (err 0)
[ 1464.494591] wl: Unknown symbol __ieee80211_get_channel (err 0)
[ 1464.494613] wl: Unknown symbol ieee80211_channel_to_frequency (err 0)
[ 1464.494625] wl: Unknown symbol ieee80211_frequency_to_channel (err 0)
[ 1464.494638] wl: Unknown symbol wiphy_free (err 0)

########## wireless info END ############


```

---

### Post by ajgreeny on 2016-02-05
Do you have the proposed repos enabled in Updates?

That has caused a lot of users to lose any connectivity as there are three errant lib packages in there. See [http://ubuntuforums.org/showthread.php?t=2311992&p=13432377#post13432377](http://ubuntuforums.org/showthread.php?t=2311992&p=13432377#post13432377) for more info, or come back again if that is not the cause.

---

### Post by lukas15 on 2016-02-05
Hi ajgreeny,

Thanks for the quick response. The proposed repos, is that the "Pre-released updates (trusty-proposed)" in the updates settings? I don't have that enabled, so it should be something else ...

I wonder if it could have something to do with the kernel. In order to do the updates I had to free up some space on the boot, and by accident I removed also the current one. I used the command apt-get purge linux-image-3.13.0-5*, but it also started to remove the 3.13.0-6* and before I realized the current one was deleted. But I reinstalled and it didn't seem to give any problems. But then after I did the updates ...

---

### Post by ajgreeny on 2016-02-05
I think it could be a result of your kernel removal "hiccup", but the honest answer is that I don't know.

I do not often use a wifi connection, and when I do it is always fully supported in the kernel with no action from me.  The Broadcom family of wifi adapters used to be a problem but I thought were generally well supported now, so I think I will have to leave this to those who know better than I.

---

### Post by lukas15 on 2016-02-08
Ok, thanks for your effort. 
I hope someone else will be able to shine his light on the situation, otherwise I guess I'll have to do a full reinstall ...

---

### Post by Vladlenin5000 on 2016-02-09
```
##### lspci ############################# 
0a:00.0 Network controller [0280]: [COLOR=#ff0000]Intel[/COLOR] Corporation [COLOR=#ff0000]Centrino Wireless-N 2230[/COLOR] [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062
```

This has nothing to do with Broadcom so following troubleshooting and tips for such class of chips shouldn't work. All the drivers related to Broadcom are blacklisted as they should be.
I also have no idea why it happened and I'm afraid what you did after the fact may have made things even worse.

Can you load the proper driver?
```
sudo modprobe iwlwifi
```

---

