---
title: "Restore to factory settings"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Feline Monstrosity on 2010-01-25
Hi there.
I own a Samsung N130 netbook and I dual boot Windows XP with Ubuntu Netbook Remix. When I boot up my computer it loads GRUB which gives me the option to boot either operating system.
Now I want to do a complete reset of my system to factory settings (I will reinstall Ubuntu afterwards) and to do so I press F4 when I boot up to enter Samsung Recovery Mode. However when I do so instead of entering recovery mode it just goes to GRUB as normal. How do I get around this?

---

### Post by blazemore on 2010-01-26
Did you accidentally your recovery partition?

---

### Post by hungry_joe on 2010-01-28
I'm a friend of Feline Monstrosity and feel like I should probably add the following details to this story as I'm suspicious he isn't going to.

After a bit of trying he found he was able to get into recovery mode using grub (as opposed to F4 on the BIOS screen).
He managed to run the system restore, and this erased his Ubuntu partition, filling the hard drive with what was essentially a fresh Windows install.
However the machine still tried to boot to grub, couldn't find it as, and got stuck in a loop, repetitively trying to load  grub and failing. he asked around and between his "tech savvy" friends he got two suggestions, do a fresh Linux install and write off the option of using Windows, or use a Windows cd to reset the computers boot record.
At this point he'd started to blame Linux for stopping his system restore from working properly and opted for the Windows option.

Basically The Linux "community" has lost a member here, albeit a slightly impatient one. I can't help but wonder why the system restore made changes to the hard drive, without changing the Master Boot Record to match, but as far as I can see that's an issue for Samsung as opposed to the Ubuntu community.

Anyway, hopefully something here will have been useful to someone, or at the least will have saved them from trying to answer the problem.

---

