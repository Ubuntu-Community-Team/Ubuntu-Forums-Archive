---
title: "Problems with Grub and Dual booting"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Equalizer1 on 2009-11-21
Hello everyone,

I am new to Ubuntu and all forms of Linux, and I just installed Ubuntu on a second partition with windows 7(installed first).  I use grub as my boot loader and it was working fine until I ran the update program in Ubuntu.  It seems that Grub may have been updated, possibly for the worse, because now I can no longer boot into my Windows 7 partition, although it does still appear in my menu.  Grub gives the error:       "error: invalid signature"  Ive tried making changes to the config files but I'm not really sure what I am doing as I am from a windows world.  Based on what config files are present, I think i have grub2 installed.  Any help would be greatly appreciated, thanks!

Also, I have two other hard drives that have been formatted NTFS, but as far as i'm aware they have no system files on them.  I am running 64 bit versions of both OS's.

---

### Post by louieb on 2009-11-21
Open Applications>Accessories>Terminal and run
```
sudo update-grub
```

---

### Post by Equalizer1 on 2009-11-21
Excellent, worked like a charm.  If you've got the time, what caused the problem? And how do I manually edit the boot list in the future?  Thanks for your timely help!

---

### Post by drs305 on 2009-11-21
You can tell which Grub you are working with from the grub menu - the version is displayed at the top. 1.97 is Grub2, 0.97 is Grub legacy. You can also run "grub-install -v" to get the version.

There are several links in my signature line that explain Grub 2 and how to edit it.

---

### Post by louieb on 2009-11-21
> **Equalizer1 said:**
> If you've got the time, what caused the problem? 

Don't know the why. Just have seen several threads with your same problem. Had updates to install - installed them - afterward GRUB gives an error trying to boot windows. Karmic is the 1st of the popular distributions to use GRUB2. Still a few thing to be worked out. 

Just a guess that there is a flaw in how the update mechanism runs update-grub. lol just as a general observation to os-prober built into GRUB2 is real good at picking up and booting another OS.

---

