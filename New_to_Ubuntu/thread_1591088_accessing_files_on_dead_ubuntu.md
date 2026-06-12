---
title: "accessing files on dead ubuntu"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-10-08
is there anyway to access my files from a dead ubuntu installation using the liveUSB? files that are locked?

if not, will installation of ubuntu again, on the same drive, allow me to access them (providing i use the same user name etc)? or will it overwrite them?

---

### Post by cgroza on 2010-10-08
Try running Nautilus as root with " gksudo Nautilus ". If you install Ubuntu right now, the files will be overwritten.

---

### Post by scradock on 2010-10-08
> **daveboy23 said:**
> is there anyway to access my files from a dead ubuntu installation using the liveUSB? files that are locked?

if not, will installation of ubuntu again, on the same drive, allow me to access them (providing i use the same user name etc)? or will it overwrite them?
If you can set up a live session using USB or CD you will be able to set file permissions that will enable you to copy your files - that only requires "read" access. You will need somewhere to copy them to - another hard drive, another USB stick, etc.

If by "locked" you mean the files were encrypted in some way things will be more difficult, as the encryption layer needs to be running and able to work with the files, and so on.

HTH

---

### Post by daveboy23 on 2010-10-09
i guess they are - i can't copy or access them

---

### Post by msandoy on 2010-10-09
If this is your computer, and you do not know if the files are encrypted, they probably are not. Start from a live CD/USB stick, open terminal, do a sudo nautilus. This will give you a root access nautilus session. You should be able to copy all files from the HD to a safe place like a USB stick.

---

### Post by daveboy23 on 2010-10-09
i already tried that, it didn't work.  i don't know how to encrypt - so i don't think they are encrypted.  when i access the folder (after the nautilus command) i see those files with an "x" on their folder.  i really don't know what to do anymore.  basically, my original ubuntu wont load (it gets to the splash screen then distorted then nothing for hours).  is there a way to fix the boot (not grub) and revert it to the origianl state? change the files, something?

i'll tell you exactly what i did: installed ati drivers from original amd site.  after that didn't boot, goot blank screen.  put "nomodeset" in the edit boot.  ubuntu booted but asked me what to do - minimal graphics etc.  there was an option there that seemed like "revert to a previous state" kinda, clicked it, and after that everything went wrong

---

### Post by KirbySmith on 2010-10-09
If the files you want appear to be broken, you might try from a live CD (or USB, I suppose) to run the appropriate version of fsck on the bad drive's linux partition to try to fix up any broken files.  I am not qualified to provide elegant instructions.  "man fsck" will provide some insight.  If the bad drive partition is formatted as ext2, 3, or 4,  and happens to be, say, sdc1, then an appropriate command would be:

```
sudo e2fsck /dev/sdc1
```(note space between k and /).  Then answer y to the repair questions.

If the repairs are successful, still operating under the live CD, you should be able to copy files you want to whatever storage medium you want to put them on.  If fsck is fully successful, you should be able to boot the formerly bad partition.

kirby

---

