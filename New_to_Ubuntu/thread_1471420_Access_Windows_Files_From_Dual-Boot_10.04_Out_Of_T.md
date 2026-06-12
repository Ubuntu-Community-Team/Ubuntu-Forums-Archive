---
title: "Access Windows Files From Dual-Boot 10.04 Out Of The Box?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by CheshireMac on 2010-05-03
Hey folks. I'm writing this in the beginners forum because I think it might be an issue that a lot of new folks are concerning themselves with when they transition from Windows to Linux.
I'm about to do a fresh install of 10.04 and I have a lot of files on my install of XP that I can't back-up due to storage restraints. 
My understanding is that I'm able to access the NTFS partition and transfer the files over, but the walkthroughs I've seen have done me no good in my test run. What I'm going to do either tonight or tomorrow is to do a fresh install of 10.04 and I'm hoping there's an "out-of-the-box" method of accessing those files so I can wipe XP off the drive and work from there. 
If anyone has any ideas, I'd be happy to hear them.

---

### Post by Arla on 2010-05-03
Not sure what walkthroughs you have looked at, but I can happily access all my NTFS drives directly from 10.04 (and 9.10) without having had to install anything special.

---

### Post by Troublegum on 2010-05-03
> **CheshireMac said:**
> What I'm going to do either tonight or tomorrow is to do a fresh install of 10.04 and I'm hoping there's an "out-of-the-box" method of accessing those files so I can wipe XP off the drive and work from there. 
If anyone has any ideas, I'd be happy to hear them.

During the installation, if you manage your partitions and mount points, you can select the ntfs partitions that you want to mount automatically. 
Not sure about the automated partitioning, but I could imagine that all partitions will get mounted automatically. If not, you can always mount them after the installation with one click on the partition in the file manager.

---

### Post by sylvainrb on 2010-05-03
By fresh install I hope you mean dual-boot at first...

But after finishing the dual boot install, open nautilus and you'll see your windows partition listed on the sidebar (no need to do anything else but click on it and get your files!).

Also you might want to defragment the windows partition once or twice before proceeding with the install...

---

### Post by CheshireMac on 2010-05-03
Yes, I do mean dual-boot. 
So, in saying what's been said, my side-by-side installs will technically not limit my hard-disk space at all? I intend to use Windows for iTunes only, but if I keep it the way it is, and use Ubuntu for the rest of the drive space, Ubuntu can use the NTFS partition for storage also, and it in turn can share the files in the Windows install, yes? Sounds like all I need to do is install.

---

### Post by Troublegum on 2010-05-03
Yes, you can do that. 
I use a ntfs partition for sharing data between Windows 7 and Ubuntu. I created symlinks from ~/Documents, ~/Pictures, etc... to the Windows 7 equivalents (C:\Users\...\Documents, C:\Users\...\Pictures), so that I have full access to my documents regardless what operating system is running.

---

