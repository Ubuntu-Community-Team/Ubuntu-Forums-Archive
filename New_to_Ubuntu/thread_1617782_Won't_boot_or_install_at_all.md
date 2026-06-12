---
title: "Won't boot or install at all?"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Siorus on 2010-11-09
Hi all,
I'm trying to get Ubuntu v10.10 installed on an old AMI MegaPlex server, but I cannot get it to boot the live version or run the installer. It gets to the main menu where it asks if you want to install the OS, rescue an existing installation, boot the live install, etc., but it won't get any further. When I tell it to boot the live install or install directly and hit enter, the screen goes blank and then it goes into standby, the activity light on the DVD drive blinks intermittently for a few minutes and then it just sits.

The Fedora 13 live CD boots fine on this thing, but I haven't found Fedora to be very user-friendly, and I'd like to get Ubuntu running if at all possible.

Here's the relevant technical specs/info on the machine:
[LIST]
[*]AMI MegaPlex quad Slot 2 server motherboard w/Intel 450NX chipset & 3 separate PCI busses (video card is in Slot #1 on the primary bus)
[*]4x 450MHz Pentium II Xeon CPUs
[*]4GB (32x128MB) ECC/REG EDO
[*]PCI GeForce FX5200
[*]Teac DVD-ROM from 2004 (maybe this is the problem? Either not compatible with Ubuntu or it doesn't like the DVD-R media I'm using?)
[*]320GB WD Scorpio Blue 2.5"/5.4k IDE drive (all I had sitting around; the BIOS obviously doesn't see the whole drive)
[*]Ubuntu v10.10 **DVD** (I haven't tried the CD version yet)
[/LIST]

I'm going to give the Ubuntu 10.10 CD and Mint v9 w/kde a try to see how either one of those work; has anyone got any other suggestions?

Thanks.

---

### Post by migs73 on 2010-11-09
Did you verify the ISO image after download/burning?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Siorus on 2010-11-09
No, but it's the same DVD I used to put 10.10 on the box that I'm posting from now, so the disc itself ought to be fine.

It doesn't seem to have liked the CD version any better. I'm beginning to think that there's something about this machine that Debian-based OSes just don't like, but I won't be able to confirm that until I get Mint burned.

---

### Post by nm_geo on 2010-11-09
> **migs73 said:**
> Did you verify the ISO image after download/burning?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


Thanks migs73 good information

---

### Post by amjjawad on 2010-11-09
[LEFT]As migs73 said:
[/LEFT]
 > > **migs73 said:**
> did you verify the iso image after download/burning?

[https://help.ubuntu.com/community/howtomd5sum](https://help.ubuntu.com/community/howtomd5sum)

And I suggest to use USB/Pen Drive for faster performance as you may know CDs/DVDs are slower.
If there's no option to boot up from USB in your BIOS (there's a solution for this issue if you're interested) then you could use a CD instead of a DVD.

---

### Post by nm_geo on 2010-11-09
Good point amjjawad I ran on a live USB for a week or two before installing.

---

### Post by amjjawad on 2010-11-09
> **Siorus said:**
> No, but it's the same DVD I used to put 10.10 on the box that I'm posting from now, so the disc itself ought to be fine.

It doesn't seem to have liked the CD version any better. I'm beginning to think that there's something about this machine that Debian-based OSes just don't like, but I won't be able to confirm that until I get Mint burned.

What version exactly are you using? the server version or the desktop version?
If you're using the desktop version, it might not be able to recognize your hardware some how (NOT SURE about this but I'm just assuming).

---

### Post by Siorus on 2010-11-09
> **amjjawad said:**
> What version exactly are you using? the server version or the desktop version?
If you're using the desktop version, it might not be able to recognize your hardware some how (NOT SURE about this but I'm just assuming).

I am indeed using the desktop version. That same thought (about it not recognizing the hardware) had crossed my mind as well. The reason I haven't tried the server version yet is that as I understand it, it comes with just a command line interface, and I dismissed it as something that I didn't really want to deal with.

However, since you brought it up, I did some searching and if all it takes to get the Gnome desktop environment running on 10.10 server is logging in and typing "sudo apt-get install ubuntu-desktop" (which is what [this article]("https://help.ubuntu.com/community/ServerGUI") appears to imply, although that deals with 9.10), that might be a valid option.

Booting from USB is basically a non-starter on this thing; it's from something like 1997 or 1998. I'd need a bootable USB 2.0 PCI card.

---

### Post by amjjawad on 2010-11-09
> **Siorus said:**
> I am indeed using the desktop version. That same thought (about it not recognizing the hardware) had crossed my mind as well. The reason I haven't tried the server version yet is that as I understand it, it comes with just a command line interface, and I dismissed it as something that I didn't really want to deal with.

When you mentioned your machine has 4 CPUs which means it's pure server machine, I thought it could be the issue. That's why there are two versions, Desktop and Server.

> 
However, since you brought it up, I did some searching and if all it takes to get the Gnome desktop environment running on 10.10 server is logging in and typing "sudo apt-get install ubuntu-desktop" (which is what [this article]("https://help.ubuntu.com/community/ServerGUI") appears to imply, although that deals with 9.10), that might be a valid option.
Yes, you could do that. If your machine is not pure server and has only (for example) Intel CPU, I could have said use the Desktop version because a Server Edition with GNOME Desktop would be the same as the Desktop version but of course it's different in your case. I think it's better to use the Server Version and then install the desktop manager you like.

> 
Booting from USB is basically a non-starter on this thing; it's from something like 1997 or 1998. I'd need a bootable USB 2.0 PCI card.You need this:
[Plop]("http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/")
Unless, you don't have USB port.

Trust me, I know very well what does it mean when you're dealing with a [very old machine]("http://ubuntuforums.org/showthread.php?t=1590614"). Oh boy, I don't want to remember my suffering for the last week with that machine :)

---

### Post by ezsit on 2010-11-09
Forget the server version, try the Alternate CD. The Alternate CD is the same as the desktop install just with a text based installer. At the end of installation you will have the desktop version installed. The Alternate version works great on almost all hardware.

---

### Post by Siorus on 2010-11-11
I've been playing with this for the past couple days in between other projects. It's time-consuming because this thing takes about 5 minutes to complete its POST.

Anyhow, I got Fedora installed and running from the hard drive but I bricked it trying to get the nVidia driver installed. I noticed it complained about some addressing issue or something while it was loading but the message went by too fast for me to see what it was actually saying so... Not much use as far as getting an idea of why Ubuntu is unhappy goes.

I've had more luck with the Ubuntu alternate cd than I did with the live discs; it's actually successfully completed the installation off of the alternate CD, but it won't boot. It displays a cursor for a few seconds and then goes to a blank screen and just sits.

I'm trying the server version now just to see what happens.

> **amjjawad said:**
> You need this:
[Plop]("http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/")
Unless, you don't have USB port.

Trust me, I know very well what does it mean when you're dealing with a [very old machine]("http://ubuntuforums.org/showthread.php?t=1590614"). Oh boy, I don't want to remember my suffering for the last week with that machine :)

Yes, but it's worthless when all of your USB ports are v1.1; CDs are faster. ;)

---

