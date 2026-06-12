---
title: "Using a windows partition"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-03-03
I started with a Vista laptop with the HD split into two partitions: C: (VistaOS) and D: (Data).

I installed Ubuntu selecting the Dual Boot option and AFAICT it created another partition for itself.  In Ubuntu I have been able to see the Data partition, and use it in the normal way.  (I accessed it through the Places menu).  When I logged in a few minutes ago I could not find it any more.  I can't think that I can have accidentally deleted it, so how do I find it again?

The other question is:  When I created a link to the Documents folder in the Data partition, I saved it on to the desktop.  It worked fine until I shut down and restarted the computer and then the link was broken.  What's going on here?

Hoping that someone will come up with an answer or two.

Nick

---

### Post by sikander3786 on 2011-03-03
Please post the output of this command from your Terminal under Applications > Accessories sub-menu.

```
sudo fdisk -lu
```

And for the link, if it was linked to the something on the same partition that has disapperead, it obviously should have broken...

---

### Post by Churchwarden on 2011-03-03
> **sikander3786 said:**
> Please post the output of this command from your Terminal under Applications > Accessories sub-menu.

```
sudo fdisk -lu
```And for the link, if it was linked to the something on the same partition that has disapperead, it obviously should have broken...

Here is the code:

nicholas@nicholas-F3E:~$ 
nicholas@nicholas-F3E:~$ sudo fdisk -lu
[sudo] password for nicholas: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc46d4b87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   123794121    61896037    7  HPFS/NTFS
/dev/sda2       123795454   312578047    94391297    f  W95 Ext'd (LBA)
/dev/sda5       187551744   312578047    62513152    7  HPFS/NTFS
/dev/sda6       123795456   184834047    30519296   83  Linux
/dev/sda7       184836096   187543551     1353728   82  Linux swap / Solaris

Partition table entries are not in disk order
nicholas@nicholas-F3E:~$ ^C
nicholas@nicholas-F3E:~$ 

The target for the link was still there.  I hadn't moved or deleted it.

BTW How do I put sections of code in the correct little box?

Nick

---

### Post by Churchwarden on 2011-03-03
That's interesting.

I restarted so that I could go and check that the D: drive was still there in Vista. It was.  When I came back into Ubuntu, there it was!

What's going on?  We wonders, yes we wonders.

Nick

---

### Post by oldfred on 2011-03-03
You probably should be permanently mounting it. When you unmount it from the temporary mount it may not reappear.

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by JKyleOKC on 2011-03-03
> **Churchwarden said:**
> BTW How do I put sections of code in the correct little box?NickAt the top of the reply window you'll see two rows of icons. Toward the right end of the lower row is a "#" character. Highlight what you want to be inside the box, then click that icon -- and the rest is automatic.

If you're pasting something in from the clipboard, click the icon **FIRST;** it will leave the cursor between the two commands, and you can simply paste right there.

---

### Post by NCLI on 2011-03-03
Hey Nicholas,
Make sure to make the thread as solved. You do that in the "Thread tools" menu in the top right corner. :)

Kind Regards,
Nicholas.

---

### Post by Churchwarden on 2011-03-04
> **NCLI said:**
> Hey Nicholas,
Make sure to make the thread as solved. You do that in the "Thread tools" menu in the top right corner. :)

Kind Regards,
Nicholas.

Thanks for all the help.  There seems to be quite  a lot to follow up on and there is much other stuff that I need to get on with first.  I will mark this as solved to stop people responding for the time being.  I will post pack when I have used all the ideas.

All the best

Nick

---

