---
title: "Formatting a Slave"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-05-09
Hello. I am using Damn Small Linux and I have two harddrives connected. I want to format my slave harddrive. What is the most quick and easy way to do what I am trying to?

---

### Post by Didius Falco on 2009-05-09
If you have Gparted installed, or on a Live CD, you can use that to wipe the partition(s) and make new ones.

If you do it while on your PC install, you have to unmount the drive before you can do it. From a Live CD, the drives shouldn't be mounted in the first place.

Regards,

Didius

---

### Post by -kg- on 2009-05-09
+1 Didius.

Are you using DSL from your hard drive?  If so, which one?  If you have it on the master drive (and you have no partitions in use on the slave drive), then it would be an easy enough matter to use GPartEd from your installation.  If you're not using any partitions off of the slave drive, then you will have nothing to unmount.  If so, unmount them (that will be about the only thing you can do otherwise).

Really, though, the easiest would be to use a [GPartEd Live CD.]("http://gparted.sourceforge.net/")  It's not a huge download (80-90 MB) and is specifically made for partitioning operations.

If you would like more information, see:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by Indian_Guy101 on 2009-05-11
Thank you. Also a quick question. How would I install either GNOME or KDE on Damn Small Linux. I am doing this for someone else and they are new to linux. The DSL GUI isn't too simple for people that are not computer savvy to even the slightest bit so I was thinking if I could install either gnome or KDE on the computer.

---

### Post by Didius Falco on 2009-05-12
I'm not sure you can. I do know it isn't supported by the DSL folks.

You might want to have a look at Puppy Linux. It's about twice the size, but it has a GUI built right in. It may be a better choice for a new linux user that is used to Windows. Have a look for yourself:

[http://www.puppylinux.org/](http://www.puppylinux.org/)

Regards,

Didius

---

