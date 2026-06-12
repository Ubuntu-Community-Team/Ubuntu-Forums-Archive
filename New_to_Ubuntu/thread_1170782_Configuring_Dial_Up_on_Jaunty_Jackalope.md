---
title: "Configuring Dial Up on Jaunty Jackalope"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2009-05-26
hi...

i just installed Jaunty Jackalope(64x) on my Compaq V3702AU laptop...

i went through earlier posts but couldnt find the appropriate and helpful one for me...

can anyone please help me configure my modem, dial up connection and get connected to net...

i executed scanModem and got a folder named Modem on the desktop but dont know how to get info from the text files in it...

can someone help me with this???

thanks... :-)

---

### Post by Sealbhach on 2009-05-26
Hi, what kind of modem have you got? Does it plug into a USB port?

.

---

### Post by randolf_ambrose on 2009-05-26
i've a built in conexant modem...

i think my modem got recognized with scanModem...

and i installed the gnome-network-admin package using the command sudo dpkg &#8208;i

now i cannot install wvdial, it gives dependency error...
i tried to install a video plugin, it also gives dependency error...

only that gnome-network-admin package could be installed with the command sudo dpkg &#8208;i

what shall i do to get connected to net...

i came this far with the help of this link [https://help.ubuntu.com/9.04/internet/C/modem.html](https://help.ubuntu.com/9.04/internet/C/modem.html)

please... can you help...

thanks for replying...

---

### Post by Sealbhach on 2009-05-26
Thanks, can you copy and paste the scanmodem data in your next post?

gedit Modem/ModemData.txt

This will help identify the modem. 

Did you enter all of your ISP data, phone number etc as suggested in the link you posted?

If so, describe what happens when you try to connect.

It may be that you may have to use Ubudsl: [http://www.ubudsl.com/en/start.php](http://www.ubudsl.com/en/start.php)

It's really easy to use.

.

---

### Post by randolf_ambrose on 2009-05-26
this is my ModemData.txt

[INDENT] Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=x86_64,  
Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009
 scanModem update of:  2009_05_12


Some modem drivers can only be used in 32 bit modem on x86_64 systems,
while some others are competent on x86_64 Systems.  Cases are:
1) [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg03119.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg03119.html) 
for the snd-hda-intel audio+modem driver. Also applicable to AC97 modem controllers.
In both cases, 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component.
2) For USB modems using the slusb.ko driver. 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component
3) The hsfmodem and hcfpcimodem drivers for Conexant chipsest modes are x86_64 competent.

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

Attached USB devices are:
 ID 13ba:0017  
 ID 04f2:b016 Chicony Electronics Co., Ltd 
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:07.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:07.0	10de:055c	103c:30d6	Audio device: nVidia Corporation MCP67 High Definition Audio 

 Modem interrupt assignment and sharing: 
 20:          4       2438   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:07.0 ----
[    0.511258] pci 0000:00:07.0: reg 10 32bit mmio: [0xfc480000-0xfc483fff]
[    0.511276] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.511279] pci 0000:00:07.0: PME# disabled
[    1.296437] pci 0000:00:07.0: Enabling HT MSI Mapping
[   11.193103] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   11.193200] HDA Intel 0000:00:07.0: setting latency timer to 64

 The PCI slot 00:07.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.18
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
00-01: Conexant Digital : Conexant Digital : playback 1

about /proc/asound/cards:
------------------------
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfc480000 irq 20

 PCI slot 00:07.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
UNEXPECTED HDA diagnostic outcome.
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:07.0:
	Modem chipset  detected on
NAME="Audio device: nVidia Corporation MCP67 High Definition Audio "
CLASS=0403
PCIDEV=10de:055c
SUBSYS=103c:30d6
IRQ=20
HDA=10de:055c
SOFT=10de:055c.HDA
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:07.0
   0403 Audio device: nVidia Corporation MCP67 High Definition Audio 
      Primary device ID:  10de:055c
    Subsystem PCI_id  103c:30d6 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	hsfmodem


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt


Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.28_11_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm

Support for Conexant chips hosted on High Definition Audio cards may require
installation of additional packages, one of the alsa-driver-linuxant packages
on  [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)  At the same time download the 
alsa-driver-1.0.17-1.patch , in case it prove to be later needed. During the
hsfmodem install, there will be a message if there is necessary installation of
alsa-driver-linuxant

The installation command for a .deb suffic packages is, with root/adm permission:
  sudo alsa* -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm

There may a message that "Dependencies" are not satisfied.  In this case the Ubuntu/Debian packages to be installed are linux-libc-dev & libc6-dev. Package
names may be different for other Linuxes. If not on your install CD, these
packages can be searched for at [http://packages.ubuntu.com](http://packages.ubuntu.com).  After download,
they can be coinstalled with:
	sudo dpkg -i li*.deb
Again try the alsa-driver-linuxant

There may be a message that the patch must be applied.  In this case get the
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2) 
Under Linux, this package is unpacked with:
$ tar jxf alsa*.tar.bz2
Next the patch is applied with:
$ patch -p0 < alsa-driver-1.0.17-1.patch

See [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html)
for details on compiling and installing replacement snd-hda-intel + its
dependent drivers.
After the installation is completed, rerun the hsfmodem installation.
Reboot and try to detect the modem with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.02full_k2.6.28_11_generic_ubuntu_i386.deb.zip 
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
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.28-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
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

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
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
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

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
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

[/INDENT]

i entered my phone number, user name and passcode... didnt enter DNS addresses...

i configured till this far...

dont know how to connect...

ad far as i know now, i need to install wvdial to connect to net no???
i cannot install wvdial deb file... getting dependency error...

my modem is a built in internal modem... conexant... not USB model... its a dial up modem...

---

### Post by Sealbhach on 2009-05-26
OK, It seems to be a Conexant HSF modem, so you can download the driver for that from here:

[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)

Have a go at that and see how you do. 
.

---

### Post by randolf_ambrose on 2009-05-26
oh...

thanks...

i'l install the driver using the installer...

i will try other things too...

i will give you the feedback in 24hrs...

i gotta go now...

thanks a lot for your help... :-)

---

### Post by randolf_ambrose on 2009-05-26
i'm getting prblems with WVDIAL when i try to connect...

---

### Post by lkraemer on 2009-05-26
/etc/wvdial.conf

should contain something like this, except your modem port
will be different along with user name and password.  Wvdial
should find your modem and set it up.

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = 3211234
Password = mypassword
Username = [email]mylogin@isp.net[/email]


If you haven't run /usr/sbin/pppconfig
you need to do that also to setup pap-secrets or chap-secrets
in /etc/ppp  It is menu driven.




lkraemer

---

### Post by randolf_ambrose on 2009-05-27
i cant even install WVDIAL...

since its installation failed due to lack of dependacy files... i downloaded the dependancy files for WVDIAL...

but when i tried to install those dependancy files, dependancy files of each of those were asked...

is this how it works???

does this mean that i'd have to download the entire plugins???

thats utter ********!!!

every time i try to install something, dependancies are asked when those dependancies are executed, dependancies of those are asked...

what shall i do...

---

### Post by achase79 on 2009-05-27
to download all the dependencies go to keryxproject.org and use that program to download the files you will need from another computer or os.

---

### Post by Sealbhach on 2009-05-27
> **randolf_ambrose said:**
> i cant even install WVDIAL...

...

every time i try to install something, dependancies are asked when those dependancies are executed, dependancies of those are asked...

what shall i do...

That's called "dependency hell" and it's the reason we have package managers in Linux like Synaptic Package manager so it handles all that stuff for you automatically. Is there any way you can get access to a wired internet connection so that you can install wvdial?

.

---

### Post by randolf_ambrose on 2009-05-27
> **achase79 said:**
> to download all the dependencies go to keryxproject.org and use that program to download the files you will need from another computer or os.

i'm downloading this...

thanks... :-)

let me see if it helps... :-)

---

### Post by randolf_ambrose on 2009-05-27
> **Sealbhach said:**
> That's called "dependency hell" and it's the reason we have package managers in Linux like Synaptic Package manager so it handles all that stuff for you automatically. Is there any way you can get access to a wired internet connection so that you can install wvdial?

.

ok...

let me tell you what i have...

i've installed UBUNTU on my laptop...

and i've a desktop loaded with windows and a dialup connection...

i tried to install WVDIAL on my ubuntu but it kept asking for dependancies and subdependancies...

how can i install WVDIAL succesfully from my offline ubuntu...

---

### Post by Sealbhach on 2009-05-27
OK, I've simulated an install of wvdial in my Ubuntu 9.04.

It tells me it will install wvdial and these other packages:

libuniconf4.4 
libwvstreams4.4-base 
libwvstreams4.4-extras 
libxplc0.3.13


So, install them in this order

libxplc0.3.13
libwvstreams4.4-base
libwvstreams4.4-extras 
libuniconf4.4

Then 

wvdial


.

---

### Post by wpshooter on 2009-05-27
All I can says is, that if you manage to get Ubuntu to connect to the Internet on any "consistent" basis via a dialup connection, then you are a better man/woman than me !!!  

I just don't think that this O/S and related software has the polish needed to run via dialup modems.

But good luck.

---

### Post by randolf_ambrose on 2009-05-27
ok...

thanks...

let me download and try...

thanks...

i'll give you the feedback... :-)

---

### Post by robert shearer on 2009-05-28
It is a while since I used dial-up on Ubuntu but here's what worked for me...

On another (connected adsl) machine download and burn an 'alternate install' disc for **Kubuntu**.

Kubuntu has a wonderful dial-up program called 'kppp'.Always worked well for me.
If you try to install it by itself into ubuntu it will bring along a whole lot of kde libraries etc etc and will lead to more dependency hell.

But, if you put your new Kubuntu install disc into your cd drive then synaptic will recognise it as a cd of software packages and ask if you want to add it to your software sources.(if it doesn't in your version of Ubuntu then you can add it manually by opening synaptic and going to settings=>repositories=>thirdparty software=>add cd-rom.

Once it is added to your repositories take the cd out then log out and back in. 

Open synaptic and search for kppp.

Select to install it and accept the other packages it drags along.

You will be asked to insert the Kubuntu cd and kpp etc will be downloaded from the cd and installed with all dependencies. Presto.!

**NOTE** I am assuming that Kubuntu still ships with kppp on the install disk.You might want to search the package site and check this **before starting** this workaround.

Note also that the Kubuntu version should be the same as the installed version of Ubuntu.  

(I will go and check too and post back)

EDIT.. looks like kppp was left off the cd(at least the live cd, still looking to see if it is on the alternate) fromm version 8.10 onwards.

EDIT#2 looks like kppp is on the 9.04 cd if this post is correct 

[http://www.nabble.com/Need-to-connect-to-internet-after-installing-9.04-td23326043.html](http://www.nabble.com/Need-to-connect-to-internet-after-installing-9.04-td23326043.html)

Anyone else using kubuntu can confirm please??? is kppp still on the install disc??


Here is something else to try.. If your original Ubuntu install cd was the live cd then reboot using it and try to connect.I recall that the gui networking window allowed a setup for dial-up that worked live but did not once it was installed.

If so then the wvdial package is on the install cd but not being installed.

Back on your installed version open a terminal and type

```
sudo gedit /etc/apt/sources.list 
```

then enter your password. 

when the sources list opens you will probably see that the install cd has been commented out.(has a # symbol at the beginning of its line)

Delete the # symbol and save and close. Open synaptic and use the "reload" then search for wvdial. Should be there and installable from the cd.

(you may need to log out and back in before opening synaptic?)

EDIT3   OK I am obviously way out of touch with current dial-up. Just booted a 9.04 live cd and looks like none of the above apply. Apologies.

I was able to all but connect however(all but because I no longer have dial-up so cannot connect) by using pppconfig and pon/poff.

Open a terminal and type

```
 sudo pppconfig
```

which should give you a set-up screen if all goes well then using

```
sudo pon 
```

should start a connection and allow you to download wvdial.

```
sudo poff 
```

will stop the connection

this caused my modem(external) to dial.

Sorry about the long post and sidetracks.

---

### Post by randolf_ambrose on 2009-05-28
wow thanks...

i'll try that...

i've my wifi working but i wish to get my dial up also working... thats why...

thanks...

---

### Post by lkraemer on 2009-06-06
How is your progress going?  Dialup working yet?

Modem Install Guide
REF:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Posting #4

Keep us informed.

lkraemer

---

### Post by GeorgeVita on 2009-06-06
Hi ** randolf_ambrose**, **Sealbhach**, **lkraemer**, **achase79**, **wpshooter**, **robert shearer**.

Please add me to those need to have **wvdial** and associated tools within Ubuntu ... just to help others use their old (dial up) or very new (3G) modems! Below is a copy of a post of me:

There are 5 .deb packages to install. You could make a zip file with all of them (be sure to check their integrity and 32/64 bit version).

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

My .zip file for i386 32bit (Info and checksums included, size: 1,04 MB):
[http://www.acomelectronics.com/GeorgeVita/wvdial_904_i386.zip](http://www.acomelectronics.com/GeorgeVita/wvdial_904_i386.zip)

I test it by copying all to a USB memory stick, and then paste them (or unzip them) to the ubuntu 9.04 running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal. Then I installed all packages by double clicking each icon (of .deb package) in "as listed in above" order (1,2,3,4 and finally 5).

I think if anybody wants to automate this, he could edit the .iso creating a new 9.04_wvdial distro:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
... or wait & hope 9.10 to include it.

Regards,
George

---

