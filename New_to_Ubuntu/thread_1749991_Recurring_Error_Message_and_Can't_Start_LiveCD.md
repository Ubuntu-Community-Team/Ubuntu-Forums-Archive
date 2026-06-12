---
title: "Recurring Error Message and Can't Start LiveCD"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by ironman462 on 2011-05-05
Hello everyone, I'm in dire need of your assistance. I keep getting an error message that I have seen others receive, but the method they use to fix it is impossible for me to try. Here's my situation...

I installed Ubuntu 10.04 onto my laptop a couple days ago and it was working properly. I played around with it, installing compiz and having fun with that and such. But when I restarted it, an error came up. Here's the error message:


[B]mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _
[/B]

I looked up how I might fix this, and people have suggested inserting the installation CD, and using the  *sudo fsck /dev/sda1 *method. However, when I try and put the disc in, the main menu asking what I would like to do comes up (Try Ubuntu, Install, etc.) and after I choose to try it, this error message comes up:


[B]BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem. squashfs[/B]


So with that option out of the way, I don't know what to do now. I tried it with my flashdrive also, but it get's stuck at the loading start up screen. Hopefully someone will be able to help me... I'm scared for my laptop.

Here are the specs of my laptop (Not so great of a laptop I know):

emachine E528
Intel Celeron 900
2 GB DDR3 Memory
Intel GMA 4500M

Thank you ahead of time for any help.

---

### Post by ironman462 on 2011-05-05
Does anyone know what's going on with my laptop? Sorry for the double post, I'm just outta ideas...

---

### Post by fabricator4 on 2011-05-05
> **ironman462 said:**
> Does anyone know what's going on with my laptop? Sorry for the double post, I'm just outta ideas...

If this is the LiveCD that you installed off, and it's not booting now, then it's possible that the CD is no longer readable. It's also possible that the hardware is failing in some way but we can't be sure.

At this point you need another boot disk to try.  I suggest [The Ultimate Boot CD]("http://www.ultimatebootcd.com/") as it also contains diagnostic software that you can run such as memtest86+

You'll need to download the iso and burn it to a CD on the computer you"re using at the moment, obviously.

Chris

---

### Post by ironman462 on 2011-05-08
At this point I have created a disc with Ubuntu 10.04, 11.04 and I even tried Fedora. None of them worked and came up with the same error message above. I also redid all of them on a flash drive with the same result. I'm outta ideas here...

---

### Post by diablo75 on 2011-05-08
Edited:  Just realized you're using a laptop which threw my theory out the window.

Although I did noticed in the error message the phrase "Input/Output error"

This type of stuff usually doesn't happen unless there's a hardware problem, like a hard drive failing to read a particular sector within the alloted timeout period.  You may have a hard drive that is failing.  As an experiment, see if you can load the Live CD with the HD removed from the laptop.

---

### Post by fabricator4 on 2011-05-09
> **ironman462 said:**
> At this point I have created a disc with Ubuntu 10.04, 11.04 and I even tried Fedora. None of them worked and came up with the same error message above. I also redid all of them on a flash drive with the same result. I'm outta ideas here...

At this point you still need to download "The Ultimate Boot CD" linked to in my post above and run the memory test on your machine.  If you're getting IO errors on squashfs one possible reason is a faulty memory module.  squashfs load into and runs out of the machine's memory.

If you're getting errors when trying to run off the LiveCD the problem is not likely to be the hard drive.  Nothing is done with the hard drives until after the CD is booted and you either try to mount the drives or install the OS to them.

How much memory and how many memory modules do you have in the machine?

Basically, we're suggesting you might have a hardware problem here...

Chris.

---

