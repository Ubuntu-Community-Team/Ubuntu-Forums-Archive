---
title: "Need help to set up the modem on Ubuntu"
date: 2005-03-24
forum: Networking &amp; Wireless
---

### Post by mesocool on 2005-03-24
Does someone can help me to take a look at this file created by scanModem.. How can I make my modem work.. Thank you so much.. #-o 


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_March_20
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions resources, search for package names with:
  linux-headers-2.6.8.1-3-386
  kernel-source-2.6.8.1-3-386
  linux-2.6.8.1-3-386
One of which must be installed if compiling drivers to match kernel 2.6.8.1-3-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at PCI_bus 0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:24d6   Modem: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
  SubSystem 104d:8128   Sony Corporation: Unknown device 8128
	Flags: bus master, medium devsel, latency 0, IRQ 201
	I/O ports at e000
	I/O ports at dc00 [size=128]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24d6 104d:8128 debian 2.6.8.1-3-386 3.3.4     i686

       
 The soft modem Subsystem operates under a controller
   8086:24d6 82801EB ICH5 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
  Driver snd-intel8x0m  may enable codec acquisition 
  === Begin mc97 codec query  ===
File /proc/asound/card1/codec97#0/mc97#1-1
 --------
1-1/0: Silicon Laboratory Si3036/8 rev 7

Extended modem ID: codec=1 LIN1
Modem status     : GPIO ADC1 DAC1 PRB(res) PRE(ADC2) PRF(DAC2) PRG(HADC) PRH(HDAC)
Line1 rate       : 12000Hz
 --------
 104d:8128 has a SIL27 codec
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 Checking through information gathered from LinModem ARCHIVES
 Modem codec information on Subsystem 104d:8128 is not in the records.
 There are the following routes toward support:
	Follow instructions in Modem/SoftModem.txt for identifying the modem under a Microsoft boot.
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.
  Test the effectiveness of the hsfmodem package from [http://www.linuxant.com/drivers/hsf/index.php](http://www.linuxant.com/drivers/hsf/index.php).

 The debian Linux includes sl-modem packages with Smartlink drivers
   Install the kernel-headers-2.6.8.1-3-386.deb
   If necessary, set a symbolic link needed for slmodem compiling:
     # ln -s /usr/src/kernel-headers-2.6.8.1-3-386 /lib/modules/2.6.8.1-3-386/build
     as described in Modem/DriverCompiling.txt
   Then install the two sl-modem/slmodem packages and follow their directions.
   Thereafter the above slamr diagnositic can be run.

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 104d is Sony. Subsystem 104d:8129 under a 8086:2486 Intel modem controller
 has a Conexant chip in a Sony Vaio grx560 laptop. 
 A bootup "acpi=on" was required for IRQ acquisition.

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) ,
  but [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) has older packages and new fixes.
      For the emerging 2.6.10 kernels, use the slmodem-2.9.9b.tar.gz  therefrom.
 Read Slmodem.txt  for details.
   
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=8086 is Intel, Inc. producing HaM and 536ep host controller free (HCF) modems, 537 soft modem
 and AC97 and MC97 controllers managing a varierty of non-Intel soft modem Subsystems.
 These subSystems often have PCI_IDs assigned by the modem assembler, rather than the chip provider.
 Download available drivers through:  [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)  with Intel-537 types at:
 [http://downloadfinder.intel.com/scripts-df/Filter_Results.asp?selCat=all&strOSs=39&ProductID=1230&page_nbr=2](http://downloadfinder.intel.com/scripts-df/Filter_Results.asp?selCat=all&strOSs=39&ProductID=1230&page_nbr=2)
 Also check at: [http://linmodems.technion.ac.il/packages/Intel/537/](http://linmodems.technion.ac.il/packages/Intel/537/)  
 for beta releases and perhaps Already compiled drivers for some Linux distributions
 A very detailed installation report cogent to 537 type modems is at:
                  [http://linmodems.technion.ac.il/archive-fifth/msg00541.html](http://linmodems.technion.ac.il/archive-fifth/msg00541.html)
 ---------------------

  ======= PCI_ID checking completed ====== 
 Update=2005_March_20
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
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by mesocool on 2005-03-24
Also, I cannot find where those packages are.. sigh..

linux-headers-2.6.8.1-3-386
kernel-source-2.6.8.1-3-386
linux-2.6.8.1-3-386

---

### Post by az on 2005-03-24
You is cool.

sl-modem-daemon is in multiverse along with sl-modem-source.  You should install the daemon and try to use the alsa module (it is GPL!)  If that fails: sl-modem-source to compile the closed-source driver.

Linux-headers and build-essential can be found on your cd.  Search for linux-headers.

sudo apt-get install build-essential linux-headers-2.6-386

---

### Post by mesocool on 2005-03-24
[QUOTE=azz]You is cool.

sl-modem-daemon is in multiverse along with sl-modem-source.  You should install the daemon and try to use the alsa module (it is GPL!)  If that fails: sl-modem-source to compile the closed-source driver.

Linux-headers and build-essential can be found on your cd.  Search for linux-headers.

sudo apt-get install build-essential linux-headers-2.6-386[/QUOTE]

After I installed these packages, the modem still cannot be found. Am I missing some other parts?:cry:

---

### Post by mesocool on 2005-03-25
I tried pppconfig as well. But it's still not working..  :cry:

---

### Post by fizgig on 2005-03-25
I didn't use the package manager to install slmodem so I don't know if it runs the program as a service but try running "slmodemd" and see what you get.  If you have an ALSA supported modem, you'll have to run "slmodem --alsa modem:1"  or modem:0 instead.  If it works, it'll will present /dev/ttySL0 as the modem link that you point your dialer at.

I wrote a whole page on this at my linux howto that further discusses how to run the program automatically as a service and make a /dev/modem link instead of the /dev/ttySL0 link the program makes.  The web page is [here](http://mattsmith.hostmatrix.org/zx5078cl/kubuntu.html).  Go to the modem section.  Hope that helps.

---

### Post by mesocool on 2005-03-25
[QUOTE=fizgig]I didn't use the package manager to install slmodem so I don't know if it runs the program as a service but try running "slmodemd" and see what you get.  If you have an ALSA supported modem, you'll have to run "slmodem --alsa modem:1"  or modem:0 instead.  If it works, it'll will present /dev/ttySL0 as the modem link that you point your dialer at.

I wrote a whole page on this at my linux howto that further discusses how to run the program automatically as a service and make a /dev/modem link instead of the /dev/ttySL0 link the program makes.  The web page is [here](http://mattsmith.hostmatrix.org/zx5078cl/kubuntu.html).  Go to the modem section.  Hope that helps.[/QUOTE]

Could you tell me where these two files are --> "libasound2-dev" and "alsa-headers"? I couldn't find them..  Thanks..

---

### Post by fizgig on 2005-03-25
I got them using apt-get.  (apt-get install libasound2-dev) for example.  I'm sorry but I don't know which repository these packages are in but give the apt-get install command a shot.

---

### Post by mesocool on 2005-03-25
I got those packages @ [http://packages.debian.org/](http://packages.debian.org/). But I failed to dpkg them.. My god.. One problem followed by another problem. I dpkg them with problem and dpkg the slmodemd.. It seems to be alright. But it still said that No such file or directory. The modem cannot be found..

Also, I don't understand these from your webpage.. Thank you.. I am so new to it. 
 [-o< 
> The ati modem has a module that is included in the 2.6.10 kernel and probably a few older versions of the kernel as well.  The module name is snd_atiixp_modem.  You should see it installed if you type "lsmod |grep modem" in a terminal.  If it isn't there, modprobe it.  If that doesn't work, you'll have to recompile your kernel with the atiixp-modem checked.

---

### Post by fizgig on 2005-03-25
At a prompt, type "lsmod |grep modem"  what does it say?

---

### Post by mesocool on 2005-03-25
It didn't say anything.. No error message. Nothing at all..

Also, I see those that extra package didn't dpkg properly, I don't know how to deal with them. But I did dpkg some files from slmodem packages. And Yesterday, after I installed that package, I failed to enter the GUI.  [-o<

---

### Post by fizgig on 2005-03-25
[font=Verdana]Ok, your first post says that your modem is the  **INTEL AC-Link Controller (ICH).  **[Here]("http://www.linuxant.com/drivers/hsf/index.php")  you can see that your exact PCI ID is listed (PCI ID 8086:24D6) and that the driver supports it.  Good news! :)

So.  You need abandon the slmodem approach and go for the hsf modem driver.  Search for the *hsfmodem *debian package and install it.  Then, run *hsfconfig *to configure it.

That page I showed above has a link to the install file that will give you more directions.
  [/font]

---

### Post by mesocool on 2005-03-25
I tried several times but it didn't work.. Here is the record that I have done..

> 

root@Home:/home/joseph # dpkg -i /home/joseph/Desktop/hsfmodem_7.18.00.03full_i3 86.deb
Selecting previously deselected package hsfmodem.
(Reading database ... 70674 files and directories currently installed.)
Unpacking hsfmodem (from .../hsfmodem_7.18.00.03full_i386.deb) ...
Setting up hsfmodem (7.18.00.03full) ...
Conexant HSF softmodem driver, version 7.18.00.03full

If you need license keys, assistance or more information, please go to:
        [http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Debian-testing/unstable linux-2.6.8.1-3-386 i686

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.8.1-3-386/build]

Building modules for kernel 2.6.8.1-3-386, using source directory
/lib/modules/2.6.8.1-3-386/build. Please wait...
done.

ERROR: no device detected by hsf driver
dpkg: error processing hsfmodem (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hsfmodem


 

And after I reboot it.. It might be saying that my modem is not a conexant modem.

Also, I got a letter from scanModem maintainer MarvS, the content of the letter is following: 


104d:8128 has a SIL27 codec shows that your modem has an Agere Systems SIL27 codec Subsystem.   This should be supported by the slmodem-2.9.9b package which you can download from  [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
In sequence
1) install the linux-headers-2.6.8.1-3-386.deb package
2) Read the Slmodem.txt
2) Use the  slmodem-2.9.9b  resource to compi;le and install the drivers


but same thing happened, it didn't work.. Also, I dont understand some of the instruction. For example, 

ALSA mode
=========

ALSA has the built-in modem drivers included in 'alsa-driver' >= 1.0.2
and in Linux kernel >= 2.6.5. Currently there is 'intel8x0m' (snd-intel8x0m)
modem driver, which supports ICH based AC97 modems (MC97).


1. Configure your kernel and enable ALSA and ICH based modem support
   ( 'Device Drivers' -> 'Sound' -> 'Advanced Linux Sound Architecture' ->
     'PCI devices' -> 'Intel i8x0/MX440; AMD768/8111 modems' ) .

[COLOR=Red]Where is Device Drivers in Ubuntu[/COLOR]

2. Build and install kernel and modules as usual (make , make modules_install,
   etc.). ICH modem driver modem module name is 'snd-intel8x0m'
  (if was configured as module).

[COLOR=Red]How to write make modules_install snd-intel8x0m in the terminal.[/COLOR]

3. Build application 'slmodemd' with ALSA support. For this in
   slmodem-2.9.x dir:

      $ cd modem
      $ make SUPPORT_ALSA=1

   This will build 'slmodemd' with ALSA support. If compilation is failed
   review Makefile (near ALSA_SUPPORT condition) and define right library
   and/or CFLAGS

4. Use option '--alsa' when running 'slmodemd' and ALSA conventional
   device name ('hw:0' or 'hw:1' for instance). If modem support in
   the kernel was enabled as module module 'snd-intel8x0m' should be loaded.
   When using ALSA modem driver you don't need to load other modules ('slamr').

[COLOR=Red]This one is totally confused...[/COLOR]

sigh..

---

### Post by fizgig on 2005-03-25
Ok, I'm reading the readme which says there is an **snd-intel8x0m** modem driver which comes with ALSA which supports ICH based AC97 modems.

STEP1:  Is that driver already loaded?  type **lsmod |grep snd-intel **to see if it's there.

STEP2:  If it isn't there, type **sudo modprobe snd-intel8x0m** and then repeat STEP1 to see if it loaded.

Report back here what you find.

---

### Post by mesocool on 2005-03-25
[COLOR=Red]It didn't show anything at all.[/COLOR]


root@Home:/home/joseph # hsfconfig
Conexant HSF softmodem driver, version 7.18.00.03full

If you need license keys, assistance or more information, please go to:
        [http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

Warning: existing driver modules found under:
        /lib/modules/2.6.8.1-3-386/
Would you like to keep using them? [no]

No pre-built modules for: Debian-testing/unstable linux-2.6.8.1-3-386 i686

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.8.1-3-386/build]

Building modules for kernel 2.6.8.1-3-386, using source directory
/lib/modules/2.6.8.1-3-386/build. Please wait...
done.



[COLOR=Red]
ERROR: no device detected by hsf driver
root@Home:/home/joseph # lsmod |grep snd-intel
root@Home:/home/joseph # sudo modprobe snd-intel8x0m
root@Home:/home/joseph # lsmod |grep snd-intel
  [/COLOR]

---

### Post by az on 2005-03-25
"1. Configure your kernel and enable ALSA and ICH based modem support
( 'Device Drivers' -> 'Sound' -> 'Advanced Linux Sound Architecture' ->
'PCI devices' -> 'Intel i8x0/MX440; AMD768/8111 modems' ) .

Where is Device Drivers in Ubuntu"


That is when you do make menuconfig when rebuilding a kernel,  You do not need to worry about this (I assume) since you are using the module that has already been built.  It should include these options since others have reported that the also module can be used for the modem in Ubuntu.

"2. Build and install kernel and modules as usual (make , make modules_install,
etc.). ICH modem driver modem module name is 'snd-intel8x0m'
(if was configured as module).

How to write make modules_install snd-intel8x0m in the terminal."

Again, never mind.



"3. Build application 'slmodemd' with ALSA support. For this in
slmodem-2.9.x dir:

$ cd modem
$ make SUPPORT_ALSA=1

This will build 'slmodemd' with ALSA support. If compilation is failed
review Makefile (near ALSA_SUPPORT condition) and define right library
and/or CFLAGS

4. Use option '--alsa' when running 'slmodemd' and ALSA conventional
device name ('hw:0' or 'hw:1' for instance). If modem support in
the kernel was enabled as module module 'snd-intel8x0m' should be loaded.
When using ALSA modem driver you don't need to load other modules ('slamr')."


Basically, do 
dpkg-reconfigure sl-modem-daemon

That automagically configures your stuff for the alsa driver if the other driver module (the proprietary one) is not there.

Here is the proprietary module for warty's original kernel.

[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

---

### Post by mesocool on 2005-03-25
> **azz]"1. Configure your kernel and enable ALSA and ICH based modem support
( 'Device Drivers' -> 'Sound' -> 'Advanced Linux Sound Architecture' ->
'PCI devices' -> 'Intel i8x0/MX440 said:**
> http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb[/url]

I bascially did the same thing as the description said.. But it is not working. My modem stilll cannot be detected.. 

Also, I got a letter from scanModem maintainer MarvS, the content of the letter is following: 


104d:8128 has a SIL27 codec shows that your modem has an Agere Systems SIL27 codec Subsystem. This should be supported by the slmodem-2.9.9b package which you can download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
In sequence
1) install the linux-headers-2.6.8.1-3-386.deb package
2) Read the Slmodem.txt
2) Use the slmodem-2.9.9b resource to compi;le and install the drivers

It asks me to use slmodem-2.9.9b.. STILL NOT WORKING.. SIGH.  ](*,)

---

### Post by fizgig on 2005-03-25
The trouble is he doesn't have the snd-intel8x0m module loaded according to the test I asked him to do.  That's what stumped me.

---

### Post by mesocool on 2005-03-25
Yes, it doesn't say anything after I run those commands.. Not even error messages. :shock:

---

### Post by fizgig on 2005-03-25
Do you see the snd-intel8x0m.ko module listed if you execute the following command?

**ls /lib/modules/`uname -r`/kernel/sound/pci/**

---

### Post by az on 2005-03-25
The alsa driver does not always work.

Use this:
[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

Lemme know if it works.

(Download it and do
sudo dpkg -i sl-modem-modules*.deb


Then do sudo dpkg-reconfigure sl-modem-daemon.  Pick the slarmr modem driver (not the alsa one) and take it from there.

---

### Post by mesocool on 2005-03-25
[QUOTE=fizgig]Do you see the snd-intel8x0m.ko module listed if you execute the following command?

**ls /lib/modules/`uname -r`/kernel/sound/pci/**[/QUOTE]

Yes, it is there. The following is so....

root@Home:/home/joseph # ls /lib/modules/`uname -r`/kernel/sound/pci/
ac97      mixart          snd-cmipci.ko   snd-intel8x0.ko    trident
ali5451   nm256           snd-cs4281.ko   snd-intel8x0m.ko   vx222
au88x0    rme9652         snd-ens1370.ko  snd-maestro3.ko    ymfpci
cs46xx    snd-als4000.ko  snd-ens1371.ko  snd-rme32.ko
emu10k1   snd-atiixp.ko   snd-es1938.ko   snd-rme96.ko
ice1712   snd-azt3328.ko  snd-es1968.ko   snd-sonicvibes.ko
korg1212  snd-bt87x.ko    snd-fm801.ko    snd-via82xx.ko

---

### Post by fizgig on 2005-03-25
If azz's approach doesn't work, try changing directories:

**cd **[b]/lib/modules/`uname -r`/kernel/sound/pci/

[/b]Then install the module from there:

**sudo insmod **[b]snd-intel8x0m

[/b]Then, to see if it installed...

**lsmod |grep snd-intel8x0m**

---

### Post by mesocool on 2005-03-25
[QUOTE=azz]The alsa driver does not always work.

Use this:
[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

Lemme know if it works.

(Download it and do
sudo dpkg -i sl-modem-modules*.deb


Then do sudo dpkg-reconfigure sl-modem-daemon.  Pick the slarmr modem driver (not the alsa one) and take it from there.[/QUOTE]

Thank you so much for you guys..

the following is the result.. Seems only half of it works..

root@Home:/home/joseph # sudo dpkg -i /home/joseph/Desktop/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb
Selecting previously deselected package sl-modem-modules-2.6.8.1-3-386.
(Reading database ... 72269 files and directories currently installed.)
Unpacking sl-modem-modules-2.6.8.1-3-386 (from .../sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb) ...
Setting up sl-modem-modules-2.6.8.1-3-386 (2.9.9-1) ...

root@Home:/home/joseph # sudo dpkg-reconfigure sl-modem-daemon
Package `sl-modem-daemon' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: sl-modem-daemon is not installed

---

### Post by mesocool on 2005-03-25
[QUOTE=fizgig]If azz's approach doesn't work, try changing directories:

**cd **[b]/lib/modules/`uname -r`/kernel/sound/pci/

[/b]Then install the module from there:

**sudo insmod **[b]snd-intel8x0m

[/b]Then, to see if it installed...

**lsmod |grep snd-intel8x0m**[/QUOTE]

Sigh.. the file cannot be found..

root@Home:/lib/modules/2.6.8.1-3-386/kernel/sound/pci # sudo insmod snd-intel8x0m
insmod: can't read 'snd-intel8x0m': No such file or directory

---

### Post by mesocool on 2005-03-25
Another thing I didn't mention is that I installed ubuntu on a different hard drive from the one where WinXp is.. Does it make any difference?  [-o<

---

### Post by fizgig on 2005-03-25
[QUOTE=mesocool]Sigh.. the file cannot be found..

root@Home:/lib/modules/2.6.8.1-3-386/kernel/sound/pci # sudo insmod snd-intel8x0m
insmod: can't read 'snd-intel8x0m': No such file or directory[/QUOTE]

you might need to add the **.ko **to the end of the file so it would be **sudo insmod snd-intel8x0m.ko**

---

### Post by mesocool on 2005-03-26
I tried that too.. But it is not working as well... Sucks, I have been working on this for 2 days.. The only difference is that it tells me "permission denied" instead of "No such file or directory". Drives me crazy..

Maybe I should try FreeBSD or some other mature Linux.. [-(

---

### Post by fizgig on 2005-03-26
I'm sorry man, I'm out of ideas.  Wish I could type on your terminal from a distance cause this is difficult this way.

---

### Post by mesocool on 2005-03-26
But thank you guys so much... I did learn something.. Hahaha.. Remote control is not a bad idea.. But the point is my Linux cannot connect to Internet.. hahaha.. :-({|=

---

### Post by mesocool on 2005-03-26
[QUOTE=fizgig]I'm sorry man, I'm out of ideas.  Wish I could type on your terminal from a distance cause this is difficult this way.[/QUOTE]

Do you think they are going to add these modem stuff up to their next version? :?:

---

### Post by mesocool on 2005-03-26
[QUOTE=fizgig]you might need to add the **.ko **to the end of the file so it would be **sudo insmod snd-intel8x0m.ko**[/QUOTE]

If I change snd-intel8x0m to snd-intel8x0m.ko, it will say that the file exsits... Should I download this find and copy it in there? :-k

---

### Post by fizgig on 2005-03-26
[QUOTE=mesocool]If I change snd-intel8x0m to snd-intel8x0m.ko, it will say that the file exsits... Should I download this find and copy it in there? :-k[/QUOTE]

Well, all the modules have to be compiled specifically for your kernel.  All the .o and .ko files you have in your /lib/modules/kernel directory should already have been compiled for your kernel so I don't know why they wont insert correctly.

I can't figure out why you can't modprobe it but, then again, I've only been doing the linux thing since last November so I'm not very experienced.

---

### Post by mesocool on 2005-03-26
[QUOTE=fizgig]Well, all the modules have to be compiled specifically for your kernel.  All the .o and .ko files you have in your /lib/modules/kernel directory should already have been compiled for your kernel so I don't know why they wont insert correctly.

I can't figure out why you can't modprobe it but, then again, I've only been doing the linux thing since last November so I'm not very experienced.[/QUOTE]

[COLOR=Red]Actually, I just started. hehe.. It's ok.. Study together.. 

I tried to use hsfmodem today.. but I got the following. It seems finishing building, but it cannot detect the modem as well.   [/COLOR]


root@Home:/home/joseph # dpkg -i /home/joseph/Desktop/hsfmodem_7.18.00.03full_i386.deb
(Reading database ... 71530 files and directories currently installed.)
Preparing to replace hsfmodem 7.18.00.03full (using .../hsfmodem_7.18.00.03full_i386.deb) ...

Removing hsf driver from /lib/modules/2.6.8.1-3-386/
Unpacking replacement hsfmodem ...
Setting up hsfmodem (7.18.00.03full) ...
Conexant HSF softmodem driver, version 7.18.00.03full

If you need license keys, assistance or more information, please go to:
        [http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Debian-testing/unstable linux-2.6.8.1-3-386 i686

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.8.1-3-386/build]

Building modules for kernel 2.6.8.1-3-386, using source directory
/lib/modules/2.6.8.1-3-386/build. Please wait...
done.

ERROR: no device detected by hsf driver
dpkg: error processing hsfmodem (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hsfmodem

---

### Post by az on 2005-03-26
Get the sl-modem-daemon package from the archive.  It is in multiverse.  I misunderstood you in that I though you had it alread installed.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)


dpkg -i sl-modem-daemon*.deb

Also, if you have not rebooted sionce you installed the module package, do

sudo depmod -a

beforehand.

Edit I made a mistake, but I fixed the URL...

---

### Post by mesocool on 2005-03-26
[QUOTE=azz]Get the sl-modem-daemon package from the archive.  It is in multiverse.  I misunderstood you in that I though you had it alread installed.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)


dpkg -i sl-modem-daemon*.deb

Also, if you have not rebooted sionce you installed the module package, do

sudo depmod -a

beforehand.

Edit I made a mistake, but I fixed the URL...[/QUOTE]

[COLOR=Red]Hey azz, this is what I got...[/COLOR]

root@Home:/home/joseph # dpkg -i /home/joseph/Desktop/sl-modem-daemon_2.9.9-1_i386.deb
(Reading database ... 71541 files and directories currently installed.)
Preparing to replace sl-modem-daemon 2.9.9-1 (using .../sl-modem-daemon_2.9.9-1_i386.deb) ...
Unpacking replacement sl-modem-daemon ...
dpkg: dependency problems prevent configuration of sl-modem-daemon:
 sl-modem-daemon depends on sl-modem-modules-new | sl-modem-source (>> 2.9.6-1) | kernel-image-2.6; however:
  Package sl-modem-modules-new is not installed.
  Package sl-modem-source is not installed.
  Package kernel-image-2.6 is not installed.
dpkg: error processing sl-modem-daemon (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sl-modem-daemon

---

### Post by az on 2005-03-26
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)


It is telling you to install this too.  Again, I though you already had this.  
You will need this too,
[http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.6.8_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.6.8_all.deb)


sudo apt-get -f install

---

### Post by mesocool on 2005-03-26
[QUOTE=azz][http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)


It is telling you to install this too.  Again, I though you already had this.  
You will need this too,
[http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.6.8_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.6.8_all.deb)


sudo apt-get -f install[/QUOTE]

 [COLOR=Red] Hey azz, it is working... But "sudo apt-get -f install" is not working.. The following is the result..  What should I do next...[/COLOR]
> 

root@Home:/home/joseph # dpkg -i /home/joseph/Desktop/module-assistant_0.6.8_all.deb
Selecting previously deselected package module-assistant.
(Reading database ... 71548 files and directories currently installed.)
Unpacking module-assistant (from .../module-assistant_0.6.8_all.deb) ...
Setting up module-assistant (0.6.8) ...
root@Home:/home/joseph # dpkg -i /home/joseph/Desktop/sl-modem-source_2.9.9-1_i386.deb
(Reading database ... 71626 files and directories currently installed.)
Preparing to replace sl-modem-source 2.9.9-1 (using .../sl-modem-source_2.9.9-1_i386.deb) ...
Unpacking replacement sl-modem-source ...
Setting up sl-modem-source (2.9.9-1) ...
root@Home:/home/joseph # dpkg -i /home/joseph/Desktop/sl-modem-daemon_2.9.9-1_i386.deb
(Reading database ... 71626 files and directories currently installed.)
Preparing to replace sl-modem-daemon 2.9.9-1 (using .../sl-modem-daemon_2.9.9-1_i386.deb) ...
Unpacking replacement sl-modem-daemon ...
Setting up sl-modem-daemon (2.9.9-1) ...
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0



root@Home:/home/joseph # sudo apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hsfmodem (7.18.00.03full) ...
Conexant HSF softmodem driver, version 7.18.00.03full

If you need license keys, assistance or more information, please go to:
        [http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

Warning: existing driver modules found under:
        /lib/modules/2.6.8.1-3-386/
Would you like to keep using them? [no]

No pre-built modules for: Debian-testing/unstable linux-2.6.8.1-3-386 i686

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.8.1-3-386/build]

Building modules for kernel 2.6.8.1-3-386, using source directory
/lib/modules/2.6.8.1-3-386/build. Please wait...
done.

ERROR: no device detected by hsf driver
dpkg: error processing hsfmodem (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hsfmodem
E: Sub-process /usr/bin/dpkg returned an error code (1)






---

### Post by mesocool on 2005-03-26
Also, I tried "sudo dpkg-reconfigure sl-modem-daemon". The only thing I can modify is region which I choose USA.. The following is the message after I done the reconfigure.. [-o< 


> root@Home:/home/joseph # sudo dpkg-reconfigure sl-modem-daemon
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

  

---

### Post by fizgig on 2005-03-27
mesocool, it looks like it's working!!  Try a dialer program and tell it to use /dev/ttSL0 as the modem and it should work!

---

### Post by mesocool on 2005-03-27
[QUOTE=fizgig]mesocool, it looks like it's working!!  Try a dialer program and tell it to use /dev/ttSL0 as the modem and it should work![/QUOTE]

Sigh. Still not working.. But the error message is changed.. This time, it shows "input/output error" if I use /dv/ttSL0. [-(

---

### Post by old dog on 2005-03-27
You are having the same problem I had with a "usb" modem due to the change from devfs to udev in both Mdk 10.1 & Fc3.

udev untill kernel 2.6.11 (or 2.6.10.770 for fc3) will  not load the correct usb module for an external modem because it is not yet capable.

The decision to implement this new system without taking into account the number of usb devices that would be disabled by it is yet another example of the desire to push ahead without pause to explore the paranoia behind it.

The fact I'm here typing this is indicative of my desire to see the Linux system in all it's flavours, put a dent in the monolith otherwise known as Windows,  but; lets not spoil the taste of the pudding before we get to serve it up. 
Don't  forget,  the vast majority of the people we are trying to convert don't give a shit.

The saying goes " old dog for a hard road" but another says " It's a hard road trying to teach old dogs new tricks"!

old dog

---

### Post by az on 2005-03-27
Remove hsfmodem.  It if for conexant modems.  You are using the sl-modem drivers.

Do sudo pppconfig 
and enter all your information. Make sure you save.  Name theconnection provider.
Use /dev/modem as this symlink if provided for you.

Open a console and type

sudo tail -f /var/log/messages

Open another console and type

sudo pon

Post the output of the first console:  (cut and past the text)

---

### Post by mesocool on 2005-03-27
[QUOTE=azz]Remove hsfmodem.  It if for conexant modems.  You are using the sl-modem drivers.

Do sudo pppconfig 
and enter all your information. Make sure you save.  Name theconnection provider.
Use /dev/modem as this symlink if provided for you.

Open a console and type

sudo tail -f /var/log/messages

Open another console and type

sudo pon

Post the output of the first console:  (cut and past the text)[/QUOTE]

[COLOR=Red]First of all, I removed the hsfmodem driver. Then the following is the text in the terimal[/COLOR]

> 

------------- first termial

root@Home:/home/joseph # sudo tail -f /var/log/messages
Mar 27 02:16:58 localhost scsi.agent[5035]: disk at /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/host0/0:0:0:0
Mar 27 02:16:58 localhost kernel: SCSI device sda: 124160 512-byte hdwr sectors (64 MB)
Mar 27 02:16:58 localhost kernel: sda: Write Protect is off
Mar 27 02:16:58 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
Mar 27 02:16:58 localhost kernel: Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Mar 27 02:17:38 localhost gconfd (root-5156): starting (version 2.8.1), pid 5156 user 'root'
Mar 27 02:17:38 localhost gconfd (root-5156): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 27 02:17:38 localhost gconfd (root-5156): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 27 02:17:38 localhost gconfd (root-5156): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 27 02:20:52 localhost pppd[3762]: Exit.


--------- second termial

root@Home:/home/joseph # sudo pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'




---

### Post by mesocool on 2005-03-27
In the network setting, it cannot detect the modem. But if I try to detect modem in Gnome ppp, it got it... Why it is..

Gnome ppp works, but I got the following message which never happened in windows.
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
TZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
TQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT2064951000
--> Waiting for carrier.
CONNECT 48000
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L3DT2064951000
--> Waiting for carrier.
CVX Access Switch.
Access is restricted to authorized users only.
login: 
login: 
login: 
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Sun Mar 27 02:59:18 2005 #-o

---

### Post by mesocool on 2005-03-27
[COLOR=Red]I got some new message!![/COLOR]

> 

root@Home:/home/joseph # sudo tail -f /var/log/messages
Mar 27 04:42:16 localhost chat[5313]: expect (phone)
Mar 27 04:42:16 localhost chat[5313]: ^M
Mar 27 04:42:16 localhost chat[5313]: ATDT<put^M^M
Mar 27 04:42:16 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:16 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:16 localhost chat[5313]: NO CARRIER
Mar 27 04:42:16 localhost chat[5313]:  -- failed
Mar 27 04:42:16 localhost chat[5313]: Failed (NO CARRIER)
Mar 27 04:42:16 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:16 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:19 localhost chat[5315]: abort on (BUSY)
Mar 27 04:42:19 localhost chat[5315]: abort on (NO CARRIER)
Mar 27 04:42:19 localhost chat[5315]: abort on (VOICE)
Mar 27 04:42:19 localhost chat[5315]: abort on (NO DIALTONE)
Mar 27 04:42:19 localhost chat[5315]: send (ATZW2^M)
Mar 27 04:42:19 localhost chat[5315]: expect (OK)
Mar 27 04:42:19 localhost chat[5315]: ATZW2^M^M
Mar 27 04:42:19 localhost chat[5315]: OK
Mar 27 04:42:19 localhost chat[5315]:  -- got it
Mar 27 04:42:19 localhost chat[5315]: send (ATDT<put^M)
Mar 27 04:42:19 localhost chat[5315]: expect (phone)
Mar 27 04:42:19 localhost chat[5315]: ^M
Mar 27 04:42:19 localhost chat[5315]: ATDT<put^M^M
Mar 27 04:42:19 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:19 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:19 localhost chat[5315]: NO CARRIER
Mar 27 04:42:19 localhost chat[5315]:  -- failed
Mar 27 04:42:19 localhost chat[5315]: Failed (NO CARRIER)
Mar 27 04:42:19 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:19 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:26 localhost pppd[5320]: pppd 2.4.2 started by root, uid 0
Mar 27 04:42:27 localhost chat[5321]: abort on (BUSY)
Mar 27 04:42:27 localhost chat[5321]: abort on (NO CARRIER)
Mar 27 04:42:27 localhost chat[5321]: abort on (VOICE)
Mar 27 04:42:27 localhost chat[5321]: abort on (NO DIALTONE)
Mar 27 04:42:27 localhost chat[5321]: send (ATZW2^M)
Mar 27 04:42:27 localhost chat[5321]: expect (OK)
Mar 27 04:42:27 localhost chat[5321]: ATZW2^M^M
Mar 27 04:42:27 localhost chat[5321]: OK
Mar 27 04:42:27 localhost chat[5321]:  -- got it
Mar 27 04:42:27 localhost chat[5321]: send (ATDT<put^M)
Mar 27 04:42:27 localhost chat[5321]: expect (phone)
Mar 27 04:42:27 localhost chat[5321]: ^M
Mar 27 04:42:27 localhost chat[5321]: ATDT<put^M^M
Mar 27 04:42:27 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:27 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:27 localhost chat[5321]: NO CARRIER
Mar 27 04:42:27 localhost chat[5321]:  -- failed
Mar 27 04:42:27 localhost chat[5321]: Failed (NO CARRIER)
Mar 27 04:42:27 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:27 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:30 localhost chat[5323]: abort on (BUSY)
Mar 27 04:42:30 localhost chat[5323]: abort on (NO CARRIER)
Mar 27 04:42:30 localhost chat[5323]: abort on (VOICE)
Mar 27 04:42:30 localhost chat[5323]: abort on (NO DIALTONE)
Mar 27 04:42:30 localhost chat[5323]: send (ATZW2^M)
Mar 27 04:42:30 localhost chat[5323]: expect (OK)
Mar 27 04:42:30 localhost chat[5323]: ATZW2^M^M
Mar 27 04:42:30 localhost chat[5323]: OK
Mar 27 04:42:30 localhost chat[5323]:  -- got it
Mar 27 04:42:30 localhost chat[5323]: send (ATDT<put^M)
Mar 27 04:42:31 localhost chat[5323]: expect (phone)
Mar 27 04:42:31 localhost chat[5323]: ^M
Mar 27 04:42:31 localhost chat[5323]: ATDT<put^M^M
Mar 27 04:42:31 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:31 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:31 localhost chat[5323]: NO CARRIER
Mar 27 04:42:31 localhost chat[5323]:  -- failed
Mar 27 04:42:31 localhost chat[5323]: Failed (NO CARRIER)
Mar 27 04:42:31 localhost kernel: codec_semaphore: semaphore is not ready [0x1][0x701300]
Mar 27 04:42:31 localhost kernel: codec_write 1: semaphore is not ready for register 0x54
Mar 27 04:42:32 localhost pppd[4994]: Exit.



---

### Post by az on 2005-03-27
1-  Make sure that the sl-modem-daemon is loading the slamr module.  Do
lsmod
and look for the snd-intel8x0m module.  Make sure it is not there.  Make sure that the slamr one is.

2-  The modem has conflicting indentification.  It may turn out to not be an intel modem (It likely is) because the vendors are not consistent with their identification.  Another problem with winmodems.

3-  The driver provided by the vendor (slamr) was licenced under terms that it was not to be used for other brands of modems (non-smartlink).  It even had versions of the driver that would mis-dial on purpose if it detevted that it was not the proper vendor id, despite having the correct chipset.  I peeved someone off at six AM one morning because of this, trying to get my modem to work.
The company changed their policy and allowed the slmodem-2.9.9 version to be user by anyone.  This is how it managed to get packaged by Debian and Ubuntu.  Marv S mentioned that the modem should work with the slmodem-2.9.9b version of the driver.
That version is available freely, but it's licence prohibits it's use in the case you do not own a smart-link modem.  (This information is something like three months old, it may have changed, but since the Debian version is still slmodem-2.9.9, I do not think so)

Basically, if you are sure that the slamr module is correctly loaded and it is still not working, follow the advice as given to you by Marv (Download the slmodem-2.9.9b version and build and install it by hand).  You should remove the sl-modem packages you have installed first, before doing that.

Good Luck.

---

### Post by mesocool on 2005-03-27
I tried to use the package he recommended, but it is not working again..

I notice that he asks to add a line
  Carrier Check = no in wvdial.conf

But I cannot open that file. Could you tell me how to open that file? Thanks. :oops:

The following is what I got after run #  wvdial

> 

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
root@Home:/home/joseph # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.


---

### Post by mesocool on 2005-03-28
Woohoo, [COLOR=Red]azz[/COLOR] and [COLOR=Red]fizgig[/COLOR], I finally dial that up.. It is working.. But only working by using wvdial.. Neither Network nor PPPon is working.. But I am happy... Thank you guys so much.. Thank you for your help.. I appreciate it.. \\:D/

---

### Post by az on 2005-03-28
linmodems.org rocks.

So does Marv Stodolsky.

Also, if you ever upgrade your kernel, you will need to also upgrade your driver module (sl-modem-module package)

---

### Post by mesocool on 2005-03-28
[QUOTE=azz]linmodems.org rocks.

So does Marv Stodolsky.

Also, if you ever upgrade your kernel, you will need to also upgrade your driver module (sl-modem-module package)[/QUOTE]

But there is another problem.. The sound is disappearing.. I think I saw an article once online, it said that the reason why the modem is not working is that the sound driver conflict with the modem driver..

NO SOUND.. You have some ideas about it?  [-o<

---

### Post by fizgig on 2005-03-28
As you can see on that page of mine I directed you to, I use the slmodemd program in combination with the ALSA module (snd-atiixp-modem) instead of with the slamr module. 

I have the slmodemd daemon running as a service upon bootup and I'm able to dial just fine.  The service does not affect my sound system (based on ALSA).

I don't know what to recommend since Azz suggests you use the slamr module and he certainly knows a lot more about this than me but I'm surprised that you weren't able to use the ALSA module (snd-intel8x0m).  It seems to me that two modules written by the ALSA team (one for sound, one for the modem) ought to work together just fine - and they do with me.

---

### Post by mesocool on 2005-03-28
[QUOTE=fizgig]As you can see on that page of mine I directed you to, I use the slmodemd program in combination with the ALSA module (snd-atiixp-modem) instead of with the slamr module. 

I have the slmodemd daemon running as a service upon bootup and I'm able to dial just fine.  The service does not affect my sound system (based on ALSA).

I don't know what to recommend since Azz suggests you use the slamr module and he certainly knows a lot more about this than me but I'm surprised that you weren't able to use the ALSA module (snd-intel8x0m).  It seems to me that two modules written by the ALSA team (one for sound, one for the modem) ought to work together just fine - and they do with me.[/QUOTE]

[COLOR=Red] Are there some cures that I don't have to change the set up I did so far but can make the sound work?  [/COLOR]

---

### Post by az on 2005-03-28
In some cases, sound and modem is an either/or situation.  I do not know what else you can do.

It is ironic.  The reason that this modem driver works for so many modems is that it uses the ac97 codec.  Essentially, it uses your sound system  That makes it easier to make a driver.

The driver is still not very mature, though.

Lucent modems are cheap. (seven bucks on ebay)

They probably work better.

---

### Post by mesocool on 2005-03-29
[QUOTE=azz]In some cases, sound and modem is an either/or situation.  I do not know what else you can do.

It is ironic.  The reason that this modem driver works for so many modems is that it uses the ac97 codec.  Essentially, it uses your sound system  That makes it easier to make a driver.

The driver is still not very mature, though.

Lucent modems are cheap. (seven bucks on ebay)

They probably work better.[/QUOTE]

The strange thing is that when the login window is showing up, I heard the drum sound. But after I enter the system, the sound is not working... It sucks. [-(

---

