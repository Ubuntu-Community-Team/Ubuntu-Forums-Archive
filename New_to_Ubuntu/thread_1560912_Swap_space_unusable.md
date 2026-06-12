---
title: "Swap space unusable"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by d5xtgr on 2010-08-25
The swap space partition on my hard disk (~500MB) has recently started showing up as 'unknown' while retaining the swap space file system, and various options in the disk utility are now grayed out.
In what I suspect is a related incident, the machine now waits on a blank screen for close to 20 seconds while booting.
How can I restore my swap space and prevent this delay from occurring?

---

### Post by Muscovy on 2010-08-25
Does the partition manager (GParted) recognize the swap space as being swap?

Also, I don't think the splash screen issue is related. Ubuntu switched to a new splash system this release, and on some graphics cards the splash doesn't display itself. How long is your total boot time?

---

### Post by leprkhn on 2010-08-25
Sadly, I can't help you with the swap issue. However, the following links should help with the boot splash problem:

[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

And if you're CLI shy:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by sikander3786 on 2010-08-25
As Muscovy mentioned, Ubuntu splash is not being displayed on all the PCs, instead it is a blank screen with blinking cursor. So no problem there I believe.

How much RAM do you have in your PC. I have 2GB and still have never seen my swap space being used. Have you tried turning off the swap off and then back on? Check the partition flags in gparted.

---

### Post by d5xtgr on 2010-08-25
Okay, I have not used Gparted before, only the disk utility.  In Gparted the swap space partition shows up as 'unknown' and 1 MB of space appears as 'unallocated' (which did not appear in the disk utility).  I don't know what this looks like under normal conditions.
More info after I reboot.

---

### Post by d5xtgr on 2010-08-25
Okay, the reboot took 37 seconds after I press enter to input my BIOS password until the desktop background appeared.  My GRUB waited for 3 seconds before defaulting to Ubuntu.  This machine has 2GB of RAM; I don't know how to tell if the swap space is actually in use.

---

### Post by wojox on 2010-08-25
You can check it with this command:

```
free
```

---

### Post by d5xtgr on 2010-08-25
Swap Space is the last line listed, with all values as zero.

---

### Post by wojox on 2010-08-25
> **d5xtgr said:**
> Swap Space is the last line listed, with all values as zero.

It's not on then. Try 

```
swapon -a
```

Have a read here [SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by d5xtgr on 2010-08-26
I get a result that says
```
swapon: cannot find the device for UUID=241faa0f-086a-48bf-9406-be99b946e7dd
```
When I run 'free' again, it still shows up as zero.

With regard to booting, the splash screen displays only for a second or two after a long period with a dark screen (there is no cursor blinking).

---

### Post by mcduck on 2010-08-26
> **d5xtgr said:**
> I get a result that says
```
swapon: cannot find the device for UUID=241faa0f-086a-48bf-9406-be99b946e7dd
```
When I run 'free' again, it still shows up as zero.

With regard to booting, the splash screen displays only for a second or two after a long period with a dark screen (there is no cursor blinking).

First format the partition into a proper swap partition, either by using gparted or with the "mkswap" command. Then run "blkid" to check the correct UUID for your new swap, and edit /etc/fstab accordingly to use that UUID. After that a reboot or "sudo swapon -a" should get the swap working. Confirm with "free -m" and you should see some swap space recognized on the last line.

What comes to partitions disappearing like that, you might want to use some SMART checking tool to check the disk.

---

### Post by d5xtgr on 2010-08-26
That worked brilliatly.  Thanks!

---

