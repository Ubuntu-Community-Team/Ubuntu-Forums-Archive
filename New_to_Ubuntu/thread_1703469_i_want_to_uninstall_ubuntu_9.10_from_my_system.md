---
title: "i want to uninstall ubuntu 9.10 from my system"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by mr q. on 2011-03-09
okay so here's the deal...I had a friend install ubuntu 9.10 a long time ago on my computer...I am no computer genius so I need to take baby steps with this...my wife hates it and wants to get XP back on her old computer...I have tried looking all over the internet to see if there are ways of uninstalling ubuntu but everyone has recommendations of how to uninstall ubuntu when you have it as a partition...I DO NOT have it as a partition, its the only OS on this computer...I tried loading the XP installation disk directly from the disk drive but it won't work, the drive won't boot the disk...i have tried the booting order on the BIOS (F9>select boot order>save settings) but it won't work either...can someone please help me...all I want is to get rid of this and install windows XP again...again I don't know very much about Linux or codes and such things so I might need some extra help...thank you...

---

### Post by Hero1969 on 2011-03-09
Is there another way to change the boot order on your computer?  For example, on mine I can hit Del key and go into the whole bios menu and set the boot order, or I can hit F12 key during the splash screens and temporarily set the boot order for one session only.  Look into this and maybe that will allow you to boot your XP cd.  From there during the XP install, delete all partion(s) and reformat (it) them as FAT or NTFS.

---

### Post by mr q. on 2011-03-09
there's only two options when I restart the computer - those are DEL or F10...when i hit DEL nothing happens, when I hit F10 it goes into the BIOS of the computer, after that, even if I re-order the boot order nothing happens...I have read that if you have GRUB, it will prevent from you booting from a disk...I have GRUB installed on the computer...

---

### Post by Hero1969 on 2011-03-09
What does the splash screen tell you DEL is for?  Sometime the timing has to be perfect so i just start hitting (in my case F12) as soon as i see letters start showing up until I see a very simple menu allowing me to choose Boot device.  Something else to check if you have two cd/dvd roms, is even though you are changing your bios to boot from cd/dvd, on some bios' you also have to change which cd/dvd to boot from.

---

### Post by sydbat on 2011-03-09
> **mr q. said:**
> I have read that if you have GRUB, it will prevent from you booting from a disk.Then you read a lie. Grub is only a bootloader. It has nothing to do with allowing or disallowing a CD to boot.

Now the questions...

1) Is your Windows XP disc a legitimate store bought copy? Or a version created from the reinstall partition originally on the computer?

2) As asked by Hero1969, do you have more than one DVD/CD drive? If so, make sure each one is set as a priority boot in the BIOS, before your hard drive.

3) Are you sure your DVD/CD drive is working properly? Sometimes this can affect (effect?) whether or not any CD will work.

4) Tell us what your hardware is. What is the CPU, RAM, etc, of your computer? Something in these details might also give us a clue to your problem.

---

### Post by mr q. on 2011-03-09
Sydbat:
1. the disc is a legitimate copy that came with the computer when it was bought several years ago
2. there is only ONE dvd/cd drive on this computer, and it's set to boot in the BIOS as #1 before the hard drive
3. the dvd/cd drive is working properly because I have tried other discs, dvd's, game cd's, and installation cd's and they all seem to work fine...
4. 320 GB HHD, Compaq Presario, 2 GB RAM, Intel(R) Celeron(R) M CPU 530 @ 1.73GHz

hope this helps...

---

### Post by sydbat on 2011-03-09
> **mr q. said:**
> Sydbat:
1. the disc is a legitimate copy that came with the computer when it was bought several years ago
2. there is only ONE dvd/cd drive on this computer, and it's set to boot in the BIOS as #1 before the hard drive
3. the dvd/cd drive is working properly because I have tried other discs, dvd's, game cd's, and installation cd's and they all seem to work fine...
4. 320 GB HHD, Compaq Presario, 2 GB RAM, Intel(R) Celeron(R) M CPU 530 @ 1.73GHz

hope this helps...Hmmm...not sure why the XP disc is not booting then. 

Do you get anything similar to "To boot from CD, hit any key..."? If not, what, exactly, does your computer do when you boot it with the XP CD in the DVD/CD drive?

---

### Post by mr q. on 2011-03-09
...what, exactly, does your computer do when you boot it with the XP CD in the DVD/CD drive?[/QUOTE]

well...nothing...when i restart the computer i am able to either press the F10 key (for BIOS) or the ESC key (for booting order)...I have tried both and neither seem to work...when I go into the F10 feature (BIOS) I select the order of booting, after that it asks you if you want to leave and save, I hit yes, then....Ubuntu starts again...
now when I hit ESC (booting order) I select the CD/DVD drive and hit enter, then....again it just loads up Ubuntu...i really don't know what is wrong with this...for some reason it just doesn't want to load off the disc to begin with...:confused:

---

### Post by Hero1969 on 2011-03-09
Something else to try, do you have any other bootable cd.  You could download [gparted]("http://gparted.sourceforge.net/livecd.php") and burn the .iso as an image using brasero.  Now try to boot from this.  I am suggesting this because sometimes the windows disks that come with a new computer are used in conjunction with another startup disk or recovery partition and don't always work by themselves.

Now if it does work don't actually do anything with gparted, this was just a suggested bootable disk.

---

### Post by Golem XIV on 2011-03-09
OK so when you set the boot order to CD first and reboot, the system still boots off the hard disk.

When you go to the BIOS setup AGAIN after this, is the CD set as 1st boot device or not?  If not, you are setting up correctly but not saving the configuration.  Make sure that you "Save and Exit" and not "Exit Without Saving" from the BIOS configuration.

---

### Post by scrooge_74 on 2011-03-09
I never liked 9.10 myself, too much problems, try using version 10.04 is much better.

As per trying to reinstall XP, I agree with the rest, seems the system is not reading the CD or is not trying to boot from the CD.

You should check that.

Any chance you can get a Linux friendly wife? ;)  kidding

---

### Post by cap10Ibraim on 2011-03-09
> **scrooge_74 said:**
> 
Any chance you can get a Linux friendly wife? ;)  kidding
:D
yes show her the 10.04 or 10.10 maybe she'll agree to upgrade

---

