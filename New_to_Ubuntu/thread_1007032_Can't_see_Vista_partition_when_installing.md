---
title: "Can't see Vista partition when installing"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by armilam on 2008-12-10
Hello! I just registered to ask my first question about Ubuntu.

I am trying to install Ubuntu 8.10 on a new partition on a machine that already has Vista installed. I used the Vista partitioner to create a new partition specifically for Ubuntu.

When I get to the partition section of the installation, however, I find that my options are 'Guided - Use Entire Disk' and 'Manual'. Manual doesn't show my current partitions and offers to start from scratch.

After much research and experimentation, I find myself in what appears to be the exact same situation as Ubunfu in this archived thread: [http://ubuntuforums.org/archive/index.php/t-984211.html]("http://ubuntuforums.org/archive/index.php/t-984211.html").

I do not have the skill to find out whether performing the 'sudo dd...' operation near the end of the thread would be smart for me. Would somebody be willing to take a look at my boot sector and let me know. Or, are there any other suggestions for fixing my situation? I have attached a file containing my boot sector.

Thank you.

---

### Post by iwallet on 2008-12-10
why dont you install it with WUBI??! it installs it "in" windows... by that i mean you insert the Ubuntu cd while running vista... and it should ask you "would you like to install ubuntu in windows" i think the max you can put is 30gigs... after you install simply restart and vista's boot loader will apear... and that when you select UBUNTU!! :D

---

### Post by armilam on 2008-12-10
That seems like a good idea, but I'd still like to find out why the Ubuntu installer won't recognize my partitions and fix the problem.

I will probably end up using Wubi, then migrating it to its own partition once I get my MBR figured out. Thanks!

---

### Post by caljohnsmith on 2008-12-10
Armilam, from your Live CD, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
I looked at the sda.MBR file that you attached in your first post, and it looks like your partition table is just fine; you only have two primary NTFS partitions right now that don't overlap according to that file, so the partition table should be OK. Did you by chance browse any files on your HDD before using the Intrepid installer? If so, that could be the reason you had problems with the installer not recognizing your partitions. I would try running the installer before you do anything else, and see if that helps.

---

### Post by armilam on 2008-12-10
This is what I got running the commands you suggested:

```
ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  23110-  23111- 185635840    7  HPFS/NTFS
/dev/sda2      23110+  38913-  15804- 126939136    7  HPFS/NTFS
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0       -       0          0    0  Empty
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x548ce754

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   371273727   185635840    7  HPFS/NTFS
/dev/sda2       371273728   625151999   126939136    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!                           
```

On my first try, I shrunk the partition using Vista and immediately tried installing Ubuntu. On my last try, I formatted the new partition with NTFS (it was my only option in the Vista disk manager) then tried installing Ubuntu. That's the state my HDD is currently in.

Also, I've discovered that my 320GB HDD is actually two 160GB HDDs in RAID 0, if that information is useful at all.

By the way, thank you for taking the time to help me out!

---

### Post by caljohnsmith on 2008-12-10
> **armilam said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total [COLOR="Red"]312581808[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x548ce754

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   371273727   185635840    7  HPFS/NTFS
/dev/sda2       371273728   [COLOR="Red"]625151999[/COLOR]   126939136    7  HPFS/NTFS

ubuntu@ubuntu:~$ sudo parted /dev/sda print
[COLOR="Red"]Error: Can't have a partition outside the disk! [/COLOR]                          
```

On my first try, I shrunk the partition using Vista and immediately tried installing Ubuntu. On my last try, I formatted the new partition with NTFS (it was my only option in the Vista disk manager) then tried installing Ubuntu. That's the state my HDD is currently in.

Also, I've discovered that my 320GB HDD is actually two 160GB HDDs in RAID 0, if that information is useful at all.

By the way, thank you for taking the time to help me out!
According to the results you posted above, your second partition ends on sector 625151999 which is almost twice the total sectors on the drive, or 312581808 sectors. But it looks like that is because you have your drives in a RAID setup. So if you want to install Ubuntu to your RAID setup, you could look at:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

But as you can see from the above link, it isn't trivial installing Ubuntu to a software-based/fake RAID setup like yours. If you don't mind taking your HDDs out of their RAID configuration, that would certainly simplify installing Ubuntu. If you did that, you would have to first fix sda drive's partition table, which wouldn't be too hard I think; I could help you with that if you want. But about installing Ubuntu to a RAID array, I can't be of much assistance with that as I have very limited experience with RAID. Let me know what you decide to do or if you would like any further help from me. :)

---

### Post by JoshuaRL on 2008-12-10
One thing to remember is that software RAID is extremely hard (and sometimes impossible) for other OSs to read.  So if you had software RAID in Windows, then Linux may not be able to read it.  Hardware RAID is different, since it uses a RAID card to connect the drives to and is pretty straightforward.  If you set up the two drives as being separate, then all OSs could get to them and you wouldn't have near as much problem.

---

### Post by armilam on 2008-12-10
Since I'm looking to use Ubuntu for experimental purposes only, I don't think it would be worth the trouble of dealing with the RAID setup. Because of that, I am going to use Wubi as iwallet suggested.

Thank you everyone for your help.

---

