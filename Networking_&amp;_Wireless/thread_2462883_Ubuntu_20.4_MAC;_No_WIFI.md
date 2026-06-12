---
title: "Ubuntu 20.4: MAC; No WIFI"
date: 2021-05-29
forum: Networking &amp; Wireless
---

### Post by nikkim on 2021-05-29
Hello,
I am not a IT guy. I installed Ubuntu on my old MAC but cannot set up WIFI. It is a dual boot from an USB. Wifi is not displayed as a network option. I already have installed a driver but still does not work. Attached please find system information and installation protocol.  Thanks for your help.


```
 buntu@ubuntu:~$ sudo lshw -C network; lsb_release -a; uname -a; sudo dmidecode -t 1
  *-network                 
       description: Network controller
       product: BCM4360 802.11ac Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:18 memory:98600000-98607fff memory:98400000-985fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM57766 Gigabit Ethernet PCIe
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0f0
       version: 01
       serial: ac:87:a3:09:07:2c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=5.8.0-43-generic duplex=full firmware=57766a-v1.15 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:98700000-9870ffff memory:98710000-9871ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
Linux ubuntu 5.8.0-43-generic #49~20.04.1-Ubuntu SMP Fri Feb 5 09:57:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.4 present.

Wrong DMI structures length: 2753 bytes announced, only 2535 bytes available.
Handle 0x000D, DMI type 1, 27 bytes
System Information
    Manufacturer: Apple Inc.
    Product Name: iMac14,1
    Version: 1.0
    Serial Number: C02NM13RF8J2
    UUID: d5d5bf82-e68d-f759-917e-7bc5ea06d9cc
    Wake-up Type: Power Switch
    SKU Number: System SKU#
    Family: iMac

Invalid entry length (0). DMI table is broken! Stop.

```


```
/C lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
03:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
03:00.1 SD Host controller [0805]: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 01)ODE]


```


```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu build-essential dkms
  dpkg-dev fakeroot g++ g++-9 gcc gcc-9 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan5 libatomic1
  libbinutils libc-dev-bin libc6-dev libcrypt-dev libctf-nobfd0 libctf0
  libfakeroot libgcc-9-dev libitm1 liblsan0 libquadmath0 libstdc++-9-dev
  libtsan0 libubsan1 linux-libc-dev make manpages-dev
Suggested packages:
  binutils-doc menu debian-keyring g++-multilib g++-9-multilib gcc-9-doc
  gcc-multilib autoconf automake libtool flex bison gcc-doc gcc-9-multilib
  gcc-9-locales glibc-doc libstdc++-9-doc make-doc
The following NEW packages will be installed:
  bcmwl-kernel-source binutils binutils-common binutils-x86-64-linux-gnu
  build-essential dkms dpkg-dev fakeroot g++ g++-9 gcc gcc-9
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan5 libatomic1 libbinutils libc-dev-bin libc6-dev libcrypt-dev
  libctf-nobfd0 libctf0 libfakeroot libgcc-9-dev libitm1 liblsan0 libquadmath0
  libstdc++-9-dev libtsan0 libubsan1 linux-libc-dev make manpages-dev
0 upgraded, 34 newly installed, 0 to remove and 260 not upgraded.
Need to get 5,134 kB/33.0 MB of archives.
After this operation, 151 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://security.ubuntu.com/ubuntu focal-security/main amd64 binutils-common amd64 2.34-6ubuntu1.1 [207 kB]
Get:2 http://security.ubuntu.com/ubuntu focal-security/main amd64 libbinutils amd64 2.34-6ubuntu1.1 [475 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 dkms all 2.8.1-5ubuntu2 [66.8 kB]
Get:4 http://security.ubuntu.com/ubuntu focal-security/main amd64 libctf-nobfd0 amd64 2.34-6ubuntu1.1 [47.1 kB]
Get:5 http://security.ubuntu.com/ubuntu focal-security/main amd64 libctf0 amd64 2.34-6ubuntu1.1 [46.6 kB]
Get:6 http://security.ubuntu.com/ubuntu focal-security/main amd64 binutils-x86-64-linux-gnu amd64 2.34-6ubuntu1.1 [1,613 kB]
Get:7 http://security.ubuntu.com/ubuntu focal-security/main amd64 binutils amd64 2.34-6ubuntu1.1 [3,380 B]
Get:8 http://security.ubuntu.com/ubuntu focal-security/main amd64 linux-libc-dev amd64 5.4.0-73.82 [1,130 kB]
Get:9 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libitm1 amd64 10.2.0-5ubuntu1~20.04 [26.4 kB]
Get:10 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libatomic1 amd64 10.2.0-5ubuntu1~20.04 [9,300 B]
Get:11 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libasan5 amd64 9.3.0-17ubuntu1~20.04 [394 kB]
Get:12 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 liblsan0 amd64 10.2.0-5ubuntu1~20.04 [144 kB]
Get:13 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libtsan0 amd64 10.2.0-5ubuntu1~20.04 [320 kB]
Get:14 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libubsan1 amd64 10.2.0-5ubuntu1~20.04 [136 kB]
Get:15 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu7~20.04.2 [1,545 kB]
Get:16 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libquadmath0 amd64 10.2.0-5ubuntu1~20.04 [146 kB]
Get:17 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libgcc-9-dev amd64 9.3.0-17ubuntu1~20.04 [2,360 kB]
Get:18 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 gcc-9 amd64 9.3.0-17ubuntu1~20.04 [8,241 kB]
Get:19 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 gcc amd64 4:9.3.0-1ubuntu2 [5,208 B]
Get:20 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 make amd64 4.2.1-1.2 [162 kB]
Get:21 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 dpkg-dev all 1.19.7ubuntu3 [679 kB]
Get:22 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libc-dev-bin amd64 2.31-0ubuntu9.2 [71.8 kB]
Get:23 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libcrypt-dev amd64 1:4.4.10-10ubuntu4 [104 kB]
Get:24 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libc6-dev amd64 2.31-0ubuntu9.2 [2,520 kB]
Get:25 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libstdc++-9-dev amd64 9.3.0-17ubuntu1~20.04 [1,714 kB]
Get:26 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 g++-9 amd64 9.3.0-17ubuntu1~20.04 [8,405 kB]
Get:27 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 g++ amd64 4:9.3.0-1ubuntu2 [1,604 B]
Get:28 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 build-essential amd64 12.8ubuntu1.1 [4,664 B]
Get:29 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libfakeroot amd64 1.24-1 [25.7 kB]
Get:30 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 fakeroot amd64 1.24-1 [62.6 kB]
Get:31 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libalgorithm-diff-perl all 1.19.03-2 [46.6 kB]
Get:32 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6 [11.3 kB]
Get:33 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 libalgorithm-merge-perl all 0.08-3 [12.0 kB]
Get:34 cdrom://Ubuntu 20.04.2.0 LTS _Focal Fossa_ - Release amd64 (20210209.1) focal/main amd64 manpages-dev all 5.05-1 [2,266 kB]
Fetched 5,134 kB in 1s (5,404 kB/s)                   
Extracting templates from packages: 100%
Selecting previously unselected package binutils-common:amd64.
(Reading database ... 189770 files and directories currently installed.)
Preparing to unpack .../00-binutils-common_2.34-6ubuntu1.1_amd64.deb ...
Unpacking binutils-common:amd64 (2.34-6ubuntu1.1) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../01-libbinutils_2.34-6ubuntu1.1_amd64.deb ...
Unpacking libbinutils:amd64 (2.34-6ubuntu1.1) ...
Selecting previously unselected package libctf-nobfd0:amd64.
Preparing to unpack .../02-libctf-nobfd0_2.34-6ubuntu1.1_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.34-6ubuntu1.1) ...
Selecting previously unselected package libctf0:amd64.
Preparing to unpack .../03-libctf0_2.34-6ubuntu1.1_amd64.deb ...
Unpacking libctf0:amd64 (2.34-6ubuntu1.1) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../04-binutils-x86-64-linux-gnu_2.34-6ubuntu1.1_amd64.deb .
..
Unpacking binutils-x86-64-linux-gnu (2.34-6ubuntu1.1) ...
Selecting previously unselected package binutils.
Preparing to unpack .../05-binutils_2.34-6ubuntu1.1_amd64.deb ...
Unpacking binutils (2.34-6ubuntu1.1) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../06-libitm1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libitm1:amd64 (10.2.0-5ubuntu1~20.04) ...
Selecting previously unselected package libatomic1:amd64.
Preparing to unpack .../07-libatomic1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libatomic1:amd64 (10.2.0-5ubuntu1~20.04) ...
Selecting previously unselected package libasan5:amd64.
Preparing to unpack .../08-libasan5_9.3.0-17ubuntu1~20.04_amd64.deb ...
Unpacking libasan5:amd64 (9.3.0-17ubuntu1~20.04) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../09-liblsan0_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking liblsan0:amd64 (10.2.0-5ubuntu1~20.04) ...
Selecting previously unselected package libtsan0:amd64.
Preparing to unpack .../10-libtsan0_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libtsan0:amd64 (10.2.0-5ubuntu1~20.04) ...
Selecting previously unselected package libubsan1:amd64.
Preparing to unpack .../11-libubsan1_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libubsan1:amd64 (10.2.0-5ubuntu1~20.04) ...
Selecting previously unselected package libquadmath0:amd64.
Preparing to unpack .../12-libquadmath0_10.2.0-5ubuntu1~20.04_amd64.deb ...
Unpacking libquadmath0:amd64 (10.2.0-5ubuntu1~20.04) ...
Selecting previously unselected package libgcc-9-dev:amd64.
Preparing to unpack .../13-libgcc-9-dev_9.3.0-17ubuntu1~20.04_amd64.deb ...
Unpacking libgcc-9-dev:amd64 (9.3.0-17ubuntu1~20.04) ...
Selecting previously unselected package gcc-9.
Preparing to unpack .../14-gcc-9_9.3.0-17ubuntu1~20.04_amd64.deb ...
Unpacking gcc-9 (9.3.0-17ubuntu1~20.04) ...
Selecting previously unselected package gcc.
Preparing to unpack .../15-gcc_9.3.0-1ubuntu2_amd64.deb ...
Unpacking gcc (4:9.3.0-1ubuntu2) ...
Selecting previously unselected package make.
Preparing to unpack .../16-make_4.2.1-1.2_amd64.deb ...
Unpacking make (4.2.1-1.2) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../17-dpkg-dev_1.19.7ubuntu3_all.deb ...
Unpacking dpkg-dev (1.19.7ubuntu3) ...
Selecting previously unselected package libc-dev-bin.
Preparing to unpack .../18-libc-dev-bin_2.31-0ubuntu9.2_amd64.deb ...
Unpacking libc-dev-bin (2.31-0ubuntu9.2) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../19-linux-libc-dev_5.4.0-73.82_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.4.0-73.82) ...
Selecting previously unselected package libcrypt-dev:amd64.
Preparing to unpack .../20-libcrypt-dev_4.4.10-10ubuntu4_amd64.deb ...
Unpacking libcrypt-dev:amd64 (1:4.4.10-10ubuntu4) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../21-libc6-dev_2.31-0ubuntu9.2_amd64.deb ...
Unpacking libc6-dev:amd64 (2.31-0ubuntu9.2) ...
Selecting previously unselected package libstdc++-9-dev:amd64.
Preparing to unpack .../22-libstdc++-9-dev_9.3.0-17ubuntu1~20.04_amd64.deb ...
Unpacking libstdc++-9-dev:amd64 (9.3.0-17ubuntu1~20.04) ...
Selecting previously unselected package g++-9.
Preparing to unpack .../23-g++-9_9.3.0-17ubuntu1~20.04_amd64.deb ...
Unpacking g++-9 (9.3.0-17ubuntu1~20.04) ...
Selecting previously unselected package g++.
Preparing to unpack .../24-g++_9.3.0-1ubuntu2_amd64.deb ...
Unpacking g++ (4:9.3.0-1ubuntu2) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../25-build-essential_12.8ubuntu1.1_amd64.deb ...
Unpacking build-essential (12.8ubuntu1.1) ...
Selecting previously unselected package dkms.
Preparing to unpack .../26-dkms_2.8.1-5ubuntu2_all.deb ...
Unpacking dkms (2.8.1-5ubuntu2) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../27-bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu7~20.04
.2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu7~20.04.2) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../28-libfakeroot_1.24-1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.24-1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../29-fakeroot_1.24-1_amd64.deb ...
Unpacking fakeroot (1.24-1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../30-libalgorithm-diff-perl_1.19.03-2_all.deb ...
Unpacking libalgorithm-diff-perl (1.19.03-2) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Preparing to unpack .../31-libalgorithm-diff-xs-perl_0.04-6_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl (0.04-6) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../32-libalgorithm-merge-perl_0.08-3_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-3) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../33-manpages-dev_5.05-1_all.deb ...
Unpacking manpages-dev (5.05-1) ...
Setting up manpages-dev (5.05-1) ...
Setting up libalgorithm-diff-perl (1.19.03-2) ...
Setting up binutils-common:amd64 (2.34-6ubuntu1.1) ...
Setting up linux-libc-dev:amd64 (5.4.0-73.82) ...
Setting up libctf-nobfd0:amd64 (2.34-6ubuntu1.1) ...
Setting up libfakeroot:amd64 (1.24-1) ...
Setting up fakeroot (1.24-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (
fakeroot) in auto mode
Setting up libasan5:amd64 (9.3.0-17ubuntu1~20.04) ...
Setting up make (4.2.1-1.2) ...
Setting up libquadmath0:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libatomic1:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libubsan1:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libcrypt-dev:amd64 (1:4.4.10-10ubuntu4) ...
Setting up libbinutils:amd64 (2.34-6ubuntu1.1) ...
Setting up libc-dev-bin (2.31-0ubuntu9.2) ...
Setting up libalgorithm-diff-xs-perl (0.04-6) ...
Setting up liblsan0:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libitm1:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libalgorithm-merge-perl (0.08-3) ...
Setting up libtsan0:amd64 (10.2.0-5ubuntu1~20.04) ...
Setting up libctf0:amd64 (2.34-6ubuntu1.1) ...
Setting up libgcc-9-dev:amd64 (9.3.0-17ubuntu1~20.04) ...
Setting up libc6-dev:amd64 (2.31-0ubuntu9.2) ...
Setting up binutils-x86-64-linux-gnu (2.34-6ubuntu1.1) ...
Setting up libstdc++-9-dev:amd64 (9.3.0-17ubuntu1~20.04) ...
Setting up binutils (2.34-6ubuntu1.1) ...
Setting up dpkg-dev (1.19.7ubuntu3) ...
Setting up gcc-9 (9.3.0-17ubuntu1~20.04) ...
Setting up gcc (4:9.3.0-1ubuntu2) ...
Setting up dkms (2.8.1-5ubuntu2) ...
Setting up g++-9 (9.3.0-17ubuntu1~20.04) ...
Setting up g++ (4:9.3.0-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mo
de
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu7~20.04.2) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.8.0-43-generic
Building for architecture x86_64
Building initial module for 5.8.0-43-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.8.0-43-generic/updates/dkms/

depmod...

DKMS: install completed.
update-initramfs is disabled since running on read-only media
Setting up build-essential (12.8ubuntu1.1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
ubuntu@ubuntu:~$ 

```

---

### Post by chili555 on 2021-05-29
> I already have installed a driver but still does not work.What do these commands tell us?

```
sudo modprobe wl && sudo dmesg | grep wl
rfkill list all
```

---

### Post by nikkim on 2021-05-29
Before  I got your response I repeated the steps shown in my protocol above and right after installation of the driver, I was able to connect to WIFI and it worked. However, when I re-started,the computer the WIFI was gone again. Could the issue be because I am booting from from an USB?

Thanks for looking into this.


```

oot@ubuntu:/home/ubuntu# sudo modprobe wl && sudo dmesg | grep wl
modprobe: FATAL: Module wl not found in directory /lib/modules/5.8.0-43-generic
root@ubuntu:/home/ubuntu# 

```

```


oot@ubuntu:/home/ubuntu# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@ubuntu:/home/ubuntu# 

```

---

### Post by chili555 on 2021-05-29
> Could the issue be because I am booting from from an USB?
Exactly. Changes to the USB, typically those burnt from the iso that includes a 'Try Ubuntu' mechanism, aren't persistant; that is, they won't survive a reboot. 

There is a system to create persistance: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) I have no current experience with it so I can't vouch that it works well, poorly or not at all.

---

