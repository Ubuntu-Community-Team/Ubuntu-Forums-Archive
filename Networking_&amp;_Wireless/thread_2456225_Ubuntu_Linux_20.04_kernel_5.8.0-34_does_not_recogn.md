---
title: "Ubuntu Linux 20.04 kernel 5.8.0-34 does not recognize WiFi"
date: 2021-01-07
forum: Networking &amp; Wireless
---

### Post by la.khan on 2021-01-07
Hi,

I updated my UL20.04 (64 bit) this morning and my Linux kernel was updated from 5.4.0-59 to 5.8.0-34. Since then, my Dell laptop does not recognize WiFi card anymore. I have followed the steps listed in [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) (How to install a driver for the Broadcom series of PCI wireless cards). These have helped me in the past for different UL versions of OS (16.04, 18.04, 20.04) and two Dell laptops.

As a test, I have switched back to kernel 5.4.0-59 and everything was working fine. However, I switched to 5.8.0-34 and followed steps in the above URL, hoping to get the WiFi working, including purging of installation of bcmwl-kernel-source. No luck in getting kernel 5.8.0-34 to detect my WiFi. So, I decided to move back to 5.4.0-59.

Since I purged bcmwl-kernel-source, I tried to install bcmwl-kernel-source using the steps listed in the above URL. The installation goes fine for kernel 5.4.0-59 but fails when it tries to process kernel 5.8.0-34.

My WiFi details are:
```

$lspci -nn -d 14e4:
06:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

The steps I followed are:
```

sudo apt purge -y bcmwl-kernel-source
sudo apt autoremove
sudo apt update
sudo apt-get install -y bcmwl-kernel-source

```
The output for the last command is
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms
Suggested packages:
  menu
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 21 not upgraded.
Need to get 0 B/1,611 kB of archives.
After this operation, 8,364 kB of additional disk space will be used.
Selecting previously unselected package dkms.
(Reading database ... 194803 files and directories currently installed.)
Preparing to unpack .../dkms_2.8.1-5ubuntu1_all.deb ...
Unpacking dkms (2.8.1-5ubuntu1) ...
Selecting previously unselected package bcmwl-kernel-source.
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu5_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu5) ...
Setting up dkms (2.8.1-5ubuntu1) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu5) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.4.0-59-generic 5.8.0-34-generic
Building for architecture x86_64
Building initial module for 5.4.0-59-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-59-generic/updates/dkms/

depmod.......

DKMS: install completed.
Building initial module for 5.8.0-34-generic
Error! Bad return status for module build on kernel: 5.8.0-34-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned error exit status 10
Processing triggers for man-db (2.9.1-1) ...
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Kernel 5.4.0-59 seems to have processed fine. The process errors out when working on kernel 5.8.0-34. How do I get the installation process NOT work on kernel 5.8.0-34? How do I get the installation process to ignore kernel 5.8.0-34?

Any help/insights/pointers in making my laptop WiFi work again is appreciated. Thanks in advance!

---

### Post by jeremy31 on 2021-01-07
What results from terminal for ```
apt rdepends linux-image-5.8.0-34-generic
```

---

### Post by la.khan on 2021-01-07
> **jeremy31 said:**
> What results from terminal for ```
apt rdepends linux-image-5.8.0-34-generic
```
@jeremy31: Thanks for the reply. Here is the output.
```

linux-image-5.8.0-34-generic
Reverse Depends:
  Depends: linux-image-generic-hwe-20.04
 |Depends: linux-modules-nvidia-455-5.8.0-34-generic
 |Depends: linux-modules-nvidia-450-server-5.8.0-34-generic
 |Depends: linux-modules-nvidia-450-5.8.0-34-generic
 |Depends: linux-modules-nvidia-440-server-5.8.0-34-generic
 |Depends: linux-modules-nvidia-418-server-5.8.0-34-generic
 |Depends: linux-modules-nvidia-390-5.8.0-34-generic
 |Depends: linux-modules-extra-5.8.0-34-generic
  Depends: linux-image-virtual-hwe-20.04-edge
  Depends: linux-image-virtual-hwe-20.04
  Conflicts: linux-image-unsigned-5.8.0-34-generic
  Depends: linux-image-generic-hwe-20.04-edge

```

---

### Post by halw on 2021-01-07
Is there any resolution to this issue yet? I have reverted to using the 5.4 kernel to get wifi on system with broadcom BCM4360 wireless card.

---

### Post by la.khan on 2021-01-07
Hi all,

I purged all packages that were part of kernel 5.8.0-34.
```

sudo apt purge linux-image-5.8.0-34-generic linux-image-unsigned-5.8.0-34-generic linux-modules-5.8.0-34-generic linux-modules-extra-5.8.0-34-generic linux-headers-5.8.0-34-generic linux-generic-hwe-20.04 linux-image-generic-hwe-20.04 linux-hwe-5.8-headers-5.8.0-34
sudo apt purge bcmwl-kernel-source
sudo apt autoremove
sudo apt update
sudo apt install bcmwl-kernel-source

```
Since all packages of kernel 5.8.0-34 were purged, they did not impact fresh installation bcmwl driver. Rebooted my machine and I have my WiFi working normally.

Since kernel 5.8.0-34 is the latest, I would prefer to use it. However, it is part of edge version whereas 5.4.59 is a stable version. I decided to retain what works seamlessly on my machine.

Just fyi ...:KS

---

### Post by halw on 2021-01-07
@la.khan, I, more or less, did the same in that I did a timeshift restore as I was having issues with sound as well. 
Don't think I'll do any updates until they can sort things out.

---

### Post by jeremy31 on 2021-01-07
I have no idea why people with 20.04 and the 5.4 kernels were updated to the 5.8.  I did a fresh 20.04 install yesterday using an old ISO and I had the 5.8 kernel and haven't been able to find out why

---

### Post by kansasnoob on 2021-01-07
> **jeremy31 said:**
> I have no idea why people with 20.04 and the 5.4 kernels were updated to the 5.8.  I did a fresh 20.04 install yesterday using an old ISO and I had the 5.8 kernel and haven't been able to find out why

Ditto!

[https://ubuntuforums.org/showthread.php?t=2456248&p=14012537#post14012537](https://ubuntuforums.org/showthread.php?t=2456248&p=14012537#post14012537)

---

### Post by halw on 2021-01-08
Update: Tried running Ubuntu 20.10 from a live USB which uses kernel 5.8 as well and wifi is not recognized there either. Wanted to give this a shot just to see if an older version of the 5.8 kernel had the same problem and it does.

---

### Post by #&amp;thj^% on 2021-01-08
> **kansasnoob said:**
> Ditto!

[https://ubuntuforums.org/showthread.php?t=2456248&p=14012537#post14012537](https://ubuntuforums.org/showthread.php?t=2456248&p=14012537#post14012537)

Just a thought, is **_"proposed" _**enabled?

---

### Post by Jim_J._Farrell_IV on 2021-01-10
why dont they use "Beta" versions to avoid issues like this, with an "Official update"

---

### Post by dzmanto on 2021-01-12
I faced the same issue with kernel 5.8.0-34.  For various reasons, you may need an installation having wifi before you resolve the wifi drivers. To get a working system having wifi 1. reboot, 2. in the grub boot menu, choose "Advanced options for Ubuntu", 3. choose "Ubuntu, with Linux 5.4.0-60-generic" 4. press enter and boot.

---

### Post by t-jeske on 2021-01-21
> **jeremy31 said:**
> I have no idea why people with 20.04 and the 5.4 kernels were updated to the 5.8.  I did a fresh 20.04 install yesterday using an old ISO and I had the 5.8 kernel and haven't been able to find out why
Ubuntu decided to ship new major kernels every 6 months starting from point release 20.04.2, which is due in February. So they have to prepare the repositories to contain everything to be available on that date. That includes an updated HWE kernel with version 5.8.

Desktop versions of Ubuntu ship with the HWE kernel by default (which makes sense). So as a consequence, the kernel now got automatically updated in preparation for the point release 20.04.2.

And yes, it was quite annoying suddenly having no WiFi anymore, without understanding why that would happen. BCM wifi cards aren't that rare, so this update supposedly hit a loooot of users. This shouldn't happen. There should be better testing that everything builds fine.

---

### Post by jeremy31 on 2021-01-21
This didn't happen with Ubuntu 16.04 or 18.04 installs.  They should already know what needs to be updated for the hwe kernel to work in the LTS as the packages already work on the short term support version with that kernel

---

### Post by matteo-vrancken on 2021-01-27
Hi all,

I didn't want to create a new topic as I assume it's related to the same issue.

Quite now to Ubuntu. I did some IT a long time ago so I'm not entirely clueless but very new to the Linux infrastructure.
Did  a fresh installment of Ubuntu on an older laptop to try it out. I've  run into an issue though with the wifi driver as it doesn't seem to be  there (currently keeping the LAN cable connected).
[URL="https://imgur.com/wwcte5g"]https://imgur.com/wwcte5g

[/URL]

So I checked the Ubuntu troubleshooting but I'm not sure how to proceed.  ( [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers) )
I first checked in *System > Administration > Hardware Drivers* for a binary driver and it shows the following: [URL="https://imgur.com/pD40yQX"]https://imgur.com/pD40yQX

[/URL]

So I try to apply those drivers, which at first fails: [https://imgur.com/i7qNENy](https://imgur.com/i7qNENy)
I try again which it then 'works' and tells me to restart to apply the changes: [URL="https://imgur.com/cNW7fiA"]https://imgur.com/cNW7fiA

[/URL]

But I've tried this several times and after rebooting, the wifi still doesn't work.
I've found this with the following command and it's a Broadcom wifi but it says 'UNCLAIMED'. ( [https://imgur.com/tHE4EeF](https://imgur.com/tHE4EeF) ) 
Could someone perhaps point me in the right direction to how to get the correct drivers, where to find them or what to do?

---

