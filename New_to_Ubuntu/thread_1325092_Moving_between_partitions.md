---
title: "Moving between partitions?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by stenella on 2009-11-13
Hi,
Is it possible to move Ubuntu, lock stock an barrel from one partition to another? I ask because, having dumped Windows, I'd like to move everything (apart from data, which is stored externally) to the 'quicker' end of the drive. I'd really like to avoid having to reinstall Vbox with the fun of getting my external drives going again... Or...if I back up the Vbox folder, does it have the USB info in it? If I opt for a total wipe and re-install?
Cheers,
stenella

---

### Post by Paqman on 2009-11-13
On modern drives you don't really get any performance boost by locating things on a particular part of the drive.

If you want to clone a partition [Clonezilla]("http://clonezilla.org/") is pretty good. You might need to set Grub up again to reflect the change in partition.

---

### Post by stenella on 2009-11-13
> **Paqman said:**
> On modern drives you don't really get any performance boost by locating things on a particular part of the drive.

If you want to clone a partition [Clonezilla]("http://clonezilla.org/") is pretty good. You might need to set Grub up again to reflect the change in partition.
Now that I didn't know! Guess I'll just use the space for storage...
Thanks,
S

---

### Post by ukripper on 2009-11-13
+1 for clonezilla. Check this nice easy step by step  tutorial here - [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by Neezer on 2009-11-13
I just recently deleted my vista partition, and left my Ubuntu on the same smaller partition (60 GB), but I reformatted the 300+ GB partition that windows was on and mounted it on /home. That way my home is on a separate partition.

Details are in this post.
[http://ubuntuforums.org/showthread.php?t=1322810&highlight=partition](http://ubuntuforums.org/showthread.php?t=1322810&highlight=partition)

So far I like it and am exploring the options that I now have because /home is a completely separate partition.

good luck with whatever you decide to do.

---

### Post by egalvan on 2009-11-13
To move a partition from one part of the disk to another, you can use gparted from a LiveCD.

If you only have one partition, this is easy, but time-consuming.

If you have more than one partition, it requites a little thought as to order of moves. Still time-consuming.

---

### Post by stenella on 2009-11-13
Thank you all for the input, I shall read the relevant threads/articles and let you know how I get on.
S

---

