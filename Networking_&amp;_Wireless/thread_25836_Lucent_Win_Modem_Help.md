---
title: "Lucent Win Modem Help"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by dfghost on 2005-04-11
I have Windows, and just installed Ubuntu Warty a week ago.  I finally got everything set up, except for the modem.  I downloaded juno.deb from juno.com.  I set it up, set all the user permissions to rwx/ group -dialout.  I then double clicked it and nothing happened.  So i went to computer > sys config > network.  I set up a modem and tried autodetect, but it said "can't find any modem." I have a Lucent Win Modem (tried to install some drivers, but didn't work!) and i know from windows XP that it's on com 3.  I tried soflinking /dev/modem to ttyS2 and hit Juno Internet (execute file on desktop from juno.deb) and nothing happened.  So, do i need a driver? (if so, what type. Link would be good).  Do i need to run a special setup, or what?  I've tried alot of stuff on these forums and nothing seems to have worked.  Any suggestions?  Thanks, in advance.

---

### Post by az on 2005-04-11
Try loading the lt_modem modules from linux-restricted-modules

sudo modprobe lt_modem

---

### Post by dfghost on 2005-04-12
I tried that, returned error: no module found.  Looked around the forums and found your scanmodem post.  Tried that, didn't work.  Followed it to the letter.  No ttLTM0 nor modem came up in dev.  Nothing happened when i autodetected.  Pasted below is the %cat ScanModem.txt file that was in the istructions.  Hope it helps.  Thanks.  (note: when ubuntu loads, I get some pci loading errors (3) from modprobe about not being able to load blah.  Could that have something to do with it - my modem is on PCI bus?)

--------------------------------------------------------------------------------------------------------

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_April_9
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.8.1-3-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
 Ubuntu 		linux-headers-2.6.8.1-3-386		[http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories](http://www.ubuntulinux.org/community/ConfigUbuntu5.04%20repositories)
 Mandrake 	kernel-source-2.6.8.1-3-386		[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/)  and other mirrors
  SuSE		linux-2.6.8.1-3-386				, ????
One of which must be installed if compiling drivers to match kernel 2.6.8.1-3-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:01:0b.0
    
Providing detail for device at PCI_bus 0000:01:0b.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:044c   Communication controller: Lucent Microelectronics LT WinModem (rev 02)
  SubSystem 11c1:044c   Lucent Microelectronics LT WinModem
	Flags: bus master, medium devsel, latency 64, IRQ 201
	Memory at cd800000 (32-bit, non-prefetchable) [disabled]
	I/O ports at b400 [disabled] [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian 2.6.8.1-3-386 3.3.4     i686

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:044c
 DSP=1

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html)
 0x044c -- Mars 3 Perseus data/fax only:North America and Global board
 0x044c -- Mars 3.2 Mercury data fax only when no eeprom is present, North America DAA

 Support has been extended to 2.6.n kernels by Rajesh K. Balan and
 Aleksey Kondratenko <alk@tut.by>, with official support from AgereSystems later following.
 Functionality requires serial_core support, either as a module or integral to the kernel.
 
 The ltmodem-2.6-alk-7.tar.bz2 can be downloaded from:
   [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) 
   with low bandwidth alternate: [http://alk.at.tut.by/ltmodem-2.6-alk-7.tar.bz2](http://alk.at.tut.by/ltmodem-2.6-alk-7.tar.bz2)
   There are detailed instructions in  [http://linmodems.technion.ac.il/archive-fifth/msg00584.html](http://linmodems.technion.ac.il/archive-fifth/msg00584.html)
   
   For kernels prior to 2.6.11, the resources at [http://ltmodem.heby.de](http://ltmodem.heby.de) can be utilized.
   
   If service cannot be established under an SMP kernel, try a uniprocessor kernel instead.  See:
   [http://linmodems.technion.ac.il/archive-fifth/msg01278.html](http://linmodems.technion.ac.il/archive-fifth/msg01278.html)



 Add either of the following lines to the Debian  /etc/apt/sources.list
 to enable automatic updates on installer availability:
   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
   deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


  The desired installer name is like:
========================================
ltmodem-2.6.8.1-3-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.8.1-3-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31a9, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.

      
 A suitable installer is not available as of this 2005_April_9 update.
 Check in the section debian at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31a9.tar.gz compiler kit.

 The list of available Installers for debian as of this 2005_April_9
 is inserted into to Modem/General.txt
  ======= PCI_ID checking completed ====== 
 Update=2005_April_9
A PCMCIA CardBus is not detected on this System.
GCCversion=
   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01178.html](http://linmodems.technion.ac.il/archive-fifth/msg01178.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias tty-ldisc-3  ppp_async  
/etc/modprobe.d/aliases:alias tty-ldisc-14 ppp_synctty
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
/etc/modprobe.d/aliases:alias ppp-compress-21 bsd_comp   
/etc/modprobe.d/aliases:alias ppp-compress-24 ppp_deflate
/etc/modprobe.d/aliases:alias ppp-compress-26 ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:CC:5A:97  
          inet6 addr: fe80::20c:6eff:fecc:5a97/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/General.txt
 Be sure to read the Ethernet section of Modem/General.txt 

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by az on 2005-04-13
Ah.  You are running Warty.  I should have noticed that!  (There are more than 500 posts per day...) The drivers are included in Hoary, you will have to compile them yourself for Warty.

Is it possible to download and burn a Hoary disk and upgrade to that?  That would be the simplest way...

---

### Post by dfghost on 2005-04-13
I have dial up, so it would take a long time to download.  Hoary isn't a convenient option for me.  So, how would i go about compiling a driver for my modem on ubuntu?

---

### Post by Maniak on 2005-04-14
dfghost,

Have a look at this thread - [http://ubuntuforums.org/showthread.php?t=20546](http://ubuntuforums.org/showthread.php?t=20546) . We managed to get our modems going on Warty.

And I hear your pain on dial-up!! I am waiting for the new CDs or finding someone on broadband.....

---

### Post by dfghost on 2005-04-16
Warty isn't really working for me.  So, I got a friend to download it and burn it to a CD for me.  I'll attempt the installation tonight.  Hope it works.  I'll let you know tommorrow.

---

### Post by dfghost on 2005-04-17
k, i installed hoary, java, juno.  Tried the sudo modprobe lt_modem (worked), and ln -s ttyS2 modem (didn't work).  Now what do i do?  I know from windows that my modem is on Com 3, and that juno only uses /dev/modem so you need to create a link to it.  But where is the driver or modem module.  When i try to autodetect, it says there is none attached.  What's going on here?

---

### Post by az on 2005-04-17
" ln -s ttyS2 modem (didn't work)."

The device created by the ltmodem driver is  /dev/ttLTM0

See here:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

### Post by dfghost on 2005-04-19
[QUOTE=azz]" ln -s ttyS2 modem (didn't work)."

The device created by the ltmodem driver is  /dev/ttLTM0

See here:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)[/QUOTE]
 So i have to instal the driver, even though i'm now on hoary?  I thought that it had the needed drivers to work Winmodems now.

---

### Post by az on 2005-04-19
[QUOTE=dfghost]So i have to instal the driver, even though i'm now on hoary?  I thought that it had the needed drivers to work Winmodems now.[/QUOTE]

The drivers are compiled for you.  They are in linux-restriced-module sin Hoary..  You just need to load them.  

Put lt_serial and lt_modem in /etc/modules in order to get the modules loaded on boot. The modem device will appear as /dev/ttLTM0 (that is a zero at the end).

---

### Post by dfghost on 2005-04-22
[QUOTE=azz]The drivers are compiled for you.  They are in linux-restriced-module sin Hoary..  You just need to load them.  

Put lt_serial and lt_modem in /etc/modules in order to get the modules loaded on boot. The modem device will appear as /dev/ttLTM0 (that is a zero at the end).[/QUOTE]
 Didn't work, autodetect still doesn't detect it, and a symlink to modem, and then using Juno doesn't work either.  Do i need to do something else, the node ttLTM0 appeared, but doesn't do anything.  Do i have to compile my own driver?

---

### Post by dfghost on 2005-06-30
well, i got tired of it and switched to DSL, yeah.  Thanks azz

---

### Post by a020000591 on 2005-07-30
[QUOTE=dfghost]I have Windows, and just installed Ubuntu Warty a week ago.  I finally got everything set up, except for the modem.  I downloaded juno.deb from juno.com.  I set it up, set all the user permissions to rwx/ group -dialout.  I then double clicked it and nothing happened.  So i went to computer > sys config > network.  I set up a modem and tried autodetect, but it said "can't find any modem." I have a Lucent Win Modem (tried to install some drivers, but didn't work!) and i know from windows XP that it's on com 3.  I tried soflinking /dev/modem to ttyS2 and hit Juno Internet (execute file on desktop from juno.deb) and nothing happened.  So, do i need a driver? (if so, what type. Link would be good).  Do i need to run a special setup, or what?  I've tried alot of stuff on these forums and nothing seems to have worked.  Any suggestions?  Thanks, in advance.[/QUOTE]
 Check in the section debian at [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
for a subsequent Installer submission.
If you need Conexant modem drivers, that company does not care as much about it's open source software customers.I`m go in

---

