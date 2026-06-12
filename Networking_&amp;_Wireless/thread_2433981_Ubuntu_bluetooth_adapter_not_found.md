---
title: "Ubuntu bluetooth adapter not found"
date: 2019-12-28
forum: Networking &amp; Wireless
---

### Post by abuti-jj on 2019-12-28
Hi,

I'm not good at linux, but somehow I managed to make wifi work after following some website advice. Could you help me with bluetooth adapter.
So far I have done the following:


sudo apt-get install dkms git build-essential
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf

after the last line, it shows: echo "options rtl8723de ant_sel=2" 

What should I do next to make bluetooth adapters found?

My system information:

                       system         Computer
/0                     bus            Motherboard
/0/0                   memory         8GiB System memory
/0/1                   processor      Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
/0/100                 bridge         Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
/0/100/2               display        HD Graphics 620
/0/100/4               generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
/0/100/8               generic        Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
/0/100/14              bus            Sunrise Point-LP USB 3.0 xHCI Controller
/0/100/14.2            generic        Sunrise Point-LP Thermal subsystem
/0/100/16              communication  Sunrise Point-LP CSME HECI #1
/0/100/17              storage        Sunrise Point-LP SATA Controller [AHCI mode]
/0/100/1c              bridge         Sunrise Point-LP PCI Express Root Port #5
/0/100/1c/0    eno1    network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.5            bridge         Sunrise Point-LP PCI Express Root Port #6
/0/100/1c.5/0  wlo1    network        RTL8723DE 802.11b/g/n PCIe Adapter
/0/100/1f              bridge         Sunrise Point LPC Controller/eSPI Controller
/0/100/1f.2            memory         Memory controller

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b5db Chicony Electronics Co., Ltd HP Webcam
Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

uname -r

5.3.0-24-generic


I tried following some online tips and also did the following:


sudo add-apt-repository ppa:hanipouspilot/bluetooth
[sudo] password for :

More info: [https://launchpad.net/~hanipouspilot/+a](https://launchpad.net/~hanipouspilot/+a) ... /bluetooth
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Kubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Err:2 cdrom://Kubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:3 [http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu](http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu) eoan InRelease
Hit:4 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan InRelease
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [97.5 kB]
Get:6 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates InRelease [97.5 kB]
Hit:7 [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) eoan InRelease
Err:8 [http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu](http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu) eoan Release
404 Not Found [IP: 91.189.95.83 80]
Get:9 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-backports InRelease [88.8 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 DEP-11 Metadata [204 B]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe amd64 DEP-11 Metadata [1,672 B]
Get:12 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/main amd64 DEP-11 Metadata [60.2 kB]
Get:13 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 48x48 Icons [9,940 B]
Get:14 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 64x64 Icons [15.1 kB]
Get:15 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 128x128 Icons [34.9 kB]
Get:16 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 DEP-11 Metadata [25.9 kB]
Get:17 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/universe DEP-11 48x48 Icons [18.5 kB]
Get:18 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/universe DEP-11 64x64 Icons [22.9 kB]
Get:19 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates/universe DEP-11 128x128 Icons [51.7 kB]
Get:20 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-backports/universe amd64 DEP-11 Metadata [7,756 B]
Reading package lists... Done
E: The repository 'cdrom://Kubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

sudo apt-get update
Ign:1 cdrom://Kubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Err:2 cdrom://Kubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease
Hit:4 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan InRelease
Ign:5 [http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu](http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu) eoan InRelease
Hit:6 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-updates InRelease
Hit:7 [http://bf.archive.ubuntu.com/ubuntu](http://bf.archive.ubuntu.com/ubuntu) eoan-backports InRelease
Hit:8 [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) eoan InRelease
Err:9 [http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu](http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu) eoan Release
404 Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'cdrom://Kubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

sudo apt install btrtl-rtl8723de-dkms
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package btrtl-rtl8723de-dkms

Thanks

---

### Post by jeremy31 on 2019-12-28
You should file a bug report, start at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by praseodym on 2019-12-28
[https://ubuntuforums.org/showthread.php?t=2367405&page=11&p=13764640#post13764640](https://ubuntuforums.org/showthread.php?t=2367405&page=11&p=13764640#post13764640)

check the FW

---

### Post by abuti-jj on 2020-01-02
Thanks. I think Ubuntu should make some avenue easier for novices, like driver installations and troubleshooting. A self diagnosis and repair solution would be great.

Would an external usb bluetooth dongle have the same problem?

---

