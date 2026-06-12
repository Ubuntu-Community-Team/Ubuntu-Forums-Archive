---
title: "bios to old?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Dn4mycrownj on 2010-02-28
Lets see, where will i start I have taken three towers that were free and have built one computer for about $25 american, that was the one stick of ram i needed.
 The computer has a supermicro P6SBA board. An external VGA card dont know what kind did not have to find drivers for it the board recognized it.  If you guys need some more information just let me know and i can get just about anything for it. a

     The HD that i found to work out of the three had win 2000 on it. I got into it and i do not like windo at all, never have. I have 9.1 on two different laptops so i was going to install it on this desktop for the kids and then put msdos as the other os for old school games.

     Before i started anything i updated the bios, with a msdos boot disk, to the current one that supermicro offered for that board. That part had no problems. After that i switched the jumper and cleared the cmos again everything still cool. 

All of this is from live cds from ubuntu images i did not download any images from outside sources.
     I started by installing msdos first well i had a corrputed disk on number 2 or something like that and the install failed halfway through. Just my luck for now. I have all them files backed up on cd just no new 3.5 to put the files on to them. Nobody used 3.5 any more lol. After that i went to put 9.1 on it. The error came up about the bios being 1999 and could not load. Then i went through all my cds and found a copy of 8.04 same thing with that. I have now tried to install the beta of 10.04. This install goes all the way through the loading line the burnt orange splash screen comes up and then it flashes a few times and goes black and the mouse spinning image comes on. This image stayed for about 30 min then i hit escape to try and quit the load of the cd and the spinning mouse icon stopped moving and frooze up. I had to do a hard shut down.  

After all of that here i am.

     Now for my question what version can i install and update to the current version or is there a patch that i can use to get this going? 

    I do not know if my 10.04 disk is good i have tried to do a clean install on the dell 1150 but the first try has not gone so i am trying it again. This is nothing new on that thing though. The 8.04 and the 9.10 are both good because i have used both of them for a clean install in the past. There is currently no OS on this desktop at this time because of the error while loading msdos. 

     I have access to a valid copy of win xp, if we need this to be able to change something else.  I also have a msdos boot 3.5 disk with the cd driver for dos on it. "tested good" 

My main goal for this computer is to run msdos 6.22 with norton commander 5.51. and a second os of ubuntu some version for the the kids to be able to use the computer need that GUI for them. 
I am even down with a way of changing the bios upgrade date if you can do that. 

Crown

---

### Post by cariboo on 2010-03-02
If you can get Lucid to boot to the desktop, your bios isn't the problem, it looks like a graphics problem. Remember the Live CD needs 348Mb to boot and load. If you have more than that installed, I would suggest running memtest from the Live CD. If the memory tests good and you still have problems, try the Alternate Install CD, as it uses a text based installer.

I would suggest going with Jaunty(9.04) or Karmic(9.10) instead of Lucid, as it is only at alpha3, and there could still be some show stopper bugs coming.

---

### Post by blazemore on 2010-03-02
As a rule of thumb, don't update your BIOS. Ever.
I've only ever had to update my BIOS once and that was because of a USB bug that occurred on all operating systems.
It's almost always not a BIOS problem.

---

### Post by mbzn on 2010-03-02
Could it not be that the system clock is 1999? Try putting the date right in the bios...

Sorry if this is not the case, but it could happen...

---

### Post by lkraemer on 2010-03-04
For Pre 2000 BIOS (dates) you might try:
1.  Puppy Linux
2.  TinyCore (Latest Version)
3.  DSL (Damn Small Linux)
4.  and maybe TinyME Acorn
5.  and maybe Slitaz

You might also try the cheatcode noapci ..... if they don't boot properly.

If you are trying DSL 4.4.10 and want to boot from the 3.5" Floppy,
and have the DSL OS on a USB Flash Drive, and transfer the boot to
USB (for those older systems that don't allow booting from USB)
PM me and I'll send you an IMG of a floppy I built that will allow
you to finish booting from USB after starting from Floppy.
The USB IMAGE is created with UNETBOOTIN, from the DSL ISO.
Link to original step by step process [http://linuxgazette.net/116/okopnik1.html](http://linuxgazette.net/116/okopnik1.html) 
The Boot process works good on my old Pre-2000 BIOS Compaq
Presario 1672 AMD K6-2 350MHZ laptop.
 
lk

---

### Post by LowSky on 2010-03-04
> **mbzn said:**
> Could it not be that the system clock is 1999? Try putting the date right in the bios...

Sorry if this is not the case, but it could happen...

Actually it can be the issue. Check the CMOS battery, more than likely you need a new one.

It could also be that Ubuntu assume the PC has APCI, which it might not. the NoAPCI option might the fix.

[http://ubuntuforums.org/showthread.php?t=1372119](http://ubuntuforums.org/showthread.php?t=1372119)

---

### Post by dzon65 on 2010-03-24
> **blazemore said:**
> As a rule of thumb, don't update your BIOS. Ever.
I've only ever had to update my BIOS once and that was because of a USB bug that occurred on all operating systems.
It's almost always not a BIOS problem.

Have this old compac 5000.By no means it was able to boot from cd.Tried everything,unetbootin,boot manager.....no way.Till I found a bios update for the medieval thing.And what do you know,kicked of immidiately.

---

