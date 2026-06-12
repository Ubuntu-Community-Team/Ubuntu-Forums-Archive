---
title: "Help with error messages please!"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by munnster on 2010-01-07
(I will apologize in advance for being wordy!) I am a total n00b with Ubuntu. 

I have been trying to install Ubuntu onto a previously used 30GB hard drive for my son to use and have had a few issues.

First off the computer I am using is an old emachine T4200
Intel Pentium 4 Processor 2GHz (w/512KB), Intel 845 chipset, 256MB SDRAM (PC133) (I am not sure if you need any more information than that).

Anyway, I have an Ubuntu 9.04 install disk I received (and previously used successfully on my own computer HD) that I used to reformat the HD.  The install went without a hitch and it restarted (after format) just fine.  When I went to start it the next day to continue setting it up for him, I got a black screen with "Operating System Not Found".  I attempted to reinstall it with the same disk and again the same thing happened. Now I admit I am a glutton for punishment and I guess do not learn from mistakes because I attempted the install with the same disk again, but checking the disk for errors (integrity?), it said there were 52(!) errors. (That is errors on the install disk, not the HD, correct?) I then proceeded to download a copy of 9.10 both ISO file as well as the alternative install and attempted both.  I got the same results both times.

My son suggested putting the HD into a different computer just to see what would happen (I figured it couldn't hurt), so putting it into an emachine T3508--Intel Celeron D Processor 356 (512KB L2 cache, 3.33GHz, 533MHz FSB),  ATI Radeon™ Xpress 200 with 1GB DDR, I got: 
GRUB LOADING. 
error: out of disk 
grub rescue>

I do not know if the T4200 was insufficient for ubuntu or if it was some other problem.  Do I scrap that machine completely and attempt a clean install on the 30GB HD yet again in a newer tower (I have room in a T6412)? Or will I have the same results?

As an aside, I did find reference to GRUB2 (in reference to grub rescue>) here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
and wondered if I should try that or if it would even work since I was planning to put it back into the T4200 and the error message with that was Operating System Not Found?

Thank you for your patience with my long post. I hope I made SOME sense! :confused:

---

### Post by bodhi.zazen on 2010-01-07
From your description your disk is corrupt.

You first need to check the integrity of the iso, you can do this by checking the md5sum.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the md5sum is OK , then burn it to disk

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then boot the CD and check the disk. It sounds as if your disk had 52 errors ? That is 52 too many errors :twisted:

In terms of your hardware, 256 Mb RAM is the minimal requirements for Ubuntu and it wikk run slow at best. I suggest a lighter distro such as Crunchbang or Puppy linux. To run Ubuntu you man need to first partition the disk and add a swap partition.

The second machine, the laptop, should be OK, although you may have a problem with ATI (I am not sure about that ATI card).

---

### Post by zkriesse on 2010-01-07
> **bodhi.zazen said:**
> From your description your disk is corrupt.

You first need to check the integrity of the iso, you can do this by checking the md5sum.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the md5sum is OK , then burn it to disk

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then boot the CD and check the disk. It sounds as if your disk had 52 errors ? That is 52 too many errors :twisted:

In terms of your hardware, 256 Mb RAM is the minimal requirements for Ubuntu and it wikk run slow at best. I suggest a lighter distro such as Crunchbang or Puppy linux. To run Ubuntu you man need to first partition the disk and add a swap partition.

The second machine, the laptop, should be OK, although you may have a problem with ATI (I am not sure about that ATI card).
Ah well Bodhi my man you pretty much said what I was going to say...just not as awesome as you did....

---

### Post by munnster on 2010-01-07
Thanks for the replies.

I did actually check the md5sum on the ISO I downloaded and it was good, so I don't understand why it didn't work (the 52 errors were on the disk I got in the mail!)

I use the second computer (with the ATI card) with my ubuntu HD and it works fine, but I already have a dual boot with XP on that machine.  I guess I will experiment with the T6412 next. If that doesn't work I will try a lighter distro.

Thanks again. :)

---

