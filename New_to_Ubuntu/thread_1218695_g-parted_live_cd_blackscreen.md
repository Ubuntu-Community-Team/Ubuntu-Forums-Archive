---
title: "g-parted live cd blackscreen"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Azatos on 2009-07-20
Yeah, I went to resize my ubuntu partion cause I needed space, and I did everything it said and there was a lot of scrolling text, it asked me to pick system language keyboard layout ect. then it went to a white screen and it started changing colors and it went to a black screen and I can't do anything, I can't eject the ******* CD and no keystrokes do anything.  So did I ****-up my BIOS or something?

EDIT:
I went into bios and changed the boot order to use CD and my OS is a vista OEM and the other is obvious

---

### Post by esalnoj on 2009-07-20
So far, your BIOS isn't messed up.

Did you burn a gparted-0.4.x.x .iso to CD, or are we talking jaunty live disk?

If using gparted-0.4.x.x .iso CD, I never could get the CD to boot properly. It loaded the kernel, but just went black screen afterwards. Not even any shell/terminal to run shutdown command.

So far, jaunty live CD's have booted properly for me. Just use gparted on jaunty live run.

---

### Post by Azatos on 2009-07-21
> **esalnoj said:**
> So far, your BIOS isn't messed up.

Did you burn a gparted-0.4.x.x .iso to CD, or are we talking jaunty live disk?

If using gparted-0.4.x.x .iso CD, I never could get the CD to boot properly. It loaded the kernel, but just went black screen afterwards. Not even any shell/terminal to run shutdown command.

So far, jaunty live CD's have booted properly for me. Just use gparted on jaunty live run.
Well after my laptop died I was able to get the damn cd out and I tried it again using the second option I had to delete the ubuntu partion, now when I boot up to the HDD I always get a GRUB 1.5 error 22.  IS there anyway to get back to my windows partion?  My laptop didn't come with a recovery cd and I don't have money to waste on another copy of vista or XP.

---

### Post by esalnoj on 2009-07-21
> anyway to get back to my windows partion?

Can you access any other computers with internet access and a CD burner?

If so, go to [HTML]http://www.supergrubdisk.org[/HTML]

and download the .iso or USB version, 

then burn yourself a CD or USB of the 0.9795 version (most recent I see).

Boot with that disk/USB, allow the kernel to load, and select "win." in the drop down menu.

That should get you temporary access to your windows until someone more experienced with grub error 22 posts here.

---

### Post by esalnoj on 2009-07-23
Once you are inside windows, use the disk management tool to extend vista to the entire drive.

Then boot the jaunty live CD and reinstall ubuntu, being sure to give it the final size you want when finished ("side by side" option in partitions setup).

The error 22 code fix I have depends on ubuntu being on the drive beside windows.

---

