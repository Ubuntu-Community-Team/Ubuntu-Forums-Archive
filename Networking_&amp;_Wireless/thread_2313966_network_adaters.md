---
title: "network adaters"
date: 2016-02-17
forum: Networking &amp; Wireless
---

### Post by amiralex32 on 2016-02-17
Dear all
             I am using ubuntu 14.4 and my network adapters is not working with ubuntu. I have tried it with windows xp and it is working well so i followed those steps but with no results

```
amiraex@Master:~$ sudo lshw -C network -numeric
[sudo] password for amiraex: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN [14E4:4311]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX [14E4:170C]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:ef9fe000-ef9fffff
```
```
amiraex@Master:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 245 not upgraded.
Need to get 2,436 kB of archives.
After this operation, 8,249 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-firmware-nonfree
Install these packages without verification? [y/N] y
Get:1 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/multiverse linux-firmware-nonfree all 1.14ubuntu3 [2,436 kB]
Fetched 2,436 kB in 1min 10s (34.8 kB/s)                                       
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 166513 files and directories currently installed.)
Preparing to unpack .../linux-firmware-nonfree_1.14ubuntu3_all.deb ...
Unpacking linux-firmware-nonfree (1.14ubuntu3) ...
Setting up linux-firmware-nonfree (1.14ubuntu3) ...
amiraex@Master:~$ sudo modprobe -r b43 && sudo modprobe b43
^Camiraex@Master:~$ sudo apt-get install build-essential linux-headers-generic lux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.19.0-25-generic is already the newest version.
linux-headers-3.19.0-25-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.8 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libstdc++-4.8-dev
  linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
Suggested packages:
  debian-keyring g++-multilib g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg
  libstdc++-4.8-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.8 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++-4.8-dev
  linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-headers-generic
The following packages will be upgraded:
  libdpkg-perl
1 upgraded, 11 newly installed, 0 to remove and 244 not upgraded.
Need to get 26.4 MB of archives.
After this operation, 114 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libstdc++-4.8-dev g++-4.8 libdpkg-perl dpkg-dev linux-headers-3.13.0-74
  linux-headers-3.13.0-74-generic linux-headers-generic
Install these packages without verification? [y/N] y
Err [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main libstdc++-4.8-dev i386 4.8.4-2ubuntu1~14.04
  404  Not Found [IP: 91.189.91.24 80]
Err [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main g++-4.8 i386 4.8.4-2ubuntu1~14.04
  404  Not Found [IP: 91.189.91.24 80]
Get:1 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/main g++ i386 4:4.8.2-1ubuntu6 [1,500 B]
Get:2 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main libdpkg-perl all 1.17.5ubuntu5.5 [179 kB]
Get:3 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main dpkg-dev all 1.17.5ubuntu5.5 [726 kB]
Get:4 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/main build-essential i386 11.6ubuntu6 [4,824 B]
Get:5 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:6 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/main libalgorithm-diff-xs-perl i386 0.04-2build4 [13.1 kB]
Get:7 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:8 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-74 all 3.13.0-74.118 [8,889 kB]
Get:9 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-74-generic i386 3.13.0-74.118 [690 kB]
Err [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-generic i386 3.13.0.74.80
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-generic i386 3.13.0.74.80
  404  Not Found [IP: 91.189.92.200 80]
Fetched 10.6 MB in 2min 24s (73.3 kB/s)                                        
E: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libstdc++-4.8-dev_4.8.4-2ubuntu1~14.04_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libstdc++-4.8-dev_4.8.4-2ubuntu1~14.04_i386.deb)  404  Not Found [IP: 91.189.91.24 80]

E: Failed to fetch [http://eg.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/g++-4.8_4.8.4-2ubuntu1~14.04_i386.deb](http://eg.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/g++-4.8_4.8.4-2ubuntu1~14.04_i386.deb)  404  Not Found [IP: 91.189.91.24 80]

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.74.80_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.74.80_i386.deb)  404  Not Found [IP: 91.189.92.200 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
amiraex@Master:~$ [http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb)
bash: [http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb:](http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb:) No such file or directory
amiraex@Master:~$ [http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb)
bash: [http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb:](http://de.archive.ubuntu.com/ubuntu/...buntu1_all.deb:) No such file or directory
amiraex@Master:~$ sudo dpkg -i ~/Downloads/linux-*.deb
dpkg: error processing archive /home/amiraex/Downloads/linux-*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/amiraex/Downloads/linux-*.deb
amiraex@Master:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 245 not upgraded.
Need to get 29.3 kB of archives.
After this operation, 146 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/main b43-fwcutter i386 1:018-2 [25.4 kB]
Get:2 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) trusty/multiverse firmware-b43-installer all 1:018-2 [3,960 B]
Fetched 29.3 kB in 8s (3,397 B/s)                                              
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 166559 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a018-2_i386.deb ...
Unpacking b43-fwcutter (1:018-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a018-2_all.deb ...
Unpacking firmware-b43-installer (1:018-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up b43-fwcutter (1:018-2) ...
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2016-02-17 16:59:53--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... 173.254.28.119
Connecting to [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com)|173.254.28.119|:80](www.lwfinger.com)|173.254.28.119|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: &#8216;broadcom-wl-5.100.138.tar.bz2&#8217;

100%[======================================>] 13,514,651   120KB/s   in 2m 38s 

2016-02-17 17:02:35 (83.6 KB/s) - &#8216;broadcom-wl-5.100.138.tar.bz2&#8217; saved [13514651/13514651]

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


```

thanks for help

---

