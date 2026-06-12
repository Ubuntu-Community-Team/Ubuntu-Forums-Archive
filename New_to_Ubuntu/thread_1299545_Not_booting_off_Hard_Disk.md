---
title: "Not booting off Hard Disk"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by ovid9 on 2009-10-24
So, I just put together my new computer.  Everything is great, I installed hardy off my liveCD and it works, except for one issue.

It won't boot off of the Hard Disk.  I have too boot from the live CD and then tell it to boot from the hard drive.

This works for now, but obviously this isn't a long term solution.  Any suggestions for why this is happening?

Also, it now says my /dmrc file isn't owned by me.  I had the fix before, but now I can't find the thread that worked last time.

Thanks!   Let me know what info you might need!

---

### Post by MelDJ on 2009-10-24
try changing your BIOS to boot from hard disk

---

### Post by Paqman on 2009-10-24
> **ovid9 said:**
> Any suggestions for why this is happening?


You haven't got Grub installed. [Reinstalling it]("http://ubuntuforums.org/showthread.php?t=224351") is easy enough.

> 
Also, it now says my /dmrc file isn't owned by me.

Try this:
```
sudo chown username:username ~/.dmrc
```

---

### Post by ovid9 on 2009-10-24
Whoop, sorry, forgot to mention that.  

I have done that.  Its set up to boot off the hard drive, I have 2.  For whatever reason, my 2ndary drive is the master, my primary is the slave, but I have it set up to boot off the primary drive.  

It goes from the initial BIOS boot screen to the screen where it boots (with the CD) but...it never moves beyond there.  It just sits and waits and looks for some reason.

---

### Post by mapes12 on 2009-10-24
Try switching the drives round. You'll need to reset the jumpers and make sure you have the cables connected the right way round i.e. correct end into m/board and correct end in drive. Reset the boot order in BIOS.

---

### Post by ovid9 on 2009-10-24
Ok, i followed the steps to setup GRUB.    It now gets me to that point but says File 15 error or something like that.

Then it gives me options of which system to boot, but it won't actually let me boot any of them.  

Following the link above my system said 

(hd1,0)

so, i typed:

> root (hd1,0)so I typed

> setup hd1It told me this:

> Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
I go to reboot, but no dice.  I get the file 15 error.  I can boot from the hard drive if i use the CD as my grub though.  I don't get it?

EDIT:  Also, as for switching the drives around, I can't.  One is a SATA, the other IDE.  So, they are kinda stuck being what they are.

---

### Post by ovid9 on 2009-10-25
*Bump*

Still not working....

It goes into select my OS and says Error 15: File Not Found

Boots just fine off of first HD using the live CD....

---

### Post by LewRockwell on 2009-10-25
OP updated system specs

previous post edited

.

---

### Post by ovid9 on 2009-10-25
I would do that, but i have an 1 IDE and 1 SATA.  I don't know how to "switch them around." 

The SATA cable is set up like it says to in the instructions, the "L" shaped connector into the drive.

And as for resetting jumpers....I'm not sure how to do that either.

All my previous experience has been the drives just plugged in and worked.

---

### Post by LewRockwell on 2009-10-25
see previous edited post

.

---

### Post by LewRockwell on 2009-10-25
and now we see that you've changed the specifications in your signature line

lol

.

---

### Post by ovid9 on 2009-10-25
Gah, I am so sorry.  You're trying to help me and here I am messing you all up.

That was my old setup.  I have my new setup in my signature now.

The 640gig is the SATA drive (what I want to boot off of) the WD800 is my IDE drive.

For whatever reason in BIOS, the WD800 is the 1st drive master, the 640gig is the slave.

The info i have posted above from my find grub info is all from my new setup.  

*Apologizes profusely to the kind people attempting to help.*

---

### Post by cariboo on 2009-10-25
You don't have the boot order set correctly in the bios. There should be somewhere in the bios that lets you set the boot order. If you want to boot from the SATA drive, set it as the first drive in the boot order.

---

### Post by LewRockwell on 2009-10-25
> **ovid9 said:**
> The 640gig is the SATA drive (what I want to boot off of) the WD800 is my IDE drive.

For whatever reason in BIOS, the 80gig IDE is the 1st drive master, the 640gig SATA is the slave.

The info i have posted above from my find grub info is all from my new setup.

just put your grub on HD0(the 80gig) and then hand it off properly to your menu.lst

this might also help out:

[http://ubuntuforums.org/showthread.php?t=1231028](http://ubuntuforums.org/showthread.php?t=1231028)

.

---

### Post by ovid9 on 2009-10-25
LewRockwell, thank's for the link.  I will try that idea out.

One final question though before I go that route.

In BIOS:
HD Boot Priority
1.. CH1 S WDC WD6400
2. CH0 M WDC WD800
3. Bootable add-in card.

IDE Channel Setups

IDE Channel 0 Master WD800
IDE Channel 1 Master TSST CDDVDW 
IDE Channel 1 Slave    WD64000


Could the fact my CDDVD drive is Chan1 Master and the WD6400 the slave be an issue?

If it shouldn't be an issue, i'll work on installing grub on my WD800 drive.

Thank's so much for all this.  lol

---

