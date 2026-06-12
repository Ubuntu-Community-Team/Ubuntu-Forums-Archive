---
title: "Another Nvidia driver problem"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by agm. on 2009-06-08
Hi I am very new to Linux and have been using it as my primary system for about a month.  Yesterday, my graphics card started doing very weird things.  It basically started making the screen jump all over the place and mess up.  I booted into safe mode this morning and it was still doing it in safe mode, but then stopped.  The only thing I was trying to do in safe mode was to turn off compiz fusion to see if that fixed the problem.  I guess it sort of did, as now, the screen does not jump, but it is not recognizing my Nvidia driver at all.  As a novice to Linux, I used the repositories for getting my driver when I started using the system, but now it says that it isn't working.

I've tried to do the "sudo nvidia-xconfig" as root (as the prompt tells me when I try to open the Nvidia driver settings) but nothing changes.

I've attached a screenshot to show what I mean with what it is doing...

Any help is greatly appreciated!

---

### Post by overdrank on 2009-06-08
Hi and welcome, what is the model of the nvidia card?
Have you tried reinstalling the drivers?

---

### Post by agm. on 2009-06-08
Sorry, forgot to include that!

It's a GeForce 7950GT

I haven't tried to reinstall the drivers because I was looking at all the help files and I got a bit confused between all the tutorials concerning from source and the repositories.  How do I go about removing the drivers?

Thanks

---

### Post by overdrank on 2009-06-08
> **agm. said:**
> Sorry, forgot to include that!

It's a GeForce 7950GT

I haven't tried to reinstall the drivers because I was looking at all the help files and I got a bit confused between all the tutorials concerning from source and the repositories.  How do I go about removing the drivers?

Thanks

I would first suggest trying the xfix option booting into recovery mode to correct the current graphical issues.
Recovery mode is usually the second choice when booting from the grub. Then you should be given 4 choices and the last being xfix. After selecting xfix and completing you should be given the 4 option again and choose to boot normally.
Then you may use the hardware drivers to reinstall the nvidia drivers. Located under system, administration.

---

### Post by agm. on 2009-06-08
Thanks so much.  I tried the xfix before and it didn't work well... I wasn't sure how to uninstall/reinstall drivers before except through terminal which seemed most likely not the way for me to begin trying to fix my driver issues.

After uninstalling and reinstalling the drivers it is now fixed!  

Problem is solved!  

Thanks so much.

---

### Post by overdrank on 2009-06-08
No problem you did all the work. ;)

---

