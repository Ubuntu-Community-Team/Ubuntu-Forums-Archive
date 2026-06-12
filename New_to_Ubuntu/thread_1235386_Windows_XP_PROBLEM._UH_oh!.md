---
title: "Windows XP PROBLEM. UH oh!"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by scootatheschool1990 on 2009-08-09
I booted my computer and selected Windows xp. It promted me to check the disk but i canceled. I then restarted my computer and now windows isn't there. I have 2 partitions and I booted ubuntu, I still can't mount to The HD with Windows XP on it... what is wrong? Here is a link to what error message is shown when trying to mount

---

### Post by -kg- on 2009-08-09
OK, since Windows wanted to perform a disk check, it is likely that XP didn't close down properly and properly "unmount" the partition (yes, Windows unmounts partitions also...it's just done invisibly in the background).

Now when you said that Windows was not there, did you mean that you couldn't boot into it or had no option from GRUB, or do you just mean that you couldn't mount the partition under Linux?  If it's just that you can't mount the partition under Linux, you pretty much need to do what the instructions in the error messages tell you, running checkdisk /f and reboot into Windows (twice, it says; who am I to argue?).  That should fix any problems and you should be able to mount the partition with no further problems.

If you couldn't boot into it, or the option was missing from GRUB, you have further problems and will likely have to re-install GRUB, or at least edit the menu.lst and add the option back in.  I'm thinking you meant the first thing, though.  Generally, if you experience the problem you supplied the screenshot of, it's a bad shutdown under Windows and can be fixed by booting back into Windows and making sure it shuts down properly and unmounts the volume.

I'm sure that I don't need to tell you not to cancel out of a disk check in the future.  It's a good idea to let it complete whether you are dual booting or not.  Every time you skip a disk check, you are gambling whether you are further breaking the OS and finally will not be able to boot into it at all without extensive repair operations or re-installation.

---

### Post by scootatheschool1990 on 2009-08-25
I have tried many times to mount the HD from Ubuntu, with the same reply "cannot mount volume". 

I have tried booting into Windows and it will just restart my computer every time. 

So what i need is a way to check the disk from ubuntu( because i cant access windows chkdsk.. if that makes any sense... :) and thank you very much for your help. Looking forward to your reply :)

---

### Post by theozzlives on 2009-08-25
Boot to the recovery console off the XP disk and run chkdsk /f from there.

---

### Post by Garyhans on 2009-08-25
Boot From your windows xp CD and watch closley at the bottom the screen. Select R for Repair. You should get the command Prompt. type chkdsk /r  don't forget space. Let it do it's work. If it comes to the point where you run the command fixmbr you will have to reinstall grub.

---

### Post by scootatheschool1990 on 2009-08-25
FIXED! I want to thank all of you for your help and support! :)

I installed Windows 7 on another Hard drive. I then connected all my hard drives to my computer and booted windows seven. Windows 7 picked up on the fact that windows xp needed to run chkdsk. so it windows 7 is my savior.

And I do think that the boot cd idea would have worked too! Thanks again :) have a wonderful day ! :) :) :)

---

