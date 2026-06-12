---
title: "No connectivity when boot Linux 4.2.0-19-generic"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by A4Skyhawk on 2015-12-04
But do have connectivity when boot Linux 4.2.0-18-generic (recovery mode).
Earlier, I downloaded the software updates as shown in the "Software Updater".  It required me to reboot to complete the install process.  When I did this, I had no connectivity.  The only way I could regain connectivity was to boot in recovery mode with Linux 4.2.0-18-generic.  Is there a bug in the software updates that I downloaded earlier?
A4Skyhawk

---

### Post by praseodym on 2015-12-04
Please run the wireless-script from the sticky-thread and show the outputs

---

### Post by A4Skyhawk on 2015-12-04
I don't have wireless from my computer - the problem is with the ethernet connection.  However, I am able to get online from my wife's computer.  
In response to $ sudo lshw -C network I get "network UNCLAIMED" and am pursuing that as a fix.

---

### Post by praseodym on 2015-12-04
It shows all info we need

---

### Post by A4Skyhawk on 2015-12-04
Output of wireless-info script:

```
                         

########## wireless info START ########## 

Report from: 04 Dec 2015 22:55 EST -0500 

Booted last: 04 Dec 2015 00:00 EST -0500 

Script from: 27 Sep 2015 00:34 UTC +0000 

##### release ########################### 

Distributor ID:    Ubuntu Description:    Ubuntu 15.10 Release:    15.10 Codename:    wily 

##### kernel ############################ 

Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11
11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 

Parameters: ro, quiet, splash, vt.handoff=7 

##### desktop ########################### 

sed: can't read /home/bill/.dmrc: No such file
or directory 

Could not be determined. 

##### lspci ############################# 

02:00.0 Ethernet controller [0200]: Realtek
Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit
Ethernet Controller [10ec:8168] (rev 11)     Subsystem: Acer Incorporated [ALI] Device
[1025:085e] 

##### lsusb ############################# 

Bus 002 Device 001: ID 1d6b:0003 Linux
Foundation 3.0 root hub Bus 001 Device 005: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 004: ID 0bda:0153 Realtek
Semiconductor Corp. Mass Storage Device Bus 001 Device 003: ID 05e3:0608 Genesys Logic,
Inc. Hub Bus 001 Device 002: ID 046d:c517 Logitech, Inc.
LX710 Cordless Desktop Laser Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub 

##### PCMCIA card info ################## 

##### rfkill ############################ 

##### lsmod ############################# 

wmi                    20480  0 

##### interfaces ######################## 

auto lo iface lo inet loopback 

##### ifconfig ########################## 

##### iwconfig ########################## 

lo        no wireless extensions. 

##### route ############################# 

Kernel IP routing table Destination     Gateway         Genmask        
Flags Metric Ref    Use Iface 

##### resolv.conf ####################### 

##### network managers ################## 

Installed: 

    NetworkManager 

Running: 

root       565     1  0 18:06 ?        00:00:00
/usr/sbin/NetworkManager --no-daemon 

##### NetworkManager info ############### 

##### NetworkManager.state ############## 

[main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true 

##### NetworkManager.conf ############### 

[main] plugins=ifupdown,keyfile,ofono dns=dnsmasq 

[ifupdown] managed=false 

##### NetworkManager profiles ########### 

##### iw reg get ######################## 

Region: America/New_York (based on set time
zone) 

country 00: DFS-UNSET     (2402 - 2472 @ 40), (6, 20), (N/A)     (2457 - 2482 @ 40), (6, 20), (N/A),
PASSIVE-SCAN     (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM,
PASSIVE-SCAN     (5170 - 5250 @ 160), (6, 20), (N/A),
PASSIVE-SCAN     (5250 - 5330 @ 160), (6, 20), (0 ms), DFS,
PASSIVE-SCAN     (5490 - 5730 @ 160), (6, 20), (0 ms), DFS,
PASSIVE-SCAN     (5735 - 5835 @ 80), (6, 20), (N/A),
PASSIVE-SCAN     (57240 - 63720 @ 2160), (N/A, 0), (N/A) 

##### iwlist channels ################### 

lo        no frequency information. 

##### iwlist scan ####################### 

lo        Interface doesn't support scanning. 

##### module infos ###################### 

##### module parameters ################# 

##### /etc/modules ###################### 

##### modprobe options ################## 

[/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci 

[/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac blacklist r8169 blacklist r8169 

[/etc/modprobe.d/blacklist-rare-network.conf] alias net-pf-3 off alias net-pf-6 off alias net-pf-9 off alias net-pf-11 off alias net-pf-12 off alias net-pf-19 off alias net-pf-21 off alias net-pf-36 off 

[/etc/modprobe.d/intel-microcode-blacklist.conf] blacklist microcode 

[/etc/modprobe.d/iwlwifi.conf] remove iwlwifi \ (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e
^iwlwifi | xargs /sbin/rmmod) \ && /sbin/modprobe -r mac80211 

[/etc/modprobe.d/mlx4.conf] softdep mlx4_core post: mlx4_en 

##### rc.local ########################## 

exit 0 

##### pm-utils ########################## 

##### udev rules ######################## 

[/etc/udev/rules.d/70-persistent-net.rules] # PCI device 0x10ec:0x8168 (r8169) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth0" 

##### dmesg ############################# 

########## wireless info END ############  
```

---

### Post by praseodym on 2015-12-05
Obviously, no wifi card is shown. For LAN download these files and save them i "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu6_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu6_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. LAN should work now. Please check in your BIOS if WLAN is active or if it can be activated there.

---

### Post by A4Skyhawk on 2015-12-05
I completed the steps that you suggested, but still have no connectivity w/ ethernet.
In BIOS, I did not see a status for WLAN, or an option to activate.
Output from wireless-info script:
```

########## wireless info START ##########

Report from: 05 Dec 2015 09:42 EST -0500

Booted last: 05 Dec 2015 00:00 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/bill/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 004: ID 0bda:0153 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              548864  0
wmi                    20480  0

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

root       599     1  0 09:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
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
blacklist r8169
blacklist r8169
blacklist r8169

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

[/etc/modprobe.d/r8168-dkms.conf]
alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by praseodym on 2015-12-05
Load the driver by hand (for LAN):
```

sudo modprobe -v r8168
```
Still no wireless device. BIOS-reset to default settings?

---

### Post by A4Skyhawk on 2015-12-05
I get:
  	 	 	 	   xxx@zzz:~$ sudo modprobe -v r8168

 [sudo] password for xxx:  

 insmod /lib/modules/4.2.0-19-generic/updates/dkms/r8168.ko  
 modprobe: ERROR: could not insert 'r8168': Exec format error

I reset BIOS to default settings.
Still no connectivity to ethernet.

---

### Post by praseodym on 2015-12-05
Ok, try to compile it directly from source:
 Download this file and save it in "Downloads":

[http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

Installation:

```
cd ~/Downloads/
sudo apt-get remove --purge r8168-dkms
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot.

---

### Post by A4Skyhawk on 2015-12-05
Completed steps, rebooted.
No connectivity to ethernet.

Here is a copy of the terminal commands and the responses:
```
                         
 xxx@zzz:~$ sudo apt-get remove --purge r8168-dkms
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Package 'r8168-dkms' is not installed, so not removed
 0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
 xxx@zzz:~$ cd /home/bill/Downloads
 xxx@zzz:~/Downloads$ sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
 r8168-dkms-8.040.00/src/
 r8168-dkms-8.040.00/src/Makefile
 r8168-dkms-8.040.00/src/r8168_asf.c
 r8168-dkms-8.040.00/src/Makefile_linux24x
 r8168-dkms-8.040.00/src/r8168_asf.h
 r8168-dkms-8.040.00/src/r8168_dash.h
 r8168-dkms-8.040.00/src/r8168_n.c
 r8168-dkms-8.040.00/src/rtltool.h
 r8168-dkms-8.040.00/Makefile
 r8168-dkms-8.040.00/dkms.conf
 r8168-dkms-8.040.00/
 r8168-dkms-8.040.00/README
 r8168-dkms-8.040.00/src/rtl_eeprom.h
 r8168-dkms-8.040.00/autorun.sh
 r8168-dkms-8.040.00/src/rtltool.c
 r8168-dkms-8.040.00/src/rtl_eeprom.c
 r8168-dkms-8.040.00/src/r8168.h
 r8168-dkms-8.040.00/src/r8168_realwow.h
 xxx@zzz:~/Downloads$ cd
 xxx@zzz:~$ sudo dkms add -m r8168-dkms -v 8.040.00
 Error! DKMS tree already contains: r8168-dkms-8.040.00
 You cannot add the same module/version combo more than once.
 xxx@zzz:~$ sudo dkms build -m r8168-dkms -v 8.040.00
 Module r8168-dkms/8.040.00 already built for kernel 4.2.0-19-generic/4
 xxx@zzz:~$ sudo dkms install -m r8168-dkms -v 8.040.00
 Module r8168-dkms/8.040.00 already installed on kernel 4.2.0-19-generic/x86_64
 xxx@zzz:~$ sudo depmod -a
 xxx@zzz:~$ sudo update-initramfs -u
 update-initramfs: Generating /boot/initrd.img-4.2.0-19-generic
 xxx@zzz:~$ echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
 blacklist r8169
 xxx@zzz:~$ 
  
```

---

### Post by praseodym on 2015-12-05
Remove it:

```
sudo dkms remove -m r8168-dkms -v 8.040.00 --all
sudo rm -r /usr/src/r8168-dkms-8.040.00 
```
Reboot and try it again. Show afterwards:
```

dkms status
locate r8168.ko | grep lib
ifconfig -a
lsmod | grep r8
cat /etc/resolv.conf
route -n
```

---

### Post by A4Skyhawk on 2015-12-05
Success.  I have connectivity!  Thanks!
Prior to making the original post, and while doing my own troubleshooting, I noticed that all the "Advanced options..." prior to 4.2.0-19 have disappeared.
Is this a concern?  Do I need to "reload" them, just in case?


```

xxx@zzz:~$ dkms status
r8168-dkms, 8.040.00, 4.2.0-19-generic, x86_64: installed (WARNING! Diff between built and installed module!)

xxx@zzz:~$ locate r8168.ko | grep lib
/lib/modules/4.2.0-17-generic/kernel/drivers/net/ethernet/realtek/r8168.ko

xxx@zzz:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f8:0f:41:cd:b4:c8  
          inet addr:10.0.0.138  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:80:c202:4ea9:fa0f:41ff:fecd:b4c8/64 Scope:Global
          inet6 addr: fe80::fa0f:41ff:fecd:b4c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11390464 (11.3 MB)  TX bytes:1152106 (1.1 MB)
          Interrupt:88 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:152912 (152.9 KB)  TX bytes:152912 (152.9 KB)

xxx@zzz:~$ lsmod | grep r8
r8168                 487424  0

xxx@zzz:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hsd1.nj.comcast.net

xxx@zzz:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

xxx@zzz:~$ 
```

---

### Post by praseodym on 2015-12-05
Where did you have "Advanced Options"?!

---

### Post by A4Skyhawk on 2015-12-05
On bootup, "Advanced options for Ubuntu" in the grub, where you can do a recovery mode boot.  BTW, what is the difference between "upstart" and "recovery"?

---

### Post by praseodym on 2015-12-05
Try:
```

sudo update-grub
```

---

