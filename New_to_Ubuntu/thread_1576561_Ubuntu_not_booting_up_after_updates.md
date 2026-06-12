---
title: "Ubuntu not booting up after updates"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by daoster on 2010-09-17
Hey all, 

I'm a newbie at Ubuntu and Linux in general.  I've just recently installed it on my Fujitsu laptop after being frustrated with Vista (kept Vista though, so it was a dualboot installation).  For a short awhile, I was enjoying it, but after updating Ubuntu from the update manager and restarting my laptop, I got a black and purple screen.  Okay...I turn off my laptop and reboot it again, and now I get this error: 

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg

I found a suggestion in another topic to try to fix the problem by booting up Ubuntu through the CD, but when I tried that, it was stuck at the Ubuntu logo for 30 min+ 

Can anybody help me?

---

### Post by Clever_Username on 2010-09-17
Please don't follow my suggestion until a more experienced person chimes in. But just to get the ball rolling on this thing, I would think a sudo update-grub issues from the live cd might help.

---

### Post by daoster on 2010-09-17
the Live CD is the CD used to install Ubuntu originally right?  

I've tried running the CD, but it's always stuck on the Ubuntu logo.

---

### Post by coffeecat on 2010-09-17
> **daoster said:**
> Hey all, 

I'm a newbie at Ubuntu and Linux in general.  I've just recently installed it on my Fujitsu laptop after being frustrated with Vista (kept Vista though, so it was a dualboot installation).  For a short awhile, I was enjoying it, but after updating Ubuntu from the update manager and restarting my laptop, I got a black and purple screen.  Okay...I turn off my laptop and reboot it again, and now I get this error: 

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg

I found a suggestion in another topic to try to fix the problem by booting up Ubuntu through the CD, but when I tried that, it was stuck at the Ubuntu logo for 30 min+ 

Can anybody help me?

Let's take one thing at a time.

The live CD that is now sticking at the Ubuntu logo - was that the one you used to install Ubuntu originally? If it worked before and doesn't now, that suggests a problem with the CD.

Can you still boot into Vista? Is Vista running OK? The reason I ask is that many things could cause the symptoms you describe, a new hardware problem being one. If Vista is OK, then a new hardware problem is less likely.

If Vista is OK, and the Ubuntu CD did originally work, I suggest you burn a new CD from your downloaded ISO. At least as a start. What was the suggestion you found in another thread?

---

### Post by daoster on 2010-09-17
> **coffeecat said:**
> Let's take one thing at a time.

The live CD that is now sticking at the Ubuntu logo - was that the one you used to install Ubuntu originally? If it worked before and doesn't now, that suggests a problem with the CD.

Can you still boot into Vista? Is Vista running OK? The reason I ask is that many things could cause the symptoms you describe, a new hardware problem being one. If Vista is OK, then a new hardware problem is less likely.

If Vista is OK, and the Ubuntu CD did originally work, I suggest you burn a new CD from your downloaded ISO. At least as a start. What was the suggestion you found in another thread?

-  Yes, the live CD that is now sticking at the Ubuntu logo was the one I originally installed Ubuntu in.  I just installed Ubuntu Wednesday night, and placed my CD away safely...the CD couldn't have degraded so quickly, could it? 

-  I forgot to mention (sorry), that Vista wasn't booting properly before I installed Ubuntu.  It kept on booting into Recovery mode.  However, Ubuntu was still working while Vista couldn't boot.  It wasn't until after updating Ubuntu this morning that the problem occured.

-  The suggestion I found on the other topic was basically to boot up using the liveCD and entering: 
sudo fdisk -l

Thanks!

---

### Post by coffeecat on 2010-09-18
> **daoster said:**
> -  Yes, the live CD that is now sticking at the Ubuntu logo was the one I originally installed Ubuntu in.  I just installed Ubuntu Wednesday night, and placed my CD away safely...the CD couldn't have degraded so quickly, could it? 

Yes, that does seem odd. But it could be just a smear or bit of dirt on the CD, so try cleaning it (gently). Nevertheless, it would be worth burning another CD if you have access to a working system. If that fails to boot that might indicate a problem with the optical drive.

> **daoster said:**
>  -  I forgot to mention (sorry), that Vista wasn't booting properly before I installed Ubuntu.  It kept on booting into Recovery mode.  However, Ubuntu was still working while Vista couldn't boot.  It wasn't until after updating Ubuntu this morning that the problem occured.

Have you managed to recover Vista?

> **daoster said:**
>  -  The suggestion I found on the other topic was basically to boot up using the liveCD and entering: 
sudo fdisk -l

That command won't fix anything, but it will show your partition layout which would be useful.

---

### Post by daoster on 2010-09-18
> **coffeecat said:**
> Yes, that does seem odd. But it could be just a smear or bit of dirt on the CD, so try cleaning it (gently). Nevertheless, it would be worth burning another CD if you have access to a working system. If that fails to boot that might indicate a problem with the optical drive.

Have you managed to recover Vista?

Okay, so I've cleaned the CD and it's still getting stuck at the Ubuntu logo.  Tried the CD on a different computer, and I was able to boot it up normally and easily.  

I've also managed to recover Vista using the recovery disk that came with my laptop, and recover Vista, so I'm able go into Vista now (Ubuntu seems to have disappeared completely from the startup though, and my HD seems to be smaller).  I'm also able to view the contents of the Live CD through Vista.

I've also tried to use a USB to boot the thing, but this is opening another can of worms...

---

### Post by coffeecat on 2010-09-18
Very odd that the live CD used to work on this machine, now doesn't but does work on another. Except for a hardware problem with the optical drive I don't know what to suggest.

> **daoster said:**
> and my HD seems to be smaller

Presumably when you view it in Vista. How exactly? It may be that the Linux partitions (or the partition table) have got messed up - which might explain the errors in your first post - and that is making Vista think that the HD is smaller than it is.

It would be really useful to see the output of 'sudo fdisk -l' but without being able to boot a CD, that's difficult, unless...

> **daoster said:**
>  I've also tried to use a USB to boot the thing, but this is opening another can of worms...

Using a bootable USB flash drive with Ubuntu is the next logical step. What was the can of worms?

---

### Post by daoster on 2010-09-18
Well, now at least I know the CD wasn't at fault!

I was able to boot via USB, but the same thing happens:  It's stuck on the Ubuntu logo (the dots on the bottom are still moving too).  It's been stuck like that for the past 45+ minutes and I've just shut it down. :(

---

### Post by coffeecat on 2010-09-18
> **daoster said:**
> I was able to boot via USB, but the same thing happens:  It's stuck on the Ubuntu logo (the dots on the bottom are still moving too).  It's been stuck like that for the past 45+ minutes and I've just shut it down. :(

At least there's a pattern. The USB is behaving the same way as the CD. Which is odd considering the CD used to work. The only time I've seen something like this on one of my machines was when I upgraded the BIOS. The new BIOS was clearly incompatible with Linux and every distro I tried got stuck in the bootup process. Fortunately, I was able to reflash the BIOS back to the older version. You haven't upgraded the BIOS, by any chance?

Whether you have or not, we need to try some boot options. Have a look here:

[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)

First, with either the CD or the USB, press F6 and then ESC at the initial menu and remove 'quiet splash' from the boot options. Then boot. Instead of the pretty dots, you get scrolling text messages. When it gets stuck, make a note of the last three or four or so lines. There may be an error message there which gives us a clue. I should have thought to suggest this before - apologies.

If there's no error message, the only thing to do is to add boot options blindly. See kernel options in that link. A favourite to try is acpi=off.

But let's hope there's a useful error message in the boot text.

---

### Post by daoster on 2010-09-18
Okay, so this is the "error message" that seems to appear (running via CD):

```
deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
Repeat this process for the rest of the CDs in your set
W: Skipping nonexistent file /cdrom/dists/lucid/main/binary-i386/Packages
W: Skipping nonexistent file /cdrom/dists/lucid/restricted/binary-i386/Packages
```


Here's the error message I get trying to boot via USB: 

```
/init: line 7: can't open dev/sr0: no medium found
/init: line 7: can't open dev/sr0: no medium found
unable to open '/dev/sda'
stdin: error 0
```

---

### Post by coffeecat on 2010-09-18
Found a couple of things for you. Someone with the same error message:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9840872](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9840872)

But nothing to fix it except a suggestion to try 9.10.

Also, this 10.04 bug seems to be what you're getting:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279)

It's interesting that both your CD errors and USB errors appear in that Launchpad thread. It might be worth reading through that to see if there's anything that might help. I'm afraid this is a hardware specific bug. You are unlucky to have the hardware that reveals it. 

If there's nothing in there that helps (uninstalling Plymouth isn't going to help while you can't get the CD booting), I suggest you try Ubuntu 9.10. It's a good release and supported for another year. Here's a link for 9.10:

[http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

If you're feeling really adventurous, you might try the upcoming Ubuntu 10.10, at least from a live CD. With luck it might be free of that bug. Here's the link for the Beta:

[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

Be warned that if it runs OK on your machine from the CD and you're tempted to install it, it's still a bit rough round the edges in places. Also there will be hundreds of MB of updates to install and up to 100 per day until it goes final early next month. Normally I wouldn't point a beginner at a development release, but yours is a special case. Until they fix that bug and release a new CD image, 10.04 seems to be a no-no on your machine.

---

### Post by Strategist01 on 2010-09-18
I don't know if this may help, but are you trying to run a 32-bit OS on a 64 bit system? I know it *shouldn't* cause issues, but I don't know...

---

### Post by daoster on 2010-09-18
First of all, I want to thank you for helping me so much so far.  

@Strategist01, nope, my laptop is a 32 bit system, and i used the 32 bit OS. 

@Coffeecat:  So I decided to try running Ubuntu 10.10 from the CD, and whoa la...it is so far, working okay!  In fact, I've been able to find the partition that Ubuntu 10.04 was installed on (this partition did NOT show up in Windows Vista). The problem is, I can't even access this partition, because everytime I click on it, an error appears:  

```
Unable to Mount Location:
dbus error org.gtk.private.remotevolumemonitor.failed an operation is already pending
```

I'm wondering if I should just format both Vista and the partition and just install Ubuntu 10.10?  

(Sorry, I realize this problem seems pretty far removed my the original problem I had asked!)

---

### Post by coffeecat on 2010-09-19
Vista won't see the Linux partition because it doesn't recognise Linux filesystems. Actually, it will see the partition if you go deep within Control Panel to [Disk Management]("http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/"). Even then it will call it a valid partition (iirc) but won't recognise it for what it is simply because it doesn't understand  Linux filesystems.

When you got that error message, had you simply booted into the 10.10 disc and gone to the Places menu? If so, that might be a bug in 10.10 - it is still in Beta. That will be resolved (hopefully) before final but doesn't help if you need to access the 10.04 partition. If you did something else then try that.

Yes, you could install 10.10 to the whole disk and simply wipe out both Vista and 10.04, if that's what you want. Make sure you have a way of restoring Vista if you need it. And see whether there is a hidden restore partition first. The Ubuntu installer will merrily wipe that too if you choose the whole disc install option. And bear in mind the caveats I made regarding potential problems with 10.10.

If you can't access the 10.04 partition and need to copy off any files, try downloading the 9.10 ISO and using that.

Lastly, if you want to install 10.10 using the 10.04 partitions, retaining Vista, you can choose the 'manual' option at the partitioning stage. You simply designate the old 10.04 root partition as '/' (shorthand for root), mark it for reformatting and proceed. (If you had a separate /home before you need to mark that for /home too, but not mark it for reformatting.) The installer will pick up the existing swap partition automatically. I can't give you any more precise details because the design of the installer has changed (I believe) since I installed the alpha version.

If you need any more help with that last bit, boot up the 10.10 (or 9.10) disc and post the terminal output of:

```
sudo fdisk -l
```Good luck and let us know how you get on.

---

### Post by daoster on 2010-09-19
Well...I don't know what happened, but apparently all is fine now... 

Basically, I booted up Ubunto 9.10 and formatted the drive that 10.04.1 was originally on...then I was able to boot up the 10.04 Live CD again (hooray), and reinstall Ubuntu (this time, wiping everything else on the drive, Vista and all).  

Just used the update manager on Ubuntu, and restarted the computer, and all seems fine now.. 

And let's hope it stays that way. 

Thanks for your help guys.

---

