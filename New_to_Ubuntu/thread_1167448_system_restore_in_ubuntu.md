---
title: "system restore in ubuntu?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-05-22
is there a feature/function in ubuntu 8.04 to restore ur system after u messed something up by accident or something? 

is there something like it would just direct u to some steps and restore ur system the last time it was up and ok?

thanks! i just wanna avoid another fresh install just in case.

btw. i installed ubuntu via wubi installer

---

### Post by t0p on 2009-05-22
There isn't a system restore as such.  If you mess up your xorg config you can reboot into recovery mode and get it to restore graphic configuration to its default settings.

**EDIT:** I just noticed you said you installed with wubi.  I don't know anything about wubi so I don't know if my advice holds true for you.

---

### Post by asmoore82 on 2009-05-22
Clonezilla can take complete sparse images of all of your PC's drives: [http://clonezilla.org/](http://clonezilla.org/)

But it's still not true "System Restore" functionality ...

If you have a complete and proper backup of your $HOME folder including all of the hidden files,
a re-install is not nearly as painful as it may sound.

I know nothing of Wubi either :/

---

### Post by Terry of Astoria on 2009-05-22
I like to make an image of my system drive with partimage - It's really pretty easy to do. Takes a few minutes on a system that's new and can be restored in a few minutes, too. Much quicker than reinstalling, then doing all the setup stuff. 
   When I'm setting up a machine, I'll usually take a couple "snapshots" along the way, saving an image just after installing all my essential programs, say, and then again after Ive got it pretty well customized and have used it a bit to "break it in"
   Partimage is comparable to "Ghost" for Windows. I like it better though.
I hear that you can copy partitions with gparted too. Backing up an image of your drive is the most accurate way to back up your system, too. It's much better than "System Restore", which can not always "Restore" your system perfectly. An image made with partimage is perfectly exact, and your boot sector is saved by default, too, if you copy the first partition.
   To install partimage, just do:
```
sudo apt-get install partimage
```
then "sudo partimage" will start it. I often copy the Windows partition on to my Linux partition, but if you are going to copy your Linux partition, you will need to run partimage from the Live CD, or a bootable USB stick. And you will need a place to put the image (you can't save it on itself) so a USB booting stick with like 8 gigs of space should work . . . or another external drive could be used for storage .
   I recommend doing your research on partimage before using it, since it's very powerful. However it is a fast and easy way to back up your drive.

---

### Post by nhasian on 2009-05-22
i'd also like to chime in with my favorite backup tool Simple Backup

```
sudo apt-get install sbackup
```

---

