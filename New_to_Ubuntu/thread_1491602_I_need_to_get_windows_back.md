---
title: "I need to get windows back"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by omnisource on 2010-05-23
Alright, I gave this entire machine to ubuntu but quickly realized that I still needed windows for a few things.

I tried making a NTFS partition when reinstalling ubuntu so I could install windows to it, but my system wont boot my windows cd

I really dont want to download some virtual machine and install it. I just want to wipe my system to windows only then install dual boot ubuntu via wubi.exe

---

### Post by presence1960 on 2010-05-23
> **omnisource said:**
> Alright, I gave this entire machine to ubuntu but quickly realized that I still needed windows for a few things.

I tried making a NTFS partition when reinstalling ubuntu so I could install windows to it, but my system wont boot my windows cd

I really dont want to download some virtual machine and install it. I just want to wipe my system to windows only then install dual boot ubuntu via wubi.exe

Boot from the Ubuntu live CD or gparted live CD and delete all partitions. Leave all space on hard disk as unallocated space. Reboot with the windows install CD/DVD and install windows. Then install Ubuntu via wubi.

---

### Post by omnisource on 2010-05-24
Ok I did what you said, It would boot to the grub rescue> prompt, whenever I put in my Windows Boot CD It would say "Checking Hardware Config" and then reboot over and over and over again. I had to re-install ubuntux64 just to post this message lol

---

### Post by anewguy on 2010-05-24
Do you mean you put your Windows boot CD in when the grub prompt appeared, or did you boot using your Windows boot CD?  It is the Windows installation CD, not just a recovery CD that requires a recovery partition on your hard disk, right?

Dave ;)

---

### Post by EssexEagle on 2010-05-24
> **omnisource said:**
> I had to re-install ubuntux64 just to post this message lol

n.b. You can always boot Ubuntu from your Live CD to use the internet, you don't have to reinstall.

---

### Post by mastablasta on 2010-05-24
> **omnisource said:**
>  dual boot ubuntu via wubi.exe
 
Wubi is not really dual boot. You can get more or less same result if you use the LiveCD. Wubi is more for testing/trying out the system.
 
Why not install windows, defrag the drive and then install linux on another partition (which will be offered later upon instalation)?

---

### Post by Paddy Landau on 2010-05-24
> **omnisource said:**
> Ok I did what you said, It would boot to the grub rescue> prompt, whenever I put in my Windows Boot CD It would say "Checking Hardware Config" and then reboot over and over and over again.
That sounds as though your computer is not booting from the CD but from the hard drive. Go to your computer's BIOS (see your computer's documentation for that) and tell it to check the CD before checking the hard drive when booting.

> **omnisource said:**
> I really dont want to download some virtual machine and install it. I just want to wipe my system to windows only then install dual boot ubuntu via wubi.exe
I do not recommend WUBI for serious use. It is too easily corrupted. It's brilliant for testing Ubuntu, but not for long-term use.

If you want to use Ubuntu long-term, install Windows first and then install Ubuntu properly as a dual boot. You'll have both Windows and Ubuntu, then.

---

### Post by skarme on 2010-05-24
Go to the BIOS and check if you've selected you're CD drive as the first boot device. If not; do so and then install windows and subsequently install ubuntu.

---

### Post by omnisource on 2010-05-24
Ok let me make this a little more clear, it was late when I wrote the original post. I know my way around the BIOS, and my CD-ROM drive is my first boot device, 

1. I booted with the linux live cd, ran GPARTED and unallocated my space, ShutDown 
2. Booted with my Windows CD, started the Windows automated prep stuff, stated a nt.dll error and went into infinite loops detecting my hardware for configuration

3. Reinstalled Ubuntu x64, this time leaving a 100gb partition as NTFS

WHAT I WANT TO DO: Wipe the drive clean again and get it to install windows. For some reason when the drive is formatted and I boot with my windows cd it goes into some infinite restarting loop detecting hardware. 

I can get my Ubuntu desktop to load the autorun of my disk but cant install it, I tried moving the cd contents to my C: drive that WINE setup, but wouldnt work there either

---

### Post by Mark Phelps on 2010-05-24
Can't install Windows from Wine ... waste of time trying.

You didn't tell us which Version of Windows you're trying to install.  A likely problem is that it's failing hardware detection if it can't find the hard drive -- but that's only probably if it's an Early version (pre-SP1) of XP, which didn't come with SATA controller drivers.  IF it's XP later than SP1, or Vista/Win7, it should already have the SATA controller drivers needed and be able to detect the HDD without problems.

---

### Post by omnisource on 2010-05-24
I have a xp home cd and vista, neither would work, But ima keep trying

---

### Post by Calash on 2010-05-24
> **omnisource said:**
> Ok let me make this a little more clear, it was late when I wrote the original post. I know my way around the BIOS, and my CD-ROM drive is my first boot device, 

1. I booted with the linux live cd, ran GPARTED and unallocated my space, ShutDown 
2. Booted with my Windows CD, started the Windows automated prep stuff, stated a nt.dll error and went into infinite loops detecting my hardware for configuration

3. Reinstalled Ubuntu x64, this time leaving a 100gb partition as NTFS

WHAT I WANT TO DO: Wipe the drive clean again and get it to install windows. For some reason when the drive is formatted and I boot with my windows cd it goes into some infinite restarting loop detecting hardware. 

I can get my Ubuntu desktop to load the autorun of my disk but cant install it, I tried moving the cd contents to my C: drive that WINE setup, but wouldnt work there either

It sounds like your Windows CD's are bad.  When was the last time you use the Windows CD's to install and had them work?


Edit:  Have you tried deleting the entire partition structure and starting from scratch?  If you have no information on the Ubuntu partition go into the LiveCD and use gparted to remove all partitions.  Then boot into Windows and try the install.  If it works you can go back to the LiveCD and adjust the partition size and install Ubuntu.

---

### Post by ronnielsen1 on 2010-05-24
> 3. Reinstalled Ubuntu x64, this time leaving a 100gb partition as NTFS

I assume this is the 1st partition. Win 7 doesn't care, I'm not sure about vista, but xp just doesn't understand not being first.

---

### Post by ronnielsen1 on 2010-05-24
> It sounds like your Windows CD's are bad.  When was the last time you use the Windows CD's to install and had them work? 	

Could also be read errors from a faulty cd/dvd drive. I've had to change the drives before to allow installing

---

### Post by omnisource on 2010-05-24
> **Calash said:**
> It sounds like your Windows CD's are bad.  When was the last time you use the Windows CD's to install and had them work?


Edit:  Have you tried deleting the entire partition structure and starting from scratch?  If you have no information on the Ubuntu partition go into the LiveCD and use gparted to remove all partitions.  Then boot into Windows and try the install.  If it works you can go back to the LiveCD and adjust the partition size and install Ubuntu.


Not trying to sound rude, but I already did that as it is in my post that you just quoted.

I doubt I have 2 bad Windows CD's It could be the CD Drive

Do I need to download new Drivers for it since I have installed Linux? It works fine so far but I havent done much with it yet.

---

### Post by tad1073 on 2010-05-24
when you boot the Windows cd instead of installing, use the fix broken system, or what ever the option is to get the command prompt, do a chkdisk to see if there are bad sectors errors etc...

---

### Post by omnisource on 2010-05-24
It doesn't get to that part.

I am pretty sure its due to not having the correct drivers installed currently for my CD-ROM drive, It is a H&L (Hitachi and LG GH10L) it came as part of a HP computer that I stole it from. I am trying to find a linux version of these drivers, and some instructions on how to install them.

---

### Post by tad1073 on 2010-05-24
> **omnisource said:**
> It doesn't get to that part.

I am pretty sure its due to not having the correct drivers installed currently for my CD-ROM drive, It is a H&L (Hitachi and LG GH10L) it came as part of a HP computer that I stole it from. I am trying to find a linux version of these drivers, and some instructions on how to install them.

If you wipe and do a clean install then no drivers are present

---

### Post by tango_ninja on 2010-05-24
I've had similar problems in the past.  

1. How old are your Windows install cds?
2. Do you have a machine specific (OEM) install disc?

The reason I ask is that you may have newer hardware (like SATA HDs) and an old Windows CD won't come with the drivers to recognise these devices. If that's the case, your options are (a) get a newer Windows install cd and hope your prev code works, or (b) try to find an OEM install cd that matches some of the hardware on your machine.

---

### Post by lkraemer on 2010-05-24
Boot the Ubuntu LiveCD.  Double check that there are no partitions existing.
If you are booting to a grub menu then something is not correct.  There
should be nothing to boot because it's unallocated.

If your version of Windows doesn't support the SATA drives, you can download
drivers for them from the internet and put them on a floppy.  Then during the CDROM
boot process you can press F6 to get them installed from the floppy.

Then Windows should continue installing.

Another option is to use your existing CDROM to Slipstream the latest
Service Pack to your copied folder and then rebuild the CDROM.  If you
are interested I have a few sites bookmarked.  And one to make a 
Minimum (Tiny) install of Windows bookmarked.


After that process is finished install Ubuntu as Dual boot.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
 
lk

---

### Post by Calash on 2010-05-24
> **omnisource said:**
> Not trying to sound rude, but I already did that as it is in my post that you just quoted.

I doubt I have 2 bad Windows CD's It could be the CD Drive

Do I need to download new Drivers for it since I have installed Linux? It works fine so far but I havent done much with it yet.

I read what you wrote as unallocated some space, not all of it.

When you boot to a Install CD of any kind, be it Linux, Windows, or even OSX, you are in a self-contained environment. The install on the hard drive is not going to have any effect on how that environment functions.

So you have to look at the easiest to hardest to fix.  First being CD's, or your CD drive.  After that, memory test followed by hard drive test.


Now, your later posts are a bit helpful.  If the Windows CD's did not come with your computer it could very well be a missing driver issue.  I would put my money on SATA as noted.

You may be able to get around this by going into the BIOS and finding the SATA mode.  Different systems will have it listed differently but usually it will have options like Compatability, Combonation, or AHCI.  Change it to a different mode and then try your windows install again.

---

### Post by ronnielsen1 on 2010-05-24
Try the install with a different cdrom or dvdrom if possible. Seriously, it can't install what it can't read. I'm pretty sure you have a bad cdrom drive.

---

### Post by SRST Technologies on 2010-05-24
> **lkraemer said:**
> Boot the Ubuntu LiveCD.  Double check that there are no partitions existing.
If you are booting to a grub menu then something is not correct.  There
should be nothing to boot because it's unallocated.

Absolutely incorrect.  A bootsector is not part of a partition.

---

### Post by omnisource on 2010-05-25
SOLUTION: Cleaned the CD With Rubbing Alcohol, worked like a charm... Which is interesting cause the CD looked clean, but so many of you were like "Bad CD" that I tried it and it worked.

Thanks a thousand times, if this forum has rep I will be giving you all some

---

