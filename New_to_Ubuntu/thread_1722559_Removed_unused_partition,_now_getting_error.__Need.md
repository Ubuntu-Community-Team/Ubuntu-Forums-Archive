---
title: "Removed unused partition, now getting error.  Need advice."
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Skaggz on 2011-04-05
Hi there.

When I originally set up my Ubuntu 10.10 install I set up a logical partition and mounted /misc to it thinking I would use this as a "go between" partition between Ubuntu and Windows.  As time went on I never really used that partition and decided to remove it and allow my other partitions to grow to take over it's space.  I burned a GParted liveCD and everything went well.  No problems there.

However when I boot up now, I get the following error on a purple screen:
[CENTER][B]The disk drive for /misc is not ready yet or is not present
Continue to wait; or Press S to skip mounting or M for manual recovery[/B][/CENTER]


I've waited.......and nothing changes.  So, I've just been pressing S to skip it and continue booting into the OS.  Once I did try pressing M, and it took me to a root command line shell.  I had no idea what commands to enter so I exited out of it.

Now it's not a huge deal, just kind of annoying.  Could someone please help out a Linux newbie and give me some guidance?  Thanks in advance.

---

### Post by lindsay7 on 2011-04-05
Can you use the Gparted disk to get a screen shot of your drive and post it here?

---

### Post by rosencrantz on 2011-04-05
Can you post your /etc/fstab file here?
It handles the mounting of non-removable drives and my guess is that /misc is still listed.
So, if there is a line in there with /misc as the second entry, just delete this particular line (sudo gedit /etc/fstab) and you should be fine. Back up the original file first (sudo cp /etc/fstab /etc/fstab.backup) in case things go south.

Cheers, rosencrantz

---

### Post by Skaggz on 2011-04-05
[CENTER][IMG]http://i1199.photobucket.com/albums/aa478/Skaggz2/gparted-1.jpg[/IMG][/CENTER]

As you can see, I did leave a 25GB NTFS partition to act as a "go-between" between Windows and Ubuntu just in case I ever thought I might need it in the the future.  Even if I could mount sda7 as /misc just to get rid of the message that would satisfy me.  However I'd like get rid of the message without doing so.

---

### Post by Skaggz on 2011-04-05
This is what my fstab file reads:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9f677e2e-6782-4885-b8bc-8e64366d7497 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=91c890cd-81ca-40b4-9b0a-b7de2e12ec00 /home           ext3    defaults        0       2
# /misc was on /dev/sda7 during installation
UUID=0E03-19B3  /misc           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=0ca0ab10-ad38-49a0-818d-87630971ab1c none            swap    sw              0       0
```


So if I remove:
```
# /misc was on /dev/sda7 during installation
UUID=0E03-19B3  /misc           vfat    utf8,umask=007,gid=46 0       1
```
I should be golden?

---

### Post by Quackers on 2011-04-05
In your /etc/fstab file put a  #  sign and a space at the start of the line I've made red. That may be enough.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9f677e2e-6782-4885-b8bc-8e64366d7497 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=91c890cd-81ca-40b4-9b0a-b7de2e12ec00 /home           ext3    defaults        0       2
# /misc was on /dev/sda7 during installation
[COLOR="Red"]UUID=0E03-19B3  /misc           vfat    utf8,umask=007,gid=46 0       1[/COLOR]
# swap was on /dev/sda3 during installation
UUID=0ca0ab10-ad38-49a0-818d-87630971ab1c none            swap    sw              0       0
```

Don't forget to save the file though!

---

### Post by Skaggz on 2011-04-05
Excellent.  Thank you so much.  To all three of you.

---

### Post by rosencrantz on 2011-04-05
'#' means comment, btw. And yes, that should fix your problem.
Good luck!

---

### Post by Quackers on 2011-04-05
No problem :-) Sorry if I just jumped in there - I just woke up :-)
Are you ok for editing the /etc/fstab file?

---

### Post by Skaggz on 2011-04-05
> **Quackers said:**
> Are you ok for editing the /etc/fstab file?
Yeah, already done.  Just haven't rebooted yet to verify that it worked.  Thanks.

*edit*: Everything is all good now.  Thanks again!

---

### Post by lindsay7 on 2011-04-05
You beat me to it, I was just typing the instructions to comment out that line.

---

