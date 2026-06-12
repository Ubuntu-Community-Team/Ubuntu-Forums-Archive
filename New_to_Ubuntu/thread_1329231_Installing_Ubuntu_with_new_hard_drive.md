---
title: "Installing Ubuntu with new hard drive"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Alex Beaton on 2009-11-17
[FONT=Times New Roman]I am installing Ubantu 9.10 on a laptop on which I have just replaced the hard drive so there is no existing O/S. Progress if normal until step 4/7, Prepare partitions. There is no choice so I don’t know what to do. If I skip by selecting forward, I get an error msg, “No root file system. Please correct from partitioning window”.[/FONT]
 
[FONT=Times New Roman]I have watched the Youtube video on installation and also looked at the GraphicaInstal document but neither refer to this problem. I suspect it might be something to do with the new drive. I haven't replace a drive before. Should I have done something other than a "mechanical fitting"?[/FONT]
[FONT=Times New Roman][/FONT] 

[FONT=Times New Roman]Can someone advise me what to do in simple terms, please.[/FONT]
[FONT=Times New Roman]Thank you.[/FONT]

---

### Post by atomizer on 2009-11-17
Try partitioning with Gparted before installing. Maybe then you can assign root and home during installation.

---

### Post by Paqman on 2009-11-17
I'd check the connectors on the drive, maybe you didn't push one of them home fully.

Can you see the drive from the BIOS?

---

### Post by philinux on 2009-11-17
> **Alex Beaton said:**
> [FONT=Times New Roman]I am installing Ubantu 9.10 on a laptop on which I have just replaced the hard drive so there is no existing O/S. Progress if normal until step 4/7, Prepare partitions. There is no choice so I don&#8217;t know what to do. If I skip by selecting forward, I get an error msg, &#8220;No root file system. Please correct from partitioning window&#8221;.[/FONT]
 
[FONT=Times New Roman]I have watched the Youtube video on installation and also looked at the GraphicaInstal document but neither refer to this problem. I suspect it might be something to do with the new drive. I haven't replace a drive before. Should I have done something other than a "mechanical fitting"?[/FONT]
[FONT=Times New Roman][/FONT] 

[FONT=Times New Roman]Can someone advise me what to do in simple terms, please.[/FONT]
[FONT=Times New Roman]Thank you.[/FONT]
+1 to above suggestions.

Boot the livecd and select try ubuntu out. At the desktop use system>admin>partition editor see if you can format the drive.

---

### Post by Bunnybugs on 2009-11-17
> **atomizer said:**
> Try partitioning with Gparted before installing. Maybe then you can assign root and home during installation.

That sounds pretty blonde to me;)

He has replaced his old drive, without giving the reason... maybe his drive is broken... gparted can only be executed from a working OS like Ubuntu or another debian based system!

---

### Post by Bunnybugs on 2009-11-17
> **philinux said:**
> +1 to above suggestions.

Boot the livecd and select try ubuntu out. At the desktop use system>admin>partition editor see if you can format the drive.


Won't work... with the LiveCD, you'll need an admin password.. that becomes available after the install and user creator!

EDIT: The install has a partition editor in it... just create a whole new partition... so pick: remove all other OS and create a new partition!

---

### Post by atomizer on 2009-11-17
> **Bunnybugs said:**
> That sounds pretty blonde to me;)

He has replaced his old drive, without giving the reason... maybe his drive is broken... gparted can only be executed from a working OS like Ubuntu or another debian based system!


like a live cd? On a live cd you are root, no password required.(just tried it out)

---

### Post by screaminfakah on 2009-11-17
You can install and run Gparted from a Live session so yes you can run it without an OS installed.

---

### Post by Paqman on 2009-11-17
> **Bunnybugs said:**
> gparted can only be executed from a working OS like Ubuntu or another debian based system!

*ahem* LiveCD.

---

### Post by ukripper on 2009-11-17
Check in BIOS first if your HDD is detected before proceeding. Then follow the steps explained as above by members.

---

### Post by philinux on 2009-11-17
> **Bunnybugs said:**
> Won't work... with the LiveCD, you'll need an admin password.. that becomes available after the install and user creator!

EDIT: The install has a partition editor in it... just create a whole new partition... so pick: remove all other OS and create a new partition!

You better try out the livecd then for your own edification ;).

---

### Post by lkraemer on 2009-11-17
You're best bet is to power off the Laptop immediately, and remove the
AC Power Plug along with the battery.  REMOVE the Hard drive you just
installed carefully.

Now look at the first Drive you removed from the computer that functioned
properly.  It is either an IDE Drive or a SATA Drive.  If you don't know
the difference, Google IDE Drive Connector or STAT Drive Connector to
know how to determine the drive type.
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://www.google.com/imgres?imgurl=http://www.laptopparts101.com/wp-content/uploads/2008/12/sata-ide-laptop-hard](http://www.google.com/imgres?imgurl=http://www.laptopparts101.com/wp-content/uploads/2008/12/sata-ide-laptop-hard)

IDE ONLY
Now, look at the IDE Drive you previously removed to determine if there
are any Drive select jumpers that need to be duplicated on the New
drive.  Most drives have a small chart on the drive label describing
the jumpers and what the selections are.  It could be strapped (jumpered) as
Master, Slave, or Cable Select.  (Most don't have any jumpers as default,
but that isn't true for my Compaq Laptops).  Once you have the jumpers
set the same, if they are needed, the BIOS should recognize the drive,
assuming you plugged it in the IDE cable with the correct side up
(that should also match the one you previously removed).  Carefully
plug in the drive and make sure the pins are fully seated.  Just be
careful and don't attempt to plug it in upside down.

SATA ONLY
SATA should be plug and play.  The BIOS should recognize the drive when
you check the BIOS settings.  The connectors are keyed and only fit
one way.  

Insert Battery, apply AC power and verify the BIOS recognizes the drive.

lk

---

### Post by Bunnybugs on 2009-11-17
> **philinux said:**
> You better try out the livecd then for your own edification ;).

I know that from experience... had the same problems... wanted to try it from livecd, because someone else asked me howto edit partitions without installing the OS...

That's what I did, and it just didn't work... or do you have a admin password for the liveCD? Because you are a development releaser;)

---

### Post by philinux on 2009-11-17
> **Bunnybugs said:**
> I know that from experience... had the same problems... wanted to try it from livecd, because someone else asked me howto edit partitions without installing the OS...

That's what I did, and it just didn't work... or do you have a admin password for the liveCD? Because you are a development releaser;)

No it just work, since the partitioner is already available to do the install. No password needed. It's in the menu too.

On some previous releases I think you might have had to actually install it to get it in the menu. But not now.

---

### Post by Bunnybugs on 2009-11-17
Okay, had this problem with the LiveCD of Karmic 64-bit... Could be something on my side, but had it on disk and on USB

---

### Post by Alex Beaton on 2009-11-18
Problem solved! Removed drive to inspect jumpers and found them the same as broken original drive. Refitted new drive and booted up. Ubuntu installed successfully. Assume that it was poor connection as Paqman suggested:-
 
> **Paqman said:**
> I'd check the connectors on the drive, maybe you didn't push one of them home fully.
 
Can you see the drive from the BIOS?
 
Thanks to everybody for their help and interest.

---

### Post by prenoob on 2009-11-18
[SIZE=3]I know nothing about Linux but I'm sure you need to check in the BIOS[/SIZE]

---

