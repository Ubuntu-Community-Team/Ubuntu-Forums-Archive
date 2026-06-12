---
title: "Can't figure out how to install broad com driver for wireless Internet on my laptop.."
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by chris231 on 2014-05-17
**Ubuntu Linux Version:**
^Cdatahead@datahead-G750JW:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

I was following the instructions at: [https://help.ubuntu.com/community/Wi...Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
--I was in subsection 12.04 in this document

**This is my network card:**
datahead@datahead-G750JW:~$ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

**Here's what it did when I tried to install the driver:**
datahead@datahead-G750JW:~$ sudo apt-get --reinstall install bcmwl-kernel-sourceReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-58 linux-headers-3.2.0-58-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,348 kB of archives.
After this operation, 4,286 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 262379 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-20-generic
Building for architecture x86_64
Building initial module for 3.11.0-20-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-20-generic/updates/dkms/

depmod........

DKMS: install completed.
**Segmentation fault**
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
datahead@datahead-G750JW:~$ sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
*   It hung here.*
^Cdatahead@datahead-G750JW:~$ sudo modprobe wl
*   It hung here, too.*

--That segmentation fault looks suspicious!

I also tried the blacklist steps toward the bottom of that web document  that install linux-firmware-nonfree and blacklist wl and b43.  I had the  exact same problems.  I also expect these will need to be  un-blacklisted in order to complete the installation.

Also...I cannot upgrade to Ubuntu 14 because Ubuntu 14 does not support  Cuda (for GPU programming), which I need for research work.  That is why  I'm using Ubuntu 12...

---

### Post by squakie on 2014-05-18
Well, I don't know anything about Cuda, but in my 14.04 repositories there are a lot of things for Cuda - are you sure it doesn't support Cuda?

---

### Post by chris231 on 2014-05-18
Yes, Ubuntu 14 is not supported per the table at: [http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/#axzz3239aMBsY](http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/#axzz3239aMBsY)
Ubuntu 14 is not a version listed in that table.

Thus I have to to do eveything in Ubuntu 12/13.

Besides that, no CUDA installations succeeded for me in 14.  They did succeed in 12.

---

### Post by squakie on 2014-05-18
I'll look into the wireless driver issue.  There are others here more qualified than I for it though.  I don't know what particular problem you had with Cuda in 14.04.  I just installed everything but the python things for Cuda from the repositories in 14.04 and everything installed fine.  Do you get a particular error?  It's very possible that the link you pointed to, showing the table of OS's supported, was done prior to the release of 14.04 - doesn't mean it doesn't work, just that it didn't exist at the time the page was created.

---

### Post by squakie on 2014-05-18
If you look at [this]("http://ubuntuforums.org/showthread.php?t=2197997") thread, you'll see that the link you posted that you were following did not work in 12.04.  They updated to 12.10 to fix things.

[This]("http://www.ubuntu.com/certification/catalog/component/pci/14e4:43b1/") link indicates that the device is supported via the 2 laptops show as certified.

[This]("http://askubuntu.com/questions/377943/no-way-to-connect-to-my-wifi-dell-m4800-ubuntu-13-10x64bits") link indicates problems but provides a type of work around.  It shows for 13.10, but should apply to 12.04 also.

I'll keep looking for more.  It's been several months now, but I thought I had seen a similar request because there is something different with the 4352 versus the 43xx models supported by some of the other drivers (including what you have been following).  I know of a couple of the experts to ask, so perhaps I can persuade one of them to come take a look here.

In the mean time, I'll keep searching.

---

### Post by squakie on 2014-05-18
I also found seveeral things via a search in the form of bcm4352:

[http://ubuntuforums.org/showthread.php?t=2220593&highlight=bcm4352](http://ubuntuforums.org/showthread.php?t=2220593&highlight=bcm4352)

[http://ubuntuforums.org/showthread.php?t=2217576&highlight=bcm4352](http://ubuntuforums.org/showthread.php?t=2217576&highlight=bcm4352)

Other - one that is simple enough *if* it's the reason:

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-12-04-bcm4312-device-is-present-but-can%27t-do-much-4175431012/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-12-04-bcm4312-device-is-present-but-can%27t-do-much-4175431012/)

There are many more out there. I wish I knew more to help you there.  Something I know from personal experience that may not be obvious:

- every time you try one "solution" and it doesn't work, be sure to back out *all* changes before trying the next.  You can end up with conflicting modules, things being blacklisted that you actually need, etc..

I find out more detail I'll let you know.

---

### Post by chris231 on 2014-05-19
This is what I tried recently while searching different forums online:

```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Per [http://askubuntu.com/questions/45063.../453430#453430]("http://askubuntu.com/questions/450631/wifi-not-working-in-ubuntu-14-04-lts/453430#453430"), I ran these commands: 
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

sudo apt-get install b43-fwcutter firmware-b43-installer

--I then rebooted

I still didn't see any wireless networks on my desktop. 
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ 
I also tried these instructions: [http://forum.osxlatitude.com/index.p...e-43b1-rev-03/]("http://forum.osxlatitude.com/index.php?/topic/6339-ubuntudebian-14e443b1-broadcom-corporation-device-43b1-rev-03/")

When I got to this command, it blew up: 
datahead@datahead-G750JW:/usr/src/b43b1-6.30.223.141$ sudo dkms build -m b43b1 -v 6.30.223.141

Kernel preparation unnecessary for this kernel. Skipping...

Building module: cleaning build area.... make  KERNELRELEASE=3.11.0-20-generic....(bad exit status: 2) ERROR (dkms  apport): binary package for b43b1: 6.30.223.141 not found Error! Bad  return status for module build on kernel: 3.11.0-20-generic (x86_64)  Consult /var/lib/dkms/b43b1/6.30.223.141/build/make.log for more  information.

Here's that log:
DKMS make.log for b43b1-6.30.223.141 for kernel 3.11.0-20-generic (x86_64)
Sun May 18 18:27:44 EDT 2014
/bin/sh: 1: [: Illegal number:
/bin/sh: 1: [: Illegal number:
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-20-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/b43b1/6.30.223.141/build/built-in.o
  CC [M]  /var/lib/dkms/b43b1/6.30.223.141/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.o
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_printstats&#8217;:
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3246:7:  warning: passing argument 1 of &#8216;wl->tkipmodops->print_stats&#8217; from  incompatible pointer type [enabled by default]
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3246:7:  note: expected &#8216;struct seq_file *&#8217; but argument is of type &#8216;char *&#8217;
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3249:4:  warning: passing argument 1 of &#8216;wl->tkipmodops->print_stats&#8217; from  incompatible pointer type [enabled by default]
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3249:4:  note: expected &#8216;struct seq_file *&#8217; but argument is of type &#8216;char *&#8217;
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c: In function &#8216;wl_reg_proc_entry&#8217;:
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3470:2:  error: implicit declaration of function &#8216;create_proc_entry&#8217;  [-Werror=implicit-function-declaration]
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3470:22:  warning: assignment makes pointer from integer without a cast [enabled  by default]
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3475:16: error: dereferencing pointer to incomplete type
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3476:16: error: dereferencing pointer to incomplete type
/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.c:3477:16: error: dereferencing pointer to incomplete type
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/b43b1/6.30.223.141/build/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/var/lib/dkms/b43b1/6.30.223.141/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-20-generic'
make: *** [all] Error 2
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
```

I'll start looking through your new suggestions bit by bit and see if any of the tips are ones I haven't tried yet.

---

### Post by wildmanne39 on 2014-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chris231 on 2014-05-19
Yeah, this person specifically says his problems were due to not having bcmwl-kernel-source:
[http://ubuntuforums.org/showthread.php?t=2217576&highlight=bcm4352](http://ubuntuforums.org/showthread.php?t=2217576&highlight=bcm4352)

I then tried installing this package (again):
```

datahead@datahead-G750JW:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,348 kB of archives.
After this operation, 4,286 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 271684 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.2_amd64.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-20-generic
Building for architecture x86_64
Building initial module for 3.11.0-20-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-20-generic/updates/dkms/

depmod........

DKMS: install completed.
**Segmentation fault**
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic

```

I know I'm not the only one getting this error message, but I couldn't find a solution to it doing a google search just now.
-------------------------------------------------------------------------------
I'd be a little hesitant to upgrade to Ubuntu 12.10, since I had to downgrade from 14 to 12 to get Cuda to work.  This was based on the "Getting started with Linux" Nvidia Cuda page, warning messages in the installer, and talking with people who use Cuda in a lab.
---------------------------------------------------------------------------------

---

### Post by squakie on 2014-05-20
WildMan is one of the experts on this.  I also contacted one of the others and they suggested the following in their P.M. to me.  Perhaps it can be of some help also.

> First, I don't think the version of bcmwl-kernel-source that apt-get  offers, in his case 6.20.155.1, supports his device. Even if he gets it  to install without complaint, he will probably not get his device to  work!

I'd ask him to purge it: sudo apt-get purge bcmwl-kernel-source.  Hopefully, he gets that done without a freeze. He may need to reboot  into recovery mode, get a terminal prompt and do it that way in order to  get video, compiz, etc. out of the picture.

He doesn't need to undo any blacklists.

Next, I'd ask him to download and install this: [http://packages.ubuntu.com/saucy/bcmwl-kernel-source](http://packages.ubuntu.com/saucy/bcmwl-kernel-source)

sudo dpkg -i bcmwl*.deb

You might also consult the log to see what went amiss: cat  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/3.13.0-24-generic/x86_64/log/make.log  in my case; his will be a bit different.

WildMan - nice to see you again!  Hope all is well.  The above was a P.M. back from another one of your expert friends there in the forum support.  They are watching the thread and I'm glad you're here as well.  Some how I managed (my fault) to delete some things on my system that it really needed, ended up with a dead system.  Had to completely reload from factory restore disks last night, haven't gotten Ubuntu back in dual boot yet.  So, I'm kind of hanging here with no way to look up/at things via my system to help.

Thanks both of you!

---

### Post by chris231 on 2014-05-20
The new package successfully installed and made wireless networks show up, but it doesn't persist on a reboot.



Yeah, bcmwl-kernel-source definitely caused me problems before.  When installing it hung on me once and caused the package manager to become locked.

Freezing did not happen until I attempted to comment out some entries in the file /etc/modprobe.d/blacklist.conf.

After that, even after backing out that config file change, the bcmwl-kernel-source installation would hang each time I ran it.  I had to purge the package from the system in order to allow package installs to work again.

There was another time a couple days ago where this package did impact my system and where I did have to go into recovery mode.


Here are the last set of entries in /etc/modprobe.d/blacklist.conf for your reference:
```

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist w
l
```


Package Installation:
```

datahead@datahead-G750JW:~/Downloads$ sudo dpkg -i bcmwl*.deb
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 280486 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb) ...
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu1) ...
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-20-generic
Building for architecture x86_64
Building initial module for 3.11.0-20-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-20-generic/updates/dkms/

depmod........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic



```

It worked when installing - I had seen wireless networks on my desktop.
However, after trying a reboot, the wireless networks don't show.
[B]Might this package have not properly persisted or not have had a configuration for startup set?

[/B]I tried reinstalling the package, and the wireless networks showed up again.  Thus now I just need to figure out how to make this driver change stay in place after reboots.Here's the log for the latest run that makes wireless networks show up:
```

datahead@datahead-G750JW:/var/lib/dkms/bcmwl/kernel-3.11.0-20-generic-x86_64/log$ cat make.log
DKMS make.log for bcmwl-6.30.223.141+bdcom for kernel 3.11.0-20-generic (x86_64)
Tue May 20 01:52:48 EDT 2014
make: Entering directory `/usr/src/linux-headers-3.11.0-20-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/wl.o
  Building modules, stage 2.
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/wl.mod.o
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/wl.ko
make: Leaving directory `/usr/src/linux-headers-3.11.0-20-generic'

```

---

### Post by squakie on 2014-05-20
Well, I'm not positive here, but it looks like:

- the driver you are building is wl

- you are stopping wl from loading because it is in the blacklist file

What I would try:

- edit the /etc/modprobe.d/blacklist.conf file
- add # to comment out the blacklist wl line (looks in your posting above it above it's split across 2 lines - make it a single line
- save the file
- reboot

If that doesn't fix it then remove the # so at least it's back to where it was.

---

### Post by squakie on 2014-05-22
Have you gotten this working yet?  If so, please post you solution for others to see and mark the thread as solved.  If not, please post back.  There are thousands of people here with way more knowledge than I have - I'm sure someone else would be quite willing to help!

---

### Post by chris231 on 2014-05-22
I've gotten it fixed...

```

sudo su 
echo wl >> /etc/modules 
exit
  Also do:

  sudo gedit /etc/modprobe.d/blacklist.conf
  and remove blacklist wl then save and close gedit.  now it should work after you reboot.

```

WildMan gave me these instructions.

---

### Post by squakie on 2014-05-23
Well, I got the edit of blacklist correct - I just thought it was probably already in the modules being loaded so I didn't have you edit modules.  Sorry about that, but glad you got it working.  BTW - there would be no difference between commenting (# at front) the line in blacklist.conf and removing it - just FYI.

---

### Post by cmcanulty on 2014-05-23
this worked for me the most important seeming to be the purge operation then the installs
[http://askubuntu.com/questions/55868/installing-...]("http://askubuntu.com/questions/55868/installing-...")

---

