---
title: "Help an idiot with a network install...please?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-01-30
I'm desperate. I've tried every other means of installing that I can find, and nothing has worked. I'm down to a network installation as my last resort, and I can't figure out how to get the job done. I've looked at the instructions here ([https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)), but they may as well be in a foreign language. I'm not computer retarded, but I'm sure feeling like it right now.

If someone would be willing to hold my hand and step me through getting this done, I'd sure appreciate it.

---

### Post by yeats on 2009-01-30
So what kind of hardware are you trying to install on? (memory, HD space, processor)?

To be clear - you've downloaded and tried the alternate install CD?

---

### Post by doctorbighands on 2009-01-30
You're right, I should clarify some things.

The target machine is a laptop, PIII 1.13GHz, 100GB HDD, 512MB RAM. It has a dysfunctional CDROM drive and the BIOS doesn't support booting from USB. There is a functional floppy drive.

I do have a home network with a desktop machine (this will be the server for the network install) running Ubuntu 8.10.

---

### Post by yeats on 2009-01-31
Yes - I can see why you're struggling - that PXE boot page assumes a lot of knowledge that I don't have either :-).  It might be a good idea to post this on one of the other boards.  That said, I worked very hard recently to get Debian etch onto an ancient Pentium III laptop with a failing CD-ROM drive.  Fortunately, in that case, I was able to let the CD drive limp along enough to get the minimal system installed (it was for a print server so it didn't need a GUI).

Anyway, if you have a working floppy drive and some spare floppies, you might look at this page (which you may have already):

[https://help.ubuntu.com/community/Installation/WithFloppies]("https://help.ubuntu.com/community/Installation/WithFloppies")

with has you use the Debian floppy installer to get things started, and an Ubuntu bootstrap program to finish the job (you would want to substitute "etch" for "sarge" here - this is obviously an out-of-date tutorial).

In any case, it looks to me like you have a fairly complicated task here, however you do it.  Feel free to post back here, but, like I said, you might get more "expert" help on one of the other boards.  

Good luck!

---

### Post by boof1988 on 2009-01-31
> **doctorbighands said:**
> You're right, I should clarify some things.

The target machine is a laptop, PIII 1.13GHz, 100GB HDD, 512MB RAM. It has a dysfunctional CDROM drive and the BIOS doesn't support booting from USB. There is a functional floppy drive.

I do have a home network with a desktop machine (this will be the server for the network install) running Ubuntu 8.10.

If you have:
[LIST=1]
[*]A working computer (with Unetbootin installed)
[*]A partitioning application on the working computer
[*]A ubuntu(or xubuntu)-8.04.2-desktop iso (I couldn't get this to work with Ubuntu 8.10)
[*]A USB adapter to connect the (now removed from target machine) HDD and the working computer
[*]The desire to attempt this crazy idea
[/LIST]

Then the following (crazy method) is an option:
[LIST=1]
[*]Create an "Installer" partition (large enough for iso image) on the HDD
[*]Use Unetbootin to copy the iso image to the "Installer" partition and  make the drive bootable
[*]Install HDD into the target machine
[*]Boot target machine and hope for the best
[*]When I have done this, not all of the options of the Unetbootin menu have worked
[*]The *Install*, *Check Integrity* and *Try Ubuntu* options have worked for me
[/LIST]

Hope this helps a little.

---

### Post by gn2 on 2009-01-31
Another option is beg, steal or borrow a bootable cardbus optical drive. (ok don't steal one)

Something like [this]("http://cgi.ebay.co.uk/New-24X-EXTERNAL-MOBILE-SLIM-PCMCIA-CD-ROM-SLIM-MINI_W0QQitemZ320331415220QQcmdZViewItemQQptZPCC_Drives_Storage_Internal?hash=item320331415220&_trksid=p3286.c0.m14&_trkparms=72%3A1690|66%3A2|65%3A12|39%3A1|240%3A1318") or just replace the dodgy internal one.

---

