---
title: "Live CD wont boot"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by kkremer212 on 2011-03-27
I am currently running 10.10 on an old Dell 8300 machine.  I had no issues booting from the CD once inside of Windows OS (XP or 7), but the disk will not boot from start up on any machine.  I have tried to go through the lists of suggestions offered on the forums, but have not had any success.  I am very new to the world of Linux, but not to computers.

What I am trying to accomplish:

I currently have installed 10.10 on my machine.  I want to access the live CD to get to the partition editor.  I then will install XP to dual boot.

Suggestions?

---

### Post by Enigmapond on 2011-03-27
Is your BIOS set to boot from a removable disk?

---

### Post by Rex Bouwense on 2011-03-27
Is this the same disk that you installed Ubuntu with?

---

### Post by kkremer212 on 2011-03-27
My computer boots from CD/DVD without issue on other disks.  BIOS is set to boot from CD first.

I have tried the same CD I used to install, and also a newly burned CD.  Same issues.  

Can't I just launch it from inside the installed program?  Open the drive and select a specific file to boot to the scree like I did with Windows?  There does not seem to be a file that will do this on either disk.

---

### Post by jramshu on 2011-03-27
How about System>Administration>Disk Utility, you can partition the drive from there.

---

### Post by kkremer212 on 2011-03-29
Found the disk utility, but it does not give the option to resize.  I have: Unmount, check, edit partition, format, edit file system and delete.  None of these will allow me to resize.  I tried looking at the format drive because it says to partition, but it wants me to re-format first.  I don't want to do that.

I still need to access my disk on a later step after I install XP to fix the boot loader on the Ubuntu partition.

---

### Post by pricetech on 2011-03-29
Try your windows disk to see if it boots.  You may have a buggy ODD.  If the disk works elsewhere then it should be a good disk.

---

### Post by kkremer212 on 2011-03-30
All other media will boot fine.  It is just the copies of ubuntu 10.10 that I downloaded.  The info is there, I can open in XP or 7 on same and other machines and access the home screens, just cannot get it to boot from startup.

When I installed I was going from XP to Ubuntu.  I opened the disk from My Computer and away I went.  I did have to follow the additional steps for "help boot from disk" to get it to work.  

If someone else knows of a good way to dual boot my machine with Ubuntu and XP I am up for it.  I just seem to have issues when I go XP first and Ubuntu second.  I have tried a couple of methods on the Ubuntu site for doing this process.  I was trying a third that someone suggested, but the Live CD boot issue is standing in my way.

Thank you for any suggestions!

---

### Post by Rex Bouwense on 2011-03-30
A quick search of the forums has yielded this [http://ubuntuforums.org/showthread.php?t=1631079](http://ubuntuforums.org/showthread.php?t=1631079).  See if it can help you.  Enjoy.

---

### Post by pricetech on 2011-03-31
You installed wubi then.

Have you tried booting the CD you made anywhere else ???

---

### Post by kkremer212 on 2011-04-05
> A quick search of the forums has yielded this [http://ubuntuforums.org/showthread.php?t=1631079](http://ubuntuforums.org/showthread.php?t=1631079).  See if it can help you.  Enjoy.

This was the first manner I tried.  I actually gave it three goes, and every time I entered XP, it would never boot again.  I could boot into ubuntu, and then into XP, but could not go on from there.  Got grub error> after I rebooted each time.

---

### Post by kkremer212 on 2011-04-05
> Have you tried booting the CD you made anywhere else ???

Yep - same issue, cannot get it to boot on own, but from a Windows machine I have can go into the file system and boot from there.  I cannot figure out the file in the ubuntu structure to select to launch it.  In windows it is an application file .exe.

---

