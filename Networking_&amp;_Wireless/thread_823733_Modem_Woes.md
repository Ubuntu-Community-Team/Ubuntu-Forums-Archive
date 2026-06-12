---
title: "Modem Woes"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by TK425 on 2008-06-09
I know, I know. Don't worry, I've done a little research, but I'm just a little confused.

Right now I have Ubuntu installed on a machine that has a softmodem (separate piece of hardware), Silicon Integrated Systems [SiS] AC'97, in the computer.

I did the hardware scan with scanModem, but I'm not sure what I'm supposed to be looking for. Apparently I'm supposed to find the driver and install it somehow? ..A little help with this would really be appreciated. Thanks.

```
 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_06_05

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive

USB modems not recognized

For candidate card in slot 00:02.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:02.6	1039:7013	1039:7013	Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller 

 Modem interrupt assignment and sharing: 
 10:       2923    XT-PIC-XT        SiS SI7012, eth0, SiS SI7013 Modem
 --- Bootup diagnostics for card in PCI slot 00:02.6 ----
[   22.360871] PCI: Found IRQ 10 for device 0000:00:02.6
[   27.033679] PCI: Sharing IRQ 10 with 0000:00:02.6
[   62.662502] PCI: Sharing IRQ 10 with 0000:00:02.6
[ 6125.199206] PCI: Found IRQ 10 for device 0000:00:02.6


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-01: Intel ICH - MIC ADC : SiS SI7012 - MIC ADC : capture 1
00-00: Intel ICH : SiS SI7012 : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC101 at irq 10
===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: 
card 1: Modem [SiS SI7013 Modem], device 0: Intel ICH - Modem [SiS SI7013 Modem - Modem]

The /proc/asound/pcm file reports:
-----------------------
00-01: Intel ICH - MIC ADC : SiS SI7012 - MIC ADC : capture 1
00-00: Intel ICH : SiS SI7012 : playback 1 : capture 1
01-00: Intel ICH - Modem : SiS SI7013 Modem - Modem : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC101 at irq 10
 1 [Modem          ]: ICH-MODEM - SiS SI7013 Modem
                      SiS SI7013 Modem at irq 10
 The modem codec file for the HDA card is: 1
--------------------------------------------------------


 The audio card hosts a softmodem chip:  0x11c11040

 The softmodem chip 0x11c11040 is only supported currently under Red Flag kernel 2.6.21-20
 Read DOCs/InfoGeneral.txt about alternative modem hardware.
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:02.6:
	Modem chipset  detected on
CLASS="Class 0703: 1039:7013"
NAME="Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller "
SUBSYS=1039:7013
PCIDEV=1039:7013
IRQ=10
SOFT=1039:7013.MC97
CodecArchived=SIL21
CHIP=0x11c11040
IDENT=slmodemd

 For candidate modem in:  00:02.6
   Class 0703: 1039:7013 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller 
      Primary device ID:  1039:7013
    Subsystem PCI_id  1039:7013 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: SIL21, a Pctel type
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:	slmodemd

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

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
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,
 linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 
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
	-rwsr-xr-- 1 root dip 269256 2007-10-04 14:57 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
```

---

