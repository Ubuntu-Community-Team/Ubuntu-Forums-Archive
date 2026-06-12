---
title: "a few questions"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by RJ12 on 2009-07-27
I want to go for a dual boot selection for Ubuntu 9.04 and Windows XP Pro. I already have Win XP Pro. Has anyone had troubles doing this. I kinda like KDE will I be able to use it with Ubuntu at certain times and certain times GNOME without installing Kubuntu. I wont be installing anymore windows oses anymore and wondering is it safe will it destory windows and how will I go about it I know I have to shrink Windows Partition but will I need to make a Swap partition which I have no clue what is for if any1 knows a tutorial on youtube or something with step by step instructions for Dualboot Windows Xp and Ubuntu 9.04 (if it is different doing it in 9.04) I would really enjoy becuase I hate Windows and want to break off the chain

---

### Post by llamabr on 2009-07-27
Hi.  Yes, you can do dual boot, and yes, you can use kde.

Tip: have a more informative subject line to get better replies.

---

### Post by Zenze on 2009-07-27
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Yes it is safe. Just shrink the size of your XP partition to make room for ubuntu. I have done it many times, never had anything get messed up. As far as using KDE, yes you can just installing with the package manager and choose which gui to use at login. The command should be something like:
```
sudo apt-get install kubuntu-desktop
```

And as far as a swap partition. This is a special partition of your drive that the OS can use to store temp files and things if for whatever reason RAM is limited. It is the same as the windows pagefile.

---

### Post by iNaitvad on 2009-07-27
Hi,
You should shrink your Windows Partition, the best program (in windows) for doing that is Acronis Disk Director (google it..taringa..), then with the Unallocated space make a new Extended Partition (Logical), on the new partition make 2 partitions:
1.- Ubuntu "/" (root)
2.- Linux Swap (i suposse the same amount of your RAM, ex.: you have 2gb of RAM SWAP=2gb)

Then reboot your computer with UBUNTU LIVE CD in, start installing, set your partitioning to MANUAL, i always use this option, then tell the installer that the new partition (the one you created for ubuntu "/" in a extended partition) will be used as /, this means it will be used as root, also select your Filesystem, I suggest Ext4, or Ext3, depending on your version.
Then tell the installer wich partition you will use for SWAP, the one of 2GB.

Start installing, after it finishes install kubuntu at Terminal, or synaptic, whatever you want...

I hope this helps, also you can check the pages above (other users answered you..)

---

