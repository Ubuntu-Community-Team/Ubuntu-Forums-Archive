---
title: "Broadcom Drivers Broken in 22.04"
date: 2023-02-06
forum: Networking &amp; Wireless
---

### Post by curtis-s-copeland on 2023-02-06
I lost my functionality on my BCMWL 4352 when I upgraded to 22.04. Has worked fine for many years and many upgrades.  I skipped from Ubuntu 18LTS to 22.04.  Went back and installed 20(.04?) and the hardware does still work. I've tried purging bcmwl-kernel-source and reinstalling but it always fails. Here is the message in the make.log that has been the issue throughout everything I have tried:


DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64)
Fri Jan 27 05:04:12 PM MST 2023
make: Entering directory '/usr/src/linux-headers-5.15.0-56-generic'




ERROR: Kernel configuration is invalid.
include/generated/autoconf.h or include/config/auto.conf are missing.
Run 'make oldconfig && make prepare' on kernel src to fix it.




make: *** [Makefile:750: include/config/auto.conf] Error 1
make: Leaving directory '/usr/src/linux-headers-5.15.0-56-generic'

---

### Post by jeremy31 on 2023-02-09
Moved to Networking

---

### Post by chili555 on 2023-02-09
Please do:

```
sudo apt update
sudo apt install --reinstall bcmwl-kernel-source
sudo modprobe wl
sudo dmesg | grep wl
```

Post the result.

---

### Post by curtis-s-copeland on 2023-02-10
only got to step 2 since it has never succeeded 

curt@talon:~$ sudo apt install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 26 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for bcmwl-kernel-source:amd64

---

### Post by curtis-s-copeland on 2023-02-10
curt@talon:~$ sudo modprobe wl
modprobe: FATAL: Module wl not found in directory /lib/modules/5.15.0-56-generic

and no grep hits in dmesg

---

### Post by chili555 on 2023-02-10
Please see and follow my answer here: [https://askubuntu.com/questions/1330140/broadcom-wi-fi-adapter-not-working-on-ubuntu-20-04-2](https://askubuntu.com/questions/1330140/broadcom-wi-fi-adapter-not-working-on-ubuntu-20-04-2)

---

### Post by curtis-s-copeland on 2023-02-10
dang, I had high hopes for that, as there were a fair number of upgrades out there.
No Joy

curt@talon:~$ sudo apt install -y bcmwl-kernel-souce
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package bcmwl-kernel-souce
curt@talon:~$ sudo apt install -y bcmwl-kernel-source
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.15.0-58 linux-headers-5.15.0-58-generic linux-image-5.15.0-58-generic linux-modules-5.15.0-58-generic
  linux-modules-extra-5.15.0-58-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 1,548 kB of archives.
After this operation, 8,079 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu8 [1,548 kB]
Fetched 1,548 kB in 1s (1,856 kB/s)            
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 363127 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu8_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by curtis-s-copeland on 2023-02-10
here's the make log
====================
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64)
Fri Feb 10 10:52:06 AM MST 2023
make: Entering directory '/usr/src/linux-headers-5.15.0-56-generic'


  ERROR: Kernel configuration is invalid.
         include/generated/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


make: *** [Makefile:750: include/config/auto.conf] Error 1
make: Leaving directory '/usr/src/linux-headers-5.15.0-56-generic'

---

### Post by curtis-s-copeland on 2023-02-10
a little different path than the one mentioned in your other post


curt@talon:/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build$ ls
dkms.conf  lib  Makefile  Makefile.orig  make.log  patches  src

also here is the version[COLOR=#232629][FONT=ui-monospace]

[/FONT][/COLOR]curt@talon:/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build$ sudo dpkg -s bcmwl-kernel-source | grep Version
Version: 6.30.223.271+bdcom-0ubuntu8

---

### Post by chili555 on 2023-02-10
Please reboot and then do:

```
sudo apt update
sudo apt -y upgrade
sudo apt autoremove
sudo apt -y install build-essential
sudo apt install --reinstall bcmwl-kernel-source
```Post the result if there is any error.

---

### Post by curtis-s-copeland on 2023-02-10
> **chili555 said:**
> Please see and follow my answer here: [https://askubuntu.com/questions/1330140/broadcom-wi-fi-adapter-not-working-on-ubuntu-20-04-2](https://askubuntu.com/questions/1330140/broadcom-wi-fi-adapter-not-working-on-ubuntu-20-04-2)


see thread replies above ^^^ 

Lastly, I'm not sure why these are held back or if it matters:

curt@talon:~$ apt list --upgradable
Listing... Done
gnome-initial-setup/jammy-updates 42.0.1-1ubuntu2.2 amd64 [upgradable from: 42.0.1-1ubuntu2]
gnome-remote-desktop/jammy-updates 42.7-0ubuntu1 amd64 [upgradable from: 42.4-0ubuntu1]
grub-efi-amd64-bin/jammy-updates 2.06-2ubuntu14 amd64 [upgradable from: 2.06-2ubuntu10]
grub-efi-amd64-signed/jammy-updates 1.187.2+2.06-2ubuntu14 amd64 [upgradable from: 1.182~22.04.1+2.06-2ubuntu10]
grub-efi-amd64/jammy-updates 2.06-2ubuntu14 amd64 [upgradable from: 2.06-2ubuntu10]
python3-software-properties/jammy-updates,jammy-updates 0.99.22.5 all [upgradable from: 0.99.22.4]
software-properties-common/jammy-updates,jammy-updates 0.99.22.5 all [upgradable from: 0.99.22.4]
software-properties-gtk/jammy-updates,jammy-updates 0.99.22.5 all [upgradable from: 0.99.22.4]
ubuntu-advantage-tools/jammy-updates 27.13.3~22.04.1 amd64 [upgradable from: 27.12~22.04.1]
update-notifier-common/jammy-updates,jammy-updates 3.192.54.5 all [upgradable from: 3.192.54]
update-notifier/jammy-updates 3.192.54.5 amd64 [upgradable from: 3.192.54]
curt@talon:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages have been kept back:
  gnome-initial-setup gnome-remote-desktop grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed python3-software-properties
  software-properties-common software-properties-gtk ubuntu-advantage-tools update-notifier update-notifier-common
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

---

### Post by curtis-s-copeland on 2023-02-10
> **chili555 said:**
> Please reboot and then do:

```
sudo apt update
sudo apt -y upgrade
sudo apt autoremove
sudo apt -y install build-essential
sudo apt install --reinstall bcmwl-kernel-source
```Post the result if there is any error.


Sorry for getting the thread out of order, just saw this.  Anyway, did update, but bombed upgrade (step 2) here is transcript

curt@talon:~$ sudo apt -y upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages have been kept back:
  gnome-initial-setup gnome-remote-desktop grub-efi-amd64 grub-efi-amd64-bin
  grub-efi-amd64-signed python3-software-properties software-properties-common
  software-properties-gtk ubuntu-advantage-tools update-notifier
  update-notifier-common
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.c
rash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned erro
r exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by curtis-s-copeland on 2023-02-10
removed the crash log and retried upgrade so it would regen the crash log:

===========

ProblemType: Package
DKMSBuildLog:
 DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64)
 Fri Feb 10 01:17:44 PM MST 2023
 make: Entering directory '/usr/src/linux-headers-5.15.0-56-generic'
 
   ERROR: Kernel configuration is invalid.
          include/generated/autoconf.h or include/config/auto.conf are missing.
          Run 'make oldconfig && make prepare' on kernel src to fix it.
 
 make: *** [Makefile:750: include/config/auto.conf] Error 1
 make: Leaving directory '/usr/src/linux-headers-5.15.0-56-generic'
DKMSKernelVersion: 5.15.0-56-generic
Date: Fri Feb 10 13:17:45 2023
Package: bcmwl-kernel-source 6.30.223.271+bdcom-0ubuntu8
PackageVersion: 6.30.223.271+bdcom-0ubuntu8
SourcePackage: bcmwl
Title: bcmwl-kernel-source 6.30.223.271+bdcom-0ubuntu8: bcmwl kernel module failed to build

---

### Post by curtis-s-copeland on 2023-02-10
I've been running ubuntu for many versions on this machine.  Wonder if there is something to these "held back" things??

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291741&stc=1[/IMG]

---

### Post by chili555 on 2023-02-10
We are going to fix this thing if it takes all night!!

```
sudo apt install --reinstall linux-headers-$(uname -r)
sudo apt install --reinstall linux-headers-generic
sudo apt -y upgrade
```

Please post the result, reboot and then we'll proceed.

---

### Post by curtis-s-copeland on 2023-02-10
ok first one didn't work:

Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Module bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.c
rash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned erro
r exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

=========
neither did the 2nd idea
===========
Unpacking linux-headers-generic (5.15.0.60.58) over (5.15.0.60.58) ...
Setting up linux-headers-generic (5.15.0.60.58) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.c
rash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned erro
r exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

===========
here's the third output, then I'll reboot

Unpacking linux-headers-generic (5.15.0.60.58) over (5.15.0.60.58) ...
Setting up linux-headers-generic (5.15.0.60.58) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.c
rash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned erro
r exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)


========
rebooting, will be back

---

### Post by curtis-s-copeland on 2023-02-10
rebooted and retried upgrade - same failure

---

### Post by chili555 on 2023-02-10
Ahhhh haaaa! I think I've got it!! Please see:

> Unpacking linux-headers-generic (5.15.0.60.58) over (5.15.0.60.58) ...
Setting up linux-headers-generic (5.15.0.60.58) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
[COLOR="#FF0000"]Building for 5.15.0-56-generic 5.15.0-60-generic[/COLOR]
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.c
rash'
Error! [COLOR="#FF0000"]Bad return status for module build on kernel: 5.15.0-56-generic[/COLOR] (x86_64)The module is being built for both of the kernel versions on your system; 5.15.0-56 and 5.15.0-60. The build fails for -56 although you are booted into -60. The build fails, writes a crash log and quits.

Reboot. Please interrupt the boot process to get the GRUB menu to boot into an earlier kernel version, namely -56. [https://www.pcsuggest.com/enter-grub-menu-on-single-boot-ubuntu-system/](https://www.pcsuggest.com/enter-grub-menu-on-single-boot-ubuntu-system/) While booted into -56, please ONLY do: 

```
sudo apt install --reinstall linux-headers-$(uname -r)
sudo apt install --reinstall linux-headers-generic

```
Do NOT try to install anything else. If all goes without error, reboot normally and try again:

```
sudo apt install --reinstall bcmwl-kernel-source

```
STOP and post the result.

---

### Post by curtis-s-copeland on 2023-02-10
ok meanwhile I did try to boot into an old kernel and it failed b/c couldn't find it ... I'll take some photos and come back.  I think this was the only 5.15.x but let me see ...

---

### Post by curtis-s-copeland on 2023-02-10
I have a feeling we're getting somewhere.  I only have 5.15.0-56 and 5.15.0-47 (which doesn't exist).  See images below.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291743&stc=1[/IMG]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291742&stc=1[/IMG]

---

### Post by curtis-s-copeland on 2023-02-10
wait let me try 56

---

### Post by curtis-s-copeland on 2023-02-10
wait I didn't try 56.  But I'm booted into 56 now with no luck.  Here is reinstall $(uname -r)
---------------------
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-so
urce.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more informati
on.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess retur
ned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------
and why not, here is generic headers
--------------------------
still looks like building for both
-------------------------
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-so
urce.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more informati
on.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess retur
ned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chili555 on 2023-02-10
I did not ask you to try to install bcmwl-kernel-source. I asked you:

> please ONLY do:

Code:
sudo apt install --reinstall linux-headers-$(uname -r)
sudo apt install --reinstall linux-headers-generic
Do NOT try to install anything else.While you are booted into -56, will you please try what I requested. Please do no anticipate or make up your own sequence. This is not useful.

---

### Post by curtis-s-copeland on 2023-02-10
hold yer horses, I am booted into 56 and did what you asked, here is the full transcript.  did we need to remove something first?
================
**curt@talon:~$ sudo apt install --reinstall linux-headers-$(uname -r)**
[sudo] password for curt: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,899 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 327733 files and directories currently installed.)
Preparing to unpack .../linux-headers-5.15.0-56-generic_5.15.0-56.62_amd64.deb ...
Unpacking linux-headers-5.15.0-56-generic (5.15.0-56.62) over (5.15.0-56.62) ...
Setting up linux-headers-5.15.0-56-generic (5.15.0-56.62) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-56-generic


Kernel preparation unnecessary for this kernel. Skipping...
applying patch 0002-Makefile.patch...patching file Makefile
Hunk #1 succeeded at 113 with fuzz 1.
Hunk #2 succeeded at 132 with fuzz 2 (offset 1 line).


applying patch 0003-Make-up-for-missing-init_MUTEX.patch...patching file src/wl/
sys/wl_linux.c
Hunk #1 succeeded at 111 with fuzz 2 (offset 12 lines).


applying patch 0010-change-the-network-interface-name-from-eth-to-wlan.patch...p
atching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 221 (offset -14 lines).


applying patch 0013-gcc.patch...patching file Makefile


applying patch 0019-broadcom-sta-6.30.223.248-3.18-null-pointer-fix.patch...patc
hing file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 2169 (offset 12 lines).


applying patch 0020-add-support-for-linux-4.3.patch...patching file src/shared/l
inux_osl.c


applying patch 0021-add-support-for-Linux-4.7.patch...patching file src/wl/sys/w
l_cfg80211_hybrid.c


applying patch 0022-add-support-for-Linux-4.8.patch...patching file src/wl/sys/w
l_cfg80211_hybrid.c
Hunk #1 succeeded at 2391 (offset 3 lines).
Hunk #2 succeeded at 2501 (offset 3 lines).
Hunk #3 succeeded at 2933 (offset 9 lines).


applying patch 0023-add-support-for-Linux-4.11.patch...patching file src/include
/linuxver.h
patching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 2919 (offset 4 lines).


applying patch 0024-add-support-for-Linux-4.12.patch...patching file src/wl/sys/
wl_cfg80211_hybrid.c
Hunk #1 succeeded at 55 (offset 5 lines).
Hunk #2 succeeded at 472 (offset 5 lines).
Hunk #3 succeeded at 2371 (offset 5 lines).
Hunk #4 succeeded at 2388 (offset 5 lines).


applying patch 0025-add-support-for-Linux-4.14.patch...patching file src/shared/
linux_osl.c
Hunk #1 succeeded at 1080 (offset 4 lines).


applying patch 0026-add-support-for-Linux-4.15.patch...patching file src/wl/sys/
wl_linux.c
Hunk #2 succeeded at 2306 (offset 4 lines).
Hunk #3 succeeded at 2368 (offset 4 lines).


applying patch 0027-add-support-for-linux-5.1.patch...patching file src/include/
linuxver.h
Hunk #1 succeeded at 595 (offset 4 lines).


applying patch 0028-add-support-for-linux-5.6.patch...patching file src/shared/l
inux_osl.c
Hunk #1 succeeded at 946 (offset 4 lines).
patching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 590 (offset 8 lines).
Hunk #2 succeeded at 784 (offset 8 lines).
Hunk #3 succeeded at 3365 (offset 22 lines).


applying patch 0029-Update-for-set_fs-removal-in-Linux-5.10.patch...patching fil
e src/wl/sys/wl_cfg80211_hybrid.c
patching file src/wl/sys/wl_iw.c
patching file src/wl/sys/wl_linux.c
patching file src/wl/sys/wl_linux.h




Building module:
cleaning build area...
make -j4 KERNELRELEASE=5.15.0-56-generic -C /lib/modules/5.15.0-56-generic/build
 M=/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build....
Signing module:
 - /var/lib/dkms/bcmwl/6.30.223.271+bdcom/5.15.0-56-generic/x86_64/module/wl.ko
Secure Boot not enabled on this system.
cleaning build area...


wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.15.0-56-generic/updates/dkms/


depmod....


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...(bad exit status: 2)
make -j4 KERNELRELEASE=5.15.0-56-generic all INCLUDEDIR=/lib/modules/5.15.0-56-g
eneric/build/include KVERSION=5.15.0-56-generic DKMS_BUILD=1...(bad exit status:
 2)
ERROR (dkms apport): binary package for evdi: 1.4.210 not found
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/evdi/1.4.210/build/make.log for more information.
Error! The /var/lib/dkms/i915-3.19-3.13/3.19.1/5.15.0-56-generic/x86_64/dkms.con
f for module i915-3.19-3.13 includes a BUILD_EXCLUSIVE directive which does not 
match this kernel/arch.
This indicates that it should not be built.
Error! The /var/lib/dkms/oem-audio-hda-daily/0.1/5.15.0-56-generic/x86_64/dkms.c
onf for module oem-audio-hda-daily includes a BUILD_EXCLUSIVE directive which do
es not match this kernel/arch.
This indicates that it should not be built.
   ...done.
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Module bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.15.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-so
urce.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more informati
on.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess retur
ned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
curt@talon:~$ sudo apt install --reinstall linux-headers-generic^C
**curt@talon:~$ sudo apt install --reinstall linux-headers-generic**
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,316 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 327733 files and directories currently installed.)
Preparing to unpack .../linux-headers-generic_5.15.0.60.58_amd64.deb ...
Unpacking linux-headers-generic (5.15.0.60.58) over (5.15.0.60.58) ...
Setting up linux-headers-generic (5.15.0.60.58) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-so
urce.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more informati
on.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess retur
ned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
curt@talon:~$

---

### Post by chili555 on 2023-02-10
Aren't you starting to realize that it is not the Broadcom drivers that are broken, it is many things on your system.

Looking at your GRUB photo, we wonder where kernel version -60 appears. It is clearly referenced above. > Building for 5.15.0-56-generic 5.15.0-[COLOR="#FF0000"]60[/COLOR]-generic

We wonder why those moldy oldy 3.13 kernel versions are still around. The last time I worked on 3.13-xx, I still had hair!

May we see: ```
cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log 
```I think I'd seriously be thinking of backup and reinstall.

May we also see: 
```
sudo apt autoremove
sudo update-grub
ls /boot
ls /usr/src

```

---

### Post by curtis-s-copeland on 2023-02-10
I'm thinking the -60 is the first grub option without any description

At this point, rebuild would have been faster, just a pain in the butt with all my apps and photo index databases to relink over TB of external HDD.  

I've sent the make log numerous times but here's everything:

```
curt@talon:~$ cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.15.0-56-generic (x86_64)
Fri Feb 10 02:53:50 PM MST 2023
make: Entering directory '/usr/src/linux-headers-5.15.0-56-generic'


  ERROR: Kernel configuration is invalid.
         include/generated/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


make: *** [Makefile:750: include/config/auto.conf] Error 1
make: Leaving directory '/usr/src/linux-headers-5.15.0-56-generic'
curt@talon:~$ ^C
curt@talon:~$ sudo apt autoremove
[sudo] password for curt: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned error exit stat
us 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
curt@talon:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/40_oem-add-missing-default.cfg'
Sourcing file `/etc/default/grub.d/50_oem-kernel-cmdline.cfg'
Sourcing file `/etc/default/grub.d/51_oem-grub-recovery-title.cfg'
Sourcing file `/etc/default/grub.d/52_oem_video_native_backlight.cfg'
Sourcing file `/etc/default/grub.d/53_set_acpi_osi.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-5.15.0-60-generic
Found initrd image: /boot/initrd.img-5.15.0-60-generic
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
Found linux image: /boot/vmlinuz-3.13.0-108-generic
Found initrd image: /boot/initrd.img-3.13.0-108-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
curt@talon:~$ ls /boot
abi-3.13.0-108-generic     initrd.img-3.13.0-108-generic          System.map-3.13.0-108-generic
config-3.13.0-108-generic  initrd.img-5.15.0-56-generic           System.map-5.15.0-56-generic
config-5.15.0-56-generic   initrd.img-5.15.0-56-generic.old-dkms  System.map-5.15.0-60-generic
config-5.15.0-60-generic   initrd.img-5.15.0-60-generic           vmlinuz
efi                        initrd.img.old                         vmlinuz-3.13.0-108-generic
extlinux                   memtest86+.bin                         vmlinuz-5.15.0-56-generic
grub                       memtest86+.elf                         vmlinuz-5.15.0-60-generic
initrd.img                 memtest86+_multiboot.bin               vmlinuz.old
curt@talon:~$ ls /usr/src
bcmwl-6.30.223.271+bdcom  linux-headers-5.15.0-56-generic  linux-headers-5.4.0-90-generic
evdi-1.4.210              linux-headers-5.15.0-60          oem-audio-hda-daily-0.1
i915-3.19-3.13-3.19.1     linux-headers-5.15.0-60-generic
linux-headers-5.15.0-56   linux-headers-5.4.0-86-generic
curt@talon:~$ 



```

---

### Post by curtis-s-copeland on 2023-02-10
@chili555, thanks for the help today, I have to go to an appointment and will check back

---

### Post by chili555 on 2023-02-10
What does this tell us:

```
sudo apt autoremove
sudo update-grub
```

---

### Post by curtis-s-copeland on 2023-02-11
Before I give up, I should mention that I created a live boot USB for 22.04 and it has the same BCMWL issue.  We can do down that path when you are ready.

Here's the transcript:

```
curt@talon:~$ sudo apt autoremove[sudo] password for curt: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing old bcmwl-6.30.223.271+bdcom DKMS files...
Deleting module bcmwl-6.30.223.271+bdcom completely from the DKMS tree.
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-56-generic 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-56-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned error exit stat
us 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
curt@talon:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/40_oem-add-missing-default.cfg'
Sourcing file `/etc/default/grub.d/50_oem-kernel-cmdline.cfg'
Sourcing file `/etc/default/grub.d/51_oem-grub-recovery-title.cfg'
Sourcing file `/etc/default/grub.d/52_oem_video_native_backlight.cfg'
Sourcing file `/etc/default/grub.d/53_set_acpi_osi.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-5.15.0-60-generic
Found initrd image: /boot/initrd.img-5.15.0-60-generic
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
Found linux image: /boot/vmlinuz-3.13.0-108-generic
Found initrd image: /boot/initrd.img-3.13.0-108-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done



```

---

### Post by chili555 on 2023-02-11
```
sudo apt update
sudo apt purge bcmwl-kernel-source
sudo apt install --reinstall linux-headers-generic
sudo apt install --reinstall linux-headers-5.15.0-56-generic
sudo apt install --reinstall linux-headers-5.15.0-60-generic
sudo apt install -y plocate
sudo updatedb
locate include/generated/autoconf.h
```bcmwl seems to be interfering every time we try to fix the system. I suggest removing it entirely so we can do some repairs. We'll install it fresh later.

---

### Post by curtis-s-copeland on 2023-02-11
I'm not sure how to assess success, but here ya go.

```
curt@talon:~$ sudo apt update[sudo] password for curt: 
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/earth/deb stable InRelease                    
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy InRelease                      
Get:4 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]     
Get:5 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease [8,041 B]       
Ign:6 https://www.scootersoftware.com bcompare4 InRelease                      
Hit:7 https://www.scootersoftware.com bcompare4 Release                        
Err:5 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Get:9 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [436 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [876 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [102 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [802 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [569 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [265 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu jammy-updates/multiverse i386 Packages [3,176 B]
Get:18 http://us.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [9,364 B]
Get:19 http://us.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:20 http://us.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [8,004 B]
Get:21 http://us.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12.5 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [41.4 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [13.3 kB]
Reading package lists... Done                                             
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'
W: GPG error: https://dl.winehq.org/wine-builds/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
curt@talon:~$ sudo apt purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 8,079 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 327733 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.140ubuntu13.1) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-60-generic
(Reading database ... 327644 files and directories currently installed.)
Purging configuration files for bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu8) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.140ubuntu13.1) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-60-generic
curt@talon:~$ sudo apt install --reinstall linux-headers-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
Need to get 0 B/2,316 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 327644 files and directories currently installed.)
Preparing to unpack .../linux-headers-generic_5.15.0.60.58_amd64.deb ...
Unpacking linux-headers-generic (5.15.0.60.58) over (5.15.0.60.58) ...
Setting up linux-headers-generic (5.15.0.60.58) ...
curt@talon:~$ sudo apt install --reinstall linux-headers-.15.0-56-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package linux-headers-.15.0-56-generic
E: Couldn't find any package by glob 'linux-headers-.15.0-56-generic'
curt@talon:~$ sudo apt install --reinstall linux-headers-5.15.0-56-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
Need to get 0 B/2,899 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 327644 files and directories currently installed.)
Preparing to unpack .../linux-headers-5.15.0-56-generic_5.15.0-56.62_amd64.deb ...
Unpacking linux-headers-5.15.0-56-generic (5.15.0-56.62) over (5.15.0-56.62) ...
Setting up linux-headers-5.15.0-56-generic (5.15.0-56.62) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-56-generic


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...(bad exit status: 2)
make -j4 KERNELRELEASE=5.15.0-56-generic all INCLUDEDIR=/lib/modules/5.15.0-56-generic/build/include K
VERSION=5.15.0-56-generic DKMS_BUILD=1...(bad exit status: 2)
ERROR (dkms apport): binary package for evdi: 1.4.210 not found
Error! Bad return status for module build on kernel: 5.15.0-56-generic (x86_64)
Consult /var/lib/dkms/evdi/1.4.210/build/make.log for more information.
Error! The /var/lib/dkms/i915-3.19-3.13/3.19.1/5.15.0-56-generic/x86_64/dkms.conf for module i915-3.19
-3.13 includes a BUILD_EXCLUSIVE directive which does not match this kernel/arch.
This indicates that it should not be built.
Error! The /var/lib/dkms/oem-audio-hda-daily/0.1/5.15.0-56-generic/x86_64/dkms.conf for module oem-aud
io-hda-daily includes a BUILD_EXCLUSIVE directive which does not match this kernel/arch.
This indicates that it should not be built.
   ...done.
curt@talon:~$ sudo apt install --reinstall linux-headers-5.15.0-60-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
Need to get 2,871 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-5.15.0-60-generic amd64 5.15.0-60.66 [2,871 kB]
Fetched 2,871 kB in 1s (3,562 kB/s)                          
(Reading database ... 327644 files and directories currently installed.)
Preparing to unpack .../linux-headers-5.15.0-60-generic_5.15.0-60.66_amd64.deb ...
Unpacking linux-headers-5.15.0-60-generic (5.15.0-60.66) over (5.15.0-60.66) ...
Setting up linux-headers-5.15.0-60-generic (5.15.0-60.66) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-60-generic


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...(bad exit status: 2)
make -j4 KERNELRELEASE=5.15.0-60-generic all INCLUDEDIR=/lib/modules/5.15.0-60-generic/build/include K
VERSION=5.15.0-60-generic DKMS_BUILD=1...(bad exit status: 2)
ERROR (dkms apport): binary package for evdi: 1.4.210 not found
Error! Bad return status for module build on kernel: 5.15.0-60-generic (x86_64)
Consult /var/lib/dkms/evdi/1.4.210/build/make.log for more information.
Error! The /var/lib/dkms/i915-3.19-3.13/3.19.1/5.15.0-60-generic/x86_64/dkms.conf for module i915-3.19
-3.13 includes a BUILD_EXCLUSIVE directive which does not match this kernel/arch.
This indicates that it should not be built.
Error! The /var/lib/dkms/oem-audio-hda-daily/0.1/5.15.0-60-generic/x86_64/dkms.conf for module oem-aud
io-hda-daily includes a BUILD_EXCLUSIVE directive which does not match this kernel/arch.
This indicates that it should not be built.
   ...done.
curt@talon:~$ sudo apt install -y plocate
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
plocate is already the newest version (1.1.15-1ubuntu2).
plocate set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
curt@talon:~$ sudo updatedb
curt@talon:~$ locate include/generated/autoconf.h
curt@talon:~$ ^C
curt@talon:~$ 



```

---

### Post by chili555 on 2023-02-11
> curt@talon:~$ locate include/generated/autoconf.h
curt@talon:~$ ^C
curt@talon:~$Very interesting, to say the least.

How about:

```
locate include/config/auto.conf
```

---

### Post by curtis-s-copeland on 2023-02-11
the ^C was just me trying to keystroke a "copy" operation.  there was no response to locating autoconfig.h

```
curt@talon:~$ locate include/config/auto.conf/usr/src/linux-headers-5.15.0-56-generic/include/config/auto.conf
/usr/src/linux-headers-5.15.0-56-generic/include/config/auto.conf.cmd
/usr/src/linux-headers-5.15.0-60-generic/include/config/auto.conf
/usr/src/linux-headers-5.15.0-60-generic/include/config/auto.conf.cmd

```

---

### Post by curtis-s-copeland on 2023-02-11
would it simplify things to be doing this from a live USB boot since I get the same trouble?  I would eliminate my oft-upgraded OS

---

### Post by chili555 on 2023-02-11
I'm certainly interested to see the exact error details from the live USB session.

I am mystified. The error above was: > ERROR: Kernel configuration is invalid.
         include/generated/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.However, include/config/auto.conf *IS *present as you showed:

> curt@talon:~$ locate include/config/auto.conf
/usr/src/linux-headers-5.15.0-56-generic/[COLOR="#FF0000"]include/config/auto.conf[/COLOR]
/usr/src/linux-headers-5.15.0-56-generic/include/config/auto.conf.cmd
/usr/src/linux-headers-5.15.0-60-generic/[COLOR="#FF0000"]include/config/auto.conf[/COLOR]
/usr/src/linux-headers-5.15.0-60-generic/include/config/auto.conf.cmdI wonder if this is a permissions problem. Let's see:

```
ls -al /usr/src/linux-headers-5.15.0-60-generic/include/config/auto.conf
```We hope its attributes are -rw-r--r-- 1 root root 219174 ; that is, writable by root and readable by everyone. If it is any different, we'll change it and try installing bcmwl again.

---

### Post by curtis-s-copeland on 2023-02-11
```
curt@talon:~$ ls -al /usr/src/linux-headers-5.15.0-60-generic/include/config/auto.conf
-rw-r--r-- 1 root root 212874 Jan 20 06:42 /usr/src/linux-headers-5.15.0-60-generic/include/config/auto.conf

```

---

### Post by chili555 on 2023-02-12
Let's make sure you have the correct versions of these:

```
sudo dpkg -s build-essential | grep Version
sudo dpkg -s gcc | grep Version
```I believe they should be Version: 12.9ubuntu3 and Version: 4:12.2.0-1ubuntu1 respectively. If not, post the versions and we'll try to reinstall the faulty package(s):

```
sudo apt update
sudo apt install --reinstall <faulty_package>

```
Then let's try again:

```
sudo apt install bcmwl-kernel-source
```

---

### Post by curtis-s-copeland on 2023-02-13
Hmmm gcc is not the same.  I tried updating but it's stuck at 4:11

```
curt@talon:~$ sudo dpkg -s build-essential | grep Version[sudo] password for curt: 
Sorry, try again.
[sudo] password for curt: 
Version: 12.9ubuntu3
curt@talon:~$ sudo dpkg -s gcc | grep Version
Version: 4:11.2.0-1ubuntu1
curt@talon:~$ sudo apt update
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 https://dl.cloudsmith.io/public/balena/etcher/deb/ubuntu jammy InRelease [5,072 B]
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:4 http://dl.google.com/linux/earth/deb stable InRelease                    
Ign:5 https://www.scootersoftware.com bcompare4 InRelease                      
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:7 https://www.scootersoftware.com bcompare4 Release              
Hit:8 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease  
Get:9 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease [8,041 B]
Hit:10 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease
Err:9 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'
W: GPG error: https://dl.winehq.org/wine-builds/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
curt@talon:~$ sudo apt install --reinstall gcc
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 19 not upgraded.
Need to get 5,112 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1 [5,112 B]
Fetched 5,112 B in 0s (27.7 kB/s)
(Reading database ... 328098 files and directories currently installed.)
Preparing to unpack .../gcc_4%3a11.2.0-1ubuntu1_amd64.deb ...
Unpacking gcc (4:11.2.0-1ubuntu1) over (4:11.2.0-1ubuntu1) ...
Setting up gcc (4:11.2.0-1ubuntu1) ...
Processing triggers for man-db (2.10.2-1) ...
curt@talon:~$ sudo dpkg -s gcc | grep Version
Version: 4:11.2.0-1ubuntu1
curt@talon:~$ 

```

---

### Post by curtis-s-copeland on 2023-02-21
@chili555
Any insights?  Still can't make and here's the make.log

```

curt@talon:~$ sudo apt install bcmwl-kernel-source
[sudo] password for curt: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 1,774 kB of archives.
After this operation, 8,090 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu10~22.04.1 [1,774 kB]
Fetched 1,774 kB in 3s (698 kB/s)                
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 328210 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu10~22.04.1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu10~22.04.1) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu10~22.04.1) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-60-generic
Building for architecture x86_64
Building initial module for 5.15.0-60-generic
Error! Bad return status for module build on kernel: 5.15.0-60-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more informati
on.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess retur
ned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
curt@talon:~$ cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log 
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 5.15.0-60-generic (x86_64)
Tue Feb 21 07:03:57 AM MST 2023
make: Entering directory '/usr/src/linux-headers-5.15.0-60-generic'


  ERROR: Kernel configuration is invalid.
         include/generated/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


make: *** [Makefile:750: include/config/auto.conf] Error 1
make: Leaving directory '/usr/src/linux-headers-5.15.0-60-generic'

```

---

### Post by curtis-s-copeland on 2023-02-21
> **chili555 said:**
> Let's make sure you have the correct versions of these:

```
sudo dpkg -s build-essential | grep Version
sudo dpkg -s gcc | grep Version
```I believe they should be Version: 12.9ubuntu3 and Version: 4:12.2.0-1ubuntu1 respectively. If not, post the versions and we'll try to reinstall the faulty package(s):

```
sudo apt update
sudo apt install --reinstall <faulty_package>

```
Then let's try again:

```
sudo apt install bcmwl-kernel-source
```


Still back at square one ...

---

### Post by curtis-s-copeland on 2023-02-21
On a live USB now with 22.04, wireless again is not working, tried to run the install the bcmwl-kernel-source here. 

Looks like it's trying to build for a -43 kernel which is weird because we were looking at -56 and -60??  Anyway, the wireless is now working on 22.04 (live USB).  I guess next is to try and over-install it onto the HDD image - hopefully keeping may apps and settings.

```
ubuntu@ubuntu:~$ sudo apt install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu build-essential cpp-11 cpp-12 dkms dpkg-dev fakeroot g++ g++-11 gcc gcc-11 gcc-11-base gcc-12
  gcc-12-base libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan6 libasan8 libatomic1 libbinutils libc-dev-bin
  libc-devtools libc6-dev libcc1-0 libcrypt-dev libctf-nobfd0 libctf0 libfakeroot libgcc-11-dev libgcc-12-dev libgcc-s1 libgomp1 libitm1 liblsan0
  libnsl-dev libquadmath0 libstdc++-11-dev libstdc++6 libtirpc-dev libtsan0 libtsan2 libubsan1 linux-libc-dev lto-disabled-list make manpages-dev
  rpcsvc-proto
Suggested packages:
  binutils-doc gcc-11-locales gcc-12-locales menu debian-keyring g++-multilib g++-11-multilib gcc-11-doc gcc-multilib autoconf automake libtool flex
  bison gcc-doc gcc-11-multilib gcc-12-multilib gcc-12-doc glibc-doc libstdc++-11-doc make-doc
The following NEW packages will be installed:
  bcmwl-kernel-source binutils binutils-common binutils-x86-64-linux-gnu build-essential cpp-12 dkms dpkg-dev fakeroot g++ g++-11 gcc gcc-11 gcc-12
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan6 libasan8 libatomic1 libbinutils libc-dev-bin libc-devtools
  libc6-dev libcc1-0 libcrypt-dev libctf-nobfd0 libctf0 libfakeroot libgcc-11-dev libgcc-12-dev libitm1 liblsan0 libnsl-dev libquadmath0
  libstdc++-11-dev libtirpc-dev libtsan0 libtsan2 libubsan1 linux-libc-dev lto-disabled-list make manpages-dev rpcsvc-proto
The following packages will be upgraded:
  cpp-11 gcc-11-base gcc-12-base libgcc-s1 libgomp1 libstdc++6
6 upgraded, 45 newly installed, 0 to remove and 390 not upgraded.
Need to get 205 MB/211 MB of archives.
After this operation, 657 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1 [5,112 B]
Get:2 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 make amd64 4.3-4.1build1 [180 kB]
Get:3 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 lto-disabled-list all 24 [12.5 kB]
Get:4 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 dpkg-dev all 1.21.1ubuntu2.1 [922 kB]
Get:5 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.1 [20.4 kB]
Get:6 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1 [112 kB]
Get:7 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6 [68.5 kB]
Get:8 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1 [192 kB]
Get:9 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libnsl-dev amd64 1.3.0-2build2 [71.3 kB]
Get:10 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libc6-dev amd64 2.35-0ubuntu3.1 [2,099 kB]
Get:11 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1 [1,412 B]
Get:12 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 build-essential amd64 12.9ubuntu3 [4,744 B]
Get:13 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1 [31.5 kB]
Get:14 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 fakeroot amd64 1.28-1ubuntu1 [60.4 kB]
Get:15 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libalgorithm-diff-perl all 1.201-1 [41.8 kB]
Get:16 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3 [11.9 kB]
Get:17 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libalgorithm-merge-perl all 0.08-3 [12.0 kB]
Get:18 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libc-devtools amd64 2.35-0ubuntu3.1 [28.9 kB]
Get:19 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 manpages-dev all 5.10-1ubuntu1 [2,309 kB]
Get:20 http://security.ubuntu.com/ubuntu jammy-security/main amd64 cpp-11 amd64 11.3.0-1ubuntu1~22.04 [9,967 kB]
Get:21 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.1 [70.0 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 bcmwl-kernel-source amd64 6.30.223.271+bdcom-0ubuntu10~22.04.1 [1,774 kB]
Get:23 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-11-base amd64 11.3.0-1ubuntu1~22.04 [20.8 kB]
Get:24 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-12-base amd64 12.1.0-2ubuntu1~22.04 [19.0 kB]
Get:25 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libstdc++6 amd64 12.1.0-2ubuntu1~22.04 [696 kB]
Get:26 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgomp1 amd64 12.1.0-2ubuntu1~22.04 [126 kB]
Get:27 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgcc-s1 amd64 12.1.0-2ubuntu1~22.04 [54.3 kB]
Get:28 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libcc1-0 amd64 12.1.0-2ubuntu1~22.04 [47.4 kB]
Get:29 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils-common amd64 2.38-4ubuntu2.1 [221 kB]
Get:30 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libbinutils amd64 2.38-4ubuntu2.1 [661 kB]
Get:31 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.1 [107 kB]
Get:32 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libctf0 amd64 2.38-4ubuntu2.1 [103 kB]
Get:33 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.1 [2,328 kB]
Get:34 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils amd64 2.38-4ubuntu2.1 [3,198 B]
Get:35 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libitm1 amd64 12.1.0-2ubuntu1~22.04 [30.2 kB]
Get:36 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libatomic1 amd64 12.1.0-2ubuntu1~22.04 [10.4 kB]
Get:37 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libasan6 amd64 11.3.0-1ubuntu1~22.04 [2,284 kB]
Get:38 http://security.ubuntu.com/ubuntu jammy-security/main amd64 liblsan0 amd64 12.1.0-2ubuntu1~22.04 [1,069 kB]
Get:39 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libtsan0 amd64 11.3.0-1ubuntu1~22.04 [2,262 kB]
Get:40 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libubsan1 amd64 12.1.0-2ubuntu1~22.04 [976 kB]
Get:41 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libquadmath0 amd64 12.1.0-2ubuntu1~22.04 [154 kB]
Get:42 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgcc-11-dev amd64 11.3.0-1ubuntu1~22.04 [2,517 kB]
Get:43 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-11 amd64 11.3.0-1ubuntu1~22.04 [20.1 MB]
Get:44 http://security.ubuntu.com/ubuntu jammy-security/main amd64 cpp-12 amd64 12.1.0-2ubuntu1~22.04 [63.8 MB]
Get:45 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libasan8 amd64 12.1.0-2ubuntu1~22.04 [2,455 kB]                                    
Get:46 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libtsan2 amd64 12.1.0-2ubuntu1~22.04 [2,477 kB]                                    
Get:47 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgcc-12-dev amd64 12.1.0-2ubuntu1~22.04 [2,618 kB]                               
Get:48 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-12 amd64 12.1.0-2ubuntu1~22.04 [73.1 MB]                                       
Get:49 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-libc-dev amd64 5.15.0-60.66 [1,341 kB]                                       
Get:50 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libstdc++-11-dev amd64 11.3.0-1ubuntu1~22.04 [2,087 kB]                            
Get:51 http://security.ubuntu.com/ubuntu jammy-security/main amd64 g++-11 amd64 11.3.0-1ubuntu1~22.04 [11.4 MB]                                       
Fetched 205 MB in 14s (15.1 MB/s)                                                                                                                     
Extracting templates from packages: 100%
(Reading database ... 206909 files and directories currently installed.)
Preparing to unpack .../cpp-11_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking cpp-11 (11.3.0-1ubuntu1~22.04) over (11.2.0-19ubuntu1) ...
Preparing to unpack .../gcc-11-base_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking gcc-11-base:amd64 (11.3.0-1ubuntu1~22.04) over (11.2.0-19ubuntu1) ...
Preparing to unpack .../gcc-12-base_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking gcc-12-base:amd64 (12.1.0-2ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Setting up gcc-12-base:amd64 (12.1.0-2ubuntu1~22.04) ...
(Reading database ... 206909 files and directories currently installed.)
Preparing to unpack .../libstdc++6_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libstdc++6:amd64 (12.1.0-2ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Setting up libstdc++6:amd64 (12.1.0-2ubuntu1~22.04) ...
(Reading database ... 206909 files and directories currently installed.)
Preparing to unpack .../libgomp1_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libgomp1:amd64 (12.1.0-2ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Preparing to unpack .../libgcc-s1_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libgcc-s1:amd64 (12.1.0-2ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Setting up libgcc-s1:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libcc1-0:amd64.
(Reading database ... 206909 files and directories currently installed.)
Preparing to unpack .../00-libcc1-0_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libcc1-0:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package binutils-common:amd64.
Preparing to unpack .../01-binutils-common_2.38-4ubuntu2.1_amd64.deb ...
Unpacking binutils-common:amd64 (2.38-4ubuntu2.1) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../02-libbinutils_2.38-4ubuntu2.1_amd64.deb ...
Unpacking libbinutils:amd64 (2.38-4ubuntu2.1) ...
Selecting previously unselected package libctf-nobfd0:amd64.
Preparing to unpack .../03-libctf-nobfd0_2.38-4ubuntu2.1_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.38-4ubuntu2.1) ...
Selecting previously unselected package libctf0:amd64.
Preparing to unpack .../04-libctf0_2.38-4ubuntu2.1_amd64.deb ...
Unpacking libctf0:amd64 (2.38-4ubuntu2.1) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../05-binutils-x86-64-linux-gnu_2.38-4ubuntu2.1_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.38-4ubuntu2.1) ...
Selecting previously unselected package binutils.
Preparing to unpack .../06-binutils_2.38-4ubuntu2.1_amd64.deb ...
Unpacking binutils (2.38-4ubuntu2.1) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../07-libitm1_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libitm1:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libatomic1:amd64.
Preparing to unpack .../08-libatomic1_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libatomic1:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libasan6:amd64.
Preparing to unpack .../09-libasan6_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libasan6:amd64 (11.3.0-1ubuntu1~22.04) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../10-liblsan0_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking liblsan0:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libtsan0:amd64.
Preparing to unpack .../11-libtsan0_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libtsan0:amd64 (11.3.0-1ubuntu1~22.04) ...
Selecting previously unselected package libubsan1:amd64.
Preparing to unpack .../12-libubsan1_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libubsan1:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libquadmath0:amd64.
Preparing to unpack .../13-libquadmath0_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libquadmath0:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libgcc-11-dev:amd64.
Preparing to unpack .../14-libgcc-11-dev_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libgcc-11-dev:amd64 (11.3.0-1ubuntu1~22.04) ...
Selecting previously unselected package gcc-11.
Preparing to unpack .../15-gcc-11_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking gcc-11 (11.3.0-1ubuntu1~22.04) ...
Selecting previously unselected package gcc.
Preparing to unpack .../16-gcc_11.2.0-1ubuntu1_amd64.deb ...
Unpacking gcc (4:11.2.0-1ubuntu1) ...
Selecting previously unselected package cpp-12.
Preparing to unpack .../17-cpp-12_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking cpp-12 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libasan8:amd64.
Preparing to unpack .../18-libasan8_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libasan8:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libtsan2:amd64.
Preparing to unpack .../19-libtsan2_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libtsan2:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package libgcc-12-dev:amd64.
Preparing to unpack .../20-libgcc-12-dev_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking libgcc-12-dev:amd64 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package gcc-12.
Preparing to unpack .../21-gcc-12_12.1.0-2ubuntu1~22.04_amd64.deb ...
Unpacking gcc-12 (12.1.0-2ubuntu1~22.04) ...
Selecting previously unselected package make.
Preparing to unpack .../22-make_4.3-4.1build1_amd64.deb ...
Unpacking make (4.3-4.1build1) ...
Selecting previously unselected package lto-disabled-list.
Preparing to unpack .../23-lto-disabled-list_24_all.deb ...
Unpacking lto-disabled-list (24) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../24-dpkg-dev_1.21.1ubuntu2.1_all.deb ...
Unpacking dpkg-dev (1.21.1ubuntu2.1) ...
Selecting previously unselected package libc-dev-bin.
Preparing to unpack .../25-libc-dev-bin_2.35-0ubuntu3.1_amd64.deb ...
Unpacking libc-dev-bin (2.35-0ubuntu3.1) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../26-linux-libc-dev_5.15.0-60.66_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.15.0-60.66) ...
Selecting previously unselected package libcrypt-dev:amd64.
Preparing to unpack .../27-libcrypt-dev_4.4.27-1_amd64.deb ...
Unpacking libcrypt-dev:amd64 (1:4.4.27-1) ...
Selecting previously unselected package rpcsvc-proto.
Preparing to unpack .../28-rpcsvc-proto_1.4.2-0ubuntu6_amd64.deb ...
Unpacking rpcsvc-proto (1.4.2-0ubuntu6) ...
Selecting previously unselected package libtirpc-dev:amd64.
Preparing to unpack .../29-libtirpc-dev_1.3.2-2ubuntu0.1_amd64.deb ...
Unpacking libtirpc-dev:amd64 (1.3.2-2ubuntu0.1) ...
Selecting previously unselected package libnsl-dev:amd64.
Preparing to unpack .../30-libnsl-dev_1.3.0-2build2_amd64.deb ...
Unpacking libnsl-dev:amd64 (1.3.0-2build2) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../31-libc6-dev_2.35-0ubuntu3.1_amd64.deb ...
Unpacking libc6-dev:amd64 (2.35-0ubuntu3.1) ...
Selecting previously unselected package libstdc++-11-dev:amd64.
Preparing to unpack .../32-libstdc++-11-dev_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libstdc++-11-dev:amd64 (11.3.0-1ubuntu1~22.04) ...
Selecting previously unselected package g++-11.
Preparing to unpack .../33-g++-11_11.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking g++-11 (11.3.0-1ubuntu1~22.04) ...
Selecting previously unselected package g++.
Preparing to unpack .../34-g++_11.2.0-1ubuntu1_amd64.deb ...
Unpacking g++ (4:11.2.0-1ubuntu1) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../35-build-essential_12.9ubuntu3_amd64.deb ...
Unpacking build-essential (12.9ubuntu3) ...
Selecting previously unselected package dkms.
Preparing to unpack .../36-dkms_2.8.7-2ubuntu2.1_all.deb ...
Unpacking dkms (2.8.7-2ubuntu2.1) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../37-bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu10~22.04.1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu10~22.04.1) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../38-libfakeroot_1.28-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.28-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../39-fakeroot_1.28-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.28-1ubuntu1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../40-libalgorithm-diff-perl_1.201-1_all.deb ...
Unpacking libalgorithm-diff-perl (1.201-1) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Preparing to unpack .../41-libalgorithm-diff-xs-perl_0.04-6build3_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl (0.04-6build3) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../42-libalgorithm-merge-perl_0.08-3_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-3) ...
Selecting previously unselected package libc-devtools.
Preparing to unpack .../43-libc-devtools_2.35-0ubuntu3.1_amd64.deb ...
Unpacking libc-devtools (2.35-0ubuntu3.1) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../44-manpages-dev_5.10-1ubuntu1_all.deb ...
Unpacking manpages-dev (5.10-1ubuntu1) ...
Setting up gcc-11-base:amd64 (11.3.0-1ubuntu1~22.04) ...
Setting up manpages-dev (5.10-1ubuntu1) ...
Setting up lto-disabled-list (24) ...
Setting up cpp-12 (12.1.0-2ubuntu1~22.04) ...
Setting up libalgorithm-diff-perl (1.201-1) ...
Setting up binutils-common:amd64 (2.38-4ubuntu2.1) ...
Setting up linux-libc-dev:amd64 (5.15.0-60.66) ...
Setting up libctf-nobfd0:amd64 (2.38-4ubuntu2.1) ...
Setting up libgomp1:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libfakeroot:amd64 (1.28-1ubuntu1) ...
Setting up libasan6:amd64 (11.3.0-1ubuntu1~22.04) ...
Setting up fakeroot (1.28-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libtirpc-dev:amd64 (1.3.2-2ubuntu0.1) ...
Setting up rpcsvc-proto (1.4.2-0ubuntu6) ...
Setting up make (4.3-4.1build1) ...
Setting up libquadmath0:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libatomic1:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libubsan1:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libnsl-dev:amd64 (1.3.0-2build2) ...
Setting up libcrypt-dev:amd64 (1:4.4.27-1) ...
Setting up libasan8:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libtsan2:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libbinutils:amd64 (2.38-4ubuntu2.1) ...
Setting up libc-dev-bin (2.35-0ubuntu3.1) ...
Setting up libalgorithm-diff-xs-perl (0.04-6build3) ...
Setting up libcc1-0:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up liblsan0:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libitm1:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libc-devtools (2.35-0ubuntu3.1) ...
Setting up libalgorithm-merge-perl (0.08-3) ...
Setting up libtsan0:amd64 (11.3.0-1ubuntu1~22.04) ...
Setting up libctf0:amd64 (2.38-4ubuntu2.1) ...
Setting up cpp-11 (11.3.0-1ubuntu1~22.04) ...
Setting up libgcc-12-dev:amd64 (12.1.0-2ubuntu1~22.04) ...
Setting up libgcc-11-dev:amd64 (11.3.0-1ubuntu1~22.04) ...
Setting up libc6-dev:amd64 (2.35-0ubuntu3.1) ...
Setting up binutils-x86-64-linux-gnu (2.38-4ubuntu2.1) ...
Setting up binutils (2.38-4ubuntu2.1) ...
Setting up dpkg-dev (1.21.1ubuntu2.1) ...
Setting up gcc-12 (12.1.0-2ubuntu1~22.04) ...
Setting up libstdc++-11-dev:amd64 (11.3.0-1ubuntu1~22.04) ...
Setting up gcc-11 (11.3.0-1ubuntu1~22.04) ...
Setting up g++-11 (11.3.0-1ubuntu1~22.04) ...
Setting up gcc (4:11.2.0-1ubuntu1) ...
Setting up dkms (2.8.7-2ubuntu2.1) ...
Setting up g++ (4:11.2.0-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu10~22.04.1) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.15.0-43-generic
Building for architecture x86_64
Building initial module for 5.15.0-43-generic
Can't load /var/lib/shim-signed/mok/.rnd into RNG
40675079457F0000:error:12000079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:106:Filename=/var/lib/shim-signed/mok
/.rnd
..+..........+......+...+.....+...+...+.+...+........+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*...+.+......+..+++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++++*..+.+.....+.+.....+...+............+.+..+...+.......+.....+..........+..+....+..+.....................
.......+.....+.+........+.+.....+.......+........+.........+......+................+.....+.+...............+..+.+..+.........+......+....+........+...+
....+...+...........+.......+..+...+.......+...........+...............+.......+.....+.......+...........+....+......+.....+......+.........+.......+..
...+.......+..+......+...+.+.........+.....+..........+..+....+.....+..........+......+..+.+..+....+.....+..........+.....+.+...+......+...+..+........
........+........+.........+...+............+.......+........+.+.........+...........+......+...+.+.....+.........+.......+......+..............+.+..+.
+....................+.+......+.....+.......+..+.........+.+..............+......+.+.....+...............+...+....+.....+.......+...+.....+......+.+...
+........+...+.+.........+.....+.+......+..+.......+...........+...+......+...............+...+...............+...+..........+.....+.........+....+....
...........+............+.....+.......+........+.......+...............+............+...+............+...+...+..............+.+....................+...
............+.......+.....+.......+...+......+.....+.+........+......+......+...+......+.+........+.+.....+.......+............+..+.+........+.......+.
...........+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
..+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*.+...+.+.....+.+..+......+.......+............+..+...+...++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++*.....+.....+...............+......+...+....+......+.....................+.....+...+...+....+........+.+......+.
..+.....+.+......+..............+.+...+..+...+...+.......+...+...+.........+...+..+.+...............+.....+....+...+...+...........+...+.......+.....+.
+.................+...+..........+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
-----
Secure Boot not enabled on this system.
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.15.0-43-generic/updates/dkms/

depmod......
update-initramfs is disabled since running on read-only media
Setting up build-essential (12.9ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
ubuntu@ubuntu:
```

---

### Post by chili555 on 2023-02-22
>  I guess next is to try and over-install it onto the HDD image - hopefully keeping may apps and settings.What was the result? All fixed now?

---

### Post by curtis-s-copeland on 2023-03-01
@chili555 I ended up wiping the entire HDD and starting over.  It worked.  Sorry to drag you through that but there must have been something we couldn't find.

Now battling all the reconfig stuff hoping to reconnect the 3.6GiB digikam index files for all the massive remote HDD's I can't access until I figure out how I had them working ...  On to another forum search for USB remotes :)

Thank YOU anyway.

---

### Post by nuttyfresh on 2023-05-18
Hi friends!
I have quickly run through the previous messages. Seems like there was mostly a play with package versions. In the end topicstarter just has reinstalled ubuntu and get his driver working. But.. is this roll-back counted as fair solution? When I have initially installed ubuntu  22.04 - Wifi driver was working well. And it stopped after recent updates.

When I do `sudo apt install bcmwl-kernel-source`
make.log has multiple errors like:
""
[COLOR=#CCCCCC][FONT=&amp]linux_osl.c:[COLOR=#569cd6]659:17[/COLOR]: [COLOR=#ce9178]**error:**[/COLOR] implicit declaration of function ‘pci_map_single’; did you mean ‘dma_map_single’?[/FONT][/COLOR]


I'm not that friendly with C...  Seems `pci_map_single` was deprecated and removed in the latest version of linux kernel
[https://lore.kernel.org/lkml/20220106222804.GA330366@bhelgaas/T/](https://lore.kernel.org/lkml/20220106222804.GA330366@bhelgaas/T/)

That seems to be a straightforward change anyway. But not sure where to commit, so that changes are not overwritten.
File that need to be fixed is:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c

[COLOR=#000000]@chili555[/COLOR]

---

### Post by chili555 on 2023-05-18
> **nuttyfresh said:**
> Hi friends!
I have quickly run through the previous messages. Seems like there was mostly a play with package versions. In the end topicstarter just has reinstalled ubuntu and get his driver working. But.. is this roll-back counted as fair solution? When I have initially installed ubuntu  22.04 - Wifi driver was working well. And it stopped after recent updates.

When I do `sudo apt install bcmwl-kernel-source`
make.log has multiple errors like:
""
[COLOR=#CCCCCC][FONT=&amp]linux_osl.c:[COLOR=#569cd6]659:17[/COLOR]: [COLOR=#ce9178]**error:**[/COLOR] implicit declaration of function ‘pci_map_single’; did you mean ‘dma_map_single’?[/FONT][/COLOR]


I'm not that friendly with C...  Seems `pci_map_single` was deprecated and removed in the latest version of linux kernel
[https://lore.kernel.org/lkml/20220106222804.GA330366@bhelgaas/T/](https://lore.kernel.org/lkml/20220106222804.GA330366@bhelgaas/T/)

That seems to be a straightforward change anyway. But not sure where to commit, so that changes are not overwritten.
File that need to be fixed is:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c

[COLOR=#000000]@chili555[/COLOR]Please start your own new question and include:

```
uname -r
sudo apt update && sudo apt -y upgrade
sudo apt install --reinstall bcmwl-kernel-source
lspci -nnk | grep 0280 -A3
```Aslo post the entire make.log. Thanks.

---

