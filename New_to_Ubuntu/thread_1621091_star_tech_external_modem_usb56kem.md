---
title: "star tech external modem usb56kem"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by ibdonna on 2010-11-13
hi downloaded the modem tool finder. Not sure if it the external modem is recognized could some take a look for me please. Any other help with installing it would be really appreciated

Am at a friends house using their internet connection to post this thanks again

Donna


 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.35-22-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=1.0.23
Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010
 scanModem update of:  2010_05_29

Distrib_ID=Ubuntu
DistribCodeName=maverick
AptRepositoryStem=http://ca.archive.ubuntu.com/ubuntu/


The dkms driver upgrade utilities are installed,

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
       snd_hda_intel           

Attached USB devices are:
 ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
 ID 0572:1300 Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP
 ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is:  [http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html](http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

Candidate PCI devices with modem chips are:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
High Definition Audio cards can host modem chips.

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:293e	1028:02aa	Audio device: Intel Corporation 82801I 

 Modem interrupt assignment and sharing: 
 46:        849   PCI-MSI-edge      hda_intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.243791] pci 0000:00:1b.0: reg 10: [mem 0xf6afc000-0xf6afffff 64bit]
[    0.243852] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.243857] pci 0000:00:1b.0: PME# disabled
[   10.349320] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.349390] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   10.349422] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.641040] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.641249] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2
00-01: STAC92xx Digital : STAC92xx Digital : playback 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6afc000 irq 46

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.35-22-generic/kernel/sound/pci/hda/snd-hda-intel.ko

 The HDA diagnostics did not recognize a modem chip on the audio subsystem,
 though a Conexant chip modem might not be recognized.

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 006:
	Modem chipset  detected on
SLOT="Bus 006 Device 002:"
NAME="Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP"
bus=006
USBmodemID=0572:1300
IDENT=hsfmodem
Driver=hsfmodem

For a detailed USB cellphone usage report, see [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03240.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03240.html) 
 For candidate modem in:  006
    Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP
      Primary device ID:  0572:1300
 Support type needed or chipset:	hsfmodem
 


Writing DOCs/Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt


For all code packages from Linuxant.com, either a driver set matching the boot kernel will be installed,
or the drivers will first be compiled and then installed. The expert on modem software for Linux is
"Support (Jonathan)" <modem.support@linuxant.com>

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.06full_k2.6.35_22_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 The directions following below need only be pursued, if the above procedures are not adequate.

Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.35_22_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, the needed drivers 
will be auto compiled anyway. Alternatively, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt



Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
NAME="Audio device: Intel Corporation 82801I "
CLASS=0403
PCIDEV=8086:293e
SUBSYS=1028:02aa
IRQ=46
HDA2=00:1b.0
SOFT=8086:293e.HDA

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
    Subsystem PCI_id  1028:02aa 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD_gcc4.4_alsa1.0.23.tar.gz from:
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)


 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.5
             and the compiler used in kernel assembly: 4.4.5

 linux-headers-2.6.35-22-generic resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.35-22-generic


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 273248 2010-07-09 12:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

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

For guidance on FAX usage, get from [http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/)  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by lkraemer on 2010-11-14
Donna,
Your Modem was detected:

[B]Attached USB devices are:
ID 0572:1300 Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP[/B]

Your information that was posted should have been sent to Marvin and the
folks at [http://www.linmodems.org](http://www.linmodems.org), as a **plain text email.**

But, for right now why don't you install wvdial and it's dependencies and
see if wvdial detects the modem.  You might find it works......

You need to download wvdial and the following dependencies for 10.04,
or whatever version you have installed......

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.


You will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```


Now after ppp is setup, you will need to set up wvdial. Power up the modem, and connect it to your port.
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```


Ref:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Posting #4

lk

---

### Post by azertyh on 2010-11-14
hello,
see the links that i posted in this topic [http://ubuntuforums.org/showthread.php?t=1620307](http://ubuntuforums.org/showthread.php?t=1620307)

---

### Post by ibdonna on 2010-11-21
lkraemer and azertyh success not really sure how it all happen  followed your directions and read all the links you posted.

Must say the more I read the more baffled I was but it worked.

I am now on the internet with ubuntu. Can not thank you all enough for all your help.

Thank you Donna.

---

