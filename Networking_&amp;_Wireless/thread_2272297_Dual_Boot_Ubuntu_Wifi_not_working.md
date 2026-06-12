---
title: "Dual Boot Ubuntu Wifi not working"
date: 2015-04-05
forum: Networking &amp; Wireless
---

### Post by Adam_Abdulhamid on 2015-04-05
Hi everyone,

I'm pretty new to Ubuntu. I just dual booted my mac (Yosemite) with Ubuntu 14.04. Everything there worked alright, and Ubuntu is up and running. The issue I'm now having is that the wifi doesn't work. It says wifi is enabled, but no networks are showing up. I tried to follow this tutorial ([http://itsfoss.com/fix-no-wireless-network-ubuntu/](http://itsfoss.com/fix-no-wireless-network-ubuntu/)), but to no avail. 

Anyone have any ideas as to what is going on? I've seen on a lot of other threads people wanting diagnostic info, so if you need me to run any scripts and update this with the output let me know.

Thanks

Edit:

Here are the results from running the wireless-script from the sticky post:
```



########## wireless info START ##########


Report from: 05 Apr 2015 16:15 PDT -0700


Booted last: 05 Apr 2015 16:12 PDT -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
	Subsystem: Apple Inc. Device [106b:0112]


04:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SS9183 PCIe SSD Controller [1b4b:9183] (rev 14)


##### lsusb #############################


Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 05ac:0259 Apple, Inc. 
Bus 001 Device 008: ID 05ac:8289 Apple, Inc. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 002: ID 12f7:1e23 Memorex Products, Inc. TravelDrive 2007 Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


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


##### nm-tool ###########################


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


########## wireless info END ############

```

---

### Post by praseodym on 2015-04-05
Please run the wireless-script from the sticky thread and show the outputs here

---

### Post by Adam_Abdulhamid on 2015-04-05
I just added the output from the script. Let me know what you think. Thanks for the help

---

### Post by wildmanne39 on 2015-04-05
Please do:
```
sudo apt-get install bcmwl-kernel-source
``` 
You will need a connection to the internet to install the driver and watch for errors.
Reboot

---

### Post by Adam_Abdulhamid on 2015-04-06
This is the output I get when I run that command:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-generic-lts-utopic linux-image-generic-lts-utopic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But nothing seems to have changed in terms of wifi, even after reboot.

---

### Post by praseodym on 2015-04-06
Hi,

this driver is buggy in 14.04, install the one from 14.10 instead:
```

sudo apt-get remove --purge bcmwl-kernel-source
wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
sudo dpkg -i *.deb
```
Reboot.

---

### Post by Adam_Abdulhamid on 2015-04-06
Worked perfectly. Thanks!

---

