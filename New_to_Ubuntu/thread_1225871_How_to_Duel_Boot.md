---
title: "How to Duel Boot?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-07-29
Is it possible to duel boot with Windows and Ubuntu after you already have Ubuntu installed? And if so, how?

---

### Post by nhasian on 2009-07-29
I dont think you want your two operating systems dueling... but if you want to dual boot, then you can either add a 2nd hard disk and install windows to it, or you can boot off a liveCD and use gparted to shrink your partition to make room for the windows install.  make sure to backup any critical data in case something goes wrong...

after you install windows it will overwrite grub, but you can use the supergrubdisk to fix it.

---

### Post by cozmicharlie on 2009-07-29
> **GodlySoup said:**
> Is it possible to duel boot with Windows and Ubuntu after you already have Ubuntu installed? And if so, how?

It is possible but it is much easier if you install windows first then Ubuntu. Not sure if you want XP or vista.  This site has a very good tutorial for both.
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Clorow on 2009-07-29
Yes, it does that by default if you install Ubuntu after Windows. However, If you install Ubuntu first then Windows, Windows won't recognize Ubuntu so you'll have to do some text editing.

In other words, if Windows is installed, then you install Ubuntu, it will automatically have you dual-boot and you won't have to do anything extra.

---

### Post by lisati on 2009-07-29
I agree that a duel where the OS puts the boot in doesn't sound good.

Some information on dual booting can be found at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by GodlySoup on 2009-07-29
Well, the thing happened to be that I installed Ubuntu to try it out and because I didn't have my Vista disks on me at the time. I like Ubuntu and have done much to figure it out by installing many applications and games that I want to keep it now that I have the disks back. 

I realize it would've been much simpler if I had had Windows on the computer first, but this instance just wasn't the case.

Thanks for the links!

Cheers, 
GS

---

### Post by cozmicharlie on 2009-07-29
> **GodlySoup said:**
> Well, the thing happened to be that I installed Ubuntu to try it out and because I didn't have my Vista disks on me at the time. I like Ubuntu and have done much to figure it out by installing many applications and games that I want to keep it now that I have the disks back. 

I realize it would've been much simpler if I had had Windows on the computer first, but this instance just wasn't the case.

Thanks for the links!

Cheers, 
GS

You could do a backup of ubuntu, load windows, reinstall ubuntu and restore your backup.  A round about method but at least it will assure everything works right.

---

### Post by GodlySoup on 2009-08-07
> **cozmicharlie said:**
> You could do a backup of ubuntu, load windows, reinstall ubuntu and restore your backup.  A round about method but at least it will assure everything works right.

What do you suggest I use to back it up?

I'm new to dual booting too, is there a way to copy files over to the next partition or whatever is created between the two operations from one to the other?

---

### Post by GodlySoup on 2009-08-10
Bump.

---

### Post by hugmenot on 2009-08-10
One chooses the weapon, the other one chooses the place.

Then you stand back and let them duke it out.

---

### Post by kansasnoob on 2009-08-10
It would be helpful to see a screenshot of Gparted. If it's not yet installed, please install gparted either using Synaptic or from terminal with this command:

```
sudo apt-get install gparted
```

Then you can find Gparted in System > Accessories > Partition Editor and then use the Screenshot tool in Accessories to take a screenshot of Gparted. That will tell us what size your drive is, how much is used and/or free, and what your current partition layout is.

**Note: you'll not want to use the "mounted" version of Gparted for actual repartitioning, that will need to be done using a live CD.**

I'd also like to know what version of Windows you're going to install.

Also, in your own words, what do you have stored on your drive that you'd hate to lose!

---

### Post by Gregz on 2009-08-10
ok I have a question then, I now have ubuntu on one hard drive and windows on another. I'm switching cables between the two now. 

Is there and easy way to dual boot both? 

Since they are on there own hard drives do I have to reinstall anything??

Thank you in advance.
                           Greg

---

### Post by kansasnoob on 2009-08-10
> **Gregz said:**
> ok I have a question then, I now have ubuntu on one hard drive and windows on another. I'm switching cables between the two now. 

Is there and easy way to dual boot both? 

Since they are on there own hard drives do I have to reinstall anything??

Thank you in advance.
                           Greg

It would be best to start a new thread specific to your own problem.

---

### Post by Gregz on 2009-08-10
ok, sorry I started thread  
                            
                           thanks

                            Greg

---

