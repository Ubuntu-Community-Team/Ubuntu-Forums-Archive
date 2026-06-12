---
title: "Wont boot up"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Pedro61 on 2009-03-26
Y'all,

After a few close shaves with Windows virus and 1 hard disk reformat, I have installed Ubuntu with a "side by side" boot option with windows (i.e. I get to choose which OS to use when I power up).

Now I do all my web surfing, emails downloads etc with Ubuntu and just leave Windows disconnected from the web and use it only for software that cant use any other OS (Photoshop and many others etc).

Its been working great for about three months. My problem arose the other day when I went to start up Ubuntu and got the attached screen. 

It just sits there and wont boot up.  Should I just reinsert the CD and reinstall (EEEK),  or is there a repair function that I could try?

I use UBUNTU 8.10 on a DELL XPS1710 laptop with 2gb ram, 2MB Cache. Intel Core Duo Processor T2600, 17" UXGA monitor, 80gb partition for Ubuntu and the other 80gb for MSWin XP SP3. All my data is on 2 external 1TB hard drives, so there's nothing but apps on the internal disk. I have always upgraded when it asked me to do so.

Please Help.  I'm a bit of a Ubuntu Luddite so any simplicity you can include with your suggestions would be very much appreciated.

Cheers

Pedro

---

### Post by esalnoj on 2009-03-27
In your Grub/Boot loading menu, select the recovery mode for ubuntu and select "Repair broken packages" with your web cable plugged in.

If this doesn't work, try reinstalling ubuntu, but don't format the empty hard drive space you splice off to NTFS.
NTFS is windows only partition format.

---

### Post by Pedro61 on 2009-03-27
OK sounds good.  Can you just tell me where I can find the Grub/Boot loading menu ?

Usually when I power up there are no options to choose anything other than the UBUNTU v WINDOWS choice.  At least up to this point of the Freeze. This choice is made right after the DELL BIOS screen.  But after that . . . zero

---

### Post by HousieMousie2 on 2009-03-27
> **Pedro61 said:**
> OK sounds good.  Can you just tell me where I can find the Grub/Boot loading menu ?

There should be two entries for every kernel, one generic, one recovery.

---

### Post by lisati on 2009-03-27
> **Pedro61 said:**
> OK sounds good.  Can you just tell me where I can find the Grub/Boot loading menu ?

Usually when I power up there are no options to choose anything other than the UBUNTU v WINDOWS choice.  At least up to this point of the Freeze. This choice is made right after the DELL BIOS screen.  But after that . . . zero

The Grub boot menu usually shows up when you first turn on your computer, after the manufacturer's splash screen.

---

### Post by esalnoj on 2009-03-27
The screen where you select windows or ubuntu is the Grub menu.

Here is an example:

(insert ubuntu flavor here)-generic
(insert ubuntu flavor here)-recovery
...and the rest of your menu.

---

### Post by Pedro61 on 2009-03-29
> **esalnoj said:**
> The screen where you select windows or ubuntu is the Grub menu.

Here is an example:

(insert ubuntu flavor here)-generic
(insert ubuntu flavor here)-recovery
...and the rest of your menu.

You mean this screen ?

There are no recovery options here - Just Windows and Ubuntu.  the next screen I get is the one at the beginning of this thread.

Help! ](*,)](*,)](*,)

---

### Post by dereferenced on 2009-03-29
as esalnoj said there should be two options for a kernel. Why don't you try repairing from the live CD instead?

---

### Post by pspsampsp on 2009-03-29
did you by any chance install from within windows ? posibly using wubi (if you know what that is)

---

### Post by mikechant on 2009-03-30
It looks like you installed Ubuntu in windows (refs to /host in first screenshot). Have you moved/deleted/renamed any folders in windows since you installed Ubuntu, particularly the Ubuntu folder or any of its sub-folders?

---

### Post by Pedro61 on 2009-04-05
Thanks for all the replies team.  Yes  I did install from within windows.   That was actually one of the options that came with the Ubuntu 8.10 disk.  I naturally didnt realise it could cause problems.

I have been accessing a Ubuntu desktop of sorts by inserting my 8.10 disk, booting from it and using it as a "Trial version"  ie  no software installs. I can surf the net and do all the standard Ubuntu trial things, but of course I cant access some of the stuff I had on my previous desktop.   I normally store all my data on external drives (which by the way both Ubuntu and Windows access with no problems),  But I had a few important folders on the Ubuntu desktop that I want to recover.  These are the critical things I want to save.  Otherwise I would be happy to just blow the whole lot away and reinstall,  even if I have to run all the upgrades and reinstall apps etc.

Does anyone know how I might be able to access that desktop without actually logging on? Say via Windows or even via the UBUNTU trial on the CD ?

Pedro

---

### Post by Pedro61 on 2009-04-09
BUMP  -  Are we allowed to do this on this forum ???

> **Pedro61 said:**
> Thanks for all the replies team.  Yes  I did install from within windows.   That was actually one of the options that came with the Ubuntu 8.10 disk.  I naturally didnt realise it could cause problems.

I have been accessing a Ubuntu desktop of sorts by inserting my 8.10 disk, booting from it and using it as a "Trial version"  ie  no software installs. I can surf the net and do all the standard Ubuntu trial things, but of course I cant access some of the stuff I had on my previous desktop.   I normally store all my data on external drives (which by the way both Ubuntu and Windows access with no problems),  But I had a few important folders on the Ubuntu desktop that I want to recover.  These are the critical things I want to save.  Otherwise I would be happy to just blow the whole lot away and reinstall,  even if I have to run all the upgrades and reinstall apps etc.

Does anyone know how I might be able to access that desktop without actually logging on? Say via Windows or even via the UBUNTU trial on the CD ?

Pedro

---

### Post by Didius Falco on 2009-04-09
Pedro:

Have a look at this: [https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

I hope it helps...

---

### Post by Pedro61 on 2009-04-12
Hey that was awesome Didius.  It sure did help.  I'm back up and running.  Thanks a million.
    \\:D/    ):P

Pedro

---

