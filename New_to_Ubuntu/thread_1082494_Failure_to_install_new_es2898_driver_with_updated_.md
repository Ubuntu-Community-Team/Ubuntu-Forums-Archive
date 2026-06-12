---
title: "Failure to install new es2898 driver with updated kernel"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Whydoe on 2009-02-27
This has been discussed before here but I've been spinning my wheels trying to get it to work.  Basically, I'm stuck with dial-up with a modem driver that forces me to reinstall when I have to update the linux kernel.  I've no problem with that.  Ever since kernel version 2.6.24-22 came out it's caused an issue with the gcc compiler.  When I install this is part of the output...

checking for gcc...4.2.4
checking for kernel gcc version...4.2.3
** error
installed gcc version 4.2.4 does not match kernel gcc version 4.2.3

I've the latest driver (ess_2.6-v0.5) which I was waiting for.  I thought that would've fixed the problem.  But no.  Most threads pertain to the problem with VMware and gcc and most of that info suggests to ignore the problem and compile the install anyway.  I can't do that with this driver.  I've also tried to use Force Version in the package manager with no result.  

It's not a big issue.  I just revert back to kernel version 2.6.24-21 after I do a big update and the modem works.  But it would be nice to have a working modem with the latest kernel running.  

Is the solution out there or do I just need to be patient till they fix this minor issue?  Remember, I'm on dail-up.... I know patience.

---

### Post by Whydoe on 2009-03-01
This is the output from scanModem.  I thought running it again booting with the newest kernel would produce a different result and perhaps help. 

--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009
 scanModem update of:  2009_02_21

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 045e:001b Microsoft Corp. SideWinder Force Feedback 2 Joystick
 ID 03f0:4117 Hewlett-Packard 
 ID 1241:1177 Belkin F8E842-DL Mouse
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:0e.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0e.0	125d:2898		Communication controller: ESS Technology ES2898 Modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 00:0e.0 ----
[   26.319936] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

PCIbus=00:0e.0
00:0e.0 Communication controller: ESS Technology ES2898 Modem (rev 02)
	Flags: fast devsel, IRQ 10
	I/O ports at b400 [disabled] [size=8]
	Capabilities: [c0] Power Management version 1


=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:0e.0:
	Modem chipset  detected on
NAME="Communication controller: ESS Technology ES2898 Modem "
CLASS=0780
PCIDEV=125d:2898
SUBSYS=none
IRQ=10
IDENT=ESS.com

 For candidate modem in:  00:0e.0
   0780 Communication controller: ESS Technology ES2898 Modem 
      Primary device ID:  125d:2898
 Support type needed or chipset:	ESS.com
 

----------------end Softmodem section --------------
 ESS chipset 125d:2898 modems are supported. Read DOCs/ESScom.txt 

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.4


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-23-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
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


 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/70-ess.rules:KERNEL=="ttyS_ESS0", SYMLINK="modem"
/etc/udev/rules.d/00-hcfpci.rules:KERNEL=="ttySHCF0", SYMLINK="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/hcfpci:alias /dev/modem /dev/ttySHCF
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:
/etc/devfs/conf.d/hcfpci.conf:LOOKUP	^(ttySHCF[0-9]|modem$) EXECUTE nice /sbin/modprobe /dev/ttySHCF
/etc/devfs/conf.d/hcfpci.conf:REGISTER	^ttySHCF0$ CFUNCTION GLOBAL symlink $devname modem
/etc/devfs/conf.d/hcfpci.conf:UNREGISTER	^ttySHCF0$ CFUNCTION GLOBAL unlink modem
     Within ancient kernel 2.4.n /etc/module.conf files:
/etc/modules.conf:alias /dev/modem /dev/ttySHCF
--------- end modem support lines --------

Is there a way of forcing the install to use a different gcc version?  I tried cc=4.2.3 and other variants with the same result.

---

### Post by Whydoe on 2009-03-09
Well, I sorta figured it out.  I didn't wreck my installation.  I had to download the gcc-4.2_4.2.3-2ubuntu7_i386.deb file and install it using Term.  Would not install using the menu driven package installer because it's an older version.  Even though other dependencies were not met (old version of cpp and other files were not there) it still allowed me to install the driver for my modem.  After updating my system to the latest kernel, nvidia driver, and such, I just reinstalled gcc 4.2.4 and the broken dependencies were gone.  However, unless they fix this issue, I'll have to do these steps over again with a new kernel version.

---

### Post by helmut_hed on 2009-09-04
Just noticed this thread...  actually this is a general problem with compiling any kernel module, not just the ESS driver.  The compiler used to compile the kernel module and the compiler used to compile the kernel itself need to be the same version, or there can be bad internal problems (kernel crashes, etc.) sometimes.  In the past Ubuntu has sometimes shipped kernels compiled with gcc versions different from the those on the system itself.  Looks like it's happening again?

---

