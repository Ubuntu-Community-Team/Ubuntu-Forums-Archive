---
title: "Space in path name issue"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by Diametric on 2010-09-29
I have a 1TB external WD HD and as I'm sure some of you know the device refers to its self as "My Book".  I cannot seem to change the name (say to My_Book) - any ideas on how to do this?  Eventually, I want to create a script to change some directory paths but fear my script will not run properly if I don't get this resolved.
 
Thanks!

---

### Post by Peter09 on 2010-09-29
try putting the text %20 where the space is, this is seen as a substitute for space in Linux.
 
If you are using the command line try using the command completion fuction (the Tab key). Start writing the command you wish to use and when you get to where there is a space hit the Tab key, with luck the command should complete automatically (or at least as far as it is non-ambiguous).

---

### Post by Diametric on 2010-09-29
Thanks, but I'm trying to figure out a way to rename the device, as opposed to writing scripts around the name of the device.  I do not wish the name to remain "My Book"

---

### Post by mc4man on 2010-09-29
Either use 'disk utility' (palimpsest) or gparted - both wouuld be in System -> Administration
(you may need to install

Then plug in drive, pick the the drive, unmount it and change the volume label

Screen shows disk utility, for gparted you pick the drive from upper corner drop down (screen 2 - r. click unmount, r. click label

Drive must be unmounted to change label with either app.

---

### Post by dcsoldschool53 on 2010-09-29
> **Diametric said:**
> I have a 1TB external WD HD and as I'm sure some of you know the device refers to its self as "My Book".  I cannot seem to change the name (say to My_Book) - any ideas on how to do this?  Eventually, I want to create a script to change some directory paths but fear my script will not run properly if I don't get this resolved.
 
Thanks!
I have a my passbook and I have to use it this way in scripts, because I have never found a way to change the name. There is a space between\ and Passport.

```
media/My\ Passport/any_needed_file
```

---

### Post by LowSky on 2010-09-29
you can always tag it like this
```

'/home/user/the space between the file'
```

---

### Post by formaldehyde_spoon on 2010-09-29
Is it the device name or partition name? You can change the partition name with gparted.

---

### Post by Diametric on 2010-09-29
> **mc4man said:**
> Either use 'disk utility' (palimpsest) or gparted - both wouuld be in System -> Administration
(you may need to install
 
Then plug in drive, pick the the drive, unmount it and change the volume label
 
Screen shows disk utility, for gparted you pick the drive from upper corner drop down (screen 2 - r. click unmount, r. click label
 
Drive must be unmounted to change label with either app.
 
This looks right - thank you.  I'll have to wait until I get home, but will try it then and post results tomorrow.
 
Cheers.

---

### Post by Diametric on 2010-09-30
Got it fixed via palimpset - and like he said, you have to unmount, then rename, then remount...took 30 seconds.
 
Thanks!

---

