---
title: "Unable to install Wise Tiger USB wifi adapter"
date: 2021-05-08
forum: Networking &amp; Wireless
---

### Post by bendover102938 on 2021-05-08
I have freshly installed Ubuntu from windows. I have zero linux experience. 
I have a "Wise Tiger model: WT-AC9019 1300M wifi adapter" that I used for wifi on windows. But I have no idea how to install it on Ubuntu. 
I have no idea what any of this code means and I feel like I am completely over my head. 
I've tried "sudo apt-get install rtl8812bu" but it comes back as "E: unable to locate package rtl8812bu" 
That is the name of the instal disk when I put it in. 

Let me know if I can provide you with any more information. Look forward to figuring out this Linux system! Thanks!

Edit: when open the cdrom folder and go through the linux folder there is a "install.sh" shell script. Reading the documents they make it sound easy but do not give any information on how to activate the shell script.

---

### Post by ajgreeny on 2021-05-08
*Thread moved to **Networking & Wireless**.* which is more appropriate and a better fit.

---

### Post by chili555 on 2021-05-08
The Linux drivers found on the included CDROM are seldom useful. They are often too old or built on some other Linux distribution, such as Fedora or Arch, et al.

Let's start fresh and get some information about the device. With the device inserted, open a terminal Ctrl+Alt+t and run:

```
lsusb
```Post the result and we'll proceed.

---

### Post by bendover102938 on 2021-05-08
Thanks for the reply, I'll post tomorrow when I'm back from work!

---

### Post by bendover102938 on 2021-05-09
I believe the device is "Realtek Semiconductor Corp. 802.11ac NIC"

---

### Post by jeremy31 on 2021-05-09
Can you post the USB ID?

---

### Post by bendover102938 on 2021-05-09
Edit: 
Bus 003 Device 006: ID 0bda:b812

---

### Post by bendover102938 on 2021-05-09
Jeremy31, I followed your wireless link to get the below info, hope this helps. 
```


########## wireless info START ##########

Report from: 08 May 2021 18:12 PDT -0700

Booted last: 08 May 2021 00:00 PDT -0700

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal

##### kernel ############################

Linux 5.8.0-43-generic #49~20.04.1-Ubuntu SMP Fri Feb 5 09:57:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 003 Device 006: ID 0bda:b812 Realtek Semiconductor Corp. 802.11ac NIC
Bus 003 Device 003: ID 046d:c07c Logitech, Inc. M-R0017 [G700s Rechargeable Gaming Mouse]
Bus 003 Device 002: ID 046d:c531 Logitech, Inc. C-U0007 [Unifying Receiver]
Bus 003 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy series, misc. (MTP mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

cfg80211              778240  0

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad

##### network managers ##################

Installed:

	NetworkManager

Running:

root         658       1  0 17:21 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Onboard Ethernet)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 5.8.0-43-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Vancouver (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.8.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.8.0-43-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.754445] r8169 0000:03:00.0 enp3s0: Link is Down

########## wireless info END ############

```

---

### Post by jeremy31 on 2021-05-09
```
sudo apt install git build-essential
git clone https://github.com/cilynx/rtl88x2bu.git
cd rtl88x2bu
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```
Reboot

---

### Post by bendover102938 on 2021-05-09
It tells me command git cannot be found. And ```
 E: Package 'git' has no installation candidate 
```

```

titaniumfire@titaniumfire-B85M-D3H:~$ sudo apt install git build-esssential

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Package git is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source



E: Package 'git' has no installation candidate

E: Unable to locate package build-esssential

titaniumfire@titaniumfire-B85M-D3H:~$ git clone http://github.com/cilynx/rtl88x2bu.git



Command 'git' not found, but can be installed with:



sudo apt install git



titaniumfire@titaniumfire-B85M-D3H:~$ sudo apt install git clone http://github.com/cilynx/rtl88x2bu.git

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Package git is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source



E: Package 'git' has no installation candidate

E: Unable to locate package clone

E: Unable to locate package http://github.com/cilynx

```

---

### Post by jeremy31 on 2021-05-09
Are you using ethernet or USB tether to a cell phone?

---

### Post by chili555 on 2021-05-09
sudo apt update first??

---

### Post by morrownr on 2021-05-09
Give this site a try:

[https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

The documentation is better.

---

### Post by mikesmith7 on 2021-05-09
apt install git should work tho? provided you've ran apt update?

---

### Post by bendover102938 on 2021-05-09
I did not know I could tether my phone for wifi. I have now done that. 
I went to update and this is what I got
```

sudo apt update
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock. It is held by process 2185 (apt-get)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to lock directory /var/lib/apt/lists/


```

---

### Post by bendover102938 on 2021-05-09
> **jeremy31 said:**
> ```
sudo apt install git build-essential
git clone https://github.com/cilynx/rtl88x2bu.git
cd rtl88x2bu
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```
Reboot

I got as far as the 6th line of code

[https://paste.ubuntu.com/p/Mdpz4G64fC/](https://paste.ubuntu.com/p/Mdpz4G64fC/)

---

### Post by bendover102938 on 2021-05-09
SOLVED! 

Thank you all for your input and patients! After connecting tether to my phone I went to the provided github page and followed the steps. 

I am looking forward to figure this system out!

Couple quick additional questions!
But posting all this code did I compromise any of my security?
and for all the code I entered incorrectly will that cause problems for me?

Thanks again I appreciate your time!

---

### Post by morrownr on 2021-05-11
> **bendover102938 said:**
> SOLVED! 

But posting all this code did I compromise any of my security?
and for all the code I entered incorrectly will that cause problems for me?

Thanks again I appreciate your time!

Probably not. If everything is working, you are probably good to go.

I maintain a repo that has a lot of information for Linux users that use USB WiFi adapters:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Nick

---

