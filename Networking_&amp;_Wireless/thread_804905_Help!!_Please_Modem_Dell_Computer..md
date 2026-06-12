---
title: "Help!! Please Modem Dell Computer."
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by littlegecko2 on 2008-05-23
Ok this is what the scanmodem tool said, but I don't know what to do with it. Its hard to read now, but I saved it on my flash drive and I'm posting it below. I need help getting my air card to connect. Its a express card, but has a USB adapter that uses both ports. 

Thanks, 

Tiffany 
[email]Tiffany_Lea@hotmail.com[/email] on MSN Messenger. (Not Online right now).


________________________________________________________________

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_05_02

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 05dc:a560 Lexar Media, Inc. 

USB modems not recognized
For candidate card in slot 00:1f.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	14f1:5422	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
  5:     559257    XT-PIC-XT        ipw2200, Intel 82801DB-ICH4
 --- Bootup diagnostics for card in PCI slot 00:1f.6 ----
[   10.253505] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   10.253515] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

 The PCI slot 00:1f.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are:


The /proc/asound/pcm file reports:
-----------------------
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9752,53 at irq 5
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1f.6:
	Modem chipset  detected on
CLASS="Class 0703: 8086:24c6"
NAME="Modem: Intel Corporation 82801DB/DBL/DBM "
SUBSYS=14f1:5422
PCIDEV=8086:24c6
IRQ=5
SOFT=8086:24c6.MC97
CodecArchived=CXT
CodecClass=CXT
IDENT=hsfmodem
Driver=hsfmodem_drivers

 For candidate modem in:  00:1f.6
   Class 0703: 8086:24c6 Modem: Intel Corporation 82801DB/DBL/DBM 
      Primary device ID:  8086:24c6
    Subsystem PCI_id  14f1:5422 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: CXT, a Conexant type using hsfmodem software.
      CXTnn is  a generic for all CXTnumbers, with  Linuxant hsfmodem software support.                  
      

Support type needed or chipset:	hsfmodem


Writing Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.07full_k2.6.24_16_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


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

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1
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

_________________________________________________________________

---

### Post by Ayuthia on 2008-05-23
You will probably want to follow this portion of your scanModem results:

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

From [http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php)
download hsfmodem-7.68.00.07full_k2.6.24_16_generic_ubuntu_i386.deb. zip
Under Linux unpack with:
$ unzip hsfmodem*.zip
Then install with:
$ sudo dpkg -i hsfmodem*.deb
Subsequently, the modem should be found with
$ sudo wvdialconf /etc/wvdial.conf
Edit in your personal information with:
$ sudo gedit /etc/wvdial.conf
and try dialing out with:
$ sudo wvdial.
See Testing.txt for details.

---

### Post by littlegecko2 on 2008-05-24
Thanks, I'm going to try that. But I may need help. Im very new to ubuntu. I'm on MSN messenger. [email]Tiffany_Lea@hotmail.com[/email]

I'm at work today but its slow and I have my laptop and interent on this computer.

Thanks, 

for the help.

---

### Post by littlegecko2 on 2008-05-24
I tried that and it said Same Verison is already installed. When I run GnomePPP and go to setup under Modem I click on Detect. It says "No modem was found on your system." I've tried changing it too USB Modem(which is how the air card it hooked up.) Its an express card air card, with usb adapter. Also on Analog Modem and ISDN modem. I really need some higher tech help. I called alltel and looked on the kyocera web site. I don't know if its a driver thing from alltel or kyocera/ or a modem driver in general on my laptop.

Thanks,
[email]Tiffany_Lea@hotmail.com[/email] on MSN messenger

---

