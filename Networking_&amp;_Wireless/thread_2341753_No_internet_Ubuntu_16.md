---
title: "No internet Ubuntu 16"
date: 2016-10-31
forum: Networking &amp; Wireless
---

### Post by concerro on 2016-10-31
I upgraded from Ubuntu 14 to 16. I think it was the .04 version of 16, and I both my wired and wireless connections are down, but I can get online with no problem for Windows. 

The computer is an HP-15 ac143 laptop.

I know who to open the command console and type commands, but I am far from a Linux expert so if I need to use a diagnostic command I would likely have to be told exactly what to type into the console.

---

### Post by howefield on 2016-10-31
Read this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") and post the wireless info script as described, that might give others the info to assist you.

---

### Post by Hadaka on 2016-10-31
Hi its 14.04 or 14.10 and 16.04 or 16.10, please use the correct full name of your Ubuntu release.
to view open a terminal ctrl/alt/t and enter..
```
cat /etc/lsb-release
```
post what version you have. also did you upgrade from your last version to the present one or did
did you install the current version new??
please also post the output of...
```
lspci -n |  awk '/0200|0280/{print $3}'
```
thanks.

---

### Post by concerro on 2016-11-01
> **howefield said:**
> Read this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") and post the wireless info script as described, that might give others the info to assist you.
Here is the info.


```
########## wireless info START ##########


Report from: 31 Oct 2016 21:47 EDT -0400


Booted last: 31 Oct 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 3.13.0-100-generic #147-Ubuntu SMP Tue Oct 18 16:48:51 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80c1]


0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company RTL8188EE Wireless Network Adapter [103c:804b]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. My Book Essential Edition 2.0 (WDH1U)
Bus 001 Device 016: ID 154b:005b PNY Flash Drive
Bus 001 Device 006: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


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


grep: /etc/resolv.conf: No such file or directory


##### network managers ##################


Installed:


	NetworkManager


Running:


root       657     1  0 21:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


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


Sorry, try again.
[[/etc/NetworkManager/system-connections/LaQuinta]] (600 root)
[connection] id=LaQuinta | type=802-11-wireless
[802-11-wireless] ssid=LaQuinta | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DDVC7X91-Wireless]] (600 root)
[connection] id=DDVC7X91-Wireless | type=802-11-wireless
[802-11-wireless] ssid=DDVC7X91-Wireless | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=70:F1:A1:61:DC:34
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/taniawifi]] (600 root)
[connection] id=taniawifi | type=802-11-wireless
[802-11-wireless] ssid=taniawifi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MFI-7133854422]] (600 root)
[connection] id=MFI-7133854422 | type=802-11-wireless
[802-11-wireless] ssid=MFI-7133854422 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Homestead]] (600 root)
[connection] id=Homestead | type=802-11-wireless
[802-11-wireless] ssid=Homestead | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/MiFi4620L Jetpack 3FF7 Secure]] (600 root)
[connection] id=MiFi4620L Jetpack 3FF7 Secure | type=802-11-wireless
[802-11-wireless] ssid=MiFi4620L Jetpack 3FF7 Secure | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Olson Network]] (600 root)
[connection] id=Olson Network | type=802-11-wireless
[802-11-wireless] ssid=Olson Network | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TRAVELER_Network]] (600 root)
[connection] id=TRAVELER_Network | type=802-11-wireless
[802-11-wireless] ssid=TRAVELER_Network | mac-address=<MAC address>
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


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #############################


########## wireless info END ############




```

---

### Post by concerro on 2016-11-01
I upgraded from 14.04 to 16.04. I was prompted to upgrade when I logged into Linux and I accepted. 

[COLOR=#000000]Hadaka, I didnt see your post until after I had logged back into Windows. I will go back into Linux and try it a little later if this information from my above post does not give me an answer.[/COLOR]

[COLOR=#DD4814]
[/COLOR][COLOR=#DD4814][[COLOR=#000000]Hadaka[/COLOR]]("https://ubuntuforums.org/member.php?u=1599436")[COLOR=#000000] [/COLOR][COLOR=#000000][Hadaka]("https://ubuntuforums.org/member.php?u=1599436")[/COLOR][/COLOR][COLOR=#000000] [/COLOR]

---

### Post by Hadaka on 2016-11-01
Hi, the info i requested was in your wireless report.
This file  /etc/udev/rules.d/70-persistent-net.rules  is not present in the 16.04 load
 so it must be left over from your 14.04.
please delete this file with command..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot and attempt to connect.
*If you are still having difficulties connecting with a wired connection
I would suggest you load 16.04 new,fresh not an upgrade as upgrades
usually dont do well.
thanks.

---

### Post by concerro on 2016-11-02
It didn't work. I will do a new install after I get my important files off just in case something else goes wrong.

Thanks for your assistance.

---

