---
title: "karmic won't boot, initramfs error ?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by techno-mole on 2009-11-25
Hello.

I have a serious issue with my Karmic 64bit install, that being it now refuses to boot, I am unable to use one of the earlier kernel versions or the recovery modes for any of the kernels.

As I dual boot I normally wait until grub has loaded and then select which OS i want, XP 64bit or Karmic 64bit, but for some reason (which I really can't fathom) I can now only boot into XP ? If I select to boot up Karmic I get a small Ubuntu symbol on screen (I assume this is the splash screen) and then I get the following.

```
Gave up waiting for root device :- common problems :

Boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
- check root= (did the system wait for the right device ?)
- Missing modules 9cat /proc/modules; ls /dev)
ALERT ! /dev/disk/by-uuid/1df41e26-8fe6-4988-9fa1-41b3c4d76f8e does not exist. Dropping to a shell !

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1Ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I have done some searches to figure out what the hell is going on, but nothing has helped any, and from what I can tell a lot of people have just re-installed ubuntu, this is not an option, as I have files I need and cannot afford to loose them.

I installed karmic 64bit from a cd which I downloaded and used, as mentioned i also run Xp 64bit on another hard drive.

I have also tried things like changing from ide to raid mode in my bios, this has not made any difference, I have also tried achi mode as well, and resetting the bios to its default settings as well, no joy.

I would be grateful for any help given, I really need to get back into karmic, with out having to re-install.

cheers.

---

### Post by Sak on 2009-11-25
I'm experiencing this same problem since yesterday's update.

I was able to restart once, after the update yesterday, but this morning when I boot I get this error.

Any help would be great.

---

### Post by SuaSwe on 2009-11-25
Before anything else, I'd suggest heading into a live environment using a trusty LiveCD and moving over whatever you need to keep to your Windows drive/partition. Chances are this is just a boot issue and that all your files are still intact. :)

I had first boot then severe performance issues with Karmic and in the end could not get it to work (ATI graphics problem, very possibly) - fortunately I have root on a different partition from home, so was able to reinstall Jaunty painlessly; if you have yours set up like this, you can do the same using a LiveCD.

In terms of getting Karmic to work, I'll leave it to the experts to advise. :D

---

### Post by rideburton56 on 2009-11-25
> **techno-mole said:**
> 
I have done some searches to figure out what the hell is going on, but nothing has helped any, and from what I can tell a lot of people have just re-installed ubuntu, this is not an option, as I have files I need and cannot afford to loose them.


Worst comes to worst, if you do have to do a full reinstall, you can use the live CD to boot, mount your partition, and copy the files that way.  Not the ideal solution, but if nothing else works, at least you won't lose your work.  I wish I had more input, good luck!

---

### Post by techno-mole on 2009-11-25
well I am a little more puzzled than I was before, why ? well I'm lucky that in my house there are 3 desktop systems and a file server.

I tried the live cd route to try and fix the issue (didnt work) so I unplugged the drive and hooked it up to my wifes karmic system, mainly to transfer the files I wanted to keep over, I have my system set up in a way that means I should (providing I pay attention) be able to install the system and leave the home directory intact (I still like to back up though)

So the aim was to back up my files, and then see if I could re-install karmic and start again, only when I put the drive back in my system the live cd didnt load up at boot, the hard drive did, and it went on to boot into karmic with no error ? I have no idea why, I can only assume that in mounting the drive in another system changed something on the drive (its id maybe ?) and now it works, I have backed up my stuff to my external and tried re-booting a number of times, but as yet I have not had the same error, but I have no idea why it is now working.

The best advice I can give is to use the live cd and copy your files some where (just to be safe) and either re-install the system with out changing the home folder (I think this depends on the partitions ?) or just do a complete install. If you have another system (ubuntu) try mounting the drive and seeing what happens when you stick it back in your system.

sorry this isnt more helpful, I'm still trying to work out both what went wrong and what happened to fix the issue.

---

