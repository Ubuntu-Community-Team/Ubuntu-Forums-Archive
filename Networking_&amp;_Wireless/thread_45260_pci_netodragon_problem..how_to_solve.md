---
title: "pci netodragon problem..how to solve"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by phyz on 2005-06-29
i have a problem which is afther i scanModem...




DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_April_19
------------ --------------  System information ------------------------
Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 kernels.  Concerning code for:
Smartlink slmodem :
   slmodem-2.9.9b.tar.gz at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html) 
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) . 
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html) 
Concerning Intel-536ep and 537
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)
   
 The kernel was assembled with compiler:  3.3.5
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.10-5-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
 Ubuntu 		linux-headers-2.6.10-5-386		[http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories](http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories)
    Debian & Ubuntu will also require kernel-kbuild package installation
 Mandrake 	kernel-source-2.6.10-5-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		linux-2.6.10-5-386				, ????  , kernels are named k_deflt
One of which must be installed if compiling drivers to match kernel 2.6.10-5-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 Modem symbolic link is:  /dev/modem -> ttySL0
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:01:00.0
    
Providing detail for device at PCI_bus 0000:01:00.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 10b9:5459   Modem: ALi Corporation SmartLink SmartPCI561 56K Modem (prog-if 00 [Generic])
  SubSystem 10a5:5459   Smart Link Ltd.: Unknown device 5459
0000:01:00.0 0703: 10b9:5459
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c000 [size=256]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5459 10a5:5459 debian 2.6.10-5-386 3.3.5     i686


 SmartLink drivers support this modem:
    10b9:5459  ALI 5459 SmartPCI561
 10b9:5459  Subsystem: 10a5:5459  ALi Corporation SmartLink SmartPCI561 56K Modem (NetoDragon)
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 
 10b9:5459 ALI545A SL1801 and 10b9:5459  ALI 5459 SmartPCI561 have SmartLink chipsets.


 These messages may aid setup of soft modems under 10b9:M5457 controllers:
   [http://linmodems.technion.ac.il/archive-third/msg02518.html](http://linmodems.technion.ac.il/archive-third/msg02518.html)
   [http://linmodems.technion.ac.il/archive-third/msg02100.html](http://linmodems.technion.ac.il/archive-third/msg02100.html)
 The slmodem-2.9.9 support was developed for 10b9:5459,
   but there a range of reports the related 10b9:5457 modemd controllers:
     fully functional;
     functional only after a power on reboot from Microsoft windows;
     hang/crash upon initiation of modem usage.
 
 10b9:5457   Modem: ALi Corporation [M5457 AC-Link Modem] 
 SubSystem 1179:0001   Toshiba America Info Systems: Unknown device 0001
 has an AgereSoftModem chip which may be supported by the Smartlink slmodem-2.9.9 driver 
     

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) ,
  but [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) has older packages and new fixes.
      For the emerging 2.6.10 kernels, use the slmodem-2.9.9b.tar.gz  therefrom.
 Read Slmodem.txt  for details.
   

  ======= PCI_ID checking completed ====== 
 Update=2005_April_19
A PCMCIA CardBus is not detected on this System.
GCCversion=
   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt
DEVPPP=crw------- 1 root root 108, 0 2005-06-29 21:01 /dev/ppp

  The current modem symbolic link is: /dev/modem -> ttySL0
  The ports /dev/ttyS0 or 1,2,3 are for standard Controller chip modems


 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
audit: initializing netlink socket (disabled)
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
  debian is not yet providing pre-compiled drivers for WinModems




1)what should i do to solve this problem and be able to dail up using pci modem?
2)how can i change the baut rate manually?

---

### Post by az on 2005-06-29
1) [https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

2) Forget about the baud rate.

---

