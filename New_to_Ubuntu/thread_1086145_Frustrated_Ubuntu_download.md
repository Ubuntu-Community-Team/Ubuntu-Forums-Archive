---
title: "Frustrated Ubuntu download"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-03-03
Emachine-T2984-512 RAM-Chip Set Intel i845 E/G/PE/GE-Ethernet connection, no NIC-Intel R Celeron CPU-2.93 GHz-Was running Windows Home Edition with some bugs.  The Machine operated surprisingly well, considering its handicaps.  Ran a MEMtest86 v2 .01, 4 Passes, 0 Errors.  Did a Fast Acronis wipe and downloaded Ubuntu 8.10 from a disk I burned on my PC.  I checked the integrity of the disk, WinMD5Sum, and it is good.  Opened the ISO and it has almost 150 files.  I have downloaded this disk on two computers, one of them three times, all successfully.  I have posted this problem before, but had not done the homework that I have done this time.  The installations [as in plural] have all gone without incident until the disk is kicked out and it goes into final install.  It asks for "User Name" and "Password" then goes into the tan screen, the one just before the system background, and stays there for a long time.  It eventually turns black and has an active cursor, no command prompt, just a black screen and the cursor operates like the program was running.  It seems like it isn't finding its way out of the MBR, and not finding the NTLDR.  I'm not bright enough to get any further.  I hope this is enough info.

---

### Post by oldos2er on 2009-03-03
The CD shouldn't be "kicked out" until the installation is done and the system reboots. I assume by "kicked out" you mean ejected.

 Have you run 'Check CD for defects' on the first menu?

---

### Post by Yed Ied on 2009-03-03
Yes, and the CD passed.  I downloaded the "WinMD5Sum".  The CD is ejected just before final install,  User name etc etc. It does every thing but finish. I've done this install before this machine and after with the same CD and all is well with it.

---

### Post by oldos2er on 2009-03-03
What type of install? Dual boot, wubi, Ubuntu only...?

---

### Post by sgosnell on 2009-03-03
When you say 'the disk passed', exactly what do you mean?  Passing the checksum just means the original downloaded file is intact, it says nothing about the actual burned CD.  Did you run the CD test on the initial boot, before the install?  Lots of CDs get burned incorrectly, with good .iso's to start with.  I'm still not entirely clear on everything you've done.

---

### Post by Yed Ied on 2009-03-03
I checked the disk on Boot menu and ran it with WinMD5sum and it checked good.  I have installed it sucessfully 4 times on other computers, once a dual boot on my XP Pro HD.  The disk is golden, it is and has been working, Great, on my diagonistic laptop for a couple months.  If we could get past the disk what could it be.

---

### Post by sgosnell on 2009-03-03
Could be a defective HDD.  The sectors holding the MBR could be bad.  Or it could be other disk problems.  That's where I would start.

---

### Post by oldsoundguy on 2009-03-03
clean the cigarette smoke and the cat hair off of the laser by using a "CD CLEANER" disk that you can get at any office supply/drug store.

---

### Post by LowSky on 2009-03-03
Try using the Alternative Install CD

here is a direct download link for 8.10 32bit
[http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent)

---

### Post by Yed Ied on 2009-03-04
I will pull the HDD and check it in another machine.  I have  every confidence in the CD.  I've had four successful installs with it, one of them I use every day, and other than being used, the CD is never out of its plastic protection.  
Would it be worth reinstalling XP Home and running CHKDSK /F to try and fix flaws in the HD?  I don't know?  Grasping at straws.

---

### Post by Yed Ied on 2009-03-04
Hey LowSky, could you give me some info on the Alternative Install?  I've downloaded and saved it but haven't even left this page yet to look at it, but I'll do that now.  Thanks

---

### Post by Yed Ied on 2009-03-04
Hey LowSky, could you give me some info on Alternative Install?  I've downloaded and saved it, I'm going now to take a look at it.  Thanks

---

### Post by athaki on 2009-03-04
It's a text based only install cd.  That means it will not have fancy graphics to hang up on.

---

### Post by RetchingRabbit on 2009-03-04
@ the OP:
This is most likely a video card/driver issue. If you can boot up your computer, and then hit CTRL+ALT+F1 that will give you a console login. Log in using you usual username, and the give us the output of ```
lspci | grep -i vga
```

---

### Post by Yed Ied on 2009-03-05
Hey you all.
I just tried to reinstall XP so I could possibly run chkdsk /f and try to fix it, but I got an immediate "MBR Error 1" and it would go no further.   I really believe I have a bad sector @ the MBR.  I know an expired AVG said it had a Virus when I got it.
Sorry to be a pain, Thanks for the help.

---

