---
title: "Scan Modem Setup"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by amdalex on 2007-02-23
Hi guys first of all I have a winmodem that I would like to get working under ubuntu 6.10. I did the modem scanner tool and I would like to have some more detailed instructions on how to setup my modem. I will show you guys modemdata.txt and maybe you guy could help me a little bit with how to get my modem working. Also I am pretty new to Linux so could you please keep the instructions simple.
Here is windmodem.txt

Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_Feb_21


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0b.0	134d:7891	134d:0001	Modem: PCTel Inc HSP MicroModem 56 

 Modem interrupt assignment and sharing: 
 11:       4478          XT-PIC  uhci_hcd:usb1, eth0

 --- Bootup diagnositcs for card in PCI slot 01:0b.0 ----
[17179572.252000] PCI: Enabling device 0000:01:0b.0 (0000 -> 0001)
[17179572.252000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  01:0b.0
   Class 0703: 134d:7891 Modem: PCTel Inc HSP MicroModem 56
      Primary PCI_id  134d:7891
 Support type needed or chipset:	PCTEL
 

    At [http://linmodems.technion.ac.il/pctel-linux](http://linmodems.technion.ac.il/pctel-linux)
 Get the pctel-0.9.7-9-rht-6.tar.gz
 Unpack under Linux with:
    tar zxf pctel*.tar.gz
 and read instuctions therein.
  Read Pctel.txt and Modem/YourSystem.txt for follow through guidance.

 Writing Pctel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 15:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options


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
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by amdalex on 2007-02-23
I downloaded and unpacked the driver but I can't get it to install. Here is the read me file. Maybe you could point me in the right direction to get the driver to install?
Here is the read me file which has the install instructions.

1. Installation
===============

1.1 Automatic installation (for beginners)
------------------------------------------
- You must be root
- You must have installed a c compiler and development tools like
  make, perl, ...
- You must have lspci in a standard path (for automated install)
- You must have installed your kernel sources, which corresponds
  to your current running kernel


a) tar zxvf pctel-version.tar.gz

b) cd pctel/

c) ./setup

If everything was ok, you will see the message "installation done" at the
end of the output.

1.2 Manual installation (for experts)
-------------------------------------
- You must be root for part (e), you can run (a)-(d) as an ordinary user if you
  wish
- You must have installed a C compiler and development tools like
  make, perl, ...
- You must have installed your kernel sources, which corresponds
  to your current running kernel


a) tar zxvf pctel-v.w.x-y-rht-z.tar.gz

b) cd pctel-v.w.x-y-rht-z/src/

c) ./configure -manual

d) make

e) make install


2. Try your driver
==================
Just to try out, if your driver works:

  2.4:                 2.6:
  insmod pctel         modprobe linmodem
  insmod ptserial      modprobe pctel
                       modprobe pctel_hw
  or

  insmod -f pctel
  insmod ptserial

-f means "force", which means, it will force loading the driver, even
with warnings.

then, look at:

lsmod

it should print pctel and ptserial (2.4) or linmodem, pctel and pctel_hw (2.6).

Look at the last few lines of dmesg to see whether the driver found the
modem or not:

dmesg | tail

If the driver is not finding the modem, and you have either a PCtel or
C-Media device you can try using the vendor_id and device_id arguments with
insmod(you can find these using lspci):

insmod ptserial vendor_id=0x1234 device_id=0x5678

Note that vendor_id and device_id do not work with Intel, Sis or Via devices.

3. Loading your driver permanently
==================================
NOT YET WRITTEN


Appendix I. PCI IDs of recognized modems
========================================
This table summarises the PCI devices that this driver supports.  For AC'97
modems, this does not guarantee that the driver will work, as this is only part
of the modem - the other part, the codec, must also be compatible for the
driver to work.

PCI ID (x)  Name                                       Chip(set)      HAL
~~~~~~~~~~  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  ~~~~~~~~~~~~~  ~~~~~~~
1039:7013*  SiS AC'97 Modem Controller                 SIS540 MR      sis
1106:3068*  VIA Intel 537 [AC97 Modem]                 VIA686A MR     via686a
134d:7890   PCtel HSP MicroModem 56                    PCT789T-C1     pct789
134d:7891   PCtel HSP MicroModem 56                    PCT 789T       pct789
134d:7892   PCtel HSP MicroModem 56                    PCT 789T-A     pct789
134d:7893   PCtel HSP MicroModem 56                    S911 K017      pct789
134d:7894   PCtel HSP MicroModem 56                    FT13           pct789
134d:7895   PCtel HSP MicroModem 56                    PCT789T-C1     pct789
134d:7896   PCtel HSP MicroModem 56                    PCT789T-C1     pct789
134d:7897   PCtel HSP MicroModem 56                    PCT789T        pct789
13f6:0211   C-Media CM8738                             CM8738         cm8738
8086:2416*  Intel 82801AA (ICHAA) AC'97 Modem          i810 MR        i8xx
8086:2446*  Intel 537 [82801BA/M (ICH2) AC'97 Modem]   i820           i8xx
8086:2486*  Intel 82801CA/M (ICH3) AC'97 Modem Ctlr    i845           i8xx
8086:24c6*  Intel 82801DB/M (ICH4) AC'97 Modem Ctlr    i855PN laptop  i8xx
8086:7196*  Intel 82440MX (Banister) AC'97 Modem Ctlr  i810 MR laptp  i8xx

* No 2.6 support - these modems are only suppoerted under 2.4 kernels.


Appendix II. Supported AC'97 Codecs
===================================
This version (3) supports the printing of AC'97 Codec Vendor IDs when compiled
with the "i8xx" HAL (hopefully the "sis" and "via686a" HALs will follow).  To
find out which codec your modem contains, you need to load "ptserial" (and
"pctel") modules and then start something like "minicom".  The codec vendor id
will be printed when the modem device is used (usually /dev/modem, symlinked
/dev/ttyS15 under 2.4 and /dev/ttyS_PCTEL0 under 2.6).  Look for a message
(using "dmesg | tail") of the form:

    Found codec SIL33 of type 2

The codec vendor id is "SIL33" (note that the number is in decimal - slamr
prints the same thing in hex - duh! - so this would equate to "SIL21").  This
indicates a Silicon Laboratories Si3038 codec, as used by PCTel.  The type 2
is an internal code, which catagorises the codec's compatability.  It has no
meaning outside of this driver.

The following codecs are recognised by the "i8xx" HAL (and presumably the other
AC'97 HALs as well):

Codec   Type  Codec Name
~~~~~~  ~~~~  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
DT2-49   1    (PCTel Delta?)
DT2-50   1    (PCTel Delta?)
SIL17    2    Silicon Laboratories Si???? (PCTel Stinger?)
SIL33    2    Silicon Laboratories Si3038 (PCTel)
TRA9     3    TriTech


Appendix III. ptserial Module Options
=====================================
The 2.4 "ptserial" module supports the following options:

Option          Meaning
~~~~~~~~~~~~~~  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
country_code=n  Sets the Country Code (see Appendix IV) to "n"
irq=n           Attempts to attach the device to IRQ "n"
iobase=n        Looks for a device at iobase address "n".

iobase1=n       Forces the driver to load for the device with the given iobase,
                iobase1 and irq.  "i8xx" and "via686a" HALs only

vendor_id=n     Forces the driver to load for the device with the given vendor
& device_id=n   and device ids.  "pct789" and "cm8738" HALs only


The 2.6 modules support the following options:

Option          Module    Meaning
~~~~~~~~~~~~~~  ~~~~~~~~  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
country_code=n  pctel     Sets the Country Code (see Appendix IV) to "n"
irq=n           pctel_hw  Attempts to attach the device to IRQ "n"


Appendix IV. Country Codes
==========================

Code  Country         Code  Country         Code  Country
~~~~  ~~~~~~~~~~~~~   ~~~~  ~~~~~~~~~~~~~   ~~~~  ~~~~~~~~~~~~~~~
  1   USA              12   KOREA            23   DENMARK        
  2   FRANCE           13   SWITZERLAND      24   AUSTRIA        
  3   GERMANY          14   NORWAY           25   S.AFRICA       
  4   ITALY            15   NETHERLANDS      26   CTR21 COUNTRIES
  5   SWEDEN           16   BELGIUM          27   CHINA          
  6   UK               17   CANADA           28   MALAYSIA       
  7   JAPAN            18   IRELAND          29   LUXUMBURG      
  8   AUSTRALIA        19   PORTUGAL         30   GREECE         
  9   SPAIN            20   POLAND           31   ICELAND        
 10   TAIWAN           21   HUNGARY          32   NEW ZEALAND    
 11   SINGAPORE        22   FINLAND          33   BRAZIL         


$Id: README,v 1.12 2006/04/04 14:45:04 robert Exp $

Sorry for the long posts I just want you guys to see everything.:(

---

### Post by amdalex on 2007-02-23
Bump

---

