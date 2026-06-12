---
title: "Switching between partitions 7.10 and 9.04"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by LyonTamer on 2009-10-17
I know, it's weird. Here's what happened. This computer has the upgraded (not clean installed) Ubuntu 9.04. A cat did the tango on the power strip while computer was mid-task, and upon rebooting afterwards had Grub error 18. Every remedy I read about did not work, so my last idea before reinstalling from my 7.10 disk, which meant losing a lot of files and sitting through all those upgrades, was to install it as a partition, hoping to save the files (docs, pics, videos, music) on the 9.04. This was successful, but now I am unable to switch between Ubuntu 7.10 and Ubuntu 9.04. Looks like the problem that caused the error message before is still there. The computer doesn't give me a choice which one to boot as, it goes directly to 7.10.

How do I switch to the 9.04 partition? Or, how do I access the files on that partition from the 7.10? Or....How do I fix whatever the problem is in Grub that's making the error 18? The floppy disk thing didn't work.

Oh yeah...Dell Inspiron 8000 laptop pc.

---

### Post by Paqman on 2009-10-17
I'm not that familiar with Error 18, seems to be when BIOS and the partition size of the disk are incompatible.

Probably what's happened is that you've suffered some corruption of the filesystem that 9.04 was installed on.

Boot up into the LiveCD and run fsck on that partition, it might be able to repair it and get you a bootable system.

---

