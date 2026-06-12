---
title: "Can I save files on a bootable DVD?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by jkdbuck76 on 2011-08-17
I have an Ubuntu 11.04 DVD that I can boot from.
 
Is there a way I can save the changes I make to the DVD?
Can I save any files to the DVD?
 
Otherwise, I boot up the DVD, make changes, do my browsing, and when I shut down, all that I did was lost.
 
Any suggestions? Or should I be using a flash drive instead?

---

### Post by Enigmapond on 2011-08-17
Welcome to the forum. The answer is no. When you run Ubuntu right from a LiveCD is utilizes only RAM. When the machine shuts down, the RAM is cleared. Is there a reason you don't want to install it?

---

### Post by aeiah on 2011-08-17
> **jkdbuck76 said:**
> Or should I be using a flash drive instead?

no particularly 'instead', but you could save things to a flash drive whilst using the livecd. 

you could also use a usb stick intead of a cd/dvd to boot ubuntu from, but by default it is read-only, like the optical discs. its possible to create a 'persistent usb' install, whereby ubuntu is on the usb stick, and any changes you make are saved to it too.

really though, the best user experience is gained from installing it properly onto a hard drive

---

### Post by jkdbuck76 on 2011-08-17
> **Enigmapond said:**
> Welcome to the forum. The answer is no. When you run Ubuntu right from a LiveCD is utilizes only RAM. When the machine shuts down, the RAM is cleared. Is there a reason you don't want to install it?
 
The PC I'm talking about is the one I use at work.
 
I installed it yesterday using WUBI and my hard drive was about 38% fragmented.
That is bad, isn't it?
 
And thanks for the help, folks.

---

### Post by aeiah on 2011-08-17
if you installed it, you dont need the dvd. you could save things to a blank dvd, if you didnt want to save things to your hard drive...

---

### Post by jkdbuck76 on 2011-08-17
> **aeiah said:**
> if you installed it, you dont need the dvd. you could save things to a blank dvd, if you didnt want to save things to your hard drive...
 
 
OK.
 
I just kinda freaked out when I saw how fragmented my hard drive became upon installation of the WUBI.
 
I'm scared to partition the drive.
 
Anything I can do to keep the drive being all fragmented?

---

### Post by dolphin194 on 2011-08-17
You could remove the ubuntu from the NTFS partition and use Gparted to resize the drive. Just make sure you make a backup of the drive before you do it, because sometimes Gparted fails and it screws your disk up.

---

### Post by jkdbuck76 on 2011-08-17
> **dolphin194 said:**
> You could remove the ubuntu from the NTFS partition and use Gparted to resize the drive. Just make sure you make a backup of the drive before you do it, because sometimes Gparted fails and it screws your disk up.

Once I partition the drive, will it always be partitioned?  Or can I undo it and just run XP (since this is a work machine)?

Or am I better off putting a Virtual Machine on this XP and running Ubuntu on it?

---

### Post by Mark Phelps on 2011-08-17
Partitioning is permanent. Once made, the changes remain.

If you're worried about "restoring" your Work PC to its original state, a good way to prepare for that is the following:
1) Download and install Macrium Reflect free edition
2) Use the option to create a Linux Boot CD
3) Plug in an external drive and image off the entire drive to it.  Use the MR option to image ALL the partitions.
4) Unplug the external drive

NOW, if you ever need to restore the machine to its current (non-Linux) state, you do the following:
1) Hook up the external drive containing the PC backup
2) Boot from the MR Linux Boot CD
3) Select a Restore operation
4) Locate the restore you saved on the external drive
5) Let the restore run to completion.

This will overwrite the ENTIRE drive, including the MBR.  So, when you're done, the PC will be exactly like it was just before you made the backup.

Also -- policies vary by work location -- but you should check to see what they are at YOUR place before you make any changes to the PC.  After all, a Work PC is the company's property, not yours.  You wouldn't want to risk your job just to experiment with a Linux distro.

---

### Post by Kixtosh on 2011-08-17
Another option is to use Puppy Linux, if your computer has a built in CD or DVD drive. It's not as "complete" or as "grown up" as Ubuntu, but it leaves the existing installation alone. It's also incredibly simple to try without harming anything. There's no need for GRUB, or any other bootloader. Upon startup, if the Puppy CD is:

A) IN the CD/DVD drive upon boot = Puppy Linux boots.
B) NOT in the CD/DVD drive upon boot = Windows boots.

Puppy is slower than Ubuntu to start up, but still only takes about one minute on any machine I've ever tried. Perhaps a little less than that, perhaps a little more, but not much either way. It can be faster to run than Ubuntu once started, however. It's a bit trickier to change things, and you'll probably want to add stuff like a different browser (Chromium or Firefox) or a full office productivity suite, but it's a very easy option to use without screwing anything up, and you can access Ubuntu software sources for what you need.

Puppy runs entirely in RAM, so your Windows work machine will remain exactly as it was before. Bluetooth was the one thing I couldn't get to work (I have a bluetooth mouse for my laptops).

To make Puppy faster, you do need to store a couple of very small files on your hard drive. These can be seen by Windows (and erased, if need be), but not opened by Windows. They basically store the settings you create when you first install Puppy (and if you modify them thereafter), and any documents you want to save, in a compressed form. Just look for files with a ".sfs" extension. You will be asked if you want to create these files when you first shut down Puppy. If you don't like it, they are optional, but you can't store things for future sessions without a saved file.

I still recommend defragmenting your Windows drive at least three times before using it (because of the stored files). You can also use a USB drive for Puppy, or just the Puppy files, if you don't like the idea of storing stuff on your hard drive, but that does require a bit more fiddling than the totally simplistic CD in or out method.

Puppy is, in my opinion, by far the easiest way to try Linux on a machine that you do not want to modify (because it's not yours, in particular).

If the hardware is older (probably more than five years old), Wary Puppy may be a better option.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

