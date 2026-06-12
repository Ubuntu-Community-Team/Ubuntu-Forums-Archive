---
title: "Where can I get a hard drive that will run ubuntu?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Sarrel on 2009-06-15
My IBM Laptop overheated and now the hard disk doesn't work anymore. The rest of it works fine though, and I think if I got it a hard disk, I could boot Ubuntu off of it, (something about being able to boot off something that isn't the main hard disk?)  and I could use it as a desktop computer, or give it to one of my friends who doesn't have a computer. I haven't been able to find one though, and I'm wondering if I need a special hard disk to boot off, and if it would cost more, and where I would find one, and how much space would it need to run ubuntu properly?(Though I  might just go ahead and get 160gb anyway.)

---

### Post by reeseslover531 on 2009-06-15
You should just need a 2.5" hard drive.  You will need to put it in the computer and that is all you need to do. Ubuntu can install in about 5gb so you don't need to worry about space.

---

### Post by sim-value on 2009-06-15
Do you mean an USB hardisk ?

---

### Post by bhadotia on 2009-06-15
> **Sarrel said:**
> My IBM Laptop overheated and now the hard disk doesn't work anymore. The rest of it works fine though, and I think if I got it a hard disk, I could boot Ubuntu off of it, (something about being able to boot off something that isn't the main hard disk?)  and I could use it as a desktop computer, or give it to one of my friends who doesn't have a computer. I haven't been able to find one though, and I'm wondering if I need a special hard disk to boot off, and if it would cost more, and where I would find one, and how much space would it need to run ubuntu properly?(Though I  might just go ahead and get 160gb anyway.)

Ubuntu uses maximum of six Gigs on my 10 gb partition I have alloted to it. I use a separate partition for /home of about 3 Gigs. And ubuntu would run on any standard HDD.

---

### Post by ugm6hr on 2009-06-15
You should just replace the internal HD that is dead.

Find the manual for your laptop; it is usually easy to replace.

Take the current HD out, and buy a similar replacement.  Only question is whether it is IDE or SATA.

Then the issue of booting from a secondary drive is redundant.

---

### Post by SunnyRabbiera on 2009-06-15
A hard drive is a hard drive, any brand should work with Ubuntu

---

### Post by redbook4574 on 2009-06-15
> **ugm6hr said:**
> You should just replace the internal HD that is dead.

Find the manual for your laptop; it is usually easy to replace.

Take the current HD out, and buy a similar replacement.  Only question is whether it is IDE or SATA.

Then the issue of booting from a secondary drive is redundant.


As an ex-IBM engineer stick with WD HDD

---

### Post by steve-shinn on 2009-06-15
Samsungs are very popular with pc builders at the moment

---

### Post by Therion on 2009-06-15
> **redbook4574 said:**
> As an ex-IBM engineer stick with WD HDD
As a non-ex IBM engineer allow me suggest the same.

Western Digital.  Period.

---

### Post by LowSky on 2009-06-15
+1 to Western Digital. If this was 5 years ago I would say Seagate but lately they make some of the worst hard drives... WD makes very good drives. for about $50 you can easily replace your burnt out drive.

Newegg.com is the best place to buy computer parts hands down

IDE
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150380+1035907889&QksAutoSuggestion=&Configurator=&Subcategory=380&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150380+1035907889&QksAutoSuggestion=&Configurator=&Subcategory=380&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

SATA
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150380+1035915133&QksAutoSuggestion=&Configurator=&Subcategory=380&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150380+1035915133&QksAutoSuggestion=&Configurator=&Subcategory=380&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

---

### Post by lkraemer on 2009-06-15
If you boot and go into the BIOS is your existing drive recognized?
If your drive is recognized , proceed, otherwise skip the next section.
Or, you could do it as a TEST.

Before I did anything to your drive I suggest the following.
Download the LiveCD's of SystemRescueCD and UBCD.  One of
these has Testdisk.  Boot each one and locate Testdisk.
Run it on your drive and see if it is recognized, or shows
any data or partitions that can be recovered.  If so, you
might not loose too much data.  Burn the ISO at a slow speed
and Disk at Once.  You can use any software for this.
Windows or Linux.  If the LiveCD's won't run, remove the drive,
Get a 2.5" to 3" drive adapter and plug the 2.5 into your
Desktop for testing (assuming IDE). SATA should be plug ready.

Open up the door/computer and remove the defective Drive.

If you go to this site:
[http://freepctech.com/pc/001/installing_ide_devices.shtml](http://freepctech.com/pc/001/installing_ide_devices.shtml)
and look down at the drive, you will see a dual row of pins that
the Ribbon cable connects to.  (This picture is NOT a 2.5" so it
does have more pins, but that does not matter)  If you don't see
a dual row of pins, then your drive is a SATA. 

Newegg and Tigerdirect has lots of drives.  Pick one that is close
to your existing one in Gigs, and is of the correct type IDE vs SATA.

VERIFY the jumper on the NEW IDE Drive to the one you removed.
Some Laptops don't use jumpers, But my old Compaq did.  I am not sure
if SATA even uses a Jumper for Drive Select.

Install the new drive and you are ready to boot a LiveCD of the
Distro of your choice.

[http://Distrowatch.com](http://Distrowatch.com)
(Some Distro's may not boot on older systems.  CrunchBang 8.04.2 will
along with Slitaz)

Checkout the CrunchBang LiveCD!
Checkout the PCLinuxOS LiveCD 2009.1

DITTO on Western Digitial..........The BEST!
  
lkraemer

---

### Post by wpshooter on 2009-06-15
> **Therion said:**
> As a non-ex IBM engineer allow me suggest the same.

Western Digital.  Period.

Also as a non-ex IBM engineer allow me to suggest Seagate drive instead - if one is available/compatible for your machine.

---

### Post by Sarrel on 2009-06-15
should I also replace the fan? I think that's probably what made the hard disk break. Are there any other reasons it could have overheated?

---

### Post by PukingPenguin on 2009-06-15
> **Sarrel said:**
> should I also replace the fan? I think that's probably what made the hard disk break. Are there any other reasons it could have overheated?

If the fan isn't running when you power up, you might need to replace it. 
Hard drives fail. not often, and not USUALLY soon, but they inevitably fail. It doesn't have to be "because" of anything, heat or otherwise.

---

### Post by H2SO_four on 2009-06-15
+1 for WD, best HDD's IMHO.

---

