---
title: "No windows after Ubuntu 10 Install"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Trophy on 2010-06-03
I think i know what the problem, is but i don't kow how to fix it.

I have three hard drives. I have/had windows XP on the first 250Gb  with a second 250gb as a slave.

I had Ubuntu 9 installed on my 500Gb hard drive.

When i turned the pc on i had a boot menu that allowed me choose ubuntu or windows.

I got the new ubuntu 10 and did a clean install on the 500Gb hard rive .. thereby removing all ubuntu 9 files.

Whe i restart it boot straight into Ubuntu 10, no menu.

If i put the first 250Gb hard drive as first boot device, i get a Grub error 15.

As much as i dislike the windows i need it for my phone contacts and backup. 

Please any help would be appreciated.

---

### Post by pk_m on 2010-06-03
When going for clean install, always install windows first and then ubuntu.

---

### Post by Trophy on 2010-06-03
I didn't want to clear the windows install. i only wanted to replace ubuntu 9 with ubuntu 10 .. and then when i turn the pc on i get the option to boot to my normal windows i have always had... or to ubuntu 10

---

### Post by JohnL2009 on 2010-06-03
I've had the same problem, and have not been able to get it resolved.  Windows first on one drive,installed first, then linux on 2nd.  Basically I have given up, windows 7 and linux do not pay nice with one another anymore.  Will wait until these problems are resolved.  At least I have one machine devoted to linux.

---

### Post by Dangger on 2010-06-03
Have you tried to fix the master boot record with the Windows CD? This  will get rid of grub and will allow you to log straight into Windows.  You will need to repair gub after that, though.

---

### Post by halitech on 2010-06-03
was all 3 drives connected when you installed Ubuntu again? Can you boot into Ubuntu and run
```
sudo fdisk -l
```
then post the results here

also, download the script here and run it and post the info

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by tad1073 on 2010-06-03
> **pk_m said:**
> When going for clean install, always install windows first and then ubuntu.

OP said that windows was already installed.

> **JohnL2009 said:**
> I've had the same problem, and have not been able to get it resolved.  Windows first on one drive,installed first, then linux on 2nd.  Basically I have given up, windows 7 and linux do not pay nice with one another anymore.  Will wait until these problems are resolved.  At least I have one machine devoted to linux.

Been running W7 since Christmas & Ubuntu for a couple of years and have had no problem with Ubuntu and W7 booting.

> **Trophy said:**
> I think i know what the problem, is but i don't kow how to fix it.

I have three hard drives. I have/had windows XP on the first 250Gb  with a second 250gb as a slave.

I had Ubuntu 9 installed on my 500Gb hard drive.

When i turned the pc on i had a boot menu that allowed me choose ubuntu or windows.

I got the new ubuntu 10 and did a clean install on the 500Gb hard rive .. thereby removing all ubuntu 9 files.

Whe i restart it boot straight into Ubuntu 10, no menu.

If i put the first 250Gb hard drive as first boot device, i get a Grub error 15.

As much as i dislike the windows i need it for my phone contacts and backup. 

Please any help would be appreciated.

have you tried:
```
sudo update-grub
```

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Mark Phelps on 2010-06-03
There are an increasing number of posts from folks who have accidentally installed GRUB 2 on ALL of their drives/partitions.  This might be what happened to you.

For future reference, the safest thing to do when having a mixture of physical drives, some with Linux distros, other with MS Windows OSs, is to disconnect the MS Windows drives whenever you do an install or upgrade.  It's easy enough later, booting into Ubuntu, to run "sudo update-grub" to automatically add the boot stanzas for the MS Windows OSs.

My guess is that you overwrite the MS Windows MBR with GRUB2.  You'll need to rewrite the MS Windows MBR on the appropriate drive.  You can do that by booting from the XP CD.

---

### Post by julio_cortez on 2010-06-03
> **JohnL2009 said:**
> windows 7 and linux do not pay nice with one another anymore.
I'm not sure it's the presence of W7 and Linux causing problem.
I installed W7 then Kubuntu 9.10 and everything was fine at the first attempt.
Then I decided to update Kubuntu from 9.10 to 10.04 doing a fresh install and everything was still flawless. Grub recognized my W7 install perfectly and now I'm happily dual-booting.

Your mileage may vary, of course.

Phelps and tad1073 are right I guess, have you tried to do a fixmbr with the XP CD and then start a "recovery" session and update GRUB?

---

### Post by Trophy on 2010-06-03
TAD1073 that worked .. thanx. Grub updated and the boot options include windows.

Now to fix what i did trying to get it working my self ... windows boot cd here i come ... 

Thanx again guys

---

