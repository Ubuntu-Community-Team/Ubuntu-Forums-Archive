---
title: "Panasonic (Matsushita) DY-WL10 Wireless Adapter / Broadcom BCM4323"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by rodrigo8 on 2014-03-27
Well I just got Ubuntu for first time and I have this Panasonic Lan Adapter model: DY-WL10 wich is not working! I been searching like crazy and I can't find a solution!
It wasn't working on Windows 8.1 neither but I found like a video to make it work doing something like a chip thing...And it works perfectly but not in here!

---

### Post by chili555 on 2014-03-27
Please open a terminal and run and post this command:```
lsusb
```Once we have that information, we will propose a solution.

---

### Post by rodrigo8 on 2014-03-27
This is what I got

Bus 001 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 006: ID 04da:1800 Panasonic (Matsushita) DY-WL10 802.11abgn Adapter [Broadcom BCM4323]
Bus 005 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 005 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2014-03-27
This is crazy! Please see here: [https://wikidevi.com/wiki/Panasonic_DY-WL10](https://wikidevi.com/wiki/Panasonic_DY-WL10)> Probable Linux driver
none, will not be supported by brcmfmacBut then see this!!! [https://wiki.debian.org/rt2800usb](https://wiki.debian.org/rt2800usb)> USB: 04DA:1800 Panasonic (Matsushita) DY-WL10 802.11abgn Adapter [Broadcom BCM4323]Why in the world would a driver for Realtek devices drive what purports to be a Broadcom?? In fact, the modaliases actually claim it!```
$ modinfo rt2800usb | grep 1800
alias:          usb:v[COLOR="#FF0000"]04DA[/COLOR]p[COLOR="#FF0000"]1800[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```I love a challenge!

Did rt2800usb load? May we see:```
lsmod | grep rt2
iwconfig
modinfo rt2800usb | grep 1800
uname -r
```Crazyyyy.

---

### Post by rodrigo8 on 2014-03-27
This is what I got
First Code
roy@ubuntu:~$ $ modinfo rt2800usb | grep 1800
$: command not found
roy@ubuntu:~$ alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*


Second Code
roy@ubuntu:~$ lsmod | grep rt2
rt2800usb              27225  0 
rt2800lib              81972  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20886  1 rt2800usb
rt2x00lib              56180  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              619465  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              499466  3 wl,rt2x00lib,mac80211
roy@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

roy@ubuntu:~$ modinfo rt2800usb | grep 1800
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*
roy@ubuntu:~$ uname -r
3.11.0-15-generic

---

### Post by chili555 on 2014-03-27
As you have seen, rt2800usb is incorrect; let's blacklist the incorrect driver:```
sudo -i
echo "blacklist rt2800usb"  >>  /etc/modprobe.d/blacklist.conf
exit
```We also see that you tried the Broadcom STA driver that is also incorrect; let's remove it:```
sudo apt-get purge bcmwl-kernel-source
```I believe the only way to get this going is ndiswrapper. Let's install it:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
```Now we grab the Windows XP driver that is required:```
wget http://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip
unzip bcm4323x_5.10.79.30_XP.zip
cd bcm4323x_5.10.79.30_XP
sudo ndiswrapper -i bcmwlhigh5.inf
sudo ndiwrapper -m
sudo modprobe ndiswrapper 
```You may safely copy and paste each command. Is your wireless working?

Please note and post any errors, warnings, etc.

---

### Post by rodrigo8 on 2014-03-27
This is what I got, and no I don't have wifi yet, Well it won't show any wifi connections


roy@ubuntu:~$ sudo -i
[sudo] password for roy: 
Sorry, try again.
[sudo] password for roy: 
root@ubuntu:~# sudo apt-get purge bcmwl-kernel-sourceReading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
root@ubuntu:~# sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
ndiswrapper-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
root@ubuntu:~# wget [http://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip](http://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip)
--2014-03-27 17:53:09--  [http://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip](http://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip)
Resolving wikidevi.com (wikidevi.com)... 192.211.52.72
Connecting to wikidevi.com (wikidevi.com)|192.211.52.72|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [https://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip](https://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip) [following]
--2014-03-27 17:53:10--  [https://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip](https://wikidevi.com/files/Drivers/Broadcom/bcm4323x_5.10.79.30_XP.zip)
Connecting to wikidevi.com (wikidevi.com)|192.211.52.72|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 873247 (853K) [application/zip]
Saving to: `bcm4323x_5.10.79.30_XP.zip.1'

100%[===========>] 873,247      793K/s   in 1.1s    

2014-03-27 17:53:12 (793 KB/s) - `bcm4323x_5.10.79.30_XP.zip.1' saved [873247/873247]

root@ubuntu:~# unzip bcm4323x_5.10.79.30_XP.zip
Archive:  bcm4323x_5.10.79.30_XP.zip
replace bcmh43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
error:  invalid response [cd bcm432]
replace bcmh43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [3x_5.10.7]
replace bcmh43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]s]ame: error:  invalid response [9.30_XP
replace bcmh43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: error:  invalid response [udo ndisw]
replace bcmh43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: new name:   inflating:  bcmwlhigh5.infsudo ndiwrapper -msudo modprobe ndiswrappery  
replace bcmh43xx64.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: bcmh43xx64.cat          
replace bcmwlhigh5.inf? [y]es, [n]o, [A]ll, [N]one, [r]ename: a
error:  invalid response [a]
replace bcmwlhigh5.inf? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: bcmwlhigh5.inf          
  inflating: bcmwlhigh5.sys          
  inflating: bcmwlhigh564.sys        
root@ubuntu:~#

---

### Post by chili555 on 2014-03-27
Please reboot and let me see:```
lsmod | grep wl
```> replace bcmh43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: new name: inflating: bcmwlhigh5.infsudo ndiwrapper -msudo modprobe ndiswrappery It looks like you typed commands on top of commands. Please try again, starting here but one at a time.> cd bcm4323x_5.10.79.30_XP
sudo ndiswrapper -i bcmwlhigh5.inf
sudo ndiwrapper -m
sudo modprobe ndiswrapperPlease let each command finish before you proceed.

---

### Post by rodrigo8 on 2014-03-27
Ok, I'm not that good sorry haha...and this is what I got!!
roy@ubuntu:~$ lsmod | grep wl
roy@ubuntu:~$ cd bcm4323x_5.10.79.30_XP
bash: cd: bcm4323x_5.10.79.30_XP: No such file or directory
roy@ubuntu:~$ sudo ndiswrapper -i bcmwlhigh5.inf
[sudo] password for roy: 
driver bcmwlhigh5 is already installed
roy@ubuntu:~$ sudo ndiwrapper -m
sudo: ndiwrapper: command not found
roy@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
roy@ubuntu:~$

---

### Post by chili555 on 2014-03-27
Please show me:```
sudo dpkg -s ndiswrapper-common
sudo dpkg -s ndiswrapper-dlms
sudo dpkg -s ndiswrapper-utils-1.9
lsb_release -d
```> roy@ubuntu:~$ sudo ndiwrapper -m
sudo: ndiwrapper: command not foundIt is not ndiwrapper; it is ndi[COLOR="#FF0000"]s[/COLOR]wrapper. Is there some problem with simply copy and paste my commands? When you see 'command not found' it might mean there is a typo; please recheck.> 0 upgraded, 0 newly installed, 0 to remove and [COLOR="#FF0000"]56 not upgraded[/COLOR].Please do:```
sudo apt-get update && sudo apt-get -y upgrade
```Reboot and give me the readings above.

---

### Post by rodrigo8 on 2014-03-27
I'll reboot right now
Last Code:
```
roy@ubuntu:~$ sudo apt-get update && sudo apt-get -y upgrade
[sudo] password for roy: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [375 kB] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [759 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [91.8 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,446 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [401 kB] 
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.2 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [237 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [96.5 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [784 kB]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,646 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [243 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en     
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [138 kB]
Fetched 3,305 kB in 3s (1,083 kB/s)                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic-lts-saucy linux-image-generic-lts-saucy
  linux-signed-image-generic-lts-saucy
The following packages will be upgraded:
  ca-certificates cups-filters file firefox gir1.2-gnomebluetooth-1.0
  gir1.2-gtk-3.0 gnome-bluetooth gnome-settings-daemon gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  initramfs-tools initramfs-tools-bin jockey-common jockey-gtk libcupsfilters1
  libgail-3-0 libglade2-0 libgnome-bluetooth8 libgnutls26 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgwibber-gtk2 libgwibber2 libmagic1
  libperl5.14 libpurple-bin libpurple0 libpython2.7 librsvg2-2 librsvg2-common
  libsmbclient libssh-4 libwbclient0 linux-firmware linux-firmware-nonfree
  linux-generic-lts-saucy linux-libc-dev linux-signed-generic-lts-saucy
  openssh-client perl perl-base perl-modules python2.7 python2.7-minimal
  samba-common samba-common-bin smbclient ssh-askpass-gnome sudo thunderbird
  thunderbird-gnome-support tzdata udisks update-manager update-manager-core
  xkb-data
60 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 139 MB of archives.
After this operation, 3,534 kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main perl amd64 5.14.2-6ubuntu2.4 [4,411 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libglade2-0 amd64 1:2.6.4-1ubuntu1.1 [53.0 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main tzdata all 2014a-0ubuntu0.12.04 [448 kB]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libperl5.14 amd64 5.14.2-6ubuntu2.4 [1,252 B]
Get:5 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main perl-base amd64 5.14.2-6ubuntu2.4 [1,513 kB]
Get:6 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main perl-modules all 5.14.2-6ubuntu2.4 [3,389 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main xkb-data all 2.5-1ubuntu1.5 [473 kB]
Get:8 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libgnutls26 amd64 2.12.14-5ubuntu3.7 [459 kB]
Get:9 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libcupsfilters1 amd64 1.0.18-0ubuntu0.2 [58.1 kB]
Get:10 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libgtk-3-bin amd64 3.4.2-0ubuntu0.7 [15.9 kB]
Get:11 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libgail-3-0 amd64 3.4.2-0ubuntu0.7 [24.0 kB]
Get:12 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libgtk-3-0 amd64 3.4.2-0ubuntu0.7 [2,285 kB]
Get:13 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libgtk-3-common all 3.4.2-0ubuntu0.7 [145 kB]
Get:14 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main librsvg2-common amd64 2.36.1-0ubuntu1.1 [21.0 kB]
Get:15 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main librsvg2-2 amd64 2.36.1-0ubuntu1.1 [105 kB]
Get:16 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libssh-4 amd64 0.5.2-1ubuntu0.12.04.3 [120 kB]
Get:17 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libwbclient0 amd64 2:3.6.3-2ubuntu2.10 [29.7 kB]
Get:18 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libsmbclient amd64 2:3.6.3-2ubuntu2.10 [2,159 kB]
Get:19 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libpython2.7 amd64 2.7.3-0ubuntu3.5 [1,188 kB]
Get:20 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main python2.7 amd64 2.7.3-0ubuntu3.5 [2,675 kB]
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main update-manager-core amd64 1:0.156.14.12 [181 kB]
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main update-manager all 1:0.156.14.12 [611 kB]
Get:23 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main python2.7-minimal amd64 2.7.3-0ubuntu3.5 [1,743 kB]
Get:24 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main file amd64 5.09-2ubuntu0.2 [19.7 kB]
Get:25 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libmagic1 amd64 5.09-2ubuntu0.2 [217 kB]
Get:26 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main sudo amd64 1.8.3p1-1ubuntu3.6 [299 kB]
Get:27 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main initramfs-tools all 0.99ubuntu13.5 [49.0 kB]
Get:28 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main initramfs-tools-bin amd64 0.99ubuntu13.5 [9,782 B]
Get:29 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main ca-certificates all 20130906ubuntu0.12.04.1 [192 kB]
Get:30 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main openssh-client amd64 1:5.9p1-5ubuntu1.2 [943 kB]
Get:31 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main gir1.2-gtk-3.0 amd64 3.4.2-0ubuntu0.7 [235 kB]
Get:32 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main cups-filters amd64 1.0.18-0ubuntu0.2 [365 kB]
Get:33 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main firefox amd64 28.0+build2-0ubuntu0.12.04.1 [30.5 MB]
Get:34 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libgnome-bluetooth8 amd64 3.2.2-0ubuntu5.1 [55.5 kB]
Get:35 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gnome-bluetooth amd64 3.2.2-0ubuntu5.1 [273 kB]
Get:36 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-gnomebluetooth-1.0 amd64 3.2.2-0ubuntu5.1 [5,746 B]
Get:37 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gwibber amd64 3.4.2-0ubuntu2.4 [157 kB]
Get:38 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service all 3.4.2-0ubuntu2.4 [39.6 kB]
Get:39 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libgwibber2 amd64 3.4.2-0ubuntu2.4 [71.0 kB]
Get:40 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main libgwibber-gtk2 amd64 3.4.2-0ubuntu2.4 [64.0 kB]
Get:41 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service-facebook all 3.4.2-0ubuntu2.4 [7,782 B]
Get:42 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service-identica all 3.4.2-0ubuntu2.4 [7,782 B]
Get:43 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gwibber-service-twitter all 3.4.2-0ubuntu2.4 [8,990 B]
Get:44 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main jockey-gtk all 0.9.7-0ubuntu7.14 [9,120 B]
Get:45 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main jockey-common all 0.9.7-0ubuntu7.14 [132 kB]
Get:46 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Get:47 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libpurple-bin all 1:2.10.3-0ubuntu1.4 [17.4 kB]
Get:48 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libpurple0 amd64 1:2.10.3-0ubuntu1.4 [1,769 kB]
Get:49 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-firmware all 1.79.10 [25.8 MB]
Get:50 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-generic-lts-saucy amd64 3.11.0.18.17 [1,742 B]
Get:51 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-libc-dev amd64 3.2.0-60.91 [865 kB]
Get:52 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-signed-generic-lts-saucy amd64 3.11.0.18.17 [1,772 B]
Get:53 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main smbclient amd64 2:3.6.3-2ubuntu2.10 [14.1 MB]
Get:54 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gnome-settings-daemon amd64 3.4.2-0ubuntu0.6.5 [481 kB]
Get:55 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main samba-common all 2:3.6.3-2ubuntu2.10 [325 kB]
Get:56 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main samba-common-bin amd64 2:3.6.3-2ubuntu2.10 [6,178 kB]
Get:57 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main ssh-askpass-gnome amd64 1:5.9p1-5ubuntu1.2 [16.0 kB]
Get:58 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main thunderbird amd64 1:24.4.0+build1-0ubuntu0.12.04.1 [29.5 MB]
Get:59 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main thunderbird-gnome-support amd64 1:24.4.0+build1-0ubuntu0.12.04.1 [9,138 B]
Get:60 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main udisks amd64 1.0.4-5ubuntu2.2 [250 kB]
Fetched 139 MB in 13s (10.2 MB/s)                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 142909 files and directories currently installed.)
Preparing to replace perl 5.14.2-6ubuntu2.3 (using .../perl_5.14.2-6ubuntu2.4_amd64.deb) ...
Unpacking replacement perl ...
Preparing to replace libperl5.14 5.14.2-6ubuntu2.3 (using .../libperl5.14_5.14.2-6ubuntu2.4_amd64.deb) ...
Unpacking replacement libperl5.14 ...
Preparing to replace perl-base 5.14.2-6ubuntu2.3 (using .../perl-base_5.14.2-6ubuntu2.4_amd64.deb) ...
Unpacking replacement perl-base ...
Processing triggers for man-db ...
Setting up perl-base (5.14.2-6ubuntu2.4) ...
(Reading database ... 142909 files and directories currently installed.)
Preparing to replace perl-modules 5.14.2-6ubuntu2.3 (using .../perl-modules_5.14.2-6ubuntu2.4_all.deb) ...
Unpacking replacement perl-modules ...
Preparing to replace libgnutls26 2.12.14-5ubuntu3.5 (using .../libgnutls26_2.12.14-5ubuntu3.7_amd64.deb) ...
Unpacking replacement libgnutls26 ...
Preparing to replace libcupsfilters1 1.0.18-0ubuntu0.1 (using .../libcupsfilters1_1.0.18-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libcupsfilters1 ...
Preparing to replace libgtk-3-bin 3.4.2-0ubuntu0.6 (using .../libgtk-3-bin_3.4.2-0ubuntu0.7_amd64.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0 3.4.2-0ubuntu0.6 (using .../libgail-3-0_3.4.2-0ubuntu0.7_amd64.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-0 3.4.2-0ubuntu0.6 (using .../libgtk-3-0_3.4.2-0ubuntu0.7_amd64.deb) ...
Unpacking replacement libgtk-3-0 ...
Preparing to replace libgtk-3-common 3.4.2-0ubuntu0.6 (using .../libgtk-3-common_3.4.2-0ubuntu0.7_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libglade2-0 1:2.6.4-1ubuntu1 (using .../libglade2-0_1%3a2.6.4-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libglade2-0 ...
Preparing to replace librsvg2-common 2.36.1-0ubuntu1 (using .../librsvg2-common_2.36.1-0ubuntu1.1_amd64.deb) ...
Unpacking replacement librsvg2-common ...
Preparing to replace librsvg2-2 2.36.1-0ubuntu1 (using .../librsvg2-2_2.36.1-0ubuntu1.1_amd64.deb) ...
Unpacking replacement librsvg2-2 ...
Preparing to replace libssh-4 0.5.2-1ubuntu0.12.04.2 (using .../libssh-4_0.5.2-1ubuntu0.12.04.3_amd64.deb) ...
Unpacking replacement libssh-4 ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.9 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.10_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.9 (using .../libsmbclient_2%3a3.6.3-2ubuntu2.10_amd64.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace libpython2.7 2.7.3-0ubuntu3.4 (using .../libpython2.7_2.7.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement libpython2.7 ...
Preparing to replace python2.7 2.7.3-0ubuntu3.4 (using .../python2.7_2.7.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.3-0ubuntu3.4 (using .../python2.7-minimal_2.7.3-0ubuntu3.5_amd64.deb) ...
Unpacking replacement python2.7-minimal ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for libgdk-pixbuf2.0-0 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up python2.7-minimal (2.7.3-0ubuntu3.5) ...
(Reading database ... 142909 files and directories currently installed.)
Preparing to replace tzdata 2013g-0ubuntu0.12.04 (using .../tzdata_2014a-0ubuntu0.12.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2014a-0ubuntu0.12.04) ...

Current default time zone: 'America/New_York'
Local time is now:      Thu Mar 27 19:24:41 EDT 2014.
Universal Time is now:  Thu Mar 27 23:24:41 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 142888 files and directories currently installed.)
Preparing to replace file 5.09-2 (using .../file_5.09-2ubuntu0.2_amd64.deb) ...
Unpacking replacement file ...
Preparing to replace libmagic1 5.09-2 (using .../libmagic1_5.09-2ubuntu0.2_amd64.deb) ...
Unpacking replacement libmagic1 ...
Preparing to replace sudo 1.8.3p1-1ubuntu3.4 (using .../sudo_1.8.3p1-1ubuntu3.6_amd64.deb) ...
Unpacking replacement sudo ...
Preparing to replace xkb-data 2.5-1ubuntu1.3 (using .../xkb-data_2.5-1ubuntu1.5_all.deb) ...
Unpacking replacement xkb-data ...
Preparing to replace initramfs-tools 0.99ubuntu13.4 (using .../initramfs-tools_0.99ubuntu13.5_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace initramfs-tools-bin 0.99ubuntu13.4 (using .../initramfs-tools-bin_0.99ubuntu13.5_amd64.deb) ...
Unpacking replacement initramfs-tools-bin ...
Preparing to replace ca-certificates 20111211 (using .../ca-certificates_20130906ubuntu0.12.04.1_all.deb) ...
Unpacking replacement ca-certificates ...
Preparing to replace openssh-client 1:5.9p1-5ubuntu1.1 (using .../openssh-client_1%3a5.9p1-5ubuntu1.2_amd64.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace gir1.2-gtk-3.0 3.4.2-0ubuntu0.6 (using .../gir1.2-gtk-3.0_3.4.2-0ubuntu0.7_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace update-manager-core 1:0.156.14.11 (using .../update-manager-core_1%3a0.156.14.12_amd64.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace update-manager 1:0.156.14.11 (using .../update-manager_1%3a0.156.14.12_all.deb) ...
Unpacking replacement update-manager ...
Preparing to replace cups-filters 1.0.18-0ubuntu0.1 (using .../cups-filters_1.0.18-0ubuntu0.2_amd64.deb) ...
Unpacking replacement cups-filters ...
Preparing to replace firefox 26.0+build2-0ubuntu0.12.04.2 (using .../firefox_28.0+build2-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace libgnome-bluetooth8 3.2.2-0ubuntu5 (using .../libgnome-bluetooth8_3.2.2-0ubuntu5.1_amd64.deb) ...
Unpacking replacement libgnome-bluetooth8 ...
Preparing to replace gnome-bluetooth 3.2.2-0ubuntu5 (using .../gnome-bluetooth_3.2.2-0ubuntu5.1_amd64.deb) ...
Unpacking replacement gnome-bluetooth ...
Preparing to replace gir1.2-gnomebluetooth-1.0 3.2.2-0ubuntu5 (using .../gir1.2-gnomebluetooth-1.0_3.2.2-0ubuntu5.1_amd64.deb) ...
Unpacking replacement gir1.2-gnomebluetooth-1.0 ...
Preparing to replace gwibber 3.4.2-0ubuntu2.3 (using .../gwibber_3.4.2-0ubuntu2.4_amd64.deb) ...
Unpacking replacement gwibber ...
Preparing to replace gwibber-service 3.4.2-0ubuntu2.3 (using .../gwibber-service_3.4.2-0ubuntu2.4_all.deb) ...
Unpacking replacement gwibber-service ...
Preparing to replace libgwibber2 3.4.2-0ubuntu2.3 (using .../libgwibber2_3.4.2-0ubuntu2.4_amd64.deb) ...
Unpacking replacement libgwibber2 ...
Preparing to replace libgwibber-gtk2 3.4.2-0ubuntu2.3 (using .../libgwibber-gtk2_3.4.2-0ubuntu2.4_amd64.deb) ...
Unpacking replacement libgwibber-gtk2 ...
Preparing to replace gwibber-service-facebook 3.4.2-0ubuntu2.3 (using .../gwibber-service-facebook_3.4.2-0ubuntu2.4_all.deb) ...
Unpacking replacement gwibber-service-facebook ...
Preparing to replace gwibber-service-identica 3.4.2-0ubuntu2.3 (using .../gwibber-service-identica_3.4.2-0ubuntu2.4_all.deb) ...
Unpacking replacement gwibber-service-identica ...
Preparing to replace gwibber-service-twitter 3.4.2-0ubuntu2.3 (using .../gwibber-service-twitter_3.4.2-0ubuntu2.4_all.deb) ...
Unpacking replacement gwibber-service-twitter ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.13 (using .../jockey-gtk_0.9.7-0ubuntu7.14_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.13 (using .../jockey-common_0.9.7-0ubuntu7.14_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libpurple-bin 1:2.10.3-0ubuntu1.3 (using .../libpurple-bin_1%3a2.10.3-0ubuntu1.4_all.deb) ...
Unpacking replacement libpurple-bin ...
Preparing to replace libpurple0 1:2.10.3-0ubuntu1.3 (using .../libpurple0_1%3a2.10.3-0ubuntu1.4_amd64.deb) ...
Unpacking replacement libpurple0 ...
Preparing to replace linux-firmware 1.79.9 (using .../linux-firmware_1.79.10_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace linux-firmware-nonfree 1.11 (using .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Unpacking replacement linux-firmware-nonfree ...
Preparing to replace linux-generic-lts-saucy 3.11.0.15.14 (using .../linux-generic-lts-saucy_3.11.0.18.17_amd64.deb) ...
Unpacking replacement linux-generic-lts-saucy ...
Preparing to replace linux-libc-dev 3.2.0-58.88 (using .../linux-libc-dev_3.2.0-60.91_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace linux-signed-generic-lts-saucy 3.11.0.15.14 (using .../linux-signed-generic-lts-saucy_3.11.0.18.17_amd64.deb) ...
Unpacking replacement linux-signed-generic-lts-saucy ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.9 (using .../smbclient_2%3a3.6.3-2ubuntu2.10_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.9 (using .../samba-common_2%3a3.6.3-2ubuntu2.10_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.9 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.10_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace ssh-askpass-gnome 1:5.9p1-5ubuntu1.1 (using .../ssh-askpass-gnome_1%3a5.9p1-5ubuntu1.2_amd64.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Preparing to replace thunderbird 1:24.2.0+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a24.4.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 1:24.2.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a24.4.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace udisks 1.0.4-5ubuntu2.1 (using .../udisks_1.0.4-5ubuntu2.2_amd64.deb) ...
Unpacking replacement udisks ...
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.4 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.5_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for cups ...
Updating PPD files for cups-filters ...
Updating PPD files for foomatic-db-compressed-ppds ...
Updating PPD files for foomatic-db-engine ...
Updating PPD files for ghostscript-cups ...
Updating PPD files for openprinting-ppds ...
Updating PPD files for c2esp ...
Updating PPD files for foo2zjs ...
Updating PPD files for gutenprint ...
Updating PPD files for hpcups ...
Updating PPD files for hpijs ...
Updating PPD files for postscript-hp ...
Updating PPD files for ptouch ...
Updating PPD files for pxljr ...
Updating PPD files for sag-gdi ...
Updating PPD files for splix ...
Setting up libperl5.14 (5.14.2-6ubuntu2.4) ...
Setting up libgnutls26 (2.12.14-5ubuntu3.7) ...
Setting up libcupsfilters1 (1.0.18-0ubuntu0.2) ...
Setting up libgtk-3-common (3.4.2-0ubuntu0.7) ...
Setting up libgtk-3-0 (3.4.2-0ubuntu0.7) ...
Setting up libgtk-3-bin (3.4.2-0ubuntu0.7) ...
Setting up libgail-3-0 (3.4.2-0ubuntu0.7) ...
Setting up libglade2-0 (1:2.6.4-1ubuntu1.1) ...
Setting up librsvg2-2 (2.36.1-0ubuntu1.1) ...
Setting up librsvg2-common (2.36.1-0ubuntu1.1) ...
Setting up libssh-4 (0.5.2-1ubuntu0.12.04.3) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.10) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.10) ...
Setting up python2.7 (2.7.3-0ubuntu3.5) ...
Setting up libpython2.7 (2.7.3-0ubuntu3.5) ...
Setting up libmagic1 (5.09-2ubuntu0.2) ...
Setting up file (5.09-2ubuntu0.2) ...
Setting up sudo (1.8.3p1-1ubuntu3.6) ...
Installing new version of config file /etc/init.d/sudo ...
Setting up xkb-data (2.5-1ubuntu1.5) ...
Setting up initramfs-tools-bin (0.99ubuntu13.5) ...
Setting up initramfs-tools (0.99ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
Setting up ca-certificates (20130906ubuntu0.12.04.1) ...
Updating certificates in /etc/ssl/certs... WARNING: Skipping duplicate certificate Go_Daddy_Class_2_CA.pem
WARNING: Skipping duplicate certificate Go_Daddy_Class_2_CA.pem
21 added, 9 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Setting up openssh-client (1:5.9p1-5ubuntu1.2) ...
Setting up gir1.2-gtk-3.0 (3.4.2-0ubuntu0.7) ...
Setting up update-manager-core (1:0.156.14.12) ...
Setting up update-manager (1:0.156.14.12) ...
Setting up cups-filters (1.0.18-0ubuntu0.2) ...
.
Setting up firefox (28.0+build2-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libgnome-bluetooth8 (3.2.2-0ubuntu5.1) ...
Setting up gir1.2-gnomebluetooth-1.0 (3.2.2-0ubuntu5.1) ...
Setting up gnome-bluetooth (3.2.2-0ubuntu5.1) ...
Setting up gwibber-service (3.4.2-0ubuntu2.4) ...
Setting up libgwibber2 (3.4.2-0ubuntu2.4) ...
Setting up libgwibber-gtk2 (3.4.2-0ubuntu2.4) ...
Setting up gwibber (3.4.2-0ubuntu2.4) ...
Setting up gwibber-service-facebook (3.4.2-0ubuntu2.4) ...
Setting up gwibber-service-identica (3.4.2-0ubuntu2.4) ...
Setting up gwibber-service-twitter (3.4.2-0ubuntu2.4) ...
Setting up jockey-common (0.9.7-0ubuntu7.14) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.14) ...
Setting up libpurple-bin (1:2.10.3-0ubuntu1.4) ...
Setting up libpurple0 (1:2.10.3-0ubuntu1.4) ...
Setting up linux-firmware (1.79.10) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
Setting up linux-generic-lts-saucy (3.11.0.18.17) ...
Setting up linux-libc-dev (3.2.0-60.91) ...
Setting up linux-signed-generic-lts-saucy (3.11.0.18.17) ...
Setting up samba-common (2:3.6.3-2ubuntu2.10) ...
Setting up smbclient (2:3.6.3-2ubuntu2.10) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.10) ...
Setting up ssh-askpass-gnome (1:5.9p1-5ubuntu1.2) ...
Setting up thunderbird (1:24.4.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:24.4.0+build1-0ubuntu0.12.04.1) ...
Setting up udisks (1.0.4-5ubuntu2.2) ...
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.5) ...
Setting up perl-modules (5.14.2-6ubuntu2.4) ...
Setting up perl (5.14.2-6ubuntu2.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libgdk-pixbuf2.0-0 ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic
Warning: No support for locale: en_US.utf8
roy@ubuntu:~$
```

---

### Post by rodrigo8 on 2014-03-27
Ok this is what I got...
First Code:
roy@ubuntu:~$ sudo dpkg -s ndiswrapper-common
[sudo] password for roy: 
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 71
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.57-1ubuntu1
Replaces: ndiswrapper-utils
Suggests: ndiswrapper-source
Description: Common scripts required to use the utilities for ndiswrapper
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains wrapper scripts to call out to the proper
 versions of whatever -utils-X.X package is installed.
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)


Second Code:
roy@ubuntu:~$ sudo dpkg -s ndiswrapper-dlms
Package `ndiswrapper-dlms' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


Third Code:
roy@ubuntu:~$ sudo dpkg -s ndiswrapper-utils-1.9
Package: ndiswrapper-utils-1.9
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 107
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ndiswrapper
Version: 1.57-1ubuntu1
Depends: libc6 (>= 2.7), ndiswrapper-common
Suggests: ndiswrapper-dkms, ndiswrapper-source
Description: Userspace utilities for the ndiswrapper Linux kernel module
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains the userspace tools. You will also need the kernel
 module package.
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)


Fourth Code:
roy@ubuntu:~$ lsb_release -d
Description:    Ubuntu 12.04.4 LTS

---

### Post by chili555 on 2014-03-27
> sudo dpkg -s ndiswrapper-dlmsndiswrapper-d[COLOR="#FF0000"]k[/COLOR]ms, please. 

Now does it load correctly?```
sudo modprobe ndiswrapper
```

---

### Post by rodrigo8 on 2014-03-27
Sorry I'm really just doing copy paste..
FIrst Code:
roy@ubuntu:~$ sudo dpkg -s ndiswrapper-dkms 
[sudo] password for roy: 
Package: ndiswrapper-dkms
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 760
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.57-1ubuntu1
Depends: dkms (>= 2.1.0.0)
Description: Source for the ndiswrapper Linux kernel module (DKMS)
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package provides the source code for ndiswrapper kernel module to be
 build with dkms.
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
roy@ubuntu:~$ 

Second Code:
roy@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

---

### Post by chili555 on 2014-03-27
> roy@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found. Sticky problem we have here. Before I come up there with a hammer, please post:```
uname -r
arch
```

---

### Post by rodrigo8 on 2014-03-27
This is what I got now!

roy@ubuntu:~$ uname -r
3.11.0-15-generic
roy@ubuntu:~$ arch
x86_64

---

### Post by chili555 on 2014-03-27
Please do:

```
wget http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-2_all.deb

wget http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-2_all.deb

wget http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-2_amd64.deb 

sudo dpkg -i ndis*.deb

sudo modprobe ndiswrapper
iwconfig
```We are installing 1.58 in place of the obviously faulty 1.57.

---

### Post by rodrigo8 on 2014-03-27
Yeeeeeeeeeeeees!! It's working now!! Thanks a lot really!! You're the smartest person in the world!! Thanks really thanks!!!

---

### Post by chili555 on 2014-03-27
Awesome. Please help the searchers by using thread tools at the top to mark Solved.

Glad it's working.

---

