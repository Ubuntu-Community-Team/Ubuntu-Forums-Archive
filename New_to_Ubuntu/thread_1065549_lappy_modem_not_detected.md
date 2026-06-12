---
title: "lappy modem not detected"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by rkakkar on 2009-02-10
i have a HP Compaq 6720s Notebook PC. it currently uses the following modem driver:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3442833&prodTypeId=321957&prodSeriesId=3442832&swLang=8&taskId=135&swEnvOID=1093#11319](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3442833&prodTypeId=321957&prodSeriesId=3442832&swLang=8&taskId=135&swEnvOID=1093#11319)

it is an internal modem. i want my dial up modem to work in ubuntu but just don't know how to configure a dial up connection. can someone walk me through it?

---

### Post by Temposs on 2009-02-10
One thing you need to keep in mind is that you can't use Windows drivers on Linux(for the most part). Often, Linux has a driver already included that will recognize your modem. You just need to initialize it properly for it to work.

I have successfully used a program called pppconfig to setup a dialup connection.

Go to this page: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6)

Find the section called "Alternative Way 2 (using pppconfig & pon/poff)" and follow the instructions.

If this doesn't work, just start trying the other methods on that page until something works.

---

### Post by Shazaam on 2009-02-10
If Temposs' way doesn't help look here...
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by rkakkar on 2009-02-10
i tried the wvdial method. but my modem is not being detected :(

```
$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
```


i then installed scanModem to try and detect my modem but i can't make heads or tails of the ModemData.txt file generated:

```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.27-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009
 scanModem update of:  2009_02_04

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	103c:30d8	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 16:      41924      42078   IO-APIC-fasteoi   uhci_hcd:usb1, HDA Intel, i915@pci:0000:00:02.0
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.596425] PCI: 0000:00:1b.0 reg 10 64bit mmio: [e4624000, e4627fff]
[    0.596425] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.596425] pci 0000:00:1b.0: PME# disabled
[   11.889925] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   11.889938] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.889967] HDA Intel 0000:00:1b.0: setting latency timer to 64

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.17
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe4624000 irq 16

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: LSI ID 1040
Address: 1
Vendor Id: 0x11c11040
Subsystem Id: 0x103c1378
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040
If not a Conexant modem, the driver agrsm with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801H "
CLASS=0403
PCIDEV=8086:284b
SUBSYS=103c:30d8
IRQ=16
HDA=8086:284b
SOFT=8086:284b.HDA
CHIP=0x11c11040
IDENT=11c11040
Driver=agrmodem+agrserial+patched_snd-hda-intel

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  103c:30d8 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:	11c11040

----------------end Softmodem section --------------

Writing DOCs/Intel.txt

LSI/AgereSystems produces several modem chipsets produces several chipsets supported by
an agrsm software packages. This includes some modems identifiable by their PCI IDs and 
others requiring ALSA diagnostics to recognize the chip, such as the 11c11040 chip hosted
on the Subsystems of many High Definition Audio cards.

There are support packages at http://linmodems.technion.ac.il/packages/ltmodem/11c11040/
The agrsm-tools package supports driver autoloading, but does not itself contain drivers.
For Debian/Ubuntu related distros, there are a few kernel-version specific packages:
   agrsm-2.6.27-7-generic_2.6.27-7.14_i386.deb
   agrsm-2.6.27-9-generic_2.6.27-9.14_i386.deb
are respectively for systems with Ubuntu 2.6.27-7-generic and 2.6.27-7-generic kernels.
   agrsm-ubuntu8.04.1-2.6.24-19-generic.tar.gz is for 2.6.24-19-generic kernels.

The currently used agrsm code is from updates at http://linux.zsolttech.com/linmodem/
see an example at: http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03863.html

Read the Modem/DOCs/Agrsm.txt

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb

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
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 eth1
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


```

---

