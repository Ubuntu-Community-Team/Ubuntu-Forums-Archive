---
title: "Linux/XP dual-boot - filesystem info"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by joshaman on 2009-03-02
I was dual-booting ubuntu with XP earlier.  I copied a few drivers/installation packages **from ubuntu **to a cd/rw **to use on my XP **partition, however when I got into XP, it didn't go well.  I couldn't use the drivers, the installation programs froze up, the drive read the cd very slowly, and the OS locked up until I ejected the cd at one point.  There was a picture i'd burned that I could view, and some text documents I could read, but that was it.  Was the cd just old and perhaps had errors or does this have something to do with **transferring files between filesystems**?  

I've read that creating a third NTFS or FAT partition would be a good way to transfer files between the 2 OS's.

---

### Post by charliehorse55 on 2009-03-02
Using drivers for a Unix System on a non Unix system... sketchy.

I don't think this will work. Sorry to break it to you man.

---

### Post by halitech on 2009-03-02
what drivers were you trying to use in windows?

far as transferring files, yes a FAT32 partition is a good idea but Ubuntu can read NTFS so you could just mount your windows partition and move the files that way. You might need to install the ntfsg3 program ( I think thats what its called)

---

### Post by joshaman on 2009-03-02
> **halitech said:**
> what drivers were you trying to use in windows?

far as transferring files, yes a FAT32 partition is a good idea but Ubuntu can read NTFS so you could just mount your windows partition and move the files that way. You might need to install the ntfsg3 program ( I think thats what its called)

thanks, that's a relief.  i'm just confused as to why XP could read the pictures and docs, but not the programs.  I guess what i'm *really* asking here is: 1. what's the reason i'm *able* to view pictures (which i burned to a cd in ubuntu) in xp but not able to use win32 programs (which i burned to a cd in ubuntu) in XP?  and why is XP reading the cd slow and roughly, i assume there's one answer to both questions? 

and charliehorse55:  the drivers are for XP :lolflag:

---

### Post by halitech on 2009-03-02
not sure why it wouldn't read the programs but maybe when you burned it changed the attributes or something so they wouldn't run.

---

### Post by russet_wolf on 2009-03-02
I personally have a third partition in NTFS format that I keep all my data on because Windows cannot access my Ubuntu partition and it's a lot of bother to make sure I transfer all the files I might need before I log out. As far as drivers and pprograms go, not sure, but try transferring directly instead of using a CD.

---

### Post by joshaman on 2009-03-02
ok so i guess this isn't common.  that's good news, it was probably a cd error.  it was an old cd and pretty scratched up.  i was suspecting some sort of ext3 filesystem burning (which i guess is impossible).

---

### Post by joshaman on 2009-03-02
> **russet_wolf said:**
> I personally have a third partition in NTFS format that I keep all my data on because Windows cannot access my Ubuntu partition and it's a lot of bother to make sure I transfer all the files I might need before I log out. As far as drivers and pprograms go, not sure, but try transferring directly instead of using a CD.that's something i think i'll do, i wasn't anticipating being unable to read the ubuntu partition from windows - thanks

---

