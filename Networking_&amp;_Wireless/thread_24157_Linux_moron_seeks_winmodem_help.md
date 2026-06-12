---
title: "Linux moron seeks winmodem help"
date: 2005-04-05
forum: Networking &amp; Wireless
---

### Post by subinfinity on 2005-04-05
Apologies in advance;  I'm sure this topic has been beaten to death in other posts, but I'm having trouble finding the information that I need.

I installed ubuntu, and it didn't detect my winmodem, so I've been digging around the linmodem stuff on the internet, and it all kind of makes my brain hurt.  I did run scanModem, and this is what I got:



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_March_27
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 with current System compiler GCC=3.3.4
    /usr/bin/gcc -> gcc-3.3

Checking for kernel-headers needed for compiling.
 kernel-headers have base folder /lib/modules/2.6.8.1-3-386/build
 kernel-headers have base folder /usr/src/linux-headers-2.6.8.1-3-386

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:01:0e.0
    
Providing detail for device at PCI_bus 0000:01:0e.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:044c   Communication controller: Lucent Microelectronics LT WinModem (rev 02)
  SubSystem 11c1:044c   Lucent Microelectronics LT WinModem
	Flags: bus master, fast Back2Back, medium devsel, latency 64, IRQ 10
	Memory at f4100000 (32-bit, non-prefetchable)
	I/O ports at 3400 [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian 2.6.8.1-3-386 3.3.4 3.3.4    i686

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

      
 A suitable installer is not available as of this 2005_March_27 update.
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

 The list of available Installers for debian as of this 2005_March_27
 is inserted into to Modem/General.txt
  ======= PCI_ID checking completed ====== 
 Update=2005_March_27
A PCMCIA CardBus is not detected on this System.
   
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
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
Local APIC disabled by BIOS -- reenabling.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
  debian is not yet providing pre-compiled drivers for WinModems



So what next?  Am I going to have to fool around with compiling?  What do I have to download?  What do I have to do to get this damn thing to work?  I'm very new to linux, and this has all been very frustrating.  

Please help.

---

### Post by m4ng0 on 2005-04-05
You have a Lucent Winmodem with a DSP. Install linux-restricted-modules package from Synaptic and it should work (the module for your modem is ltmodem).

---

### Post by az on 2005-04-05
It is not lt_modem?

sudo lsmod
To see if it automatically loaded by hotplug.

sudo modprobe lt_modem
To load it.

sudo tail /var/log/messages
To see if there is anything funky going on once it loads.

---

### Post by subinfinity on 2005-04-05
Urgh.  Couldn't find ltmodem in synaptic... according to the description, linux-restricted-modules had madwifi, fglrx, and nvidia... no mention of ltmodem.  Did lsmod...  lt_modem was not listed...  Did modprobe, got a FATAL:  Module not found.  Apparently I don't have the ltmodem module...  I'm guessing I'm going to have to download and compile it..?  What now?  8-[

---

### Post by az on 2005-04-05
Can you install Hoary?

---

### Post by subinfinity on 2005-04-06
I could... If I had a high speed connection.  I did order the cd, but that's another few weeks of waiting...

---

### Post by m4ng0 on 2005-04-06
This worked for me in Warty:
1. download [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7.tar.bz2)
2. install from Synaptic:
   linux-headers for your kernel
   build-essential
3. unpack the tar.bz2, enter the directory and type
   make
   you will get ltmodem.ko and ltserial.ko
4. type
   sudo mkdir /lib/modules/`uname -r`/other
   sudo cp *.ko /lib/modules/`uname -r`/other
5. create /etc/modutils/ltmodem:
    sudo gedit /etc/modutils/ltmodem
    and write these lines in it:
alias /dev/modem ltserial
alias char-major-62 ltserial
alias /dev/tts/LT0 ltserial
6. type:
    sudo update-modules
7. type:
    sudo cp docs/ltmodem.rules /etc/udev/rules.d/
8. load the module:
    sudo modprobe -v ltserial
9. check if it was loaded:
    lsmod | grep lt
10. create your connection:
    sudo pppconfig

---

### Post by subinfinity on 2005-04-06
I followed your instructions to the letter, and I'm still having weird issues...  pppconfig doesn't autodetect the modem and says I have to specify it manually... and I don't know which port it's on, or if it's a symolic link, or any of that...  Whenever I go to Networking in system configuration and click activate, it does in fact dial out, and I hear all the modem squeals and hisses, but when I try using firefox, it says that any website I enter can't be found...

So close and yet, so far.
 ](*,)

---

### Post by m4ng0 on 2005-04-07
You should use pppconfig specifying /dev/modem as device if you have it (you should have it, when ltserial is loaded it creates it) or, if you don't have /dev/modem, specify /dev/ttyLT0.
Then, remember to use DNS numbers given by your ISP. There is an option in pppconfig where you can choose to use DNS numbers provided by your ISP when connecting.

---

### Post by subinfinity on 2005-04-07
Ok... Went to pppconfig and fixed those probs... But now what?  Do I use pon?  wvdial?  set up a connection in networking?  when I tried pon, it said that the file 'provider' does not exist in etc/ppp/peers/, and plog said the file etc/chatscripts/provider file doesn't exist.  I looked, and there is a provider.bak in both directories....

Where to now, boss? :confused:

---

### Post by az on 2005-04-07
If you have a connection named provider, 
pon 
will dial it.

If you have a connection named "internet" you would need to do
pon internet

---

### Post by subinfinity on 2005-04-09
When I did pppconfig, I named the connection 'provider' but for some bizarre reason it didn't save a config file, it saved the config file as a backup.  I guess it's a minor wrench in the works, but it's a wrench nonetheless.  My god, this is so unbelievably head-splitting.  Allow me to vent for a moment:  I'm not a dumb person, I've used computers for most of my life, and have some aptitude with them.  Yet this whole episode has been utterly flummoxing.  How could someone with marginal intelligence and little or no computer experience ever be expected to navigate the vaguaries of source code, compilation, config files, symlinks, and all this arcane insanity?  And thus, the oft-repeated line:  If anyone ever hopes to compete with M$, then their shtuff has to be EASY.  But that's not going to change overnight, nor does it help me right now.  So sorry about the rant.  Back to the situation at hand:  What's going on?  What do I do next?

---

### Post by az on 2005-04-09
did you do sudo pppconfig.

You also have to tell it to save before quitting...

---

### Post by subinfinity on 2005-04-09
Yes and yes.  I ran pppconfig again, deleted the connection and reconfigured it, saved, etc.  and this time it saved correctly...  But I'm not out of the woods yet.  Tried pon, and it dialed and squealed, I opened firefox and tried to go to a website.  It said the website could not be found, and then hung up.  I did plog, and this is what I got:

:  No auth is possible
:  sent [LCP ConfRej id=0x9 <auth pap>]
:  sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x6d209e75> <pcomp> <accomp>]
:  rcvd [LCP ConfReq id=0xa <asyncmap 0x0> <magic 0x69085a0d> <pcomp> <accomp> <auth pap>]
:  No auth is possible
:  sent [LCP ConfRej id=0xa <auth pap>]
:  LCP:  timeout sending Config-Requests
:  Connection terminated.
:  Hangup (SUGHUP)
:  Exit.

?!?!??!!?!?!?

---

### Post by az on 2005-04-10
You are not connecting.  Not all ISP have the same authentification protocol.  Can you find out what yours'is?

---

### Post by subinfinity on 2005-04-10
O Happy Day!!!  Victory!!  Can it be?  I'm CONNECTED!!!!  In Ubuntu!!!  I'm writing this in firefox!!!  I'm so giddy!!!!    Endless thanks!!!!  Dare I be so jubilant?  Oh well, if something else goes wrong, I'll definately bring my questions here first.  


Many, many thanks. :grin:

---

### Post by az on 2005-04-11
What was the problem?

---

