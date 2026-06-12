---
title: "How to connect Cisco Linksys Wifi USB key to Ubuntu 14.04"
date: 2016-02-28
forum: Networking &amp; Wireless
---

### Post by abcuser on 2016-02-28
Hi,
I have installed Ubuntu 14.04 LTS on my PC and updated software to the latest level (sudo apt-get update && sudo apt-get -y dist-upgrade). Ubuntu is running without any issue. The only problem I have is with my Wifi USB key that I don't know how to configure.

I have had this Wifi USB key installed successfully on my other Windows 7 PC and Wifi USB key was working without an issue. I installed Wifi USB driver from CD, but the same drivers can be downloaded from internet.

I have "Cisco Linksys AE1200" Wifi USB key. Exact info about this device is at URL: [http://www.linksys.com/us/support-product?pid=01t80000003K7hFAAS](http://www.linksys.com/us/support-product?pid=01t80000003K7hFAAS) On this web site there is Download link to download drivers: [http://www.linksys.com/us/support-article?articleNum=148511](http://www.linksys.com/us/support-article?articleNum=148511) (click on rectangle at "Hardware version 1")  but this drivers are only available for Windows XP, Windows Vista and Windows 7. But I need a solution for Ubuntu.

Before inserting Wifi USB key into PC USB connector I have executed command:
```
lsusb | grep Wireless
```
and nothing was displayed. I inserted Wifi USB key and executed the same command and Wifi USB key was recognized:
```
Bus 002 Device 002: ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
```

I looked at the System Settings | Software & Update | Additional Drivers - message "Searching for available drivers" is displayed and after few seconds the list is empty with message "No additional drivers available" and additional message "No proprietary drivers are in use".

Any idea how to configure this Wifi USB device?
Thanks

---

### Post by abcuser on 2016-02-28
I searched the web the most useful is this forum thread: [http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter](http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter)

I updated Ubuntu:
```
sudo apt-get update && sudo apt-get -y dist-upgrade 
```

I checked if latest kernel headers are installed
```
sudo apt-get install linux-headers-$(uname -r) 
```
Already installed.

I checked if dkms is installed:
```
sudo apt-get install dkms 
```
Already installed.

Plug in Wifi USB and list the device:
```
lsusb | grep Wireless
```
and output is:
```
Bus 002 Device 002: ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
```

I searched for the packages:
```
apt-cache search ndiswrapper
```
and out put was:
```

ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
ndiswrapper-common - Common scripts required to use the utilities for ndiswrapper
ndiswrapper-dkms - Source for the ndiswrapper Linux kernel module (DKMS)
ndiswrapper-source - Source for the ndiswrapper Linux kernel module
ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper Linux kernel module

```

I installed packages and no error was returned:
```
sudo apt-get install ndiswrapper-common
```
```
sudo apt-get install ndiswrapper-source
```
```
sudo apt-get install ndiswrapper-utils-1.9
```
```
sudo apt-get install ndiswrapper-dkms
```
**Edit:** Most probably dkms package did return some error I was just not expecting it and probably not noticing the error returned.

Download Wifi USB driver:
```
wget http://downloads.linksys.com/downloads/driver/1224667593495/AE1200xp.zip
```

I extracted zip file:
```
unzip AE1200xp.zip
```

Changed directory:
```
cd xp
```

List install file:
```
ls *.inf
```

Install driver:
```
sudo ndiswrapper -i bcmwlhigh5.inf
```
Got error:
```

installing bcmwlhigh5 ...
couldn't find section "Linksys_AE1200.files.NTamd64" -
installation may be incomplete
couldn't find section "Linksys_AE2500.files.NTamd64" -
installation may be incomplete

```

Opened bcmwlhigh5.inf:
```
gedit bcmwlhigh5.inf
```
and according to the [http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter](http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter) searched for:
```

[Linksys_AE2500.files.NT]
AE2500xp.sys,,,6

```
Underneath it, add this:
```

[Linksys_AE1200.files.NTamd64]
    AE1200xp64.sys,,,6

[Linksys_AE2500.files.NTamd64]
    AE2500xp64.sys,,,6

```
and save the file. The problem is Windows XP was very successful in 32-bit version so the driver install files have them, but 64-bit Windows XP never really got pretty much working, so 64-bit settings where left out of inf file.

Checked what is the state of driver:
```
sudo ndiswrapper -l
```
and output is:
```
bcmwlhigh5 : invalid driver!
```

Uninstall invalid driver:
```
sudo ndiswrapper -e  bcmwlhigh5
```

Install driver again with repaired inf file.
```
sudo ndiswrapper -i bcmwlhigh5.inf
```
Installed successfully.

Check if driver is installed OK:
```
bcmwlhigh5 : driver installed
	device (13B1:0039) present

```

Unplug Wifi USB and plug it again. Now according to forums the blue light on Wifi USB key should turn on, but it doesn't.

I tried to install kernel module:
```
sudo depmod -a
```
Several second to wait and not output returned, so probably OK.

Installed module:
```
sudo modprobe ndiswrapper
```
and ouptput:
```
modprobe: FATAL: Module ndiswrapper not found.
```

I looked at /var/crash/ and there is only one file: ndiswrapper-dkms.0.crash
with content:
```

ProblemType: Package
DKMSBuildLog:
 DKMS make.log for ndiswrapper-1.59 for kernel 4.2.0-30-generic (x86_64)
 ned feb 28 12:42:12 CET 2016
 make: Entering directory `/usr/src/linux-headers-4.2.0-30-generic'
   LD      /var/lib/dkms/ndiswrapper/1.59/build/built-in.o
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/crt_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/hal_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/ndis_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/ntoskernel_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/ntoskernel_io_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/rtl_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.59/build/usb_exports.h
   MKSTUBS /var/lib/dkms/ndiswrapper/1.59/build/win2lin_stubs.h
   CC [M]  /var/lib/dkms/ndiswrapper/1.59/build/crt.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.59/build/hal.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.59/build/iw_ndis.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.59/build/loader.o
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c: In function &#8216;load_sys_files&#8217;:
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:157:4: error: implicit declaration of function &#8216;__vmalloc&#8217; [-Werror=implicit-function-declaration]
     __vmalloc(load_driver->sys_files[i].size,
     ^
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:156:19: warning: assignment makes pointer from integer without a cast [enabled by default]
    pe_image->image =
                    ^
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:207:5: error: implicit declaration of function &#8216;vfree&#8217; [-Werror=implicit-function-declaration]
      vfree(driver->pe_images[i].image);
      ^
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c: In function &#8216;add_bin_file&#8217;:
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:298:2: error: implicit declaration of function &#8216;vmalloc&#8217; [-Werror=implicit-function-declaration]
   bin_file->data = vmalloc(driver_file->size);
   ^
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:298:17: warning: assignment makes pointer from integer without a cast [enabled by default]
   bin_file->data = vmalloc(driver_file->size);
                  ^
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c: In function &#8216;wrapper_ioctl&#8217;:
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:789:15: warning: assignment makes pointer from integer without a cast [enabled by default]
    load_driver = vmalloc(sizeof(*load_driver));
                ^
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c: In function &#8216;wrapper_ioctl_compat&#8217;:
 /var/lib/dkms/ndiswrapper/1.59/build/loader.c:884:11: warning: assignment makes pointer from integer without a cast [enabled by default]
    kdriver = vmalloc(sizeof(*kdriver));
            ^
 cc1: some warnings being treated as errors
 make[1]: *** [/var/lib/dkms/ndiswrapper/1.59/build/loader.o] Error 1
 make: *** [_module_/var/lib/dkms/ndiswrapper/1.59/build] Error 2
 make: Leaving directory `/usr/src/linux-headers-4.2.0-30-generic'
DKMSKernelVersion: 4.2.0-30-generic
Date: Sun Feb 28 12:42:17 2016
DuplicateSignature: dkms:ndiswrapper-dkms:1.59-2:/var/lib/dkms/ndiswrapper/1.59/build/loader.c:157:4: error: implicit declaration of function &#8216;__vmalloc&#8217; [-Werror=implicit-function-declaration]
Package: ndiswrapper-dkms 1.59-2
PackageVersion: 1.59-2
SourcePackage: ndiswrapper
Title: ndiswrapper-dkms 1.59-2: ndiswrapper kernel module failed to build
ApportVersion: 2.14.1-0ubuntu3.19
Architecture: amd64
Dependencies:
 adduser 3.113+nmu3ubuntu3
 apt-utils 1.0.1ubuntu2.11
 base-passwd 3.5.33
 binutils 2.24-5ubuntu14
 busybox-initramfs 1:1.21.0-1ubuntu1
 coreutils 8.21-1ubuntu5.3
 cpio 2.11+dfsg-1ubuntu1.2
 cpp 4:4.8.2-1ubuntu6
 cpp-4.8 4.8.4-2ubuntu1~14.04.1
 dbus 1.6.18-0ubuntu4.3
 debconf 1.5.51ubuntu2
 debconf-i18n 1.5.51ubuntu2
 debianutils 4.4
 dkms 2.2.0.3-1.1ubuntu5.14.04.5
 dpkg 1.17.5ubuntu5.5
 e2fslibs 1.42.9-3ubuntu1.3
 e2fsprogs 1.42.9-3ubuntu1.3
 fakeroot 1.20-3ubuntu2
 findutils 4.4.2-7
 gcc 4:4.8.2-1ubuntu6
 gcc-4.8 4.8.4-2ubuntu1~14.04.1
 gcc-4.8-base 4.8.4-2ubuntu1~14.04.1
 gcc-4.9-base 4.9.3-0ubuntu4
 ifupdown 0.7.47.2ubuntu4.3
 initramfs-tools 0.103ubuntu4.2
 initramfs-tools-bin 0.103ubuntu4.2
 initscripts 2.88dsf-41ubuntu6.3
 insserv 1.14.0-5ubuntu2
 iproute2 3.12.0-2ubuntu1
 isc-dhcp-client 4.2.4-7ubuntu12.4
 isc-dhcp-common 4.2.4-7ubuntu12.4
 klibc-utils 2.0.3-0ubuntu1
 kmod 15-0ubuntu6
 libacl1 2.2.52-1
 libapparmor1 2.8.95~2430-0ubuntu5.3
 libapt-inst1.5 1.0.1ubuntu2.11
 libapt-pkg4.12 1.0.1ubuntu2.11
 libasan0 4.8.4-2ubuntu1~14.04.1
 libatomic1 4.8.4-2ubuntu1~14.04.1
 libattr1 1:2.4.47-1ubuntu1
 libaudit-common 1:2.3.2-2ubuntu1
 libaudit1 1:2.3.2-2ubuntu1
 libblkid1 2.20.1-5.1ubuntu20.7
 libbz2-1.0 1.0.6-5
 libc-dev-bin 2.19-0ubuntu6.7
 libc6 2.19-0ubuntu6.7
 libc6-dev 2.19-0ubuntu6.7
 libcap2 1:2.24-0ubuntu2
 libcgmanager0 0.24-0ubuntu7.5
 libcloog-isl4 0.18.2-1
 libcomerr2 1.42.9-3ubuntu1.3
 libdb5.3 5.3.28-3ubuntu3
 libdbus-1-3 1.6.18-0ubuntu4.3
 libdebconfclient0 0.187ubuntu1
 libdrm2 2.4.64-1~ubuntu14.04.1
 libexpat1 2.1.0-4ubuntu1.1
 libfakeroot 1.20-3ubuntu2
 libgcc-4.8-dev 4.8.4-2ubuntu1~14.04.1
 libgcc1 1:4.9.3-0ubuntu4
 libgmp10 2:5.1.3+dfsg-1ubuntu1
 libgomp1 4.8.4-2ubuntu1~14.04.1
 libgpm2 1.20.4-6.1
 libisl10 0.12.2-1
 libitm1 4.8.4-2ubuntu1~14.04.1
 libjson-c2 0.11-3ubuntu1.2
 libjson0 0.11-3ubuntu1.2
 libklibc 2.0.3-0ubuntu1
 libkmod2 15-0ubuntu6
 liblocale-gettext-perl 1.05-7build3
 liblzma5 5.1.1alpha+20120614-2ubuntu2
 libmount1 2.20.1-5.1ubuntu20.7
 libmpc3 1.0.1-1ubuntu1
 libmpfr4 3.1.2-1
 libncurses5 5.9+20140118-1ubuntu1
 libncursesw5 5.9+20140118-1ubuntu1
 libnih-dbus1 1.0.3-4ubuntu25
 libnih1 1.0.3-4ubuntu25
 libpam-modules 1.1.8-1ubuntu2
 libpam-modules-bin 1.1.8-1ubuntu2
 libpam-runtime 1.1.8-1ubuntu2
 libpam-systemd 204-5ubuntu20.18
 libpam0g 1.1.8-1ubuntu2
 libpcre3 1:8.31-2ubuntu2.1
 libplymouth2 0.8.8-0ubuntu17.1
 libpng12-0 1.2.50-1ubuntu2.14.04.2
 libprocps3 1:3.3.9-1ubuntu2.2
 libquadmath0 4.8.4-2ubuntu1~14.04.1
 libselinux1 2.2.2-1ubuntu0.1
 libsemanage-common 2.2-1
 libsemanage1 2.2-1
 libsepol1 2.2-1ubuntu0.1
 libslang2 2.2.4-15ubuntu1
 libss2 1.42.9-3ubuntu1.3
 libstdc++6 4.8.4-2ubuntu1~14.04.1
 libsystemd-daemon0 204-5ubuntu20.18
 libsystemd-login0 204-5ubuntu20.18
 libtext-charwidth-perl 0.04-7build3
 libtext-iconv-perl 1.7-5build2
 libtext-wrapi18n-perl 0.06-7
 libtinfo5 5.9+20140118-1ubuntu1
 libtsan0 4.8.4-2ubuntu1~14.04.1
 libudev1 204-5ubuntu20.18
 libustr-1.0-1 1.0.4-3ubuntu2
 libuuid1 2.20.1-5.1ubuntu20.7
 libxtables10 1.4.21-1ubuntu1
 linux-libc-dev 3.13.0-79.123
 lsb-base 4.1+Debian11ubuntu6
 make 3.81-8.2ubuntu3
 makedev 2.3.1-93ubuntu1
 manpages 3.54-1ubuntu1
 manpages-dev 3.54-1ubuntu1
 module-init-tools 15-0ubuntu6
 mount 2.20.1-5.1ubuntu20.7
 mountall 2.53
 multiarch-support 2.19-0ubuntu6.7
 netbase 5.2
 passwd 1:4.1.5.1-1ubuntu9.2
 patch 2.7.1-4ubuntu2.3
 perl-base 5.18.2-2ubuntu1
 plymouth 0.8.8-0ubuntu17.1
 plymouth-theme-ubuntu-text 0.8.8-0ubuntu17.1
 procps 1:3.3.9-1ubuntu2.2
 psmisc 22.20-1ubuntu2
 sensible-utils 0.0.9
 systemd-services 204-5ubuntu20.18
 sysv-rc 2.88dsf-41ubuntu6.3
 sysvinit-utils 2.88dsf-41ubuntu6.3
 tar 1.27.1-1
 tzdata 2015g-0ubuntu0.14.04
 udev 204-5ubuntu20.18
 upstart 1.12.1-0ubuntu4.2
 util-linux 2.20.1-5.1ubuntu20.7
 uuid-runtime 2.20.1-5.1ubuntu20.7
 zlib1g 1:1.2.8.dfsg-1ubuntu1
DistroRelease: Ubuntu 14.04
InstallationDate: Installed on 2014-10-09 (506 days ago)
InstallationMedia: Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)
PackageArchitecture: all
ProcVersionSignature: Ubuntu 4.2.0-30.36~14.04.1-generic 4.2.8-ckt3
RelatedPackageVersions:
 dpkg 1.17.5ubuntu5.5
 apt  1.0.1ubuntu2.11
Tags:  trusty
Uname: Linux 4.2.0-30-generic x86_64
UpgradeStatus: No upgrade log present (probably fresh install)
_MarkForUpload: True

```

It looks like something wrong with this module or something. Any idea what do to next?
Thanks

---

### Post by abcuser on 2016-02-28
I looked at the problem and I reported a bug to bug tracker by executing command:
```
ubuntu-bug ndiswrapper-utils-1.9
```

Bug report is at: [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1550915](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1550915)

---

### Post by abcuser on 2016-02-29
Hi,
I would like to update this thread with my solution to the problem if someone having the same problem. My reported bug was marked as duplicate of another bug, so this is known problem!

Let get first why this problem existed in first place. Before I plugged my Cisco Linksys AE1200 Wifi USB key into Ubuntu I have upgraded Ubuntu to 14.04.4 (sudo apt-get update && sudo apt-get -y dist-upgrade) and according to the [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop) **upgraded** kernel to "wily" kernel. I just thought having the latest kernel would just fix any problem (by the way this is default kernel with Ubuntu 14.04.4 if downloaded now from official Ubuntu web site!!!). Big mistake, I wasted two days figuring out that this kernel update was *major problem* to my WiFi USB key configuration.

How I fixed the problem:
1. In Terminal to find out what is the current kernel.
```
uname -r
```
and output was: 4.2.0-30-generic 
2. I restarted Ubuntu and in boot menu from "Advanced options" I selected "3.13.0-79-generic".
3. Ubuntu started up and I repeated the command in terminal and now getting the: 3.13.0-79-generic". OK, now I am back to official "Ubuntu 14.04" kernel.
4. Now I have uninstalled the following packages:
```
sudo apt-get purge linux-generic-lts-wily linux-headers-4.2.0-30 linux-headers-4.2.0-30-generic linux-headers-generic-lts-wily linux-image-4.2.0-30-generic linux-image-extra-4.2.0-30-generic linux-image-generic-lts-wily
```
Note: So I uninstalled linux-generic-<every version with wily and 4.2> and linux-image-<every version with wily and 4.2>
5. Rebooted Ubuntu and check the kernel number:
```
uname -r
```
and output is still: 3.13.0-79-generic
6. Now I have uninstalled driver (because this is faulty driver with faulty kernel):
```
sudo ndiswrapper -e  bcmwlhigh5
```
7. I have uninstalled whole software from ndiswrapper and installed it again. This is requited to make sure ndiswrapper kernel module is recompiled against currently installed kernel (in my case 3.13.0-79-generic).
```
sudo apt-get purge ndiswrapper-common ndiswrapper-dkms ndiswrapper-source ndiswrapper-utils-1.9
sudo apt-get install ndiswrapper-common ndiswrapper-dkms ndiswrapper-source ndiswrapper-utils-1.9
```
Note: There was a message that new kernel module was compiled.
8. I have unplugged Wifi USB key and inserted it back. I spotted the blue led light was turned on on Wifi USB key what a joy!
9. Just to make sure kernel module is OK:
```
sudo depmod -a
sudo modprobe ndiswrapper
```
both commands without error.
10. Rebooted Ubuntu to make sure Wifi USB is working fine (blue led light) and it was.
11. From top Ubuntu panel I have selected my wireless network typed in my wireless network SSID and bingo, my WiFi wireless network is working excellent. What a joy.

P.S. I got to tell I am little bit disappointed that new kernel (wily kernel) was added to Ubuntu 14.04 LTS without updating dkms module according to bug report [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1514243](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1514243) The kernel 4.2.0-30 was added to the Ubuntu 14.04.4 but ndiswrapper kernel module was still at "ndiswrapper 1.59-2" but it is obvious from bug report that this problem was solved in Wily by upgrading the "ndiswrapper 1.59-5".
Regards

---

### Post by nigel_pain2 on 2016-05-01
Hi, I thought this was the answer to my problems. I installed 14.04 LTS (kernel 4.2.0-35) on an ancient laptop (c. 12 years old), with a Lincsys PCMCIA wifi adapter. No Linux driver so I was going to go down the ndiswrapper route and then got the bug reported in 1514243.
However, when I tried kernel 3.13.0-24 it didn't even recognise the ethernet device (only loopback showing with ifconfig). I'm fairly new to Linux so I'm probably missing something! Any ideas?
Thanks

---

### Post by abcuser on 2016-05-02
@nigel_pain2, honestly I gave up on this Wifi USB key. I manage to make it working like describing above, but Wifi connection was pretty unstable, founding out few days after I have written my previous post when connection drops every few minutes without known reason. Having laptop on exactly the same location as my PC with Wifi USB key having zero problems with Wifi on laptop and dropping connection on my PC Wifi USB key every few minutes. Probably some bug or something nasty. Extremely frustrating, unable to normally work with it.

I just gave up after reading that this software wrapper is not maintained any more upstream, so I lost interest on fixing something that is difficult if not impossible to fix. Few days latter I have both standard network UTP cable and connected my router to my PC with it having zero problems.

In my case getting into the trouble in the first place I just grabbed Wifi USB key connected to some old Windows like PC where it was working without a problem. The "moral" story is, don't try to connect Windows only devices to Linux computer. When new hardware component is going to be bought make SURE that it is officially supported for Linux (Linux drivers) unless you are heading into hell of a problems using some workarounds like wrappers.

---

