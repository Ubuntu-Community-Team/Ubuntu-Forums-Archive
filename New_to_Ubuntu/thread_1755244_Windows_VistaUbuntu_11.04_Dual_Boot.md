---
title: "Windows Vista/Ubuntu 11.04 Dual Boot"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by Jay08 on 2011-05-11
what i would like to do is have Vista and programs (Zune, AutoCad, Office, etc.) on one partition; Ubuntu on another; then one for all data (music, pics, etc.)

Would like to have swap at 1.5Gb

Was also seeing something about a separate /home partition. would this be where Applications are saved, or just personal settings. and is there  any gain from having it separate?
would look like this:
(Vista/Shared/Ubuntu/home/swap) is this correct, does it matter where they fall?

Also what should the partitions be formatted as? Ubuntu and /home should be ext4, and Vista should be ntsf i believe, but what format will both be able to read/write to?
HD is 250Gb but reads at 231, what should the sizes be on the vista and ubuntu partitions to allow for growth.

Im not as computer savvy as i would like to be, sry for what is probably a stupid question

---

### Post by wildmanne39 on 2011-05-11
> **Jay08 said:**
> what i would like to do is have Vista and programs (Zune, AutoCad, Office, etc.) on one partition; Ubuntu on another; then one for all data (music, pics, etc.)

Would like to have swap at 1.5Gb

Was also seeing something about a separate /home partition. would this be where Applications are saved, or just personal settings. and is there  any gain from having it separate?
would look like this:
(Vista/Shared/Ubuntu/home/swap) is this correct, does it matter where they fall?

Also what should the partitions be formatted as? Ubuntu and /home should be ext4, and Vista should be ntsf i believe, but what format will both be able to read/write to?
HD is 250Gb but reads at 231, what should the sizes be on the vista and ubuntu partitions to allow for growth.

Im not as computer savvy as i would like to be, sry for what is probably a stupid question

Hi,first if you install ubuntu 11.04 from live cd when it gets to the partition it will ask you if you want to divide the free space in half, half for vista and half for ubuntu. If you go this route ubuntu will set the partitions for you which is a lot easier for a new user,other wise you could end up wiping out windows altogether and not having an ubuntu bootable system either. Windows will not be able to see anything on your ubuntu system, but ubuntu can see your windows system. You can also import your documents, bookmarks and the like. I would allow ubuntu to have half your disk space. Also if you let ubuntu do your partitions it will create your swap the same size as the amount of ram you have in your system. Pay very close attention to what the screen says when you install ubuntu. Hope this helps.:P

---

### Post by Jay08 on 2011-05-11
So Ubuntu can read the NTFS filesystem? I think id rather just have a larger Windows partition and mount that as default in Ubuntu, is this possible. Like maybe 60Gb for Ubuntu, whatever for swap, then the rest for windows/data. Also, what benefits would I get from having a separate home partition aside from not losing settings on a fresh install of Ubuntu?
 
Thanks for the help

---

### Post by oldfred on 2011-05-11
I do not like to read & write from foreign systems. Windows can be picky. You should set your windows system partition as read only. In Ubuntu you can see and accidentally modify all the system files.

The shared NTFS partition is best. You can read & write from it without problem from both systems. Some windows users even suggest a separate data partition so when you have to reinstall windows your data is safe. (You still need good backups).

Smaller system partitions also help system performance slightly. Drive does not have to search entire drive for the files most often used.

The /home has both your (most hidden) user settings and your data. If you set up your system to have data in the shared NTFS partition /home does not have to be large or not even a separate partition. 

Your windows system partition has to be primary and you are limited ot 4 primary partitions. But Ubuntu works from logical partitions and windows will read a shared NTFS partition that is logical.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by pritam_par on 2011-08-01
You have asked many questions.

1) No need for 1.5 GB swap area , 500MB is enough.
2)/home partition will only contain the personal files and folder and won't let other user to see your files.
3)Ubuntu can read NTFS file format but Windows cannot read ext4 file format. It means you can access all your windows file from Ubuntu but you cannot access file stored in ext4 file format drive.
4)You can assign 15GB for Ubuntu and around 50GB for Vista that will be optimal.

---

### Post by amjjawad on 2011-08-01
Check the [2nd link]("http://ubuntuforums.org/showthread.php?p=10257675") in my signature.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

