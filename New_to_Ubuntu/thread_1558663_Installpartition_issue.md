---
title: "Install/partition issue"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by a.v.l on 2010-08-22
I've just installed Ubuntu 10.04 over Vista and Ubuntu 8.04 and specified that the whole 250 GB hard drive should be used. The installation went fine and on restarting I noticed that Grub lists Ubuntu 8.04 as one of options, (it shouldn't be there) I cannot see Ubuntu 10.04 listed in Grub either, but it does load automatically within a few seconds.

Thinking I had made an error when installing 10.04 I attempted to re-install it again. This time when I got to the partition page I took a photo which I've included here. I've also posted a photo of the Grub at start-up. 

My question is why is Ubuntu 8.04 still shown in Grub when I specified that the whole hard drive be used and why isn't Ubuntu 10.04 listed in Grub.  My other question is does the photo of the partition convey that I have used the whole 250 GB hard drive installing 10.04. Your help would be appreciated.

---

### Post by TeoBigusGeekus on 2010-08-22
Should you have chosen 
"Erase and use the entire disk"
instead of
"Install them side by side..." ?

---

### Post by a.v.l on 2010-08-22
> **TeoBigusGeekus said:**
> Should you have chosen 
"Erase and use the entire disk"
instead of
"Install them side by side..." ?

Thanks for your post. Yes I did choose to erase the entire disk during the initial 10.04 install. The photo of the partition was taken when I decided to try another install of 10.04. When I saw the second partition I stopped the second install and posted my question.

It seems to me that I have already used the whole 250 GB for 10.04 and yet Grub suggests otherwise...

---

### Post by skatinjj on 2010-08-22
> **a.v.l said:**
> Thanks for your post. Yes I did choose to erase the entire disk during the initial 10.04 install. The photo of the partition was taken when I decided to try another install of 10.04. When I saw the second partition I stopped the second install and posted my question.

It seems to me that I have already used the whole 250 GB for 10.04 and yet Grub suggests otherwise...

The picture of the partition screen does show nothing but 10.04 LTS, but something is still on the hard drive to suggest otherwise which can happen if the format isn't done enough/properly.

Since the whole drive is being used anyway, just use the manufacturer's tool for your hard drive to wipe it completely or possibly GParted from the live cd.

---

### Post by -kg- on 2010-08-22
It does look like 10.04 is the only partitions on the hard drive.  Before you wipe everything, did you try pulling up a terminal and using the command:

```
sudo update-grub
```
?

I don't know how the installer caught the 8.04 installation when it didn't exist, but the command above might save you a whole bunch of work in wiping the entire drive and reinstalling everything.  If not, then nothing is hurt and you can just go ahead with "Plan A".

---

### Post by a.v.l on 2010-08-23
Thanks for the advice everyone. I've just discovered written on the case of my laptop that it has two x 250 GB hard drives which might explain my situation. My problem now is how do I get to the other hard drive to format it. Gparted just shows the one 250 GB drive?...............

---

### Post by TeoBigusGeekus on 2010-08-23
Install ubuntu on the first drive (sda) by using the entire drive option and then force your pc to boot from this drive by changing the bios settings.

---

### Post by a.v.l on 2010-08-23
> **TeoBigusGeekus said:**
> Install ubuntu on the first drive (sda) by using the entire drive option and then force your pc to boot from this drive by changing the bios settings.

Thanks again. Please allow me to update my situation. 

Initially I had Vista, Ubuntu 8.04 and Ubuntu 10.04 on this laptop. I reinstalled Ubuntu 10.04 and chose to use the whole hard drive to install over the other operating systems. 

When the new 10.04 OS had completed its installation, Grub gave me the option of choosing the **new** or the **old **version of Ubuntu 10.04...... or my old version of Ubuntu 8.04. Selecting either of these options opened the operating systems fully. The older version of 10.04 had the programs I'd previously added. Ubuntu 8.04 opened and had the programs I'd previously installed too. So my new installation had not written over the old OS's as I understand.

Having taken another look at gparted, I can select both hard drives sda and sdb I think I have my new version of 10.04 on sda and perhaps the first version of 10.04 and 8.04 are on sdb but I'm unsure. If this is so, how can I remove the fist installaion of 10.04 and 8.04 from this drive and use this drive for extra storage space for my new installation of 10.04?

I've added two photos of both hard drives in gparted in the hope that it will help.

---

### Post by QLee on 2010-08-23
[QUOTE=a.v.l]...
Having taken another look at gparted, I can select both hard drives sda and sdb I think I have my new version of 10.04 on sda and perhaps the first version of 10.04 and 8.04 are on sdb but I'm unsure. If this is so, how can I remove the fist installaion of 10.04 and 8.04 from this drive and use this drive for extra storage space for my new installation of 10.04?
...[/QUOTE]

Boot up through your working GRUB to the "new" install, write a file to that filesystem. Use whatever method you're familiar with to find that file and what partition it is on. That might help a bit.

From that new install that you have booted up if it is in fact on sda, delete the logical partitions in the extended partition on sdb and repartition the way you want it for your system. Don't forget that 4.62GiB ntfs partition sdb1, it still has 3GiB data of some kind on it.

That's what I would try after I was sure I had the correct partition for the OS I wanted to keep.

---

### Post by a.v.l on 2010-08-23
> **QLee said:**
> Boot up through your working GRUB to the "new" install, write a file to that filesystem. Use whatever method you're familiar with to find that file and what partition it is on. That might help a bit.

From that new install that you have booted up if it is in fact on sda, delete the logical partitions in the extended partition on sdb and repartition the way you want it for your system. Don't forget that 4.62GiB ntfs partition sdb1, it still has 3GiB data of some kind on it.

That's what I would try after I was sure I had the correct partition for the OS I wanted to keep.

Thanks you, it appears I am getting somewhere. Now I have partitioned sdb and now I have only Ubuntu 10.04 appear in Grub and 10.04 opens up normally.

I suspect that the re-partitioned disc sdb is not quiet right though. It appears in "Computer" but I'm unable to access it to add a file or image. If I try and drag and drop a file into this newly partition drive  I get the message shown in image 0943. If I open the partitioned drive and try and drag a fine into it I get the message shown in 0944. 

A few images of this problem are attached as well as the new partition created. Any help would be appreciated to make disc sdb accessible.

---

### Post by QLee on 2010-08-24
[QUOTE=a.v.l]...
I suspect that the re-partitioned disc sdb is not quiet right though. It appears in "Computer" but I'm unable to access it to add a file or image. If I try and drag and drop a file into this newly partition drive  I get the message shown in image 0943. If I open the partitioned drive and try and drag a fine into it I get the message shown in 0944. 
...[/QUOTE]

Did you format the new partition, I think I would have chosen to use ext4 since the install is of 10.04.

Something here may be useful for you:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by a.v.l on 2010-08-24
> **QLee said:**
> Did you format the new partition, I think I would have chosen to use ext4 since the install is of 10.04.

Something here may be useful for you:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks for coming back again. Last night I created a new partition on drive sdb the second hard drive and set the file system to NTFS. I'm unsure if this partition was formatted by gparted but can now access the second 250 GB hard drive and add files and photos there. Is there a way of testing this using the terminal? Photo included of the NTFS partition and sdb drive with files added.

---

### Post by QLee on 2010-08-24
[QUOTE=a.v.l]...Is there a way of testing this using the terminal? ...[/QUOTE]

What is it you want to "test". If the files are there in Nautilus they are there from the command line too. You've been successful achieving the goal, good for you!

---

### Post by a.v.l on 2010-08-24
> **QLee said:**
> What is it you want to "test". If the files are there in Nautilus they are there from the command line too. You've been successful achieving the goal, good for you!

Thank you so much for your help. I was unsure if I had done this correctly for two reasons. First gparted formatted the second drive in seconds which I didn't expect. Secondly, a YouTube video of an NTFS partition done in gparted shows the NTFS file system mount point as  NTFS  media/disk and mine shows NTFS media/49C8A3853AFA6AAD I'm unsure why there is a number after media instead of NTFS media/disk as appears in the YouTube photo attached. Anyway, I must thank you again for your help it has been very much appreciated.

---

### Post by QLee on 2010-08-24
[QUOTE=a.v.]...Secondly, a YouTube video of an NTFS partition done in gparted shows the NTFS file system mount point as  NTFS  media/disk and mine shows NTFS media/49C8A3853AFA6AAD I'm unsure why there is a number after media instead of NTFS media/disk as appears in the YouTube photo attached...[/QUOTE]

Mount points can be located where the system admin (in this case, you) wants them to be, your current one is shown where it automounts.

Read through those links I gave you previously and add the one about ntfs this time, since you chose to use an ntfs partition for your data. You will probably want it mounted at boot time (from fstab) in a location with read-write permissions, depending on how you choose to use it.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by a.v.l on 2010-08-24
> **QLee said:**
> Mount points can be located where the system admin (in this case, you) wants them to be, your current one is shown where it automounts.

Read through those links I gave you previously and add the one about ntfs this time, since you chose to use an ntfs partition for your data. You will probably want it mounted at boot time (from fstab) in a location with read-write permissions, depending on how you choose to use it.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Much appreciate you help,thanks again.

---

