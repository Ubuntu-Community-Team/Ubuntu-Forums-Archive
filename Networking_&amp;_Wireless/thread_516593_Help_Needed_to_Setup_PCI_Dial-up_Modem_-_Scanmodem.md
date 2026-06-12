---
title: "Help Needed to Setup PCI Dial-up Modem - Scanmodem completed"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by Computers without Borders on 2007-08-03
Hi Gang!

I am unable to get my Thinkpad T21 dial-up modem working (Chip# MPCI 3A56GSP-100PA).  Below is my ModemData.txt .  I also ran "sudo wvdialconf /etc/wvdial.conf" but no modem was found.

Any help would be amazing for this newbee.  I am dead sick of Windows and want this opensource to work--but I really have zero experience with it.

Regards,

James

--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 5.10 "Breezy Badger" 
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
 scanModem update of:  2007_August_01


ALSAversion
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:00:03.1	115d:000c	8086:2408	Serial controller: Xircom Mini-PCI V.90 56k Modem

 Modem interrupt assignment and sharing: 
 11:      60351          XT-PIC  uhci_hcd:usb1, yenta, yenta, CS46XX

 --- Bootup diagnostics for card in PCI slot 0000:00:03.1 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  0000:00:03.1
   Class 0700: 115d:000c Serial controller: Xircom Mini-PCI V.90 56k Modem
      Primary PCI_id  115d:000c
 Support type needed or chipset:	Agere.DSP
 


 The modem has a supported Lucent/Agere  Mars or Apollo DSP (digital signal 
 processing) chipset. Support packages for 2.6.n kernels are at: 
 [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

 See AgereDSP.txt for Details.
  DSP=1

 Vendor 115d is XIRCOM, which was purchased by Intel
 The following devices have Lucent/AgereSystems DSP chipsets supported by the
 Martian variant of the AgereSystems ltmodem software.
 
    XIRCOM 0x115d          0x0000-0x000F
    XIRCOM 0x115d          0x0440-0x045c
    XIRCOM 0x115d          0x0010-0x03ff


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udevdb

 The kernel was compiled with gcc version 3.4.5 and a compiler is not installed

To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) 
 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	gcc-3.4 make linux-headers-2.6.12-9-386


If a driver compilation files with message including some lack of some FileName.h (stdio.h for example. 
Some additional kernel-header files need installation to /usr/include.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:
$ sudo apt-get -s install linux-kernel-devel
While some of the files may be on the install CD, others may have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)

For Ubunut feisty, additional packages required were:
 build-essential curl debhelper dpkg-dev g++ g++-4.1 gettext git-core gitk
 html2text intltool-debian kernel-package kernel-wedge libc6-dev
 libcurl3-gnutls libdigest-sha1-perl liberror-perl libstdc++6-4.1-dev
 linux-libc-dev po-debconf rcs tcl8.4 tk8.4


Checking pppd properties:
	-rwsr-xr--  1 root dip 257688 2005-05-27 12:16 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by helmut_hed on 2007-08-06
You are in luck!  It's a supported Lucent/Agere chipset modem, according to the output you supplied:

[begin quote]
The modem has a supported Lucent/Agere Mars or Apollo DSP (digital signal
processing) chipset. Support packages for 2.6.n kernels are at: 
[end quote]

download the package listed right after that message and follow the instructions in "INSTALL".

Good luck,
Jeff

---

### Post by {{DoX}} on 2008-05-11
Sorry about the whole archive bump and whatnot but Ive got the same thing goin on heres my Modemdata.txt from my thinkpad T20

--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_05_02

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 090c:6000 Feiya Technology Corp. 

USB modems not recognized
For candidate card in slot 00:03.1, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:03.1	115d:000c	8086:2408	Serial controller: Xircom Mini-PCI V.90 56k Modem

 Modem interrupt assignment and sharing: 
 11:      15195    XT-PIC-XT        uhci_hcd:usb1, yenta, yenta, eth0, CS46XX
 --- Bootup diagnostics for card in PCI slot 00:03.1 ----
[  741.347349] PCI: Found IRQ 11 for device 0000:00:03.1
[  744.008849] PCI: Sharing IRQ 11 with 0000:00:03.1

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:03.1:
	Modem chipset  detected on
CLASS="Class 0700: 115d:000c"
NAME="Serial controller: Xircom Mini-PCI V.90 56k Modem"
SUBSYS=8086:2408
PCIDEV=115d:000c
IRQ=11
IDENT=Agere.DSP

 For candidate modem in:  00:03.1
   Class 0700: 115d:000c Serial controller: Xircom Mini-PCI V.90 56k Modem
      Primary device ID:  115d:000c
 Support type needed or chipset:	Agere.DSP
 

----------------end Softmodem section --------------

 The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset. 
Support packages for 2.6.n kernels are at:
 [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) , with current update martian-full-20071011.tar.gz

 See AgereDSP.txt for Details.


 Vendor 115d is XIRCOM, which was purchased by Intel
 The following devices have Lucent/AgereSystems DSP chipsets supported by the
 Martian variant of the AgereSystems ltmodem software.
 
    XIRCOM 0x115d          0x0000-0x000F
    XIRCOM 0x115d          0x0440-0x045c
    XIRCOM 0x115d          0x0010-0x03ff


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. When compiling ALSA drivers, the utility "patch" will also be needed.



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 15:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

pretty much the same but I downloaded the file already linked and have no clue what to do with it...

[EDIT] this is on Ubuntu 8.04 Hardy Heron from April 2008 un-updated

---

### Post by helmut_hed on 2008-05-11
Hi DoX,

Hopefully you now have a copy of this file:

[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz)

You want to "untar" it - i.e., liberate the various files from within it:

tar xzf martian-full-20080407.tar.gz

Then enter the resulting directory:

cd martian-full-20080407

and follow the directions in the INSTALL file.

Good luck,
Jeff

---

