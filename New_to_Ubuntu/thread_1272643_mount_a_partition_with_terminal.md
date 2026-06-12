---
title: "mount a partition with terminal?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by james_newbie on 2009-09-22
I'm unable to mount a partition using terminal. I've tried mount /dev/(sda5) and (hda5) and (data) which is the label of the ntfs partition. No trouble doing it from the GUI but I get a message that the partition is not listed in a couple of files when I try to mount it using terminal.

I have a single hard drive. Windows is on a primary partition and the data partition and linux partitions are on an extended partition. The ntfs data partition is on sda5.

What is the mount blah blah blah command to give me access to it?

---

### Post by jrev on 2009-09-22
If you start windows or Linux the system will mount the necessary partitions. So why would you start mounting other partitions ?

Have a look at [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

---

### Post by amauk on 2009-09-22
you need to specify 2 things
what device you want to mount
and where you want it mounted

mount device mountpoint
```
mount /dev/sda5 /media/my_partition
```

---

### Post by james_newbie on 2009-09-23
Thanks amauk, I was missing the "where." Got it working now.

jrev: Ubuntu is not automatically mounting the partition that I want to access via the terminal--that partition does not show up with ls unless it is mounted. I think that I have to add a line to the fstab file to do this. Thanks for the link, it was very helpful.

---

### Post by HarrisonNapper on 2009-09-23
Yeah, I would just add the line to fstab if it's a storage partition.

---

