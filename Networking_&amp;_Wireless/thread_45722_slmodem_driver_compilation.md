---
title: "slmodem driver compilation"
date: 2005-07-01
forum: Networking &amp; Wireless
---

### Post by kagashe on 2005-07-01
Hi,

I downloaded scanmodem and run it. Modem.txt indicates that it is slmodem. It is asking me to download slmodem-2.9.9d.tar.gz which I have done.

It seems that I have to compile this driver for which following is required:
> The kernel was assembled with compiler:  3.3.5
 a gcc-3.3.5  package must be installed to support driver compiling

A package kernel-kbuild-2.6.3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.

Please help me with these things so that I can compile the modem driver.

kagashe

---

### Post by az on 2005-07-01
[https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

---

### Post by kagashe on 2005-07-01
I have already downloaded and tried after installating these packages on:
[https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

It is not working. I am not sure whether what I have is a smartlink or PCtel modem because in WindowsXP it shows as a Smartlink modem but PCtel drivers are installed.

I am now reproducing the ModemData.txt file from scanmodem below and please tell me what to do.
>  DO use the following line as the email Subject Line, to alert cogent experts:
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
 a gcc-3.3.5  package must be installed to support driver compiling

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

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

Modem candidates are at PCI_buses:  0000:01:01.0
    
Providing detail for device at  0000:01:01.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 134d:2189   Modem: PCTel Inc: Unknown device 2189 (rev 04) (prog-if 00 [Generic])
  SubSystem 134d:1002   PCTel Inc: Unknown device 1002
0000:01:01.0 0703: 134d:2189 (rev 04)
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 21
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 134d:2189 134d:1002 debian 2.6.10-5-386  3.3.5 none    i686

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==
 Under 2.6.n kernels, there is NO support for this Pctel modem.
 Read ModemData.txt  and Pctel.txt in the new sub-folder Modem/
 The 134d:2189 is a PCTel 688T modem which is currently NOT supported see:
	[http://linmodems.technion.ac.il/archive-fifth/msg00057.html](http://linmodems.technion.ac.il/archive-fifth/msg00057.html)

  ======= PCI_ID checking completed ====== 
 Update=2005_June_24
A PCMCIA CardBus is not detected on this System.
GCCversion=none
   
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
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
DEVPPP=crw------- 1 root root 108, 0 2005-07-01 19:08 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
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

kagashe

---

### Post by alastair on 2005-07-02
This appears to say it is "Pctel", and unsupported ...

```
 == Checking PCI IDs through modem chip suppliers ==
Under 2.6.n kernels, there is NO support for this Pctel modem.
Read ModemData.txt and Pctel.txt in the new sub-folder Modem/
The 134d:2189 is a PCTel 688T modem which is currently NOT supported see:
http://linmodems.technion.ac.il/arc...h/msg00057.html
```

Unless someone else has a bright idea.

To try anyway, you'll need to have a compiler and kernel headers e.g. install :

build-essential
linux-headers-2.6.10-5-386

---

### Post by kagashe on 2005-07-02
> Unless someone else has a bright idea.

To try anyway, you'll need to have a compiler and kernel headers e.g. install :

I think when I have already tried with the instructions on this page:
[https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

compiling it may produce the same results unless it is a driver with a different version. Now I have a question here.
The driver on wiki.ubuntu is sl.modem.daemon_2.9.9a whereas linmodem site has version 2.9.9d
It appears to me that it is a different version.

However, I have extensively serched the archive on linmodem site and find that they are looking for a volunteer who is proficient in c++ to develop the driver under expert guidance. Look at the post below:
[http://linmodems.technion.ac.il/archive-fifth/msg02734.html](http://linmodems.technion.ac.il/archive-fifth/msg02734.html)

They are looking for a person for more than 6 months now:
[http://linmodems.technion.ac.il/archive-fifth/msg00057.html](http://linmodems.technion.ac.il/archive-fifth/msg00057.html)

I hope someone can come foreward to help me and other users of this modem (there are so many posts on linmodem site).

kagashe

---

### Post by mingus on 2005-08-15
There are minor differences between 2.9.9a and the latest 2.9.9e.  I found 2.9.9a better because there is the sl-modem-daemon package to go with it.

From other threads, looks like a pctel driver is a problem.  Apparently this is a AC97 modem which is why slmodem is being suggested; slmodem operates with the slamr driver for the smartlink chipset but also an Alsa driver (snd_intel8x0).  Slamr can only be loaded if the smartlink chipset is present, so the init script at boot checks for this and if it is not there, loads the Alsa driver instead.  You should see this in your boot messages and in shutdown.  Sometimes it is also necessary to edit the script's config file /etc/default/sl-modem-daemon, change the device from "auto" to "hw:0" or "hw:1" (try both).

---

### Post by kagashe on 2007-05-03
Hi,

After installing Feisty on this Desktop I have downloaded and run the scanmodem utility once again and the output of the file ModemData.txt is as follows:
 > Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_April_23


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:01.0	134d:2189	134d:1002	Modem: PCTel Inc HSP56 MicroModem

 Modem interrupt assignment and sharing: 
 16:      92210   IO-APIC-fasteoi   eth0

 --- Bootup diagnositcs for card in PCI slot 01:01.0 ----
[   14.713311] PCI: Cannot allocate resource region 0 of device 0000:01:01.0
[   14.713314] PCI: Cannot allocate resource region 1 of device 0000:01:01.0
[   15.947917] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 16

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  01:01.0
   Class 0703: 134d:2189 Modem: PCTel Inc HSP56 MicroModem
      Primary PCI_id  134d:2189
 Support type needed or chipset:	slamr
 

 134d:2189  is a PCTel HSP56 MicroModem 688T modem with the Oasis chipset.
 Under 2.6.n kernels, it is only supported through the Smartlink slamr.ko driver.

The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 09:11 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

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

It seems the modem is now supported:
> 134d:2189  is a PCTel HSP56 MicroModem 688T modem with the Oasis chipset.
 Under 2.6.n kernels, it is only supported through the Smartlink slamr.ko driver.

The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

How to procced?

kagashe

---

### Post by Matchless on 2007-05-04
Have a look here maybe it will help [http://132.68.73.235/linmodems/pctel-linux/](http://132.68.73.235/linmodems/pctel-linux/)

---

### Post by boon on 2007-05-05
Kagashe,

have you subscribed to the linmodems.org mailing list?

I think that is the best place to post the output of the scanModem utility and to ask for questions on what to do next. They are the experts.

---

### Post by kagashe on 2007-05-05
> **boon said:**
> Kagashe,

have you subscribed to the linmodems.org mailing list?

I think that is the best place to post the output of the scanModem utility and to ask for questions on what to do next. They are the experts.Yes. I have received their first reply and compiled the modules ungrab-winmodem and slamr, however, it is not working. I get the following messages:
> [ 6048.558867] slamr: SmartLink AMRMO modem.
[ 6048.559564] slamr: probe 134d:2189 SL1900 card...
[ 6049.617526] slamr: cannot init card.
[ 6330.584710] slamr: SmartLink AMRMO modem.
[ 6330.585618] slamr: probe 134d:2189 SL1900 card...
[ 6331.633887] slamr: cannot init card.
I have sent another mail to the list just now.

There is not much on the list if I search with "688T". At least there is no success reported for this modem.

kagashe

---

### Post by Matchless on 2007-05-09
I think you may be flogging a dead horse here! You may have to dump your modem or swop it with a Windows user. That is the only other advice I can unfortunately give you.

---

### Post by boon on 2007-05-09
> I think you may be flogging a dead horse here! You may have to dump your modem or swop it with a Windows user. That is the only other advice I can unfortunately give you.
__________________
Regards,
Matchless


Not necessarily! With the help of the linmodems.org site and their maillist, I have got my winmodem working successfully under feisty.

In the case of some winmodems, free software drivers are not available, but again, the linmodems.org folks are most likely to be able to give you an authoritative answer on this.

---

### Post by _duncan_ on 2007-05-09
I agree with Matchless.

134d:2189 is a PCTel modem based on the Oasis chipset. I bumped into this type of modem while helping a friend get dial-up connection with Ubuntu. I couldn't get it to work despite being relatively familiar with the smartlink linux driver.

After a month of chasing dead-ends, i finally prevailed upon my friend to go to the nearest computer shop and grab another modem with a smartlink chipset for 5 US dollars. It took all of 15 minutes for me to set things up afterwards.

Moral of the story: winmodems can be a real pain to set up in linux. But their biggest advantage is that they are quite cheap and abundant. If you have difficulty with an existing winmodem that came with the computer, replacing it with one that is well-supported in linux is a viable and time-saving alternative.

---

### Post by kagashe on 2007-05-10
> **Matchless said:**
> I think you may be flogging a dead horse here! You may have to dump your modem or swop it with a Windows user. That is the only other advice I can unfortunately give you.I don't depend on this modem. This desktop has internet connection through eth0. I wanted to use the modem as a dialup back up in case the network is down (which happens in rainy season because it is cable internet connection).

kagashe

---

### Post by Matchless on 2007-05-12
> **boon said:**
> Not necessarily! With the help of the linmodems.org site and their maillist, I have got my winmodem working successfully under feisty.

In the case of some winmodems, free software drivers are not available, but again, the linmodems.org folks are most likely to be able to give you an authoritative answer on this.

Very true, I have quite a collection of wimodems (and always on the scrounge for any!) and have been able to get most of them working on one or another version of Ubuntu with help from other people who are much more in the know. Some have had some issues and others work very well. If you really research in depth you will find drivers that only work on some versions of linux and kernels and some that work on most. There are patches, hacks and even "illegal" cracks, but some of the really older and out of manufacture winmodems will never get ported to the latest kernel versions, due to the fact that hardly anyone uses these any more and the people who have the know how may not be able to get their hands on any of these.
The people at linmodems are obviously providing fantastic modem support, but they are also inhibited when it comes to legal issues, such as for conexant modems etc.
Anyway glad to hear and see that we have another windows user (your profile!) that has started using linux and also got their modem working in linux. Well done and welcome!

---

