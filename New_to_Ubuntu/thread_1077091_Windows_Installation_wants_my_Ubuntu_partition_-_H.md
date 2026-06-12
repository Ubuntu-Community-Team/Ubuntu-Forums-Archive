---
title: "Windows Installation wants my Ubuntu partition - HELP"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by longtom on 2009-02-22
Hi,

this time I'm in real trouble!

I wanted to reinstall my XP, but after deleting my windows partition from the XP setub menu, it tells me it needs my Ubuntu partition to go ahead.

Must I now wipe my Ubunutu partition?  What is going on?  I can't have my XP not on this machine yet and need help urgently.

regards

longtom

Well - whatever.  I need to install XP now - so I will unplug my Ubuntu drive and hope for the best.  Wish me luck....

---

### Post by taurus on 2009-02-22
What happens to the old windows partition?  Did you reformat it to ntfs?

---

### Post by -kg- on 2009-02-22
> Well - whatever. I need to install XP now - so I will unplug my Ubuntu drive and hope for the best. Wish me luck....

That should work.  If you're able to unplug the drive with Ubuntu on it and have another drive to install XP on, then you should have no problem installing XP.  If you come back to read this because of problems, it's likely because Ubuntu was on the master drive and you didn't set the slave drive to master once you unplugged the other one.

Once you have it installed, though, you will either need to reinstall GRUB into the MBR (XP installation will install it's own boot loader) or you will have to switch to the drive you want to boot to in BIOS, which isn't a terrible burden, but it's a lot more convenient (to me) to install GRUB and select the OS from the menu at boot time.

However, if you had the free space available (and if there was a sufficient amount), I don't understand why XP wouldn't go ahead and install in it.  [This web page]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") describes how to install XP with Linux installed first, in case you have large problems.

---

### Post by longtom on 2009-02-22
Thank you for everybodys help.

I'm back in Ubuntu.  No I need to edit my grub so it recognises my XP.  XP was reinstalled as well.

> 
owever, if you had the free space available (and if there was a sufficient amount), I don't understand why XP wouldn't go ahead and install in it.

Good question.  The only thing I can think about is, that my Ubuntu is on an IDE drive and my XP partition on a sata drive.  Somehow the PC wants to grab the IDE drive as master over all...(had that before in XP as well when I wanted to format a drive from another PC)

Well - still work to do.  Get my XP drive permanently mounted and shared, get grub sorted, make my links permanent....

I know, peanuts for the intermediate user - but I have to read it up first again.

If you guys can think of anything I must look out for or can do to speed up the process, don't hold back:

greetings

longtom

---

### Post by Bradtek on 2009-02-22
Quite possible Windows setup has no idea about your SATA drive.
While it loads a bunch of more well known drivers yours may not be one of them.

At the start of the Windows XP Setup watch the text at the bottom of screen. It says  (something like)

Press F6 now to load 3rd party SCSI or RAID driver

This is where you have the option to load the correct drivers so your SATA drive will be recognised and enable you to Install there.

XP setup only accepts Drivers on Floppy drive, so if you ever go through this again, dont forget to download and put the drivers on a Floppy Disc.

---

