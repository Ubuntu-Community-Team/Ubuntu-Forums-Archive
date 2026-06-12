---
title: "Need to format unallocated into FAT32"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Reckers on 2009-03-11
I have no elaborate ubuntu knowledge, so when it comes to matters that require skill, I am hopeless. I now turn to this wise board once again.

I have a 200 gigabyte hard drive. 185 of it naturally available.
45 gb's partitioned for my vista os, 11 for ubuntu.  Leaving 129 for my music and other data, but that portion is reading as unallocated.

Vista will not let me partition it, apparently it is literally impossible through vista home premium.

I have no idea how to go about doing so in Ubuntu.  Anyone care to guide me?

Thank you very much.

---

### Post by Peter09 on 2009-03-11
Use an application called gparted - it is in the repositories. If the partion is not mounted ou can use it from your desktop. It will let you format and resize a partition.

---

### Post by Reckers on 2009-03-11
repositories?  I know, I'm oblivious.

---

### Post by Peter09 on 2009-03-11
Repositories are the areas on the internet where applications are. To get gparted you issue this command in a terminal.

```
sudo apt-get install gparted
```

the application apt-get will then go onto the internet to the correct repository and download and install gparted.

For a GUI - use

System->Administration->Synaptic Package Manager

This shows you all the available applications, gparted will be there somewhere, tick the box and apply.

---

### Post by Reckers on 2009-03-11
I installed Gparted. I believe I formatted the uanllocated space as FAT32.
Gparted told me that I cannot have more than four primary partitions, so I did away with my swap space.
But I cannot find the new partition. Gparted titles it as /dev/sda4 and says there is 130.53 GiB, but I'm not finding it.

Suggestions?

---

### Post by ivanvajar on 2009-03-11
Partition is not shown in Places/Removable media?

---

### Post by Reckers on 2009-03-11
Not under the places tab on the toolbar no.  Not sure how to dig deeper than that with accuracy.

---

### Post by ivanvajar on 2009-03-11
Did you reboot your computer?

---

### Post by ivanvajar on 2009-03-11
If your partition isn't there after reboot, open Terminal and type 

> sudo fdisk -l

nd post me output.

---

### Post by Reckers on 2009-03-11
Part of me was fearful of a reboot, not exactly sure why.
But apparently I was simply fearful of success.
Thank you one, thank you all.
Once again, the wisdom of the crowd solves the problem.

---

### Post by ivanvajar on 2009-03-11
Put some good stuff on your new partition! :-) Ubuntu!

---

