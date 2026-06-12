---
title: "Ubuntu 16.04 - No network devices available"
date: 2016-10-15
forum: Networking &amp; Wireless
---

### Post by shibisnjothy on 2016-10-15
Hello,

Everything was fine with my Ubuntu 16.04 on Lenovo Yoga 3 until last night. 

[I][B]When I booted the computer today morning, I was not able to connect to WiFI. It says, "No network devices available". 

[/B][/I]I've been searching to resolve the issue, but no luck. I would appreciate any help.
```


########## wireless info START ##########

Report from: 15 Oct 2016 17:42 IST +0530

Booted last: 15 Oct 2016 00:00 IST +0530

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 006: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 010: ID 18d1:4ee1 Google Inc. Nexus 4 / 10
Bus 001 Device 002: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
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

##### network managers ##################

Installed:

    NetworkManager

Running:

root       713     1  0 17:21 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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

[[/etc/NetworkManager/system-connections/MyJio]] (600 root)
[connection] id=MyJio | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MyJio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SNW - WPJB 1]] (600 root)
[connection] id=SNW - WPJB 1 | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SNW - WPJB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HPl33t]] (600 root)
[connection] id=HPl33t | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HPl33t
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airtel-E5573-0AB4]] (600 root)
[connection] id=Airtel-E5573-0AB4 | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Airtel-E5573-0AB4
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IndiSmart]] (600 root)
[connection] id=IndiSmart | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=IndiSmart
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HIPL]] (600 root)
[connection] id=HIPL | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HIPL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IndiSmart 1]] (600 root)
[connection] id=IndiSmart 1 | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=IndiSmart
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SNW - WPJB]] (600 root)
[connection] id=SNW - WPJB | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SNW - WPJB
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WHITEBOX]] (600 root)
[connection] id=WHITEBOX | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WHITEBOX
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ellesmera]] (600 root)
[connection] id=Ellesmera | type=wifi | permissions=user:shibi:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Ellesmera
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/XMASLIGHT]] (600 root)
[connection] id=XMASLIGHT | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=XMASLIGHT
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/VIRUS]] (600 root)
[connection] id=VIRUS | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VIRUS
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

##### dmesg #############################

########## wireless info END ############


```

---

### Post by chili555 on 2016-10-15
We would also like to see:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

---

### Post by shibisnjothy on 2016-10-15
Thanks for the quick response...

Here is what I get.

```

[LEFT]modprobe: ERROR: ../libkmod/libkmod-module.c:832 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)

[/LEFT]





```

---

### Post by chili555 on 2016-10-15
> could not find module by name='iwlwifi'Whaaaaat?? Crazy!

Let's look for it:```
sudo updatedb
locate iwlwifi.ko
```I suspect that an update to your kernel version, also known as linux-image, has gone wrong. We may need to try to repair it.

Can you interrupt the boot process with the right shift key to get to the GRUB menu and select advanced options and boot into an earlier kernel version? Does the wireless work as expected then?

[http://i107.photobucket.com/albums/m287/mirandasnyder/20140317_105035.jpg](http://i107.photobucket.com/albums/m287/mirandasnyder/20140317_105035.jpg) In this example, rather than kernel version 3.5.0-48, we'd select and boot into the earlier 3.2.0-60.

---

### Post by shibisnjothy on 2016-10-15
Here is the output. Also, I see that the file is available only for the earlier kernels. I am going to attempt to booth into an earlier kernel.

```

/lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/4.4.0-38-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/4.4.0-42-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko


```

---

### Post by shibisnjothy on 2016-10-15
Booting into an earlier kernel worked! I booted into the kernel 4.4.0.42-generic from Grub.

Can we make everything work in the new kernel as well? :)

---

### Post by praseodym on 2016-10-15
Please check
```

grep iwl /etc/modprobe.d/*
dmesg | grep iwl
```

---

### Post by howefield on 2016-10-15
> **shibisnjothy said:**
> Booting into an earlier kernel worked! I booted into the kernel 4.4.0.42-generic from Grub.

Can we make everything work in the new kernel as well? :)

There have been a few forum threads about kernel 4.4.0.43 giving rise to issues such as yours. From 4.4.0.42 try..

```
sudo apt update
```
```
sudo apt upgrade
``` 

You are looking for a new kernel 4.4.0.44 which was released very shortly after the previous one. After a sudo apt update you can use

```
apt list --upgradeable
```

to see what packages are waiting there for you..

---

### Post by shibisnjothy on 2016-10-15
I ran the commands from both 'kernel 4.4.0.43-generic' and 'kernel 4.4.0.42-generic'

**kernel 4.4.0.43-generic - I didn't get any output for the 'dmesg | grep iwl' command**
```

grep: /etc/modprode.d/*: No such file or directory[COLOR=#000000][FONT=Arial][/FONT][/COLOR]

```

**kernel 4.4.0.42-generic - (the kernel in which wifi now works)**
```

grep: /etc/modprode.d/*: No such file or directory[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR][    2.118417] iwlwifi 0000:02:00.0: Unsupported splx structure
[    2.121410] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
[    2.131005] iwlwifi 0000:02:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    2.172242] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    2.172584] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    2.173089] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    2.287721] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.289337] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.059264] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.059874] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.159281] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.159936] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled

```

---

### Post by shibisnjothy on 2016-10-15
> **howefield said:**
> There have been a few forum threads about kernel 4.4.0.43 giving rise to issues such as yours. From 4.4.0.42 try..

```
sudo apt update
```
```
sudo apt upgrade
``` 

You are looking for a new kernel 4.4.0.44 which was released very shortly after the previous one. After a sudo apt update you can use

```
apt list --upgradeable
```

to see what packages are waiting there for you..

This worked! Now everything is back to normal. 

Thank you chili555, howefield, praseodym!

---

