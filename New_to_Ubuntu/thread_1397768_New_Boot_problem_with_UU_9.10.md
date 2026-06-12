---
title: "New Boot problem with UU 9.10"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by tommark on 2010-02-03
Dell Latitude D610 with Win XP SP3, 1G ram, 60G Hard Disk; Ubuntu 9.10 installed w. Wubi. 
At the double boot screen when I hit Enter for Ubuntu I get a new message:
"Windows could not start because the following file is missing or corrupt:
<windows root>\system32\hal.dll Please re-install a copy of the above file."
When I go to Microsoft for more information I get (for me, a newbie,) confusing information about the "recovery console", hal.dll, and ntoskrnl.exe. 
After the last Ubuntu crash, I re-loaded with Wubi, and painstakingly fine-tuned it until I had it just as I wanted. Then this happened. Am I better off NOT using Wubi, and partitioning my C disk to install Ubuntu by itself in a second partition? 
I truly appreciate the way someone always gets back to me quickly with solutions, but... if I can only look forward to spending about 4 hours a week trying to find solutions, I can't see any valid reason for using Linux. I installed it because of its reputation for not crashing as Windows is wont to do. My Ubuntu is a helluva lot more trouble than Windows ever was.
If there is actually a way to install a more crash-resistant Linux, somebody please let me know.
Again, thank you very much
Tom Markham
[email]tomm@astound.net[/email]

---

### Post by drs305 on 2010-02-03
There is a wubi bug that might be causing your problem. Take a look at *meierfra's* solutions page and see if reinstalling *wubildr *solves the issue:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by warfacegod on 2010-02-03
> Am I better off NOT using Wubi, and partitioning my C disk to install Ubuntu by itself in a second partition? 

This is a matter of opinion in many ways. If you are referring to stability, then yes, any OS will be much more reliable installed as an actual OS as opposed to what amount to an installed program. You are, in essence, running two Operating Systems at the same time. There is an inherent instability in doing so.

> ...I can't see any valid reason for using Linux. I installed it because of its reputation for not crashing as Windows is wont to do. My Ubuntu is a helluva lot more trouble than Windows ever was.
If there is actually a way to install a more crash-resistant Linux, somebody please let me know.

As a continuation of my comments above, let me ask you this. What makes you think that Linux would be stable if you install it inside of an inherently unstable OS?

---

### Post by meierfra. on 2010-02-03
> hal.dll, and ntoskrnl.exe. 
These are files needed to boot Windows, so they are not relevant for your problem.

> <windows root>\system32\hal.dll Please re-install a copy of the above file."
I would  guess that either the   file C:\boot.ini is messed up or that  the file C:\wubildr.mbr is missing. Either way it should be fairly easy to fix your problem

Do you have an  Ubuntu Live CD?  If yes,click on this link 
[CENTER][http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) [/CENTER]
and follow the instruction  to run the boot info script and post the RESULTS.txt. That should give us  the necessary information to determine the exact cause of your error message.


> Am I better off NOT using Wubi, and partitioning my C disk to install Ubuntu by itself in a second partition? 
A regular Ubuntu install is more stable since it will not be infect by corruptions  in your C:drive.

> You are, in essence, running two Operating Systems at the same time.
 The Windows Operating System is used  to install Wubi. But  after installation,  Wubi is complete independent  from the Window Operating System.  The Windows Operating system does not run while Wubi is running.

---

### Post by warfacegod on 2010-02-03
> The Windows Operating System is used to install Wubi. But after installation, Wubi is complete independent from the Window Operating System. The Windows Operating system does not run while Wubi is running.

In the back of my head, I simply label Wubi as another virtual machine in spite of the fact that I know this to not be true.

---

