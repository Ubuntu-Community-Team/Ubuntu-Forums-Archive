---
title: "Installing modem"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by Rabindranath on 2007-06-24
I have tried the scan modem tool and it gave a series of outputs. I dont know what it is. Tell me where to download drivers for my dialup modem 56k. It is a HSP56 Micro Modem. Please help me as I cant even play mp3 files as I am unable to connect to the internet. I am attaching the files obtained by using the scan modem tool.
I am using kubuntu and kppp as the dialer. What are the entries to be filled in it. How do I configure my modem?
Help me please.

Thanks in advance.










 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
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
 scanModem update of:  2007_June_19


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 06:01.0	134d:2189	134d:1002	Modem: PCTel Inc HSP56 MicroModem 

 Modem interrupt assignment and sharing: 
 20:          0          0   IO-APIC-fasteoi   serial

 --- Bootup diagnositcs for card in PCI slot 06:01.0 ----
[    3.093569] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[    3.093809] 0000:06:01.0: ttyS1 at I/O 0xb808 (irq = 20) is a 16450
[    3.093963] 0000:06:01.0: ttyS2 at I/O 0xb810 (irq = 20) is a 8250
[    3.094116] 0000:06:01.0: ttyS3 at I/O 0xb818 (irq = 20) is a 16450
[    3.094187] Couldn't register serial port 0000:06:01.0: -28

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	8086:e202	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 16:     130204          0   IO-APIC-fasteoi   uhci_hcd:usb5, HDA Intel, i915@pci:0000:00:02.0

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   18.017112] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.017136] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:2668 is a High Definition Audio card, possibly hosting a soft modem.
 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:2668 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW
      Primary PCI_id  8086:2668
    Subsystem PCI_id  8086:e202 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and
to test get the package SLMODEMD-1.0.13.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
2) The hsfmodem software for Conexant chipset modems: Read Conexant.txt

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-02: ALC880 Analog : ALC880 Analog : capture 2
00-00: ALC880 Analog : ALC880 Analog : playback 1 : capture 2

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem


----------------end Softmodem section --------------

scanModem could not identify the Support Type needed from diagnosics or archives.
	If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.


Writing Intel.txt

 Freeware support may be available for a few Conexant chipset modems 
 with support confirmed only for the PCI_id chipset  14f1:2f00.
 See  [http://ubuntuforums.org/showthread.php?t=180632](http://ubuntuforums.org/showthread.php?t=180632)

 Otherwise formal support for Conexant chipset modems are available ONLY through 
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers).  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 [http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B](http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B) reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 Read Conexant.txt

Writing Conexant.txt

Writing Smartlink.txt
============ end Smartlink section =====================

 For candidate modem in PCI bus:  06:01.0
   Class 0703: 134d:2189 Modem: PCTel Inc HSP56 MicroModem
      Primary PCI_id  134d:2189
 Support type needed or chipset:	slamr
 

 134d:2189  is a PCTel HSP56 MicroModem 688T modem with the Oasis chipset.
 Under 2.6.n kernels, it is only supported through the Smartlink slamr.ko driver.

The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


 Download slamr-2.6.20-15-generic.tgz from [http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)
 under Linux, open a terminal and unpack with:
 $ tar zxvf slamr*.tgz
 Move into the unpacked folder
 $ cd slamr-2.6.20-15-generic
 Look around
 $ ls
 Run the 
 $  sudo ./setup

 Afterwards do:
 $ slmodemd --help
 $ slmodemd --countrylist &> Clist.txt
 If not in the USA, look for your COUNTRY_NAME therein.
 Do and edit with:
 $ sudo gedit  /etc/default/sl-modem-daemon
 and therein replace the USA in the line:
 SLMODEMD_COUNTRY=USA
 This will provide for the correct Country setting in the automated:
    slmodemd -c COUNTRY /dev/slamr0

 Read the Smartlink.txt and YourSystem.txt 

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth0:avah
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

---

### Post by sharke on 2007-06-24
The driver could be the pctel go here [http://linmodems.technion.ac.il/pctel-linux/](http://linmodems.technion.ac.il/pctel-linux/)
download redhat for ubuntu extract and dead the readme file.
Regards
Sharke

---

### Post by Rabindranath on 2007-06-24
ok. Thanks. How to compile the source package?

---

### Post by sharke on 2007-06-24
Download this pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz
extract files and this will create a folder pctel open folder and read the readme file this has instructions on howto install.
Regards sharke
Ps  It is midnight here and i have to go to work at 5am will check tomorrow and see how you get along.
Regards
Sharke

---

