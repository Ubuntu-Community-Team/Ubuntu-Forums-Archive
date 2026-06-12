---
title: "Using Gparted to resize a partition"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by newport_j on 2010-07-20
I am trying to use gparted to repartition and create a new partition in my drive the new partition is for Win Xp. I cannot repartition the main partition because it is mounted. What is the work around? How do I unmount the partition so I may resize it?
 
Newport_j
 
 
Also, I am using the gparted live cd. My laptop igmnores it when I boot up and just goes into Ubuntu 8.04 thta is on the hard disk. How do I use this disk - force my laptop to use this disk? The live cd gparted disk that is.

---

### Post by howefield on 2010-07-20
> **newport_j said:**
> What is the work around?

Use the Live CD 
 
> Also, I am using the gparted live cd. My laptop igmnores it when I boot up and just goes into Ubuntu 8.04 thta is on the hard disk.

Check your boot sequence settings in BIOS to ensure it looks at the CD before the hard disk.

---

### Post by amendt on 2010-07-20
When your computer first boots the screen flashes "press f12 to boot from another device" or "press delete to go into bios" Going into bios to change your boot device is the harder of the 2 options.

---

### Post by drs305 on 2010-07-20
Tips on using Gparted to resize an Ubuntu system partition:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")
The title mentions expanding / but the info relates to any partitioning operation on the / partition.

Look about half way down the post. The first part deals with a bug in Jaunty that was originally the reason for the post.

---

### Post by newport_j on 2010-07-21
Okay, i am booting from the Gparted Live CD. I get a screen that gives the options:
 
GParted Live (Default Settings)
Other Modes of GParted Live
Local operating system in hard drive (if available)
Memory Test using Memtest86+ 
 
I choose the first one or GParted Live (Default Settings) amd much text flashes across the screen
 
It asks a keymap question and I choose "dont't touch keymap" and then OK
 
Then its asks about language and I choose 33 or English
and it asks bout which mode 0, 1 or 2. I choose 
 
I choose ForceVideo (choice 1) and it asks about screen resolution. I take 2 1024 x 768. 
 
Then it asks about video drivers and I take the default vesa.
 
Then it asks about color depth and I choose 3 for 8. I want to keep it simple.
 
It then gives me a 
 
fatal server error no screens found
 
 
and it sends me to [http://wili.x.org](http://wili.x.org)
 
and var/log.Xorg.x.log
 
I just want to Gparted dialog sreen that gives me the choice of drives to select
 
 
[[IMG]http://gparted.sourceforge.net/screens/gparted_1_small.png[/IMG]]("http://gparted.sourceforge.net/screens/gparted_1_big.png")
 
Why can't I get it? Why this detour? I just need to boot from a drive that is mounted if I use Gparted on the hardrive. So I use the Gparted Live CD so no drives are mounted, but this is what I get. What is going on? I know Gparted works of my system because as I said I get the screen when I type 
 
sudo gparted and then a password
 
, I get the screen above, but the dive I want to change is mounted. I can do nothing to it.
 
I just need the screen.
 
 
Newport_j

---

### Post by eriktheblu on 2010-07-21
I've always just used the default settings on the Gparted live CD with no issues. It's probably just a settings issue.

If you have an Ubuntu live CD, you can use that instead.

---

### Post by drs305 on 2010-07-21
> **newport_j said:**
>  it asks bout which mode 0, 1 or 2. I choose 
 
I choose ForceVideo (choice 1) and it asks about screen resolution. I take 2 1024 x 768. 
 

Did you try Option 0? It is the least hassle and may take you right into the gparted gui.

---

### Post by akelsall on 2010-07-21
I'm not at my personal computer to look, but those menu options don't look like what I normally see (I'll verify tonight). Maybe try downloading a burning a different version of Ubuntu (LiveCD) and boot to it and see the menu options are different.

Andy

---

### Post by newport_j on 2010-07-21
Okay, the way I fixed that was to not take the default driver and to declare one in my case -ATI. It worked! I thought VESA would stand in for everything - wrong!
 
Now I have this unallocated space that has been formatted for NTFS. I want to install Windows XP on t. How do I do that?
 
I now have the following:
 
 
 
 
 
 
Partition File System Label Size Used Unused Flags
 
/dev/sda1 ext3 11.85GiB 9.27 GiB 2.58 GiB boot
 
/dev/sda3 ntfs Windows 42.60 GB 65.77 GiB 42.54 GiB
 
/dev/sda2 extended 1.44 GiB
 
/dev/sda5 linux-swap 1.44 GiB
 
 
 
 
Now I have a big partition for Windows 42.60 GiB. Thta is where I want to install Windows. I have the Windows disk, so how do I get it into that partition?
 
I am aware that I am blowing away GRUB. But I believe that is the last thing to do. So I will put that off until Windows is installed.
 
 
Newport_j

---

### Post by oldfred on 2010-07-21
If you set the boot flag on the NTFS partition, it should install just fine. It will not see the other partitions.

---

