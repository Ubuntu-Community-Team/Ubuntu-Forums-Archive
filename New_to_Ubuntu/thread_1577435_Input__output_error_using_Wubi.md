---
title: "Input / output error using Wubi"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by Iminister on 2010-09-18
Not Quite Solved but Moving On

Well spent a lot of hours trying this thing and I have run into ridiculous problems. I am trying to get it to work on an old T2862 with 504Mb Ram from Walmart. Wubi loaded Kubuntu and that worked but I didn't like it. I took the computer home but did not have internet. Somehow I got Wubi to start loading Ubuntu but then I hit the [COLOR=Red][COLOR=Black]errno5, input/output error. Needless to say this is an impossible error that seems to randomly get bypassed by some. I tried everything. So I tried two HP CD-rs burned at x8 speed. Then I got the following when booting from DVD rom and from USB stick:

[/COLOR][/COLOR]Intel(R) Boot Agent Version 4.1.08
Copyright (C) 1997-2002, Intel Corporation

Intel (R) Boot Agent PXE Base Code (BA1210BC)
Copyright (C) 1997-2003, Intel Corporation

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent

Look I'm a systems guy not a programmer and it has become pretty clear to me that Ubuntu will not work for my needs. If there is some magic wisdom out there lay it on me but I'm done reading through hosts of posts that don't work.

All hardware is working under Windows XP.

All Ubuntu versions are 10.04

---

### Post by uRock on 2010-09-18
What graphics card does your system have?

Did you download the correct image for your CPU's architecture? (32bit or 64bit)

Have you hit any key when the first purple screen comes up, so that you can test the disks you have [burn]("https://help.ubuntu.com/community/BurningIsoHowto")t?

You can also [MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM") your disks to see if the image properly downloaded.

You may also want to try downloading and [running]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate") the[ Alternate Installer]("http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-alternate-i386.iso.torrent").

---

### Post by Iminister on 2010-09-18
> **uRock said:**
> What graphics card does your system have?

Did you download the correct image for your CPU's architecture? (32bit or 64bit)

Have you hit any key when the first purple screen comes up, so that you can test the disks you have [burn]("https://help.ubuntu.com/community/BurningIsoHowto")t?

You can also [MD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM") your disks to see if the image properly downloaded.

You may also want to try downloading and [running]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate") the[ Alternate Installer]("http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-alternate-i386.iso.torrent").

Thanks uRock

Yes on 32 bit

I was able to run it as a "live CD" or "demo" when I had Wubi load it up. Like you hit Esc when booting it up. But I didn't know about the purple screen thing and hit a key.


I will try MD5Sum but I don't think it is a CD problem

Alternate Installer sounds complicated. I have read some about it.

---

### Post by Krios on 2010-09-18
I'm not sure what you're trying to accomplish, and since I'm relatively new to Ubuntu myself, I'd like to ask you, are you trying to dual boot? are you trying to run Ubuntu by itself? What I've done in the past while learning, is just reinstall the system. You said it was an old computer, but is it your only computer? Regardless, if you're wanting a dual boot, what I've done is to use Windows to erase the Ubuntu and clean off the HD except for Windows, (because I'm dual booting) then reinstall Ubuntu. I switched from Kubuntu because it didn't allow me the flexibility that Ubuntu allows, however, that may be because I'm not that familiar with Kubuntu to begin with. Regardless, Ubuntu loaded fine and I've customized it and am now using it more than Windows. I love it!

---

### Post by CharlesA on 2010-09-18
Normally "Input/Output Error" either means that the OS is having problems reading the CD, or the hard drive is having problems.

Judging from the "Intel (R) Boot Agent PXE Base Code (BA1210BC)" it looks like it's trying to boot off the network. I'm guessing the hard drive is having problems.

Are you able to boot into Windows at all? Wubi installs inside Windows, and it's not a true dual-boot type thing.

---

### Post by beew on 2010-09-18
Install Ubuntu in an external drive and then plug it in and see if it works. Wubi is not a real installation (neither is running from a live CD because you won't be able to modify kernel by changing graphic drivers etc, but Wubu is not even live CD, it is a Windows program basically)

Now since you only have ~500mb you may want to try Lubuntu instead,--I have tried to install Ubuntu on an old machine with 514 mb or ram and it was really sluggish but Lubuntu worked beautifully, needed some work for the broadcom wireless card but it was fixed easily after installing the right packages. Also, I have never been able to get KDE to work on wireless  and I have tried different machines so you may want to keep that in mind. (Not to spread FUD against KDE but this is my experience with KDE and other people I know tried to install Kubuntu and similarly couldn't get wireless to work)

---

### Post by jtarin on 2010-09-18
> **CharlesA said:**
>  Wubi installs inside Windows, and it's not a true dual-boot type thing.I was just about to make a correction to that statement, but I see it has been corrected.
> Sharing a computer between two operating systems often requires dual booting. You can use either operating system on the computer, but not both at once. Each operating system boots from and uses its own hard drives or disk partitions.
This is what I would recommend to the OP but if the desire is to install inside Windows a word of caution this can lead to varied difficulties not often solvable due to the unique configuration of the host environment.

---

### Post by wilee-nilee on 2010-09-18
I have found that a full install to a thumb is pretty usable. You just have to make sure the grub bootloader goes to the MBR of the thumb though. Ubuntu unpacks to 2.4 gigs so you just have to choose a thumb of the size that you think will work for you.

Sorry it didn't work for you otherwise.

---

### Post by beew on 2010-09-18
> **wilee-nilee said:**
> I have found that a full install to a thumb is pretty usable. You just have to make sure the grub bootloader goes to the MBR of the thumb though. Ubuntu unpacks to 2.4 gigs so you just have to choose a thumb of the size that you think will work for you.

Sorry it didn't work for you otherwise.

Actually I would suggest a full installation in an external hard disk (like an old 20G hard drive) instead of a thumb drive. I have a full install in a 8 G thumb drive,  it works but kind of slow. A liveusb with persistence however is fast because like a live CD it uses ram directly, but not a real installation (but a live usb with persistence doesn't support modifying the system like installing graphic drivers so it may not be useful for tetsing if OP is having problem with graphic drivers)

---

### Post by bodhi.zazen on 2010-09-18
> **jtarin said:**
> I was just about to make a correction to that statement, but I see it has been corrected.
This is what I would recommend to the OP but if the desire is to install inside Windows a word of caution this can lead to varied difficulties not often solvable due to the unique configuration of the host environment.

wubi is in fact dual booting. wubi uses the windows boot loader and the ubuntu "partition" is a file that is loop mounted.

[img]http://wubi-installer.org/images/boot-screen.jpg[/img]

See also:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

I doubt the OP problem is related to wubi, it is either a hardware problem, bad burn, or too little RAM.

---

### Post by CharlesA on 2010-09-18
Thanks for the info bodhi.zazen. I wasn't sure how Wubi worked, since I've always installed Ubuntu in VMs instead of from inside Windows.

I still have a feeling that the cause of the problem is hardware related.

---

### Post by jtarin on 2010-09-18
> **bodhi.zazen said:**
> wubi is in fact dual booting. wubi uses the windows boot loader and the ubuntu "partition" is a file that is loop mounted.

You can debate that point with the Redhat manual:
> Appendix G. Configuring a Dual-Boot System
Sharing a computer between two operating systems often requires dual booting. You can use either operating system on the computer, but not both at once. _Each operating system boots from and uses its own hard drives or disk partitions_.


---

### Post by jtarin on 2010-09-18
Are you still not able to boot with the Live CD? If you can get to the Gnome desktop and using a terminal give us the output of ```
sudo fdisk -l
```

---

### Post by CharlesA on 2010-09-18
The wubi partition is mounted the same way you mount an ISO.

---

### Post by jtarin on 2010-09-18
> **CharlesA said:**
> The wubi partition is mounted the same way you mount an ISO.

Yes but you can't move a CD/DVD drive....a partition block where it expects to mount can be changed.Therefore I think this is a logical debate on hardware versus software.I stand corrected if this assumption is improbable.

---

### Post by jtarin on 2010-09-18
The system doesn't know where to look for the boot data.
```
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent
```
This shows it's trying to boot across the network and not finding an image to download.

---

### Post by CharlesA on 2010-09-18
> **jtarin said:**
> The system doesn't know where to look for the boot data.
```
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent
```
This shows it's trying to boot across the network and not finding an image to download.

Indeed. It would be a good idea to check the bios to see if the boot order is correct, as well as make sure that the hard drive is being detected correctly.

---

### Post by jtarin on 2010-09-19
And heed the message "Check cable"

---

### Post by bodhi.zazen on 2010-09-19
> **jtarin said:**
> You can debate that point with the Redhat manual:

Wubi is dual booting and your seem fixated on some type of physical partition. You cna boot a CD or DVD, Grub can boot an iso, SLAX and Wolvix can also boot from an ISO, you can use a flash drive if you wish, and wubi uses a loop mounted file. These are variations on the "partition" theme.

wubi certainly is not virtualization and one is not running ubuntu within windows in any way. You boot Windows or Ubuntu, one or the other, not both at the same time.

---

### Post by jtarin on 2010-09-19
I'm glad you enlightened me on fixations it seems they abound.....and you may call WUBI a dual boot if you would like, however it is not by definition a true dual boot. You can paint a pig and its still a pig.:P
_We probably should get back on topic and address the OP's problem rather than mine._

---

### Post by waynefoutz on 2010-09-19
> **jtarin said:**
> I'm glad you enlightened me on fixations it seems they abound.....and you may call WUBI a dual boot if you would like, however it is not by definition a true dual boot. You can paint a pig and its still a pig.:P

It is dual booting. The Wubi install is an independent OS. It's not a stable install by any means, and the fact that a lot of new users are using it as a permanent install is something I don't condone. It is a great way to give Ubuntu a test run, and kick the tires, but it's not meant to be used for the long haul. 

As for the original poster, make sure you delete all traces of the first wubi install where you tried to install Kubuntu. Make sure you delete the \ubuntu folder from your Windows hard drive. Then give it another go. Instead of downloading and burning the CD, just go to [http://wubi-installer.org/]("http://wubi-installer.org/") and download the .exe file and wubi will download the proper iso file for you, no need to burn a disk. When you've made up your mind, burn a disk and install it for real.

---

### Post by jtarin on 2010-09-19
> **waynefoutz said:**
> It is dual booting.Sorry, but I've drawn the line in the sand.:P

---

### Post by jtarin on 2010-09-19
Do we agree it is at least a loopback device that is trying to be mounted?

---

### Post by waynefoutz on 2010-09-19
> **jtarin said:**
> Sorry, but I've drawn the line in the sand.:P

It modifies the MBR and uses the Windows bootloader.

---

### Post by waynefoutz on 2010-09-19
> **jtarin said:**
> Do we agree it is at least a loopback device?

ok, I'll give you that...

---

### Post by jtarin on 2010-09-19
> **waynefoutz said:**
> It modifies the MBR and uses the Windows bootloader.WUBI is an entry in the Windows bootloader. The only change to the MBR is the one that Windows
makes when writing a new loader to the MBR after the entry has changed via bcedit.

---

### Post by Iminister on 2010-09-19
> **Krios said:**
> I'm not sure what you're trying to accomplish, and since I'm relatively new to Ubuntu myself, I'd like to ask you, are you trying to dual boot? are you trying to run Ubuntu by itself? What I've done in the past while learning, is just reinstall the system. You said it was an old computer, but is it your only computer? Regardless, if you're wanting a dual boot, what I've done is to use Windows to erase the Ubuntu and clean off the HD except for Windows, (because I'm dual booting) then reinstall Ubuntu. I switched from Kubuntu because it didn't allow me the flexibility that Ubuntu allows, however, that may be because I'm not that familiar with Kubuntu to begin with. Regardless, Ubuntu loaded fine and I've customized it and am now using it more than Windows. I love it!

I don't care whether I dual boot or not. I'll take anything at this point. I just wanted to try out Ubuntu through Wubi. I liked it and could get used to it. Wubi won't work now because I don't have internet connection in Win XP but it never did completely load Ubuntu so I used Kubuntu which I didn't like. Then I tried to boot from the Live CD and just install Ubuntu but that failed. I wan't it to work but it won't.

---

### Post by Iminister on 2010-09-19
> **CharlesA said:**
> Normally "Input/Output Error" either means that the OS is having problems reading the CD, or the hard drive is having problems.

Judging from the "Intel (R) Boot Agent PXE Base Code (BA1210BC)" it looks like it's trying to boot off the network. I'm guessing the hard drive is having problems.

Are you able to boot into Windows at all? Wubi installs inside Windows, and it's not a true dual-boot type thing.

Windows has no problems and I hesitate to just delete it, reformat the hard drive, and try and install Ubuntu because it doesn't look like Ubuntu can install. Umm... I don't know about booting from a network. I see that option come up when the system starts up but I don't hit the button to do that. The boot order is: DVD, Usb, HDD.

---

### Post by Iminister on 2010-09-19
> **bodhi.zazen said:**
> 

I doubt the OP problem is related to wubi, it is either a hardware problem, bad burn, or too little RAM.

Please, please tell me it is too little ram!

---

### Post by Iminister on 2010-09-19
> **jtarin said:**
> Are you still not able to boot with the Live CD? If you can get to the Gnome desktop and using a terminal give us the output of ```
sudo fdisk -l
```

thanks Jtarin but nothing will work now because it won't load from the ISO because of the second problem I stated at the open.

---

### Post by Iminister on 2010-09-19
> **jtarin said:**
> The system doesn't know where to look for the boot data.
```
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent
```This shows it's trying to boot across the network and not finding an image to download.

I think that is helpful jtarin but how do I stop it from booting on a network... I don't really know what that means. I do not have that in the BIOS boot options that I know of. DVD is first, followed by USB, then HDD.

---

### Post by Iminister on 2010-09-19
> **CharlesA said:**
> Indeed. It would be a good idea to check the bios to see if the boot order is correct, as well as make sure that the hard drive is being detected correctly.

Thanks CharlesA. Windows XP boots flawlessly... I mean for Windows. I don't even know what the boot option would be for a network in the BIOS but it is not in my current order at all.

---

### Post by Iminister on 2010-09-19
> **jtarin said:**
> And heed the message "Check cable"


Thanks jtarin but it can boot Windows XP and I can read all drives in Windows XP and use them... read/write.

---

### Post by Iminister on 2010-09-19
> **waynefoutz said:**
> It is dual booting. The Wubi install is an independent OS. It's not a stable install by any means, and the fact that a lot of new users are using it as a permanent install is something I don't condone. It is a great way to give Ubuntu a test run, and kick the tires, but it's not meant to be used for the long haul. 

As for the original poster, make sure you delete all traces of the first wubi install where you tried to install Kubuntu. Make sure you delete the \ubuntu folder from your Windows hard drive. Then give it another go. Instead of downloading and burning the CD, just go to [http://wubi-installer.org/](http://wubi-installer.org/) and download the .exe file and wubi will download the proper iso file for you, no need to burn a disk. When you've made up your mind, burn a disk and install it for real.

thanks Waynefoutz but I can't seem to boot from a CD because of my second original problem that I can't get the computer to see the iso on CD or USB. I'd install Ubuntu right now if I could.

---

### Post by CharlesA on 2010-09-19
Gotcha. It won't boot from the CD, but boots fine from the hard drive.

Are you able to at least boot off the livecd and select "check for defects" from the menu? (hit any key when the first purple screen comes up)

---

### Post by Iminister on 2010-09-19
> **CharlesA said:**
> Gotcha. It won't boot from the CD, but boots fine from the hard drive.

Are you able to at least boot off the livecd and select "check for defects" from the menu? (hit any key when the first purple screen comes up)

See the Live CD thing I only got to work when Ubuntu was kindof installed by Wubi. I mean kindof because it would not completely load onto the hard drive at about 48% it would get the errno5 problem. I could run it as "demo" as one of the choices through the startup menu for Ubuntu after choosing Ubuntu on the dual boot screen.

---

### Post by bodhi.zazen on 2010-09-19
If you can not boot a CO, download the wubi installer here :

[http://wubi-installer.org/](http://wubi-installer.org/)

It is an .exe 

Run the .exe and it will install Ubuntu .

Here is a walk thorough :

[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

---

### Post by CharlesA on 2010-09-19
> **Iminister said:**
> See the Live CD thing I only got to work when Ubuntu was kindof installed by Wubi. I mean kindof because it would not completely load onto the hard drive at about 48% it would get the errno5 problem. I could run it as "demo" as one of the choices through the startup menu for Ubuntu after choosing Ubuntu on the dual boot screen.

It kinda sounds like a bad burn, or a corrupted ISO imo. Have you already verified the MD5sum of the ISO before burning it to cd?

> **bodhi.zazen said:**
> If you can not boot a CO, download the wubi installer here :

[http://wubi-installer.org/](http://wubi-installer.org/)

It is an .exe 

Run the .exe and it will install Ubuntu .

Here is a walk thorough :

[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

+1 to those.

---

### Post by alzie on 2010-09-19
Is the XP install NTFS or FAT32?  It seems to me on FAT32 the virtual disc needs to be set to 4GB. (I mean the amount of disc space WUBI asks you to allow for it) NTFS has no restrictions. 

An alternative is to put the WUBI installer and the appropriate ISO file into the same folder and run the install from there.  WUBI "should" see the ISO and use that rather than trying to find the network.

I am currently running a WUBI install (10.04) and when I installed from the CD it still downloaded the ISO package from the net.  I'm not sure if it is a WUBI issue or a burning issue.

WUBI for all intents and purposes is a full install.  You can download, install, modify anything the same way you would in a traditional install.  I have even run a version update from 8.04 to 8.10 in WUBI with success.

---

### Post by Iminister on 2010-09-21
Well, this is not completely resolved.

I did find disks did not work so by the 5th one I was able to boot off of it. However, Ubuntu 10.04 still received "errno5" at about 48% installation. This could not be solved using Wubi or installing from a cd. I did not try the alternate install. Instead I installed xubuntu from a cd and that seems to work fine. Just had to download some other things I wanted and everything seems okay.

---

