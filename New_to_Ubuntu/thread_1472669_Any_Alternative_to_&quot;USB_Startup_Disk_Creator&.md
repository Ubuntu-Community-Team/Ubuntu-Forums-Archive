---
title: "Any Alternative to &quot;USB Startup Disk Creator&quot;?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-04
Hello, 
am having problems using System/Admin/USB Startup Disk Creator.

I want to put desktop-10.04-i386.iso onto my USB and make it bootable. What alternative program/method is there?

Please help.

---

### Post by BugBuster on 2010-05-04
Try unetbootin for linux.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Though it is in the ubuntu repos, I would recommend you download the latest package from the unetbootin homepage. The latest unetbootin build supports the ubuntu 10.04 iso...which i am not quite sure the version found in the repo does.

---

### Post by hanzj on 2010-05-04
BugBuster,
Thanks so much.

[]("https://launchpad.net/%7Egezakovacs/+archive/ppa")[]("http://unetbootin.sourceforge.net/unetbootin-linux-latest")

---

### Post by hanzj on 2010-05-04
I tried to add the PPA but got this
> sudo add-apt-repository ppa:gezakovacs/ppa  

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv BCCCC1E2835433FA7DB85D51D45DF2E8FC91AE7E
gpg: requesting key FC91AE7E from hkp server keyserver.ubuntu.com
[B]
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error[/B]


Please help.

---

### Post by natravis on 2010-05-04
Presuming that you are connected to the internet while this is happening, "gpg: keyserver timed out" may mean that the keyserver is getting slammed and you can try again in a little bit. Or it could be offline, though I doubt that. Wait a few minutes and try to add it again.

---

### Post by frillybob on 2010-05-04
I made mine bootable via command promt! It was strange though! I didn't even use a program. Well I'd tell you how to do it but it looks like you already figured it out!

---

### Post by hanzj on 2010-05-04
I am online. 8-)

---

### Post by hanzj on 2010-05-04
frillybob,
well, this unetbootin alternative is having some problems too, so I would love to hear your command-prompt method.

---

### Post by natravis on 2010-05-04
> **hanzj said:**
> I am online. 8-)

I said presuming (knowing that you were probably posting from the internet connected computer) because I have seen worse. I just tried to grab the key from my office and got a timeout. I guess the keyservers could be getting hit hard with people trying to update.

---

### Post by hanzj on 2010-05-04
is there a way to use the program without the key?

---

### Post by Didius Falco on 2010-05-04
I agree that it is probably just a temporary problem with the keyserver, but if you are in a hurry, you can download the *.deb file you need from here:

[https://launchpad.net/~gezakovacs/+archive/ppa/+packages]("https://launchpad.net/%7Egezakovacs/+archive/ppa/+packages")

Then install it using the following command:

```
sudo dpkg -i package_name.deb 
```

You need to either be in the directory where it is located or specify the path to it. you can also use the GDebi Package Installer, found in **Menu/System Tools** to install it.

Regards,

Didius

---

### Post by hanzj on 2010-05-04
In UNetbootin, what's the difference between 10.04_Live and Daily_Live? Is the Daily one better?

---

### Post by hanzj on 2010-05-04
thanks, didius.

---

### Post by Didius Falco on 2010-05-04
> **hanzj said:**
> In UNetbootin, what's the difference between 10.04_Live and Daily_Live? Is the Daily one better?

The Daily Live are iso files created every day during testing - you want the final release - **ubuntu-10.04-desktop-i386.iso** for a 32 bit install or **ubuntu-10.04-desktop-amd64.iso** for a 64 bit install.

You are very welcome, BTW - just saw your latest post.

---

### Post by hanzj on 2010-05-04
It's interesting that unetbootin, unlike USB Startup Disk creator, doesn't format the USB drive, but immediately starts with the copying of files.

---

### Post by hanzj on 2010-05-04
i used unetbootin and rebooted my comp and booted off the usb drive but, after seeing the new ubuntu 10.04 logo and the horizontal line of dots, i get an error message saying something like "unknown user id".

Aaagh. Wish things would just work.

---

### Post by natravis on 2010-05-04
> **hanzj said:**
> i used unetbootin and rebooted my comp and booted off the usb drive but, after seeing the new ubuntu 10.04 logo and the horizontal line of dots, i get an error message saying something like "unknown user id".

Aaagh. Wish things would just work.

Perhaps you could clarify what problems you had originally with USB System Creator and we could help you with that.

---

### Post by hanzj on 2010-05-04
natravis,

1. the formatting in startup disk creator doesn't work.
[https://bugs.launchpad.net/ubuntu/+s...or/+bug/457737]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/457737")

2. When it seems that startup disk creator does complete the job, the installation process has always got stuck (out of the 4 attempts I did).

---

### Post by oldfred on 2010-05-04
I followed these instructions using grub2  and loop mounting the ISO directly. I just copy the ISO the USB key and edit grub.cfg and boot. And I have several other ISOs on the USB key since mine is 4GB. 

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)

---

### Post by Zionoxis on 2010-05-04
I also have tried this. The computer just says that Windows did not boot properly if I click 'boot from removable storage device'. I tried this on my Netbook after putting it on my flash drive....any idea why?
It is an 8GB and saved as the usual FAT32 (or whatever format Windows 7 reads [I feel like such a noob])

---

### Post by frillybob on 2010-05-04
this only works on vista/win7 srry
 
 
 
. Insert your USB (1GB+ preferable) stick to the system and backup all the data from the USB as we are going to format the USB to make it as bootable. 
 
2. Open elevated Command Prompt. To do this, type in CMD in Start menu search field and hit Ctrl + Shift + Enter. Alternatively, navigate to Start > All programs >Accessories > right click on Command Prompt and select run as administrator. 
3. When the Command Prompt opens, enter the following command: 
DISKPART and hit enter. 
LIST DISK and hit enter. 
Once you enter the LIST DISK command, it will show the disk number of your USB drive. In the below image my USB drive disk no is Disk 1. 
4. In this step you need to enter all the below commands one by one and hit enter. As these commands are self explanatory, you can easily guess what these commands do. 
SELECT DISK 1 (Replace DISK 1 with your disk number) 
CLEAN 
CREATE PARTITION PRIMARY 
SELECT PARTITION 1 
ACTIVE 
FORMAT FS=NTFS 
(Format process may take few seconds) 
ASSIGN 
EXIT 
Don&#8217;t close the command prompt as we need to execute one more command at the next step. Just minimize it. 
5. Insert your Windows (in this case your ubuntu cd) DVD in the optical drive and note down the drive letter of the optical drive and USB media. Here I use &#8220;D&#8221; as my optical (DVD) drive letter and &#8220;H&#8221; as my USB drive letter. 
6. Go back to command prompt and execute the following commands: 
D:CD BOOT and hit enter. Where &#8220;D&#8221; is your DVD drive letter. 
CD BOOT and hit enter to see the below message. 
BOOTSECT.EXE/NT60 H: 
(Where &#8220;H&#8221; is your USB drive letter) 
7. Copy Windows (Ububntu) DVD contents to USB. 
You are done with your bootable USB. You can now use this bootable USB as bootable DVD on any computer that comes with USB boot feature (most of the current motherboards support this feature). Note that this bootable USB guide will not work if you are trying to make a bootable USB on XP computer. 
 
 
sorce- [http://bootdisk.com/pendrive.htm](http://bootdisk.com/pendrive.htm)

---

### Post by hanzj on 2010-05-04
A better alternative to Ubuntu 9.10's USB Startup Disk Creator is... the Ubuntu 10.04 version. I got the 10.04 version and it's much better. formats and installs iso flawlessly.

UPDATE: I'm not so sure if the iso installation is flawless. I've tried several ubuntu isos (desktop amd64; desktop i386, alternate amd64) and I still can't complete the ubuntu 10.04 install.

---

### Post by k3lt01 on 2010-05-05
Old Fred gave you some links to look at in post 19 about 7 hours ago. In your other thread dealing with this same issue I gave you the same link. Try it out.

---

### Post by hanzj on 2010-05-05
will try the "HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2" method[SIZE=4][/SIZE]

---

### Post by C.S.Cameron on 2010-05-05
You might be dealing with a bad iso download.
Check your MD5SUM.

---

### Post by G.D.C. on 2010-05-05
I had a similar issue attempting to create a USB startup disk. To solve the issue where the Startup Disk Creator wouldn't let me format, I had to unmount the drive before I could format it.
 
When I tried to boot from the disk, it seemed that for whatever reason, the USB stick was showing up in the BIOS as a hard drive instead of a removable storage device, and below my internal HD on the list of priorities. I had to change that, and then change it back once the install had completed.

---

### Post by hanzj on 2010-05-05
Could all 4 ISOs be bad?

How do I check the MD5Sum? Where is a copy of the correct MD5Sum?


Found correct md5sum hash numbers at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
(from [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))

---

### Post by hanzj on 2010-05-07
I was able to upgrade to the ubuntu10.04 version of usb-creator-gtk (USB startup disk creator).

I downloaded afresh the ubuntu10.04-desktop-i386 iso and verified the md5sum.
I loaded the iso onto my 1GB SDCard/USBCard-reader.
After the copy was finished, I rebooted the computer and booted from the SDCard/USB.

I choose "Try Ubuntu without installing" option.
The new Ubuntu10.04 logo appears. Then I get a black screen with this message:



> Busybox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

(initramfs) Unable to find a medium containing a live file system..


After this failed attempt, I restarted the computer and tried the "Install Ubuntu" option, but got the same error message.

Help.

---

### Post by k3lt01 on 2010-05-08
hanzj, please stick to using one thread. I have answered your question, partially, on the other thread.

---

### Post by dakra137 on 2010-05-09
YES, there is another alternative to USB Startup Disk Creator, if what you want to do is really **use** what you create, rather than use it to install onto another system:

I did an INSTALL from CD onto an 8GB stick. 

[LIST]
[*]Did NOT select side-by-side installation onto the computer's disk.
[*]Did specify installation onto USB drive.
[*]Set it up as 6GB EXT3 root and 2GB SWAP. 
[*]Clicked on ADVANCED options to install the boot manager onto the stick too.
[/LIST]

By doing this, it has my userid and password. I can install software onto it, have updates automatically processed, etc.

It also boots faster.

When using it, for maximum portability, do not activate any special drivers for the video card on the machine you install at.

---

### Post by malom on 2010-05-12
Hi Dakra,
Could you please provide a link or explain how to do this?
Would love to be able to have my own portable OS on my flash stick.

---

### Post by DrKenobi on 2010-05-12
> **hanzj said:**
> Hello, 
am having problems using System/Admin/USB Startup Disk Creator.

I want to put desktop-10.04-i386.iso onto my USB and make it bootable. What alternative program/method is there?

Please help.

You can make a normal installation in your USB drive. I'm using a USB drive of 4GB as hard drive an it's working fine. I also couldn't use the USB Startup Creator, but I don't recommend it, it took ages to boot if you use it.

---

### Post by oldfred on 2010-05-12
Herman has info on USB flash or SSD drive install:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

I also have a USB set up just for ISO using grub.This is just for installs to save CDs.
MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

---

### Post by kansasnoob on 2010-05-12
I prefer Portable Linux:

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

---

### Post by Linuxforall on 2010-05-12
Been using this since Jaunty and never had any issues really.

---

### Post by hanzj on 2010-05-12
drkenobi,
hmmm. are you suggesting that usb startup creator is used not so much to save on CD-rom installation of ubuntu onto one's hard drive, but as an emergency means of restoring a bad hard drive? 

(I was trying to use usb-startup-disk creator for the purpose of saving myself from burning the ubuntu 10.04 desktop iso onto a compact-disk.)

---

### Post by hanzj on 2010-05-12
I have given up trying to save  a compact disc from being used for a one-time use of installing Ubuntu. I went ahead and burnt ubuntu 10.04 x86 desktop iso onto a 700 mb CD-R, then restarted the computer and did a fresh install. That was problem-free.

---

### Post by DrKenobi on 2010-05-12
> **hanzj said:**
> drkenobi,
hmmm. are you suggesting that usb startup creator is used not so much to save on CD-rom installation of ubuntu onto one's hard drive, but as an emergency means of restoring a bad hard drive? 

(I was trying to use usb-startup-disk creator for the purpose of saving myself from burning the ubuntu 10.04 desktop iso onto a compact-disk.)

I said that you can make a fresh install in your USB Drive.

---

### Post by hanzj on 2010-05-12
drkenobi,
but i didn't want to make a fresh install on my usb drive. I wanted to make the fresh install on my hard drive, and the usb drive was just a desired means to that end.

---

### Post by DrKenobi on 2010-05-12
> **hanzj said:**
> drkenobi,
but i didn't want to make a fresh install on my usb drive. I wanted to make the fresh install on my hard drive, and the usb drive was just a desired means to that end.

hanzj, ok. I also try to use the USB Startup Creator, but it didn't work. Maybe you should follow oldfred's post.

> **oldfred said:**
> Herman has info on USB flash or SSD drive install:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

I also have a USB set up just for ISO using grub.This is just for installs to save CDs.
MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

Sorry for my english, i'm not so good. :)

---

