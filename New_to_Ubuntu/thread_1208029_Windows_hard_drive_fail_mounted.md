---
title: "Windows hard drive fail mounted"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by flylehe on 2009-07-08
Hi,
I have both Windows XP and Ubuntu 8.10 on my laptop. My XP abnormally turned itself off when I open some website with heavy videos. Then I switched to start Ubuntu, and found my Windows D drive failed to be mounted. 

Back at the time when I installed Ubuntu, my Windows C and D drives were specified to be mounted automatically as "/windows-c" and "/windows-d". 

What can I do now to mount my D under Ubuntu? This is not the first time I have such problem. Last time I start in Windows and let it finish its checking its hard drive, then switch back to Ubuntu and problem solved. Now I wonder if I can solve the problem without rebooting into Windows?

BTW my C is fat32 and my D is ntfs.

Thanks and regards!

---

### Post by mattbutsko on 2009-07-08
Since Windows didn't unmount correctly it may still be "stuck in the on position". If it is, ubuntu can't mount it.

Try starting windows and as soon as it's finished starting, properly shutting it down via Start>Shut Down. Wait for it to fully shutoff, then start ubuntu and try mounting it.

This can also happen if you hold the power button in for four seconds to turn off the computer.

Hope this helps.

---

### Post by oldfred on 2009-07-09
You can mount it manually with a force option. 
sudo *mount* -t *ntfs*-3g /dev/[DEVICENAME] [LOCATIONOFMOUNT] -o *force*
This could cause problems so use at you own risk. This is meant more to extract data if you cannot get into Windows. I have used it once or twice and it did not cause corruption but I only read a few files before I rebooted Windows and got a normal shutdown.
You probably should mount read only also to prevent compounding the potential problems caused by the abnormal shutdown of windows. As previously commented Windows should be normally shut down.
The newest version of the ntfs-3g drivers has a recover mode that may solve some of these types of problems.
[http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

---

