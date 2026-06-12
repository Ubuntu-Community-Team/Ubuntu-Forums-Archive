---
title: "Problem in mounting partition."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by John Rupert on 2010-05-01
I have just installed ubuntu 10.04 today.  And I tried to open the partitions I have in my PC.  And I opened the partitions (Places->Computer->Windows),  The first time I was able to do it.  Then I installed some packages like VLC through 'Ubuntu Software Center'.  After a some time I found every thing was successfully installed.   But the application was showing as it is being installed.  And I couldn't anything in my PC.  As I felt the computer is not working, I preferred to give a hard restart.  
    After the restart I tried to open the partition again.  But this time I couldn't.  Because I can't find the partitions inside Computer.  (Places->Computer).    Can any one help me in this matter?

---

### Post by oldfred on 2010-05-01
Welcome to the forums.

Ubuntu will not open partitions that windows has set the chkdsk flag. Your hard shutdown may have set that even though you were in Ubuntu. 

You should use your windows cd and run chkdsk on the partition:

In windows run "chkdsk /f". Although you can also use "ntfsfix" in Ubuntu:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY x- drive y - partition

sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".
-

---

### Post by srs5694 on 2010-05-01
> **oldfred said:**
> Ubuntu will not open partitions that windows has set the chkdsk flag. Your hard shutdown may have set that even though you were in Ubuntu.

This is mostly correct, but just a bit off: Most modern filesystems have an "in use" flag, which is set whenever the filesystem is mounted and then unset whenever an OS unmounts the filesystem. If the system crashes before the filesystem is unmounted, the "in use" flag will remain set, which serves as an indicator that the volume was not cleanly unmounted, and that it may therefore be in an inconsistent state. There's no need to set a "check" flag at the time of a crash; it's set when the filesystem is mounted. Both Linux and Windows set this flag when they access an NTFS volume. Linux, quite rightly, refuses to access an NTFS volume if its "in use" flag is set at the time the system tries to mount the filesystem, since Linux doesn't have a complete filesystem check utility for NTFS. (Linux can mount Linux-native filesystems after an unclean shutdown because fsck and its filesystem-specific helpers can be used to clean up a Linux-native filesystem prior to mounting them when the system boots.) Linux does have a very minimal NTFS check utility (ntfsfix), but it just does some very basic sanity checks and then sets the "in use" flag so that Windows will do a more complete check when it next boots.

Ultimately, oldfred's solution is correct: Boot the computer to Windows. Windows should automatically check the disk when it sees that its "in use" flag is set. If it doesn't manually running CHKDSK in Windows should do the job. When you reboot, the partition should again be accessible in Linux.

---

### Post by John Rupert on 2010-05-02
Thanks Oldfred,srs5694.

    ntfsfix didn't work out.  I have deleted all the contents in the windows.  Because I don't want to use windows anymore. Is there any other solution to fix this problem?

---

### Post by oldfred on 2010-05-02
If you have deleted windows what problem do you still have? I thought it was mounting the windows partition that needed filechecks.

---

