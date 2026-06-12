---
title: "Downgrade Problems"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by vckeating on 2009-01-12
Hi all,

Have a really bizarre problem here.  I've been using Intrepid on a older Compaq laptop for the last couple of weeks and got frustrated with the Network Manager problems.  I was going to downgrade to Hardy, but I find that none of the installation CDs will boot properly.  My drive will read audio CDs of the same make, and the installation CDs run fine on my XP machine, the boot order is correct, etc., but for some reason when I pop in the install machine the CD drive just makes churning noises for a while before the computer decides to boot from the hard drive.  

I should also mention that I can't 'see' the install disks from ubuntu either - but all other CDs/DVDs are fine.  I don't have the option to boot from a pen drive in my BIOS, so I was hoping that there's something obvious I'm overlooking or an alternative way of going about installing Hardy.

Thanks!

---

### Post by mapes12 on 2009-01-12
If you're using a Live CD then try an [Alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") instead.

---

### Post by bhadotia on 2009-01-12
> **vckeating said:**
> Hi all,

Have a really bizarre problem here.  I've been using Intrepid on a older Compaq laptop for the last couple of weeks and got frustrated with the Network Manager problems.  I was going to downgrade to Hardy, but I find that none of the installation CDs will boot properly.  My drive will read audio CDs of the same make, and the installation CDs run fine on my XP machine, the boot order is correct, etc., but for some reason when I pop in the install machine the CD drive just makes churning noises for a while before the computer decides to boot from the hard drive.  

I should also mention that I can't 'see' the install disks from ubuntu either - but all other CDs/DVDs are fine.  I don't have the option to boot from a pen drive in my BIOS, so I was hoping that there's something obvious I'm overlooking or an alternative way of going about installing Hardy.

Thanks!

I also had similar issue, XP was reading the discs fine (after a lots of churning), but ubuntu couldn't and neither ubuntu nor XP were able to burn discs. The problem was that my CD drive was messed up. Try if CD is able to boot from another computer (may be of some friend).

---

### Post by vckeating on 2009-01-12
Hey all,

Yes, I think the problem is with the CD drive.  I just made a boot CD on the Ubuntu machine (previously I made them on my XP one) and it created and recognised it ok.  Now I'm getting stuck through the installation process though with a similar 'churning' noises.  If this doesn't work in the end, and there's no pen drive boot option, is that it for my list of ways to install Hardy?

Cheers!

Edit:  Well, it looks like it didn't work - ended up stalling on the Ubuntu screen with a flashing caps lock light.

---

### Post by flyingsliverfin on 2009-01-12
try 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

there are many ways to install ubuntu 8.04 there. 
you might want to try using the smart boot manager method or the Installation/FromLinux

---

### Post by perlluver on 2009-01-12
> **vckeating said:**
> Hey all,

Yes, I think the problem is with the CD drive.  I just made a boot CD on the Ubuntu machine (previously I made them on my XP one) and it created and recognised it ok.  Now I'm getting stuck through the installation process though with a similar 'churning' noises.  If this doesn't work in the end, and there's no pen drive boot option, is that it for my list of ways to install Hardy?

Cheers!

Edit:  Well, it looks like it didn't work - ended up stalling on the Ubuntu screen with a flashing caps lock light.

That flashing Caps Lock key, when did it happen?  While Ubuntu was loading?  It sounds like a kernel panic, or the disk might have been bad.

---

### Post by vckeating on 2009-01-12
Hi everyone,

perlluver - it happened during the first Ubuntu screen, when the bar is moving back and forth.  I assume that it couldn't read part of the CD so it just quit after a while.  

flyingsliverfin - This might work.  I'm just downloading the alternate CD now and reading through the instructions.  

Cheers all!

---

### Post by bhadotia on 2009-01-12
> **perlluver said:**
> That flashing Caps Lock key, when did it happen?  While Ubuntu was loading?  It sounds like a kernel panic, or the disk might have been bad.

> **vckeating said:**
> 
perlluver - it happened during the first Ubuntu screen, when the bar is moving back and forth.  I assume that it couldn't read part of the CD so it just quit after a while.  


You check what went wrong by checking the boot messages. Press ctrl+alt+f1 keys to get to the console, there you can scroll through the boot messages using shift+page up and shift+page down keys.

---

### Post by albinootje on 2009-01-12
> **vckeating said:**
>  I've been using Intrepid on a older Compaq laptop for the last couple of weeks and got frustrated with the Network Manager problems.
Instead of going back to Hardy, you can try wicd instead of N.M. first :

-> [http://wicd.sf.net](http://wicd.sf.net)

---

### Post by vckeating on 2009-01-12
Thanks for everyone's help on this one.

I gave the 'From Linux' instructions a go a few different ways, both manually and using Unetbootin, but couldn't get past errors when it came to formatting the hard drive - the full format would come back with an error while creating a new partition came back with 'not big enough' or something similar (although I think it was plenty large, unless Ubuntu has space requirements > 10GB)

Anyway, going with the path of least resistance, I'm giving the wicd program a shot to see if this solves my problems - the biggest one of which was being able to connect to a WPA wireless signal at school.  If not, it's back to the drawing board and I'll have to figure out what's going wrong above.

Thanks again to everyone who helped out.

---

