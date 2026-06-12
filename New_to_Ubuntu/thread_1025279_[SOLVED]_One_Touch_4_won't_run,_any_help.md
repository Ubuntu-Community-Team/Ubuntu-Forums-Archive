---
title: "[SOLVED] One Touch 4 won't run, any help?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by jayef on 2008-12-29
I recently installed Ubuntu 8.10 with recommendations from my cousin. 
I also just got a Maxtor OneTouch 4. Before trying to install it to my computer, the one with Ubuntu, I installed it to my home computer, it runs windows XP. (I don't know if that will mean anything) Anyway, I plugged it into my computer and when I try to Autorun it says it can't find the autorun program. Then, I try to click the "Launch" icon in the File Browser and it says 

[/media/OneTouch 4/Launch.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/OneTouch 4/Launch.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/OneTouch 4/Launch.exe or
          /media/OneTouch 4/Launch.exe.zip, and cannot find /media/OneTouch 4/Launch.exe.ZIP, period.

Any help on getting this to run?

---

### Post by igknighted on 2008-12-29
You don't need to run or install anything (ditto with windows, actually).  Those programs are really just adware/bloatware, designed to put their logo in front of you.  When you plug the drive in, you should see an icon for it appear on the desktop, you can access the drive there and use it like any other drive.

---

### Post by jayef on 2008-12-29
Thanks man. I was thinking about just not installing it actually. But I wanted a second opion on what to do.

---

### Post by TransitMan on 2008-12-29
I've got a OneTouch. Went in with gparted, formatted the drive to NTFS and haven't looked back.

BTW, the OneTouch comes formatted in 32-bit format, which is why I reformatted to NTFS, to store files larger than 4GB.

---

### Post by jayef on 2008-12-29
Mine came formatted in NTFS, I have the 750GB drive. If you wouldn't mind though, could you expain why you partitioned it? And also, is there a way to safely remove it/shut it off?

---

### Post by igknighted on 2008-12-29
> **jayef said:**
> Mine came formatted in NTFS, I have the 750GB drive. If you wouldn't mind though, could you expain why you partitioned it? And also, is there a way to safely remove it/shut it off?

Because the default partition on his did not support files larger than 4gb (vfat/fat32 file system).  He didn't partition it per se, just reformatted.

---

### Post by jayef on 2008-12-30
Word, thanks again man! and high five for both being from NY, lol.

---

### Post by newbee70 on 2008-12-30
> **jayef said:**
> Mine came formatted in NTFS, I have the 750GB drive. If you wouldn't mind though, could you expain why you partitioned it? And also, is there a way to safely remove it/shut it off?

to safely remove it you right click on the disk desktop icon, then click on unmount. it is then safe to remove.

---

### Post by c.hawkins on 2008-12-30
I just plugged mine in (Maxtor Onetouch 4 640GB) and the system is saying it can't mount it. It shows up in the browser but it is unaccessable. I just put Ubuntu on my system yesterday so please help me out and avoid using too many abreviations. I am REALLY happy with the system (8.10) so far but I am unclear on where things are.

---

### Post by jayef on 2008-12-30
> **c.hawkins said:**
> I just plugged mine in (Maxtor Onetouch 4 640GB) and the system is saying it can't mount it. It shows up in the browser but it is unaccessable. I just put Ubuntu on my system yesterday so please help me out and avoid using too many abreviations. I am REALLY happy with the system (8.10) so far but I am unclear on where things are.

I'll try to give you a hand here, since I too had trouble mounting at first.
In "Places" you should click "home folder". Once that opens, on the left there should be a list of places on your computer, one being OneTouch 4. Right click it and then click mount. If that doesn't work, you can try to force mount it using this

```
sudo mount -t ntfs /dev/sdc1 "/media/OneTouch4 Plus" -o force
```

Hopefully that will help a bit :)

---

