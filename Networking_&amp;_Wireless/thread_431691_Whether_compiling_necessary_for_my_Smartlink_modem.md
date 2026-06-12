---
title: "Whether compiling necessary for my Smartlink modem?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by kagashe on 2007-05-03
Hi,

After running ScanModemtool the output of ModemData.txt is as follows:
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
The following lines confirm that the modem could be used with Smartlink slamr.ko driver:
> 134d:2189  is a PCTel HSP56 MicroModem 688T modem with the Oasis chipset.
 Under 2.6.n kernels, it is only supported through the Smartlink slamr.ko driver.

The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.
Now I have to read the file Smartlink.txt which is as follows:

 > Smartlink modem setup.
 -----------------------------------------------------------
 The modem should setup with:
    sudo modprobe ungrab-winmodem
    sudo modprobe slamr
    sudo  slmodemd -c YOUR_COUNTRY   /dev/slamr0
 which should announce creation of ports:
    /dev/ttySL0 --> /dev/pts/N   , N some number
 Specify the symbolic link  /dev/ttySL0  as the port to be used by dailer software.


 SmartLink ([http://www.smlink.com/](http://www.smlink.com/)) chipset modems are sold under a variety 
 of BrandNames, and have vendor IDs 163c, 2000, 2003, and 2004. Conexant bought
 Smartlinks's modem techhology sector in 2005. While Linux updates are not
 expected from Conexant, Linux support is still very good thanks to volunteer
 Linux maintainer Sasha Khapyorsky. Get his updated software from:
	[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)

 A high level support component is a smart helper:            slmodemd
 Acting through one of several drivers, it creats ports dynamically and
 supports COMM and FAXing functions.  During facsimile usage, the AT&F command 
 is not supported. A means of implmenting the CNG is lacking, because this
 function is encoded within the dsplibs.o precompiled at Smartlink, Inc. See
    [http://marc.theaimsgroup.com/?t=116026350800001&r=1&w=2](http://marc.theaimsgroup.com/?t=116026350800001&r=1&w=2)
    [http://marc.theaimsgroup.com/?l=hylafax&m=116041369404444&w=2](http://marc.theaimsgroup.com/?l=hylafax&m=116041369404444&w=2)
 Usage of SMP (Symmetric MultiProcessor) mother boards is
 supported. For service on 64 bit AMD x86_64 processor mother boards, see
        [http://linmodems.technion.ac.il/archive-fourth/msg02594.html](http://linmodems.technion.ac.il/archive-fourth/msg02594.html)
	[http://linmodems.technion.ac.il/archive-fifth/msg02490.html](http://linmodems.technion.ac.il/archive-fifth/msg02490.html)
 However a 64 bit compilation of a proprietary dsplibs.o conponent is not
 available. Hence for modem usage the computers must be operated in 32 bit mode.

 The slmodemd supports a few different types of modem drivers.  Below the suffix 
 .ko means the modular form of a driver, before loading into the kernel. The
 slmodemd does not access the modem hardware directly. Rather access is provided
 through lower sophistication drivers. Prior to usage of a slamr driver, there
 must be a release of serial driver interference by loading of:  ungrab-winmodem.ko
 For PCI card modems with Smartlink chips the driver used is:    slamr.ko 
 For USB modems with ID 0483:7554 use Smartlink driver:          slusb.ko 
 For ALSA (Advanced Linux Sound Architecture) modem drivers, see the Table below.

 Sasha's core resources are:
 ----------------------------
 ungrab-winmodem.tar.gz - for compiling a ungrab-winmodem.ko driver
 slmodem-2.9.11-MostRecentDate.tar.gz  - the core code resource for compiling
    and installing slmodemd, slamr.ko and slusb.ko.  The slmodemd dynamically 
    creates ports and provides higher level COMM functions, after driver
    loading. Not being a driver, slmodemd serves under alternative boot kernels.
 ALSA modem drivers, included with 2.6.n kernel+module releases.
 
 Some derivative resources at [http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)
 SLMODEMD.gcc4.1.tar.gz - containing a compiled slmodemd and usage instructions.
    When used with ALSA modem drivers, further compiling is not necessary.
    > SLMODEMD.gcc4.1.tar.gz will suffice for getting online, though read on about automation. <<< See Compiling_slmodemd below, for details.
 sl-modem-daemon-SomeVersion.deb - an installer for Debian related distros.
    It has slmodemd and scripts for starting slmodemd at boot.
    This package is also available from repositories of Debian related distros  
    Ubuntu, Kbuntu, Ebuntu, Xandros, Kanotix and others.
 sl-modem-daemon-SomeVersion.tar.gz has the same contents, but is repackaged
    in an easily opened format, for access to its automation scripts.
    After unpacking, they are resident in the etc/  subfolder
 sl-modem-source-SomeVersion.deb - is a Debian installer for the slamr and slusb
    source code.  It is Not necessary for ALSA driver usage.
 slamr-KernelVersion.tar.gz - for several Ubuntu KernelVersions, containing:
    ungrab-winmodem.ko, slamr.ko, slusb.ko, slmomdem, setup script and as 
    a convenience, the sl-modem-daemon-SomeVersion.deb.  Look in the folder:
    [http://linmodems.technion.il/packages/smartlink/ubuntu/](http://linmodems.technion.il/packages/smartlink/ubuntu/)

 Slmodemd actions
 -----------------------------------------
 Start working with slmodemd with commands:
	slmodemd --help
        slmodemd --countrylist
 The long output can be written to a Clist.txt file with: 
        slmodemd --countrylist &> Clist.txt
 Find your COUNTRY_NAME within the 2nd column if the list and record it.
 It will be used in capital letters during the modem setup command.
 Try USA if your COUNTRY is not in the list.

 Before modem setup root/adm capacity must be acquired with:
	su - root
 or by prefixing commands with "sudo" for Ubuntu Linux and its cousins.
 The setup command is:
        sudo slmodemd -c COUNTRY_NAME --alsa slmodemd_device
 if successful there will be reported dynamic creation of:
        /dev/ttySL0 --> /dev/pts/N    , with N a number
 The /dev/ttySL0 is a symbolic link to the real modem port /dev/pts/N ,
 and it is /dev/ttySL0 which should be named to dialup utilities such
 as wvdial.  The "--alsa" is only needed for usage with ALSA modem drivers.
 Throughout a dialout session  slmodemd MUST be kept running. Open another
 console/termimal to startup dialout software such as wvdial.

 The slmodemd device nodes
 ---------------------------
 The slmodemd_device is different for the several modem drivers.
 For usage with slamr.ko , the slmodemd_device is /dev/slamr0 , within 
 the command sequence:
        sudo modprobe ungrab-windmodem
        sudo modprobe slamr
	sudo slmodemd -c COUNTRY_NAME /dev/slamr0
 For USB modem usage:
        sudo modprobe slusb
	sudo slmodemd -c COUNTRY_NAME /dev/slusb0
 For a modems using a ALSA driver, details are below.

 The /dev/slamr0 and /dev/slusb0 will be made the slmodem installation
 processes. However, they usually will NOT survice reboot, because
 most current Linux have ports created in volatile RAM space. However
 the these devices can be manually created under root/adm persmission with:
	sudo mknod -m 600 /dev/slamr0 c 242 0
	sudo mknod -m 600 /dev/slusb0 c 243 0
 if automation scripts are not yet in place.

 For automation of RPM using Linux distros see:
    [http://www20.brinkster.com/olivares/slmodemd-setup-1.html](http://www20.brinkster.com/olivares/slmodemd-setup-1.html)
 For any Distro the following lines will serve in /etc/modprobe.conf or subfolders of
   /etc/modprobe.d/:
--------------
alias char-major-243 slusb
alias char-major-242 slamr

# The following  install and remove commands are to be written as single lines.
#    Preloads ungrab-winmodem and creates a device node upon "modprobe slamr"
install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
# rpm using distros should use "uucp" rather than "dialout"

#     Removes slamr and ungrab-winmodem successively:
remove  slamr  /sbin/modprobe -r --ignore-remove  slamr ;  /sbin/modprobe -r --ignore-remove ungrab-winmodem

#	creates /dev/slusb uponn slusb driver loading.
install slusb modprobe --ignore-install slusb ; test -e /dev/slusb0 || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)
# rpm using distros should use "uucp" rather than "dialout"



 Usage with ALSA modem drivers
 --------------------------------
 See SoftModem.txt for a description of the hardware.  For a modem using 
 an ALSA driver, the slmodemd_device only has to be  specified within the 
 slmodemd command line.  A preliminary "mknod something" command is not necessary. 
 The Table shows hardware PCI ID, its card type, driver and slmodemd_device name.
 The ALI5451 and HDA (High Definition Audio) cards can host softmodems. For these
 cards hw:0,0  is the audio card designation and the modem Subsystem on it 
 is most commonly hw:0,1 , but there are some hw:0,6 cases. For the older
 soft modem controller family, the ALSA software first assigns hw:0 to an audio
 card, and the following modem designation is hw:1 or equivalently modem:1
 An attempt to use modem:0 may initially appear successful, but modem:0 or hw:0 
 is actually the companion audio card. 

PCI  ID      controller           ALSA driver      slmodemd_device 
=========    ===============    ===============    ===================
several      HDA cards          snd-hda-intel      hw:0,1  or  hw:0,6
10b9:5451    ALI5451 audio      snd-ali5451        hw:0,1
------------------ softmodem controllers --------------------------
1002:434d    ATI                snd-atiixp-modem   modem:1 
1002:4378    ATI                        "            "
1106:3068    VIA                snd-via82xxx-modem   "
8086:xxxx    many Intel         snd-intel8x0m        "
10de:00d9    Nvidia Corp            "                "
    SIS 630                "                "
   Others?                          "   test         "
---------------------------------------------------------------------------
* The scanModem script tries to determine ALSA modem driver and slmodemd_device 
dynamically from /proc/asound/ information, or the internal Archive as a fallback.

 Do a precautionary unloading and reloading of the driver.
	su - root 	(not for Ubuntu)
	sudo modprobe -r driver
	sudo modprobe driver
 This precaution is sometimes necessary, because a driver may functionally die
 although loaded. But usually it can be skipped.
 For this System, scanModem deduced slmodemd_device is:  
 For most modems the setup command is:
	sudo slmodemd -c COUNTRY_NAME --alsa modem:1
 For modems on HDA cards, the command is:
 	sudo slmodemd -c COUNTRY_NAME --alsa hw:0,1  
             though there have been cases of  hw:0,6
 For the ALI5451 hosted modems, a shortbuffer (-s) option is needed:
	sudo slmodemd -s -c COUNTRY_NAME --alsa hw:0,1


 The slamr diagnostic
 ---------------------
 Sasha has provided slamr.ko with a capability for reporting softmodem codecs,
 even for modems not supported fully by slamr. This is useful when other
 resources do not report out the modem codec, needed to distinguish between 
 hsfmodem, slamr and ALSA driver support alternatives.
 This slamr test is Not effective for softmodems on HDA audio cards.

 The test routine is:
    sudo modprobe ungrab-winmodem
    sudo modprobe slamr
 followed by a readout from the dmesg buffer with:
    dmesg | grep slamr
 Among the few output lines, there is one like:
    slamr: mc97 codec is SIL27
 reporting in this example an ALSA driver supported, Agere Systems codec SIL27.
 Conexant codecs have format CXTnm, nm a number. These modems are not ALSA driver supported.
 Softmodems with all other codecs should be ALSA driver plus slmodemd supported.

This file is not asking me to compile the driver. It is telling me to set up as follows:
> The modem should setup with:
    sudo modprobe ungrab-winmodem
    sudo modprobe slamr
    sudo  slmodemd -c YOUR_COUNTRY   /dev/slamr0
 which should announce creation of ports:
    /dev/ttySL0 --> /dev/pts/N   , N some number
 Specify the symbolic link  /dev/ttySL0  as the port to be used by dailer software.Since the recommended driver is "slamr.ko" and not "slamr" the relevant portion for setting up is as follows:
 > The slmodemd supports a few different types of modem drivers.  Below the suffix 
 .ko means the modular form of a driver, before loading into the kernel. The
 slmodemd does not access the modem hardware directly. Rather access is provided
 through lower sophistication drivers. Prior to usage of a slamr driver, there
 must be a release of serial driver interference by loading of:  ungrab-winmodem.ko
 For PCI card modems with Smartlink chips the driver used is:    slamr.koIt appears to me that there is no need to compile the driver but the file "ModemData.txt" also refers to "YourSystem.txt" which reads as follows:

> This file should NOT be sent to [email]Discuss@Linmodems.org[/email]
It has common guidance for modem usage after setup.


  Interfererce with browser naviagation:
  -------------------------------------
  Other COMM channels can interfere with browsing under dialout.
   Suspect channels set during your scanModem run were shown by:  ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:0F:EA:96:71:AF  
          inet addr:172.35.40.30  Bcast:172.35.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:eaff:fe96:71af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:4850 txqueuelen:1000 
          RX bytes:34557233 (32.9 MiB)  TX bytes:3994031 (3.8 MiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

  A block with "lo" is an internal loopback test and harmless.

  However, other COMM channels such as ethernet "eth0" will block browser function
  through dialout connections. Domain Name Services (DNS) needed for browsing
  will be blocked by an ineffective default usage of the eth0 assigned DNS.

  If is wisest to disable bootup establishment of alternate channels in your Control Center.
  Depending on your Linux distribution,
  one of the following root/admin commands may alternatively be effective:
  # ifdown eth0
  # ifconfig eth0 down
  # /etc/init.d/network stop
  # /etc/init.d/networking stop
  Be wary that some Systems will periodically try to re-establish internet.
  So if browsing should suspiciously fail, recheck with
    ifconfig
---------------------------- end COMM Channels --------------------------
  Ubuntu is not yet providing pre-compiled drivers for WinModems

 The Modem/DriverCompiling.txt  is a MUST READ,
 if you are not experienced in configuring kernel-source/
 or get "unresolved symbols" upon driver insertion.

  Most recent WinModem fixes are in:  [http://linmodems.technion.ac.il/FAQ.html](http://linmodems.technion.ac.il/FAQ.html)
  
(4) For guidance on automation see  [http://linmodems.technion.ac.il/archive-fourth/msg03734.html](http://linmodems.technion.ac.il/archive-fourth/msg03734.html)
and the scripts in the slmodem-2.9.n/scripts folder/
The following line is confusing:
> Ubuntu is not yet providing pre-compiled drivers for WinModems

Any comments?

kagashe

---

### Post by mtalexan on 2007-05-04
Basically it just means that Ubuntu doesn't have anything setup to make your job easier in installing the drivers.  You're going to have to compile the drivers yourself and deal with any associated problems rather than Ubuntu having files that are already compiled for you to use.

---

### Post by Matchless on 2007-05-04
Not familiar with your modem, but if the smartlink drivers will work here is a guide that may help you [http://ubuntuforums.org/showthread.php?t=190728&highlight=smartlink](http://ubuntuforums.org/showthread.php?t=190728&highlight=smartlink)

---

### Post by hasala on 2008-02-06
(if you use this method you can forget about the rpms no rpm will be needed to be installed for you to get the modem running.)
RATHER THAN EXTERNAL MODEMS internal modems offloads a lot of funtionality to the software driver.it has always been a big problem to configure those internal modems or(WINMODEMS/LINMODEMS) to work with linux because of manufacturers not supporting linux (and also the driver being pretty much more complex than ) But due to a great person Linux maintainer Sasha Khapyorsky writing the neccassary drivers needed to work the winmodem , now using a internal modem in linux has become as easy as ABC.


Linux maintainer: Sasha Khapyorsky. Get his updated software from:
[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)


what to do.

1. download a software called scanmodem from the foresaid site.

2. Browse [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) and  download scanModem.gz .
 Within a Linux partition open up a console and type in the following commands
    gunzip scanModem.gz
 To make it executable:
    chmod +x scanModem
 Run diagnositics with:
    ./scanModem 
3.scanmodem will check your hardware and software and then write its diagnostics to a subdir called modem.

4.open the ModemData.txt file.and go to   -----------end Softmodem section----------- part .

5.it will give the softwares you need to download and install.

6.if u have not installed the source at the installation of the distro. please install it.(source of the kernel) from the installation cd/dvd.

7.then install the downloaded software.

8.go to scanmodem/modem and open the diagnostic file chipsetname.txt eg:Smartlink.txt/conexant.txt .

9.In the start of the doc it gives the commands you have to run at the console to load the drivers that u downloaded and installed.

10.make sure that the smpppd, pppd services are installed and running.else install both and remember to enable them.

11.dial up using kinternet(i prefer it) or kppp. put to stupid mode option..now configure kinternet and the modem properly.to do that 
 goto yast->network devices ->modem.
           1.choose your modem device and press edit.
              enter modem device as /dev/ttySL0 and enter the details of the isp. if you are not sure call customer support for internet of your isp (internet provider) and get the required details such as number to dial and prefix.username
and password.

           2.remember to definitely check the box for stupid mode.

now every thing is set up

enjoy the internet with a great browser like firefox/opera.!!!!!!!
(with this you do not need any rpm for you to download,what you compile is enough)
if u have any comments or questions please mail to:dharmawardena_06@elect.mrt.ac.lk

						or [email]hasaladharmawardena@yahoo.com[/email]
or //(hasalaid@gmail.com).

hasala dharmawardena
faculty of engineering
department of electrical engineering([www.elect.mrt.ac.lk](www.elect.mrt.ac.lk))
University Of Moratuwa
SRILANKA

regards from srilanka , hasala.         ([www.hasala.bravehost.com](www.hasala.bravehost.com))

---

