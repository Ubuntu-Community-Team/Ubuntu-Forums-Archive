---
title: "After the latest release, broadcom43142 card is bugged."
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by chdimosthenis on 2015-12-22
Updated when Ubuntu prompted, without mistakenly paying much attention in the details and since then my broadcom card is off.

That's the output of the log file after "bcmwl-kernel-sources" installation and I think the problem lies on the gcc version and one configuration that's been introduced in newer versions, the fstack-protector-strong.

Although, I might be wrong... 

```
sudo more /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log
[sudo] password for dimos: 
DKMS make.log for bcmwl-6.30.223.248+bdcom for kernel 4.2.0-22-generic (x86_64)
&#932;&#961;&#953; 22 &#916;&#949;&#954; 2015 01:15:19 &#956;&#956; EET
make: Entering directory '/usr/src/linux-headers-4.2.0-22-generic'
Makefile:669: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-stro
ng not supported by compiler
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.o
gcc: error: unrecognized command line option &#8216;-fstack-protector-strong&#8217;
scripts/Makefile.build:258: recipe for target '/var/lib/dkms/bcmwl/6.30.223.248+
bdcom/build/src/shared/linux_osl.o' failed
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/src/shared/linux_osl.
o] Error 1
Makefile:1398: recipe for target '_module_/var/lib/dkms/bcmwl/6.30.223.248+bdcom
/build' failed
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.248+bdcom/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.2.0-22-generic'


```

How do I proceed from here? Any thoughts?

**EDIT:** Ethernet connection is working. Bluetooth after the update was working, but when I tried to reinstall "bcmwl-kernel-sources" (which is the proper as you can see below and on the [BROADCOM WIRELESS TABLE]("http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers")) has been disabled.
```
lspci -nn -d 14e4:
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

---

### Post by chili555 on 2015-12-22
What gcc version is installed?```
gcc  --version
```For comparison, my 15.10 install returns:```
gcc (Ubuntu 5.2.1-22ubuntu2) 5.2.1 20151010
```If yours is lower, I'd try:```
sudo apt-get update && sudo apt-get -y dist-upgrade
```Reboot and check again:```
gcc --version
```If you now have 5.2.1-22, then:```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by chdimosthenis on 2015-12-22
My 15.10 installation runs this version
```
gcc (Ubuntu 4.8.5-1ubuntu1) 4.8.5


```

it sticks to that version even after the dist-upgrade.

---

### Post by chili555 on 2015-12-22
Are you trying to compile this from source code or just the recommended apt-get?

What does this tell us?```
sudo dpkg -s gcc-base | grep Status
sudo dpkg -s build-essential | grep Status
```

---

### Post by chdimosthenis on 2015-12-22
If you are referring to the bcmwl-kernel-source, I have installed it as apt-get and deb.
Here is the output:

```
sudo dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu7_amd64.deb
(Reading database ... 213531 files and directories currently installed.)
Preparing to unpack bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu7_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu7) over (6.30.223.248+bdcom-0ubuntu7) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu7) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 4.2.0-22-generic
Building for architecture x86_64
Building initial module for 4.2.0-22-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.2.0-22-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-22-generic
```

**Also**:
```
sudo dpkg -s gcc-base | grep Status
[sudo] password for dimos: 
dpkg-query: package 'gcc-base' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


```

```
sudo dpkg -s build-essential | grep Status
[sudo] password for dimos: 
Status: install ok installed


```

**In addition**:
```
sudo apt-get install g++-5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++-5 is already the newest version.


```

**But**: 
```
gcc --version
gcc (Ubuntu 4.8.5-1ubuntu1) 4.8.5
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

---

### Post by chili555 on 2015-12-22
Please try:```
sudo apt-get install gcc-base
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source
```If it fails again,let us see the /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log report again.

---

### Post by chdimosthenis on 2015-12-22
Thank you for your time.

I now managed to install the bcmwl-kernel-source, after installing the proper packages for the latest gcc version.

---

### Post by chili555 on 2015-12-22
Awesome! Glad it's working.

---

