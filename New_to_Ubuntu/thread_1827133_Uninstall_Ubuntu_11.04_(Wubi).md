---
title: "Uninstall Ubuntu 11.04 (Wubi)?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by beneathnylon on 2011-08-17
Hello

I borked my Ubuntu 11.04 trying to get Compiz-fusion to work.  I installed Ubuntu using Wubi installer via Windows7 on a x64 machine.  Wubi made the system dual boot.

I mainly want to uninstall Ubuntu 11.04 and install a lower version of Ubuntu (ie 10.04).

Is their a guide or tutorial here that a newbie can follow?

Thanks

---

### Post by lmarmisa on 2011-08-17
You can uninstall Ubuntu with Wubi like any other program of Windows7.

This video can help you:

[http://www.youtube.com/watch?v=iW1V6TuZZmc](http://www.youtube.com/watch?v=iW1V6TuZZmc)

---

### Post by beneathnylon on 2011-08-17
Thanks,

I had no idea it would be that simple.  I was expecting something more complicated.

Excellent Job Ubuntu!

---

### Post by kip152 on 2011-08-19
Well, no.
I installed the same thing the same way, but I can't access Windows anymore. It's still there, because partition manager shows it. But I don't have an option on start up of using Windows. It goes straight to the ubuntu login screen.
I can't get rid of ubuntu, and I can't access Windows.
I would really appreciate any help so I can get rid of ubuntu. I'd have to pay about as much as I paid for this computer to get recovery disks, so I'm basically screwed.

---

### Post by Frogs Hair on 2011-08-19
See this tread . [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by kip152 on 2011-08-19
Okay, I didn't use Wubi, I downloaded Ubuntu 11.04 onto a disk and used that. So I don't have the program to get rid of Ubuntu because I used a disk. I guess I'm outta luck.

---

### Post by Frogs Hair on 2011-08-19
So you have a traditional dual boot with Ubuntu on its own partition ? If so grub can be repaired so you can access Windows . There are many threads about this problem and I would suggest a forum and Google search because the problem has been resolved for many users.

---

### Post by kip152 on 2011-08-19
I've been at this for 16 hours straight. I searched grub stuff earlier, and tried a few things before I found this thread. Everything seems to be aimed at fixing problems to go from Windows to ubuntu, not the other way around.

---

### Post by Basher101 on 2011-08-19
how about you login to ubuntu, open a terminal and type ```
sudo update-grub
```maybe your windows was not fetched by grub...try that, reboot and see if it sloved your problem

---

### Post by kip152 on 2011-08-19
Yep. Tried that a while ago, got the error message, Can't remember exactly what it was, but I remember trying that one a couple of times. Some other commenters said sometimes it works, sometimes it doesn't.
As of this moment, I deleted ubuntu partition manager, but I know I have to do something else to get it to boot up right. I'm running on the CD now.

---

### Post by yaddoshi on 2011-08-19
If your system came with a Windows 7 install disk you may be able to boot into recovery mode and repair your Windows 7 installation (if you don't have a Windows 7 disk but you have a friend who is running Windows 7 you can [make a System Repair Disk]("http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html") on their system).  Based on your description it sounds to me like grub overwrote your master boot record (MBR) on your hard drive, [here's how to fix that]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html"). Bear in mind doing this will remove your ability to access your LINUX partition.

Alternatively, since you were planning on switching to an earlier version of Ubuntu, you could just make yourself a new install disk and boot from that disk to install Ubuntu, which should also restore access to your Windows system when grub is rewritten.

Good luck!

---

### Post by kip152 on 2011-08-19
Newer computers no longer have those disks, they have it set up so that information is already in the system, all you have to do is hit F11. But because I can't access Windows, that doesn't work either.

---

### Post by Mark Phelps on 2011-08-19
If you have another working Windows PC, Google for and download the latest Hiren's Boot CD.  It has utilities on it that will allow you to repair the MBR on your old PC and from there, you will be able to get into SAFE mode to repair the actual Windows 7 boot loader.

---

