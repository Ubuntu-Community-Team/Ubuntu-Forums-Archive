---
title: "Update Problem"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by feral1939 on 2010-01-31
I was given a copy of 9.04 which I installed side by side with Vista. The installation went OK until I tried to update to 9.10 plus the security updates but the update manager informed me that there was not enough free space on the hard disc and I needed to find another 1524M to allow the updates. I find this very strange as there is 34+ Gbfree space on my hard drive. I tried reinstalling the program but it made no difference and I would greatly appreciate some help to overcome this problem bearing in mind that I am not very computer literate. I also note that there is no way I can uninstall Ubuntu as it does not appear anywhere on my files.  Thanks in anticipation.

---

### Post by Rex Bouwense on 2010-01-31
> **feral1939 said:**
> I was given a copy of 9.04 which I installed side by side with Vista. The installation went OK until I tried to update to 9.10 plus the security updates but the update manager informed me that there was not enough free space on the hard disc and I needed to find another 1524M to allow the updates. I find this very strange as there is 34+ Gbfree space on my hard drive. I tried reinstalling the program but it made no difference and I would greatly appreciate some help to overcome this problem bearing in mind that I am not very computer literate. I also note that there is no way I can uninstall Ubuntu as it does not appear anywhere on my files.  Thanks in anticipation.

You may have 34+ Gigs free but how much free space do you have on the partition that you installed Ubuntu.  If I were to guess, there isn't much.  To check see partition editor under System>Administration.

---

### Post by feral1939 on 2010-01-31
Thanks for your quick reply. I installed 9.04 on the same partition as Windows.

---

### Post by Rex Bouwense on 2010-01-31
So you installed Ubuntu inside of Windows.  Can you still get into Ubuntu 9.04 or is it overwritten by 9.10?

---

### Post by feral1939 on 2010-01-31
I can't get into 9.10 at all as I cannot update from 9.04 to 9.10 because of space problem. When I installed 9.04, I chose the option to install side by side with Windows but that option did not give the opportunity to make a separate partition. I think that I really don't know what I am doing.

---

### Post by Rex Bouwense on 2010-01-31
OK, if you chose the option to install side by side, then there are separate partitions.  Did you use a live CD to install Ubuntu 9.04?  If you did slide it back into your CD drive and boot from it.  Choose the option to try Ubuntu without making changes to your computer.  Once it boots up click System>Administration>Partition Editor.  You will be able to see your partitions from there.
BTW can you still boot into Widows?

---

### Post by feral1939 on 2010-01-31
I used the live CD to install it. I slid the CD in and accessed the partition editor which showed 34Gb unused GiB boot (?) but is only one partition. I can still boot into Windows or Ubuntu from startup

---

### Post by Rex Bouwense on 2010-01-31
Now I am confused.  When you boot into 9.04, can you update?  We already know that you cannot upgrade.

---

### Post by feral1939 on 2010-01-31
I cannot neither update or upgrade because of the insufficient free space - different amounts of free space for the upgrade or update.

---

### Post by natravis on 2010-01-31
boot into Ubuntu and run

```
sudo fdisk -l
```

from the command line. You can accomplish this from either your installation or from the live cd (after mounting the hard drive).

Post the code using the tags so we can see what your partitions look like (size and free space, specifically).

If you installed side-by-side, it should have created separate partitions and you may just need to reduce the Windows partition some (best practice is from Windows) then increase the Ubuntu partition (best practice is from Live CD). Pending the output of that command, we will post appropriate instructions or links to instructions.

---

### Post by feral1939 on 2010-01-31
Thank you for your help. It looks as though the fault lies with the side by side installation as it did not create a separate partition for Ubuntu but put it in the windows partition thus I am unable to increase the size or reduce the size of either.         
BTW, the code sudo fdisk -1 was not accepted as the "-1" option was stated as invalid.

---

### Post by Ebonhawke on 2010-01-31
I believe it isn't a '1', but rather a lower-case L

---

### Post by feral1939 on 2010-01-31
Thanks, I tried it with an "ell" but it displayed one partition only so it looks as though the only option to overcome the problem is to clean install Vista again which I am very reluctant to do and then try to install Ubuntu again as there isn't any way I can uninstall Ubuntu as it is buried in the Windows partition.

---

### Post by natravis on 2010-02-01
> **feral1939 said:**
> Thanks, I tried it with an "ell" but it displayed one partition only so it looks as though the only option to overcome the problem is to clean install Vista again which I am very reluctant to do and then try to install Ubuntu again as there isn't any way I can uninstall Ubuntu as it is buried in the Windows partition.

So it was installed via Wubi. You should not need to do any re-installing of Windows. If you wish to do a true side-by-side install (highly recommended for performance), there are lots of guides on dual boot installs but the core is this, for you:
[LIST]
[*][Uninstall Wubi]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")
[*]Defrag Windows
[*]Reduce Windows partition size using Disk Management (Rt-click on My Computer -> Manage -> Storage -> Local -> Rt-click on HDD and Shrink Volume to desired size ([http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista))
[*]Install Ubuntu from CD (preferably latest version, 9.10) and select either manual partitioning or guided install next to windows. (I prefer manual for absolute control over the process and learning ... [https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning))
[*]...
[*]Profit (make sure you run all updates for both systems)
[/LIST]

See [http://help.ubuntu.com/community/WindowsDualBoot](http://help.ubuntu.com/community/WindowsDualBoot) for an very good list of options and how to implement them.

Let us know if this works for you.

---

