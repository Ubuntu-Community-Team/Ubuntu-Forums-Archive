---
title: "proprietary fglrx driver"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by MOLicious on 2010-05-02
First I am a Forum Noob, Secondly I'm a Ubuntu Noob.., 
 i have an old acer,
which the D2D recovery can no longer recover the system to factory  Settings and OS. My Acer specs are listed below.

Specifications

* ACER Extensa 5420
* AMD Turion 64x2 Mobile [[COLOR=#00c800][COLOR=#00C800 ! important][FONT=arial][COLOR=#00C800 ! important][FONT=arial]Technology[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://phoronix.com/forums/showthread.php?p=125530#")  TL-58 (1.9GHz)
* ATi Mobility Radeon HD 2400 XT Video Chipset(256MB Discrete Ram)
* 2GB DDR2 Ram
* 250GB (5400rpm) S-ATA HDD (dual drives)
* 15.4" WXGA CrystalBrite LCD (1280 x 800)
* DVD-Super Multi Optical Drive
* Media Card Reader (SD, Memory Stick, Pro, xD)
* VGA output
* S-Video output
* D-sub output
* 4 USB 2.0 ports
* Firewire
* Infrared port
* Analog [[COLOR=#00c800][COLOR=#00C800 ! important][FONT=arial][COLOR=#00C800 ! important][FONT=arial]modem[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://phoronix.com/forums/showthread.php?p=125530#")
* Microsoft Windows Vista Home Premium


I installed Ubuntu 10.04 LTS

video problem, 
VGA out... Is connected to a LCD tv (which is being used for a second monitor) second monitor is recognized under....SYSTEM>PREFERENCES>MONITORS...... as unknown. I can change the resolution size, only one resolution works, but the flicker and distortion destroy the image very badly. I   could change refresh rate but only one value available.
I decided i might need to try the "proprietary fglrx driver"

followed directions on this page,[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
(yes i know these instructions are for another build of both Ubuntu and fglrx, but thought was close enough) 
get error at step 11.
(yes i know i need to change the file name from 9-10-.... to 10-4-.....)
the error reads as follows

execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No  such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.uHeMrv

not sure on how to fix my little problem and would appreicate any input  and advice thank you all.

---

### Post by madjr on 2010-05-02
well is not so old because yours is better Acer than mine and this one is like 2 years old

is your video card supported by the official ati drivers?

i can only use the open source driver because ati dropped support for my card, but works well for what i do

but envy should tell you. Remember to backup and have cd ready in case you need to revert back or reinstall


[http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic](http://ubuntuguide.net/install-nvidiaati-graphics-card-driver-in-ubuntu-910karmic)

[http://linuxers.org/howto/how-install-nvidiaati-graphic-cards-drivers-ubuntu-using-envy-ng](http://linuxers.org/howto/how-install-nvidiaati-graphic-cards-drivers-ubuntu-using-envy-ng)

[https://launchpad.net/envy](https://launchpad.net/envy)

am not sure if envy is out yet for 10.04 could take a week or 2

but you can contact the author
[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

---

### Post by MOLicious on 2010-05-02
I purchased this machine in July of 07, she's aging. 
I just installed Ubuntu last night so ....
I don't know what I have

---

### Post by sadaruwan12 on 2010-05-02
I don't know why it's not working on your laptop with that ATI I have a pretty old VGA card from ATI it's a Radeon X1551 but the binary drivers that comes with Ubuntu works just fine out of the box for me.

Try envy and try the drivers from ATI or other wise before doing that connect your laptop to the net and try System -> Administration -> hardware Drivers. See if any new binary drivers get listed there if get listed then install them that might solve the problem.

---

### Post by MOLicious on 2010-05-02
[https://launchpad.net/envy](https://launchpad.net/envy) where is the download button i cant for the life of me find it?

[

---

### Post by MOLicious on 2010-05-02
> **sadaruwan12 said:**
> Try envy and try the drivers from ATI or other wise before doing that connect your laptop to the net and try System -> Administration -> hardware Drivers. See if any new binary drivers get listed there if get listed then install them that might solve the problem.


I can't seem to find a download button for envy,

system>admin>hardware drivers just give me the wireless card

need answer to error message

execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No  such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.uHeMrv

am i doing something wrong after downloading? before installing? Do I need envy to install the driver i already downloaded?

---

### Post by sadaruwan12 on 2010-05-02
> **MOLicious said:**
> [https://launchpad.net/envy](https://launchpad.net/envy) where is the download button i cant for the life of me find it?

[

[Click Me]("http://albertomilone.com/envyngfaq.html#A"), Use these instructions to get your envy copy.

---

### Post by sadaruwan12 on 2010-05-02
> **MOLicious said:**
> I can't seem to find a download button for envy,

system>admin>hardware drivers just give me the wireless card

need answer to error message

execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No  such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.uHeMrv

am i doing something wrong after downloading? before installing? Do I need envy to install the driver i already downloaded?

Well the error is to say that the Catalyst Control Center file is not there and have not been compiled I got the similar error when I use the driver installer from the ATI so buildpackage command is getting exited.

It's not a problem occurs something done by you but it's problem because of ATI's lack of Linux support.

Envy is a GUI front end which will help you to install drivers with out getting too complicated.

---

### Post by MOLicious on 2010-05-02
thank you for your assistance

---

### Post by FlapBags on 2010-05-06
I own an Acer Extensa 5420, and it does NOT have HD graphics, it has a Radeon X1250 in it.

Its also NOT dual hard drives, its Dual Partitions on a single drive, there is no way to install TWO drives in your laptop sir.

But now that you have the correct information about your hardware, allow me to say that there apparently is no proper drivers for our laptop right now for Ubuntu x64

The current drivers ATi  offers for the x1250 will not install on ubuntu 10.04 x64 LTS

root@Ubuntu-acer:~# sh /home/devadmin/Downloads/ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.zL6f67
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.zL6f67
root@Ubuntu-acer:~#

---

### Post by ublackwhiteu on 2010-05-18
> **sadaruwan12 said:**
> Well the error is to say that the Catalyst Control Center file is not there and have not been compiled I got the similar error when I use the driver installer from the ATI so buildpackage command is getting exited.

It's not a problem occurs something done by you but it's problem because of ATI's lack of Linux support.

Envy is a GUI front end which will help you to install drivers with out getting too complicated.

well, I got the same error, but 
1. envy gives an error as well in karmic (might be, because I got 2 gfx cards .. but that's a wild guess)
2. envy does not support lucid

so, any other ideas on how to solve this?

@ MOLicious : how did you solve your problem?

---

### Post by proxess on 2010-05-18
There are no FGLRX for for non-HD ATi GPUs unless you're using 8.10 and catalyst 9.2. Use the FOSS drivers in Lucid. They're awesome anyway.

---

