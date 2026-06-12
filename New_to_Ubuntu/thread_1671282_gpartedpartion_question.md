---
title: "gparted/partion question"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by asf_73 on 2011-01-19
I've installed Ubuntu successfully but without partitioning my HD. My question is, can I successfully partion my drive without having to erase my drive, partition my drive than reinstall Ubuntu.  Thanks in advance

---

### Post by madjr on 2011-01-19
sure you can.

but one question, how did you install without partitioning?


you can follow these guides to partition:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

---

### Post by asf_73 on 2011-01-19
Thanks for the reply @madjr. I ran DBAN to completely wipe out my HD due to my 4yr old laptop being very laggy/slow. a bit on the extreme end but I felt it was necessary. Once I had settled on downloading Ubuntu I had totally forgotten to partition my drive. During the install, it asked me did I want to split my HD with another O/S or run Ubuntu alone. I wanted to see if I could partition the HD with Ubuntu but it seemed a bit out of my league, so I simply let it be.

---

### Post by 123456789123456789123456 on 2011-01-19
that is my question also, I did not think that was possible, I would assume you used the entire disk when you installed Ubuntu, if so you can use the partition manager to repartition the disk.

---

### Post by Quackers on 2011-01-19
Ubuntu probably created the partitions it needs, using the whole disc.
Please go to synaptic package manager and install gparted. Then System > Admin > gparted and run the program. After a few seconds it will scan your disc and report the partition structure. Please post a screenshot of that window.

---

### Post by asf_73 on 2011-01-19
Thanks @Quackers @123 for some strange reason I can't seem to attach my pic on here. The above icons aren't responding. Any way it shows:  /dev/sda1   (size)89.33 GB   (used)4.45GB   (unused)84.88GB  Boot /dev/sda2         3.83  GB /dev/sda5 (Linux-swap?)     3.83  GB

---

### Post by asf_73 on 2011-01-19
Would you recommend that I repartition the drive further? To better maximize drive utilization. I really don't feel the need to re-install MS (ugh) but I want to avoid any potential problems with bad file sectors due to un-partitioned space (if that makes sense).  Thanks fellas

---

### Post by Quackers on 2011-01-19
> **asf_73 said:**
> Thanks @Quackers @123 for some strange reason I can't seem to attach my pic on here. The above icons aren't responding. Any way it shows:  /dev/sda1   (size)89.33 GB   (used)4.45GB   (unused)84.88GB  Boot /dev/sda2         3.83  GB /dev/sda5 (Linux-swap?)     3.83  GB

Use New reply rather than quick reply and then click on "manage attachments", browse to your piccie and double-click it, click on "upload", when it's uploaded click on close window. Submit reply. Et voila! enclosed screenshot :-)

---

### Post by asf_73 on 2011-01-19
Let's see if this works @Quackers. Sorry for the crappy pic

---

### Post by asf_73 on 2011-01-19
Now I want to shrink the HD space from sda1 but when I hit create partition table, fire alarms and lightning came from everywhere informing me that I was about to erase the HD, which obviously I don't want to do.  Your recommendations sir

---

### Post by Quackers on 2011-01-19
The present partitions take up the whole disc, it seems.
If you want to resize sda1 you will first need to boot from the live cd/usb and choose "try ubuntu". When the desktop loads start gparted and then right-click on the swap partition and select "swapoff". Apply the change if required (green tick).
Then you should be able to right-click on sda1 and select resize/move. Then pick what size you want and then click on the green tick to apply the change.
If all goes well you should see some unallocated space when it's finished.
Right-click on your swap partition again and select "swapon". You're done :-)

---

### Post by asf_73 on 2011-01-19
Let's see if this is a better pic

---

### Post by asf_73 on 2011-01-19
@Quackers I had no idea I had a screen capture program that came with Ubuntu (applications/accessories/take a screen shot). Ubuntu for the win

---

### Post by asf_73 on 2011-01-19
@Quackers Still have no idea what that linux-swap (sda5) line is. Any ideas?

---

### Post by Quackers on 2011-01-19
Yes, it's a swap partition :-) It's like the paging file in Windows - like extra memory, but slower. With the amount of ram that computers have nowadays it's not needed much, but ubuntu will create one in an "old-style" default installation.
Did you see post #11 about what you need to do? It needs to be done from the live desktop, not your normal desktop.

---

### Post by asf_73 on 2011-01-19
Yes I did see post #11 and I'll let you know how everything turns out. Thanks for the help bruv.

---

### Post by Quackers on 2011-01-19
No problem :-)

---

### Post by madjr on 2011-01-20
> **asf_73 said:**
> @Quackers I had no idea I had a screen capture program that came with Ubuntu (applications/accessories/take a screen shot). Ubuntu for the win

yes, it comes with most things one would need, in fact one can even suggest new or missing things (and if the community is positive about it, then there's a very good chance of getting it), development is totally open :)

anyway, if you need any further help with the partitioning, then this little guide gives a quick overview:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

