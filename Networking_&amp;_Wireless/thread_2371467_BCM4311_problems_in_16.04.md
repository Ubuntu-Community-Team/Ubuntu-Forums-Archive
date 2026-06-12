---
title: "BCM4311 problems in 16.04"
date: 2017-09-12
forum: Networking &amp; Wireless
---

### Post by bayouoldguy on 2017-09-12
I have exactly the same laptop, BCM4311 card & running 14.04 LTS , no problem connecting wireless. I am however, trying to run the 16.04 32 bit from a "live USB" & cannot connect wireless or reset any configuration ( reboot deletes any config reset ). I do have connection on wired Ethernet. My "lspci -v" output shows: Capabilities :<access denied>; Kernel driver in use: b43-pci-bridge; Kernel modules: ssb. Any suggestions? I wanted to try the 16.04 before a clean install.....G

Moderator note: split from [https://ubuntuforums.org/showthread.php?t=2369099](https://ubuntuforums.org/showthread.php?t=2369099)

---

### Post by chili555 on 2017-09-12
> **bayouoldguy said:**
> I have exactly the same laptop, BCM4311 card & running 14.04 LTS , no problem connecting wireless. I am however, trying to run the 16.04 32 bit from a "live USB" & cannot connect wireless or reset any configuration ( reboot deletes any config reset ). I do have connection on wired Ethernet. My "lspci -v" output shows: Capabilities :<access denied>; Kernel driver in use: b43-pci-bridge; Kernel modules: ssb. Any suggestions? I wanted to try the 16.04 before a clean install.....GI believe you can install the needed firmware as described above in a live session. Then unload and reload the driver.```
sudo modprobe -r b43 && sudo modprobe b43
```

---

### Post by bayouoldguy on 2017-09-13
> **chili555 said:**
> I believe you can install the needed firmware as described above in a live session. Then unload and reload the driver.```
sudo modprobe -r b43 && sudo modprobe b43
```

I did the software update & install as per the above & did the driver unload/reload. No change. I am using a USB live download, "ubuntu-16.04.03-desktop-i386.iso" & created the USB using rufus-2.16.exe. I seem to have a live USB that does not allow a setting change if rebooted. I have a wired connection & have allowed the updates to download as asked by the "update app ". I do not have any connection search when I set up the wireless account. I have a wireless connection on this laptop when I boot into the bootloader, ubuntu 14.04/windows Vista. I could not get a working livw USB thru the "ubuntu download/create live disc" method......G
( I am commenting from my Windows 7 desktop )

---

### Post by chili555 on 2017-09-13
> I seem to have a live USB that does not allow a setting change if rebooted. Unless you install on a USB with persistence, then this is true of all live sessions.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Nonetheless, it is possible to install the firmware and unload and reload the driver. Please try again with:```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe -r bcma
```And follow it with:```
sudo modprobe b43
```Does the wireless come to life?```
iwconfig
dmesg | grep b43
```Is the wireless turned off by the hardware switch?```
rfkill list all
```>  I have a wireless connection on this laptop when I boot into the bootloader, ubuntu 14.04/windows Vista.If it works as expected in 14.04, there should be no doubt whatever that it can easily be made to work in 16.04.

---

### Post by bayouoldguy on 2017-09-13
command "sudo modprobe -r ssb" 
; "modprobe: FATAL: Module ssb is in use"

command "rfkill list all" ; O: dell-wifi: Wireless LAN
                                     Soft blocked: no
                                     Hard blocked: no

( command "dmesg | grep b43" found b43 firmware load from the forum page "failed with error -2", 6  places, suggests specified "http://wireless.kernel.org/en/users/Drivers/b43#device firmware" path to get correct download....I will backtrack & follow up....G

---

### Post by chili555 on 2017-09-13
The module ssb may be in use by your ethernet device. Please try:```
sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe -r bcma
```Followed by:```
sudo modprobe b43
```And for the ethernet:```
sudo modprobe b44
```Check the log:```
dmesg |
 grep b43
```

---

### Post by bayouoldguy on 2017-09-14
Found on "https://wiki.debian.org/bcm43xx" page..."Drivers"....."More info.....The b43, b43legacy, brcmsac and wl drivers DO NOT support any USB device".......does this give support that a "live USB" will not run the b43xx Drivers ? The "failed with error" messages seem to support that. All I wanted to do was try 16.04 before a clean install, wiping out an up & running 14.04 using the b43 Driver ??...G

---

### Post by chili555 on 2017-09-14
> .does this give support that a "live USB" will not run the b43xx Drivers ?No. It means that the listed drivers will not support a USB wireless device. Yours is a PCI device. The statement you cite is entirely unrelated to live USB or DVD sessions.

Did you try what I suggested above?

Again, I repeat, if it works as expected in 14.04, there should be no doubt whatever that it can easily be made to work in 16.04.

---

### Post by bayouoldguy on 2017-09-14
Latest output:dmesg | grep b43
```
[   34.288600] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   34.332057] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   34.332080] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   34.371517] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   34.376704] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   34.379299] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   34.379347] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   34.379353] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.379359] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   34.379363] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1875.733979] b43-wlan ERROR: Dual-core devices are not supported
[ 1875.733994] b43: probe of ssb0:0 failed with error -524
```

---

### Post by wildmanne39 on 2017-09-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by bayouoldguy on 2017-09-14
```
ubuntu@ubuntu:~$ dmsg | grep b43
No command 'dmsg' found, did you mean:
 Command 'qmsg' from package 'torque-client' (universe)
 Command 'qmsg' from package 'torque-client-x11' (universe)
 Command 'dmesg' from package 'util-linux' (main)
dmsg: command not found
ubuntu@ubuntu:~$ dmesg | grep b43
[   34.288600] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   34.332057] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   34.332080] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   34.371517] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   34.376704] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   34.379299] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   34.379347] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   34.379353] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.379359] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   34.379363] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1875.733979] b43-wlan ERROR: Dual-core devices are not supported
[ 1875.733994] b43: probe of ssb0:0 failed with error -524
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 4,120 B/27.2 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release i386 (20170801) xenial/main i386 b43-fwcutter i386 1:019-2 [23.1 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse i386 firmware-b43-installer all 1:019-2 [4,120 B]
Fetched 4,120 B in 0s (15.7 kB/s)                  
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 194418 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_019-2_i386.deb ...
Unpacking b43-fwcutter (1:019-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-2_all.deb ...
Unpacking firmware-b43-installer (1:019-2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up b43-fwcutter (1:019-2) ...
Setting up firmware-b43-installer (1:019-2) ...
No chroot environment found. Starting normal installation
--2017-09-14 15:40:50--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... 173.254.28.119
Connecting to [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com)|173.254.28.119|:80](www.lwfinger.com)|173.254.28.119|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: &#8216;broadcom-wl-5.100.138.tar.bz2&#8217;

broadcom-wl-5.100.1 100%[===================>]  12.89M  4.70MB/s    in 2.7s    

2017-09-14 15:40:53 (4.70 MB/s) - &#8216;broadcom-wl-5.100.138.tar.bz2&#8217; saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
ubuntu@ubuntu:~$ sudo modprobe -r b43 bcma
ubuntu@ubuntu:~$ sudo modprobe b43
ubuntu@ubuntu:~$
```

---

### Post by bayouoldguy on 2017-09-14
Oops.....will try to remember....G

---

### Post by bayouoldguy on 2017-09-14
Did not work......

---

### Post by bayouoldguy on 2017-09-14
deleted

---

### Post by chili555 on 2017-09-14
You pasted the script itself; we need the diagnostic result that is produced after you run the script and it generates a report.

---

### Post by bayouoldguy on 2017-09-14
Sorry, I have not done this for a few years.....thought it looked weird !...G

---

### Post by bayouoldguy on 2017-09-14
Lets try this again.....G

---

### Post by bayouoldguy on 2017-09-14
Again !
```
########## wireless info START ##########

Report from: 14 Sep 2017 20:32 UTC +0000

Booted last: 14 Sep 2017 00:00 UTC +0000

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:13 UTC 2017 i686 i686 i686 GNU/Linux

file=/cdrom/preseed/ubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, ---, maybe-ubiquity

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Latitude D620 [1028:01c2]
	Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dell_smbios            16384  2 dell_wmi,dell_laptop
b43                   397312  0
bcma                   57344  1 b43
mac80211              700416  1 b43
cfg80211              532480  2 b43,mac80211
ssb_hcd                16384  0
wmi                    16384  1 dell_wmi
ssb                    57344  2 b43,ssb_hcd
video                  40960  3 dell_wmi,dell_laptop,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF1]>  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5f8b:4d14:d70d:27f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34281944 (34.2 MB)  TX bytes:2130169 (2.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49807 (49.8 KB)  TX bytes:49807 (49.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp9s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp9s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp9s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lusfiber.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1382     1  0 20:26 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5752 Gigabit Ethernet PCI Express (Latitude D620)
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5752-v3.19
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/enp9s0
GENERAL.IP-IFACE:                       enp9s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b31824ce-87d1-3ec8-af7f-6cd696d12c85
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b31824ce-87d1-3ec8-af7f-6cd696d12c85 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.104/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lusfiber.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.104
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = lusfiber.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1505507188
DHCP4.OPTION[22]:                       host_name = ubuntu
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::5f8b:4d14:d70d:27f4/64
IP6.GATEWAY:                            
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_domain_search = lusfiber.net.
DHCP6.OPTION[3]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        dhcp6_server_id = 0:2:3:9:5:5:94:10:3e:2:bd:25
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:70:53:23:76:15:50:fa:8f:3a:c8:1d:8d:6b:1f:91:11

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

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

enp9s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5F955FFEA61C80144A2B433
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C645ADA4C8790A787B7C8E9
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[mac80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[ssb]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     38B7A1BE5CF467C3CF164D5
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
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

[   33.252255] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   33.315573] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   33.315594] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   33.357689] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   33.364096] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   33.364146] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   33.364151] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   33.364155] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   35.330755] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready (repeated 2 times)
[   38.480412] tg3 0000:09:00.0 enp9s0: Link is up at 1000 Mbps, full duplex
[   38.480416] tg3 0000:09:00.0 enp9s0: Flow control is off for TX and off for RX
[   38.480461] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2017-09-14
You can try
```
sudo apt-get update
```
```
sudo apt-get install firmware-b43-installer
```
```
sudo modprobe -r b43
```
```
sudo modprobe -r ssb
```
```
sudo modprobe b43
```
Hopefully that works and it can use the firmware but since you are using something other than a hard disk install, you will have to do this to use wifi after every boot

---

### Post by bayouoldguy on 2017-09-14
Again !
```
########## wireless info START ##########

Report from: 14 Sep 2017 20:32 UTC +0000

Booted last: 14 Sep 2017 00:00 UTC +0000

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:13 UTC 2017 i686 i686 i686 GNU/Linux

file=/cdrom/preseed/ubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, ---, maybe-ubiquity

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Latitude D620 [1028:01c2]
	Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dell_smbios            16384  2 dell_wmi,dell_laptop
b43                   397312  0
bcma                   57344  1 b43
mac80211              700416  1 b43
cfg80211              532480  2 b43,mac80211
ssb_hcd                16384  0
wmi                    16384  1 dell_wmi
ssb                    57344  2 b43,ssb_hcd
video                  40960  3 dell_wmi,dell_laptop,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF1]>  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5f8b:4d14:d70d:27f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34281944 (34.2 MB)  TX bytes:2130169 (2.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49807 (49.8 KB)  TX bytes:49807 (49.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp9s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp9s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp9s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lusfiber.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1382     1  0 20:26 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5752 Gigabit Ethernet PCI Express (Latitude D620)
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5752-v3.19
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/enp9s0
GENERAL.IP-IFACE:                       enp9s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b31824ce-87d1-3ec8-af7f-6cd696d12c85
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b31824ce-87d1-3ec8-af7f-6cd696d12c85 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.104/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lusfiber.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.104
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = lusfiber.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1505507188
DHCP4.OPTION[22]:                       host_name = ubuntu
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::5f8b:4d14:d70d:27f4/64
IP6.GATEWAY:                            
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_domain_search = lusfiber.net.
DHCP6.OPTION[3]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        dhcp6_server_id = 0:2:3:9:5:5:94:10:3e:2:bd:25
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:70:53:23:76:15:50:fa:8f:3a:c8:1d:8d:6b:1f:91:11

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

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

enp9s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5F955FFEA61C80144A2B433
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C645ADA4C8790A787B7C8E9
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[mac80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[ssb]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     38B7A1BE5CF467C3CF164D5
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
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

[   33.252255] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   33.315573] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   33.315594] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   33.357689] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   33.364096] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   33.364146] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   33.364151] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   33.364155] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   35.330755] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready (repeated 2 times)
[   38.480412] tg3 0000:09:00.0 enp9s0: Link is up at 1000 Mbps, full duplex
[   38.480416] tg3 0000:09:00.0 enp9s0: Flow control is off for TX and off for RX
[   38.480461] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2017-09-14
You can't reboot after running the commands as the firmware can not be saved on the USB or DVD that you are booting into

---

### Post by bayouoldguy on 2017-09-14
```

ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 121 not upgraded.
Need to get 4,120 B/27.2 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 cdrom://Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release i386 (20170801) xenial/main i386 b43-fwcutter i386 1:019-2 [23.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 firmware-b43-installer all 1:019-2 [4,120 B]
Fetched 4,120 B in 0s (16.8 kB/s)            
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 194445 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_019-2_i386.deb ...
Unpacking b43-fwcutter (1:019-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-2_all.deb ...
Unpacking firmware-b43-installer (1:019-2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up b43-fwcutter (1:019-2) ...
Setting up firmware-b43-installer (1:019-2) ...
No chroot environment found. Starting normal installation
--2017-09-14 21:18:26--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: &#8216;broadcom-wl-5.100.138.tar.bz2&#8217;

broadcom-wl-5.100.1 100%[===================>]  12.89M  4.50MB/s    in 2.9s    

2017-09-14 21:18:29 (4.50 MB/s) - &#8216;broadcom-wl-5.100.138.tar.bz2&#8217; saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
ubuntu@ubuntu:~$ sudo modprobe -r b43
ubuntu@ubuntu:~$ sudo modprobe -r ssb
modprobe: FATAL: Module ssb is in use.
ubuntu@ubuntu:~$ sudo mpdprobe b43
sudo: mpdprobe: command not found
ubuntu@ubuntu:~$ sudo modprobe b43

```

---

### Post by jeremy31 on 2017-09-14
Post results for ```
lsmod | grep ssb
```

---

### Post by bayouoldguy on 2017-09-14
Thanks, thats what I originally thought. I had in the past set up wireless using a "live USB", but I think sonething has changed.......I did not want to lose my 14.04 running, but may have to venture into the unknown !.......G

---

### Post by jeremy31 on 2017-09-14
I think I found it
```
sudo modprobe -r b43
```
```
sudo modprobe -r ssb_hcd
```
```
sudo modprobe -r ssb
```
```
sudo modprobe b43
```

I didn't notice that ssb_hcd depended on ssb on that is why you got the module in use errror

---

### Post by bayouoldguy on 2017-09-14
```

ubuntu@ubuntu:~$ lsmod | grep ssb
ssb_hcd                16384  0
ssb                    57344  2 b43,ssb_hcd

```

---

### Post by bayouoldguy on 2017-09-14
jeremy31.......You found it ! I am connected to wireless & looking like I can do the upgrade to 16.04 !.......Remind my if I need to post "solved", but this was not my original post....G

---

### Post by jeremy31 on 2017-09-14
See [https://ubuntuforums.org/showthread.php?t=2369099&p=13686958#post13686958](https://ubuntuforums.org/showthread.php?t=2369099&p=13686958#post13686958) and see if that works
Once it is installed it is easier as you can reboot and Ubuntu 14.04 still has a little more than 18 months of support

I see you found it

---

### Post by jeremy31 on 2017-09-14
I split the topic, see if you can use thread tools to mark as solved

---

### Post by bayouoldguy on 2017-09-14
Thanks, good work by all that got involved......G
Edited to remind forum viewers.....just follow the instructions of the mods & sr ppl. You will get your problem solved. I fiddled around for a week before finally doing the suggested posting....There is knowledge in the forum !!.....G

---

### Post by bayouoldguy on 2017-09-16
An update 9-16-17.....I did a clean install of 16.04 & I am up & running on the old D620 laptop. I had to "purge bcmwl-kernel-source" to get the b43 driver install to "keep" on reboot. Also got my new Canon TS6000 printer installed after finding " cnijfilter2-5.40-1-deb.tar.gz" on the net. It will update thru the "cups" printer app......G

---

