---
title: "BCM43142 Problem"
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by Martin.K.Iliev on 2015-09-27
Hello there,
 Can someone help me please - I have problem sinse kernel update 3.19.0-26+ (27,28,29,30) - wifi does not work anymore. 
I try alot of sugestions from another places, but no result. So I will be glad if someon can help me turning on my WiFi again.

Hardware - Dell Inspiron 15 3000 series (3543)
OS - Ubuntu 15.04 kernel 3.19.0-30
WIFI - Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

I alredy tried the broadcom sticly post (purge bcmwl-kernel-source and reinstall it with error below)

```

&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;&#1090;&#1072; &#1079;&#1072; &#1089;&#1098;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;&#1090;&#1086;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1057;&#1083;&#1077;&#1076;&#1085;&#1080;&#1090;&#1077; &#1053;&#1054;&#1042;&#1048; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; &#1097;&#1077; &#1073;&#1098;&#1076;&#1072;&#1090; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;:
  bcmwl-kernel-source
0 &#1072;&#1082;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1080;&#1088;&#1072;&#1085;&#1080;, 1 &#1085;&#1086;&#1074;&#1080; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;, 0 &#1079;&#1072; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1074;&#1072;&#1085;&#1077; &#1080; 0 &#1073;&#1077;&#1079; &#1087;&#1088;&#1086;&#1084;&#1103;&#1085;&#1072;.
&#1053;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1077; &#1076;&#1072; &#1089;&#1077; &#1080;&#1079;&#1090;&#1077;&#1075;&#1083;&#1103;&#1090; 0 B/1509 kB &#1072;&#1088;&#1093;&#1080;&#1074;&#1080;.
&#1057;&#1083;&#1077;&#1076; &#1090;&#1072;&#1079;&#1080; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1103; &#1097;&#1077; &#1073;&#1098;&#1076;&#1077; &#1080;&#1079;&#1087;&#1086;&#1083;&#1079;&#1074;&#1072;&#1085;&#1086; 8038 kB &#1076;&#1086;&#1087;&#1098;&#1083;&#1085;&#1080;&#1090;&#1077;&#1083;&#1085;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1086;.
&#1048;&#1079;&#1073;&#1080;&#1088;&#1072;&#1085;&#1077; &#1085;&#1072; &#1087;&#1086;-&#1088;&#1072;&#1085;&#1086; &#1085;&#1077; &#1080;&#1079;&#1073;&#1088;&#1072;&#1085;&#1080;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; bcmwl-kernel-source.
(&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1073;&#1072;&#1079;&#1072;&#1090;&#1072; &#1076;&#1072;&#1085;&#1085;&#1080; ... 375185 &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1087;&#1072;&#1087;&#1082;&#1080; &#1074; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090;&#1072; &#1089;&#1072; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;.)
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1079;&#1072; &#1088;&#1072;&#1079;&#1087;&#1072;&#1082;&#1077;&#1090;&#1080;&#1088;&#1072;&#1085;&#1077; &#1085;&#1072; .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb ...
&#1056;&#1072;&#1079;&#1087;&#1072;&#1082;&#1077;&#1090;&#1080;&#1088;&#1072;&#1085;&#1077; &#1085;&#1072; bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
&#1048;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1077; &#1085;&#1072; bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-30-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
&#1054;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072; &#1085;&#1072; &#1090;&#1088;&#1080;&#1075;&#1077;&#1088;&#1080;&#1090;&#1077; &#1079;&#1072; initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic




```

Here is the output from the wireless-info script:


```



########## wireless info START ##########


Report from: 27 Sep 2015 11:52 EEST +0300


Booted last: 27 Sep 2015 14:51 EEST +0300


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-30-generic #33-Ubuntu SMP Mon Sep 21 20:58:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


default


##### lspci #############################


06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]


07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:0655]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 003 Device 003: ID 0c45:670b Microdia 
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 248a:8566  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


cfg80211              540672  0 
dell_wmi               16384  0 
mxm_wmi                16384  0 
sparse_keymap          16384  1 dell_wmi
snd_soc_rt5640         94208  0 
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi


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


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       831     1  0 11:51 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


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


[[/etc/NetworkManager/system-connections/Mimi200-AP]] (600 root)
[connection] id=Mimi200-AP | type=wifi
[wifi] ssid=Mimi200-AP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Home-WiFi]] (600 root)
[connection] id=Home-WiFi | type=wifi
[wifi] ssid=Home-WiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kostas.KTTS0X]] (644 root)
[connection] id=kostas | type=wifi
[wifi] ssid=kostas | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/krasi13]] (600 root)
[connection] id=krasi13 | type=wifi
[wifi] ssid=krasi13 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Home-WiFi 1]] (600 root)
[connection] id=Home-WiFi 1 | type=wifi
[wifi] ssid=Home-WiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Sviloza-Residence]] (600 root)
[connection] id=Sviloza-Residence | type=wifi
[wifi] ssid=Sviloza-Residence | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ALCATEL ONE TOUCH IDOL]] (600 root)
[connection] id=ALCATEL ONE TOUCH IDOL | type=wifi
[wifi] ssid=ALCATEL ONE TOUCH IDOL | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kostas]] (600 root)
[connection] id=kostas | type=wifi
[wifi] ssid=kostas | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Iliqn vds]] (600 root)
[connection] id=Iliqn vds | type=wifi
[wifi] ssid=Iliqn vds | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Sofia (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.19.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        09:1D:B2:76:17:3D:83:37:42:E9:6A:C8:70:59:1A:DB:9B:CC:DA:53
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   11.080903] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0a5c-21d7.hcd failed with error -2
[   11.080910] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-0a5c-21d7.hcd not found


########## wireless info END ############



```

Thank you!

With best regards M.Iliev

---

### Post by chili555 on 2015-09-27
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.I suggest you try:```
sudo apt-get install linux-headers-generic
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by Martin.K.Iliev on 2015-09-27
Thats worked! Thanks alot for the fast replay!

Best regards M.Iliev

---

