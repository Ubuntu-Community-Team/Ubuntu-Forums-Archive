---
title: "Main drive not mounting on start up"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by HaveLotsToLearn on 2011-03-28
I've search the forums but can't find a solution to my particular problem.
FWIW, running Maverick on Dell Latitude D520.
Computer went to sleep and had to do a hard shut down. When I started the computer it said /root not found, etc.

When I boot from a LiveCD and try to mount the hard drive, it takes 15 minutes and returns: Unable to mount 77 GB filesystem. Dbus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.... 

I've run fdisk -l and know that the device name is /dev/sda1

When I run e2fsck -fyv /dev/sda1 I get:
  Device or resource busy while trying to open /dev/sda1
  Filesystem mounted or opened exclusively by another program?

When I run umount /dev/sda1 I get
   /dev/sda1 is not mounted (according to mtab)

I can't get testdisk (either from System>Administration>Synaptic Package Manager or apt-get update, then apt-get install testdisk

What should I try next??

Thanks for your help,
 JH

---

### Post by _0R10N on 2011-03-28
Since I can't think of a solution for your problem, I would recommend you to be practical and reinstall the OS, without formatting. That should solve that kind of problem, and get rid of any other not visible so far (since you cannot mount the partition correctly)

---

### Post by HaveLotsToLearn on 2011-03-28
And by not formatting, I'll still have all my files?

---

### Post by Dutch70 on 2011-03-28
Do you have a separate /home partition? If you do, then don't format /home and you shouldn't lose anything. That's the purpose of having /home.

Also, you should almost never have to do a hard shut down.

Did you try holding down (Alt+prt scrn) while hitting R-E-I-S-U-B one at a time with a short pause between each key? That will reboot your computer safely. 
That's "BUSIER" spelled backwards.

Edit: You can change the order to R-S-E-I-U-B. The reason for that is to make it easier to remember. In a sentence. **R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring.
Or Reboot System Even If Utterly Broken. :) 
What it does...
r &#8211; takes the control of the keyboard back from X.
s &#8211; writes the data from the disc cache to the hard disk.
e &#8211; sends SIGTERM to all processes except init.
i &#8211; sends SIGKILL to all processes except init
u &#8211; remounts all the filesystems readonly (basically a measure to help you reboot safely)
b &#8211; reboots the system

---

### Post by HaveLotsToLearn on 2011-03-28
Dutch,
 Those are two great things to know. I wish I had known them before.
  I do not have a separate /home partition.
 -JH

---

### Post by Dutch70 on 2011-03-28
If you have to reinstall, now would be a good time to create one.

You may be able to open Gparted, right click the partition & select check. That will attempt to check & repair the filesystem. 
I've never used it, but if you're going to reinstall, I would try that first.

---

### Post by HaveLotsToLearn on 2011-03-28
GParted gets stuck on the e2fsck -fyv /dev/sda1 command and gets the same error message I received (noted above).

Any other ideas?

---

### Post by Dutch70 on 2011-03-28
That's while running from the live cd/usb right? 

I must say I'm all out of ideas.

---

### Post by HaveLotsToLearn on 2011-03-28
Yep, using LiveCD. :(

---

### Post by HaveLotsToLearn on 2011-03-28
Is there anything I can do with fstab or mtab to force sda1 to mount?

---

### Post by Dutch70 on 2011-03-28
Well, lets have a look at fstab.

```
sudo gedit /etc/fstab
```

Paste the contents into your next post between code tags. Use the "#" symbol in the toolbar for code tags.

While your at it, why don't you post a screenshot of gparted, I'd just like to see your partitions. Please use the paper clip in the toolbar to post the pic.

---

### Post by HaveLotsToLearn on 2011-03-28
fstab says:

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

I can't take a screenshot of Gparted but here's what it says:
```
/dev/sda1    ext4    71.6GiB    24.16GiB used    47.44 GiB unused    boot (under flags)
/dev/sda2    extended    2.93GiB
* then, as nested part of sda2:*
  /dev/sda5    linux-swap    2.93GiB
```

---

### Post by HaveLotsToLearn on 2011-03-28
New Info

So, I booted up using Parted Magic.
I have no idea what I'm doing with it but I went into Partition Editor and it shows /sda1 as mounted at /media/sda1

Since that is now mounted, can I do a proper shutdown and restart?

---

### Post by HaveLotsToLearn on 2011-03-28
I was able to back up my data within PartedMagic onto my external hard drive.

Now I'd like to reinstall Ubuntu 10.10 to make sure everything is working correctly.  

What is the best way to partition the drive?
I have an 80GB hard drive. From the earlier posts, it sounds like I should have a root partition, home partition and swap partition. 
  A) Is that right?  
  B) How big should each of those be?  
  C) Should root and home be ext4 file systems? 
  D) What's the recommended mount points?

Then, once I do that, how do I tell it to stores files in the home partition?

p.s. I just put a sticker on my computer to NOT do a hard shutdown and to use <Alt + Prnt Scrn> R - S - E - I - U - B so that I hopefully never have to do this again.

---

### Post by Dutch70 on 2011-03-29
Yes, that's right.

1. Swap = same size as your physical RAM.
2. "/" aka "root" 10-20GB - mount point is /
3. /home = the remainder of your hdd. mount point is /home.

Format them to ext4 and ignore the recommendations of swap in this link. I'ts talking about people with very little RAM. 
[[COLOR="Blue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

This is current for swap size.
[[COLOR="Blue"]SwapFAQ[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

I included an example pic of an hdd with a /home partition.

---

### Post by HaveLotsToLearn on 2011-03-29
Thanks for your help Dutch.

---

### Post by Dutch70 on 2011-03-29
You're quite welcome. 

Hope everything goes well for you. :guitar:

---

