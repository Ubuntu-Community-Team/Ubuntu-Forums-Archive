---
title: "Is my laptop dead?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by MsMixer on 2009-06-29
Hey all! I've been hunting around on message boards for someone who has a similar problem to mine, but I've had no luck.  I'm a new Ubuntu Jaunty user.  I'm running a Dell Latitude D600 laptop with a 250g external Seagate Drive.  At first it was a dual boot machine (XP and Jaunty) until I decided to get rid of XP.  Jaunty worked great for a few months with some minor driver issues, until I started to get error messages on startup.  After hitting y multiple times, my Ubuntu would eventually load.   Now, all I get are error messages and Ubuntu won't load.  Also, the last time I was able to log in, my mouse wouldn't respond and my CD/DVD drive would read every CD as blank.  I'm willing to do a complete wipe, but I'm not sure how because the drive isn't working.  Anyone else encounter this?  Help!?!

---

### Post by overdrank on 2009-06-29
> **MsMixer said:**
> Hey all! I've been hunting around on message boards for someone who has a similar problem to mine, but I've had no luck.  I'm a new Ubuntu Jaunty user.  I'm running a Dell Latitude D600 laptop with a 250g external Seagate Drive.  At first it was a dual boot machine (XP and Jaunty) until I decided to get rid of XP.  Jaunty worked great for a few months with some minor driver issues, until I started to get error messages on startup.  After hitting y multiple times, my Ubuntu would eventually load.   Now, all I get are error messages and Ubuntu won't load.  Also, the last time I was able to log in, my mouse wouldn't respond and my CD/DVD drive would read every CD as blank.  I'm willing to do a complete wipe, but I'm not sure how because the drive isn't working.  Anyone else encounter this?  Help!?!

Hi and welcome, are you able to boot a live cd of Ubuntu?
What was the error message you received?
Are you using the external drive to boot Ubuntu?

---

### Post by MsMixer on 2009-06-29
> **overdrank said:**
> Hi and welcome, are you able to boot a live cd of Ubuntu?
What was the error message you received?
Are you using the external drive to boot Ubuntu?

I am unable to boot from the live CD, and I am not using the external drive to boot.
I am getting dozens of error messages.  But they cycle through so quickly it's hard to read them.  These two seem to be recurring, though. (the x's represent different numbers).

[xxx.xxxx] ata1.00: status: { DRDY ERR }
[xxx.xxxx] ata1.00: error: { UNC }

They are by no means the only ones I see, just the ones that show up the most.

Thanks!

---

### Post by QIII on 2009-06-29
It is possible that either your CD or your hard drive is going bad.

Linux systems can be more sensitive to impending hd failure than other OSs.

Try using you windows install disk.  If it doesn't run at all from CD (assuming your BIOS is set to boot from CD first), you might have a problem with the CD drive.

If it installs to your hard drive, you may still have issues with the hd.  But at least that is somewhere to start and let us know how that goes so we can take a stab at where to go from there.

---

### Post by philcamlin on 2009-06-29
its probably ths os thats corrupt no your laptop isnt dead because its not hardware i hope :)

---

### Post by MsMixer on 2009-06-29
> **QIII said:**
> It is possible that either your CD or your hard drive is going bad.

Linux systems can be more sensitive to impending hd failure than other OSs.

Try using you windows install disk.  If it doesn't run at all from CD (assuming your BIOS is set to boot from CD first), you might have a problem with the CD drive.

If it installs to your hard drive, you may still have issues with the hd.  But at least that is somewhere to start and let us know how that goes so we can take a stab at where to go from there.

I'm sure it's possible that one or the other is going bad, but it seems strange that everything failed at once.  
My BIOS is set to boot from CD first, and I don't have a Windows install disk...Windows is dead to me.  
Fwiw, both drives worked fabulously until yesterday.  I wonder if I royally screwed up by ignoring and attempting to fix the multitude if error messages.

---

### Post by QIII on 2009-06-29
It probably isn't both drives.  It may not even be one drive.  The errors you are getting could very well be issues with software.

I'm doing some research now.

By the way, do you at least get to the GRUB menu?

Edit:  Just scrolled up and looked.  DRDY ERR indicates the device is not ready...

---

### Post by MsMixer on 2009-06-29
> **philcamlin said:**
> its probably ths os thats corrupt no your laptop isnt dead because its not hardware i hope :)

I hope that's the case.  Is there any way to wipe my external drive if I can't log into Ubuntu?  The farthest I can get is "myname@localhost:~$".

Oh yeah, my wireless internet failed two days before everything else, although I could still connect to my router with an ethernet cable.

Thanks.

---

### Post by philcamlin on 2009-06-29
crapp your dropping to shell !!!!!!!

sudo install ubuntu-desktop 

see if thet gets you anywhere :popcorn:

after that install

sudo apt-get install gpart << that will format your drive for you

---

### Post by OutOfReach on 2009-06-29
> **MsMixer said:**
> I am unable to boot from the live CD, and I am not using the external drive to boot.
I am getting dozens of error messages.  But they cycle through so quickly it's hard to read them.  These two seem to be recurring, though. (the x's represent different numbers).

[xxx.xxxx] ata1.00: status: { DRDY ERR }
[xxx.xxxx] ata1.00: error: { UNC }

They are by no means the only ones I see, just the ones that show up the most.

Thanks!

Interesting...I had the same exact error some months ago on my laptop, the hard drive died. Now, I'm not sure if this is the exact problem for you though..as others have said it just might be that the OS is corrupted.

---

### Post by MsMixer on 2009-06-29
> **philcamlin said:**
> crapp your dropping to shell !!!!!!!

sudo install gnome-desktop 

see if thet gets you anywhere :popcorn:

Tried it...here's what I got:

sudo: can't mkdir /var/run/sudo: Read-only file system
[sudo] password for myname:
install: missing destination file operand after 'gnome-desktop'
Try 'install --help' for more information.
myname@localhost:~$

---

### Post by philcamlin on 2009-06-29
well im out of ideas beside the hard drive failure :(

---

### Post by MsMixer on 2009-06-29
> **philcamlin said:**
> crapp your dropping to shell !!!!!!!

sudo install ubuntu-desktop 

see if thet gets you anywhere :popcorn:

after that install

sudo apt-get install gpart << that will format your drive for you

oops, didn't see the second part of your post.  Here's the output for that:

sudo: can't mkdir /var/run/sudo: Read-only file system
[sudo] password for myname:
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
myname@localhost:~$ *Starting anac(h)ronistic cron anacron
*Starting anac(h)ronistic cron anacron
*Starting anac(h)ronistic cron anacron

---

### Post by emeraldgirl08 on 2009-06-29
If you have access or could maybe borrow a friends computer with a USB Enclosure you could wipe the drive clean!

Google and download Killdisk and burn it as a bootable image on CD. The program will make a one-pass zeroing out method. 

After it is wiped you can reinstall your Ubuntu and have another go at it.

---

### Post by Zero0hm on 2009-07-14
Had the same problem after moving drives around in a pc I was turning into a fileserver. Took me about an hour to figure it out. 
[LIST=1]
[*]I booted off a rescue USB key [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[*]mount /dev/sda1 /mnt/tmp
[*]cd /mnt/tmp/etc
[*]nano fstab
[*]removed entries that no longer exist
[*]reboot
[/LIST]
Worked for me. Hope this helps someone.

---

### Post by nhasian on 2009-07-14
first lets see if your hard disk is okay.  go to the hard disk manufacturer's website and download their diagnostic tools.  it will take several hours to run.  if your hard disk is not failing:

try running an fsck on the drive to repair your data.  if that doesnt resolve the issue, try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") or [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by The Cog on 2009-07-14
I had a D600 until recently. I used it happily for several years. The hard disk started erroring a few weeks ago though, and finally wouldn't boot at all. Maybe these hard drives have a natural life span that is near its end?

In my case, the drive had been making buzzing noises gently for a few months so I had my suspicions that it might be on the way out.

I think that even the live CD will try to read the drive (and use the swap partition if it finds one) so a dying hard drive might perhaps also explain problems with the live CD.

In my case, a new drive and a restore from backup got everything working sweetly again. Just before I was issued with a newer model laptop anyway.

---

### Post by HereInOz on 2009-07-14
I would go for a Hard drive failure.  If the unit is more than 3 years old, the chance of a drive failure is fairly high.

---

### Post by mikechant on 2009-07-14
If possible you could try disconnecting the power from the hard drive and then see if you can boot from the LiveCD.

---

### Post by LewRockwell on 2009-07-14
given that the optical drive is acting strangely also I'd be more inclined to think there was a power quality issue

that could also cause video and main board anomalies as well

of course, if the OP never posts again we'll be in the dark FOREVER...lol.

.

---

