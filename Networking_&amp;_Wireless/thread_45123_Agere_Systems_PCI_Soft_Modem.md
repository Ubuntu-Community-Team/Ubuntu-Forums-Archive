---
title: "Agere Systems PCI Soft Modem"
date: 2005-06-28
forum: Networking &amp; Wireless
---

### Post by Prudentissimus on 2005-06-28
Hello,

Here's what I got running scanModem:



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_June_24
------------ --------------  System information ------------------------
 Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 and later kernels.  Concerning code for:
Smartlink slmodem :
   slmodem-2.9.9d.tar.gz at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
      has the current fixes.  Related messages are:
   [http://www.datiku.com/documents/2610_migration.php](http://www.datiku.com/documents/2610_migration.php)
   [http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html) 
   [http://linmodems.technion.ac.il/archive-fourth/msg03736.html](http://linmodems.technion.ac.il/archive-fourth/msg03736.html) .
   [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  has an upgrab-winmodem.tar.gz,
       providing a driver to alleviate inappropriate capture of a winmodem by a serial port driver. 
Lucent/Agere DSP/ltmodem:
  [http://linmodems.technion.ac.il/archive-fourth/msg03733.html](http://linmodems.technion.ac.il/archive-fourth/msg03733.html) 
Concerning Intel-536ep and 537
   [http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto/) 
   [http://linmodems.technion.ac.il/archive-fifth/msg00280.html](http://linmodems.technion.ac.il/archive-fifth/msg00280.html)
   [http://linmodems.technion.ac.il/archive-fifth/msg00881.html](http://linmodems.technion.ac.il/archive-fifth/msg00881.html)
   
 The kernel was assembled with compiler:  3.3.5
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

A package kernel-kbuild-2.6.3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.10-5-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.10-5-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.10-5-386	   If not present on install CDs search
 FedoraCore4 kernel-devel-2.6.10-5-386
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.10-5-386		 , kernels are named k_deflt
One of which must be installed if compiling drivers to match kernel 2.6.10-5-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

Modem candidates are at PCI_buses:  0000:01:09.0
    
Providing detail for device at  0000:01:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:048c   Communication controller: Lucent Microelectronics V.92 56K WinModem (rev 03)
  SubSystem 11c1:044c   Lucent Microelectronics: Unknown device 044c
0000:01:09.0 0780: 11c1:048c (rev 03)
	Flags: bus master, medium devsel, latency 32, IRQ 5
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:048c 11c1:044c debian 2.6.10-5-386  3.3.5 3.3.5    i686

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
 

  Class 0703:  11c1:048c is still NOT supported under Linux, as of 2005_June_24
  It is a "software" modem without a digital signal processing (DSP) chipset.
  The ltmodem drivers from [http://ltmodem.heby.de](http://ltmodem.heby.de) resources for DSP modems do NOT provide support,
    A dialout terminates with "No Carrier" or a Hang if usage of the ltmodem drivers is attempted.


  ======= PCI_ID checking completed ====== 
 Update=2005_June_24
A PCMCIA CardBus is not detected on this System.
GCCversion=3.3.5
   
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
----active COMM services are ------------
eth1      Link encap:Ethernet  HWaddr 00:0E:A6:A4:17:65  
          inet6 addr: fe80::20e:a6ff:fea4:1765/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
 Be sure to read the Ethernet section of Modem/YourModem.txt 
DEVPPP=crw------- 1 root root 108, 0 2005-06-28 15:06 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
audit: initializing netlink socket (disabled)
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.

  Beginning with Fedora 2  kernel-2.6.6-1.427, kernel-headers needed 
  for compiling drivers are provide at: /lib/modules/kernel-version/build/
  Thus upgrading above kernel 2.6.5-1.358 to 2.6.6-* is Stongly Recommended
  
  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian is not yet providing pre-compiled drivers for WinModems




Please help.... What can I do, i have a Lucent DSP...


I need it to work on my Linux. Pleas help.

---

### Post by az on 2005-06-29
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

---

### Post by Prudentissimus on 2005-06-29
how do i do step 4....?

I've done steps 1 through 3.

---

### Post by az on 2005-06-29
You may not need to.

4. since the 2.6.10 kernels have some problems with these modules, put the following in the grub boot commands (at the place where it will get updated!): pci=routeirq Do not forget to update grub

sudo update-grub

Example:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro pci=routeirq

---

### Post by Prudentissimus on 2005-06-29
[QUOTE=azz]You may not need to.

4. since the 2.6.10 kernels have some problems with these modules, put the following in the grub boot commands (at the place where it will get updated!): pci=routeirq Do not forget to update grub

sudo update-grub

Example:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro pci=routeirq[/QUOTE]
 OK, now I can autodetect my modem /dev/modem

in the uh Networks...

So umm, do I have to put in the ACCESS number and Username password etc??? Do I have to configure my modem in Networks as to ACTIVATE it?

or do I leave the configs to PENGGY?

---

### Post by Prudentissimus on 2005-06-29
[QUOTE=Prudentissimus]OK, now I can autodetect my modem /dev/modem

in the uh Networks...

So umm, do I have to put in the ACCESS number and Username password etc??? Do I have to configure my modem in Networks as to ACTIVATE it?

or do I leave the configs to PENGGY?[/QUOTE]
 and umm now PENGGY detects /dev/lt**** something I couldn't remember

anyways...

WHen Penggy tries to dial the number 5298291, it says doesn't have dial Tone....

Please help...

---

