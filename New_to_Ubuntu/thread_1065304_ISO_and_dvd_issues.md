---
title: "ISO and dvd issues"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by WiseMaturin on 2009-02-09
So I cannot seem to play DVDs at all.
I have even tried to burn an iso and then play it through my DVDrom, and that doesn't seem to work either.

What all should I try to do to make it work?
I have tried using konsole to mount the disc since I cannot seem to access it otherwise, but I cannot run any games or movies that way.


Any and all help would be much appreciated.

---

### Post by 3rdalbum on 2009-02-09
First up: Do you have libdvdcss2 from the Medibuntu repository?

Have you tried using VLC to play DVDs?

---

### Post by unplugged23 on 2009-02-09
I had a similar issue. Make sure you install all the proper codecs. Make sure your IDE cables are connected properly and are not damaged. Also make sure if its an older drive that its a CD/DVD ROM drive and not just a CD drive.

---

### Post by WiseMaturin on 2009-02-09
I have not tried VLC, and I'm not sure if I have libdvdcss2 or not. I will check first thing in the morning so sleep does not cloud the issue.

---

### Post by WiseMaturin on 2009-02-10
I installed libdvdcss2, and now I most definitely CAN play dvds on VLC. Thank you very much!

On to iso problem: I have tried to make a copy of several discs, of varying types. But anytime I tried to run an iso burned onto a dvd, it opens the disc like a folder. And I cannot for the life of me figure out how to run anything on the discs.

---

### Post by jerome1232 on 2009-02-10
When the discs mount and show their contents is there just a .iso file on the disc or does it have several folders and etc... as it should.

---

### Post by WiseMaturin on 2009-02-10
> **jerome1232 said:**
> When the discs mount and show their contents is there just a .iso file on the disc or does it have several folders and etc... as it should.

Some discs it shows an iso, and some it shows *some* of the expected folders. And I don't know if that is a function of HOW I burned the discs, or if it's reading it a little strange.

I tried backing up my copy of Oblivion, and I don't think the copy has all the files it needs to play. Which is more than slightly annoying, because I tend to scuff up my games quite often, and I'd rather not have to repurchase any of them.

---

### Post by jerome1232 on 2009-02-10
If it shows up as just a .iso file then you accidentally burned the disc wrong, make sure you always chose the write image to disc or similar in your disc burning program.

How did you make the iso's? Maybe the iso is just bad.

Could try using dd to image the cd and then burn the resulting image to disc.

On my computer my dvd-rom is /dev/scd0 your's may be different, so you'd have to change the if=/dev/scd0 to match.

```
dd if=/dev/scd0 of=mycd.iso conv=notrunc
```

---

### Post by WiseMaturin on 2009-02-11
I tried using K3b, and just using the copy cd function in that. And I tried to use the 'burn DVD iso image..." to reburn it to a new dvd, but even though the iso should fit on the DVD, it is missing oblivionlauncher.exe and setup files and probably more that I'm not aware of.
It might just be a problem with Wine though, that because it's not the original disc it's acting shitty on me.

---

### Post by WiseMaturin on 2009-02-12
I looked up how to mount the iso from linux, and even that doesn't work.

I'm out of ideas now. lol

---

