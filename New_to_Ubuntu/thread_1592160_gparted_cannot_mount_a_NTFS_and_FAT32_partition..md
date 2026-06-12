---
title: "gparted: cannot mount a NTFS and FAT32 partition."
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-10-10
Greetings,

I've got an Asus EEE PC 1001P dual-booting Win7 Professional and Xubuntu 10.10.  I installed GParted to work with the partitions on the laptop's hard drive, but whenever I open it up, it refuses to mount the primary NTFS partition and a FAT32 partition on an extended partition. I get an error saying that it is locked.  Is Windows doing this, and how do I work around this to at least access the FAT32 partition? I like to transfer files between my OSes, so having access to the partition would be nice.

Thanks!

--Red

---

### Post by amjjawad on 2010-10-10
> **Redmage913 said:**
>  I like to transfer files between my OSes, so having access to the partition would be nice.

Thanks!

--Red

Sorry, not sure what exactly to do with the first part so I don't want to make any guess :)

As for the last part of your question ... the best way is to create /data partition in Ubuntu and format it as FAT32.
In that case, both Windows and Ubuntu will be able to access that partition. In that case, you could easily transfer any data between them so easily. Just put the files that you want to access them using Win7 and Ubuntu in /data and that's all :)

---

### Post by coffeecat on 2010-10-10
@Redmage913, I think you're a bit muddled as to what Gparted is for. The probable reason Gparted is showing locks by the partition is that they are already mounted, not that it cannot mount them. Gparted is for manipulating partitions and for creating filesystems. It can copy whole partitions but it is not designed  for copying files. 

If you already have NTFS and FAt32 partitions on your machine, all you need do is to automount them from the Places menu and do simple drag and drop copies of whatever you want to copy.

Except if you have already mounted the partitions with /etc/fstab, then all you have to do is to navigate to the mountpoint using Nautilus and drag and drop anything you want to copy.

Perhaps if you tell us more of your setup and what you want to do, then someone can help.

---

### Post by amjjawad on 2010-10-10
> **coffeecat said:**
> Perhaps if you tell us more of your setup and what you want to do, then someone can help.

A screenshot for your partitions will be very helpful.

---

### Post by Redmage913 on 2010-10-10
Hey,

The reason why i attached this with gparted was because it was the only way I could figure out how to see the partitions in question. They do not list under the Places menu, and I do not get an unmount option in gparted.

I attached a screenshot of my netbook's hard drive layout in gparted.  It looks a mess, I know; much of that is that I haven't gotten rid of the Win7 restore partition and the mini Linux partition with the secondary power button (it's an Eee PC thing).

I do not have an "unmount" option with either of the large NTFS and FAT32 partitions, and I cannot mount them either.  The only way I can get any messages regarding the partitions is to open up gparted.

---

### Post by amjjawad on 2010-10-10
> **Redmage913 said:**
> Hey,

The reason why i attached this with gparted was because it was the only way I could figure out how to see the partitions in question. They do not list under the Places menu, and I do not get an unmount option in gparted.

I attached a screenshot of my netbook's hard drive layout in gparted.  It looks a mess, I know; much of that is that I haven't gotten rid of the Win7 restore partition and the mini Linux partition with the secondary power button (it's an Eee PC thing).

I do not have an "unmount" option with either of the large NTFS and FAT32 partitions, and I cannot mount them either.  The only way I can get any messages regarding the partitions is to open up gparted.

Not sure what coffeecat's opinion is but I think you could keep everything as it's.
sda1 is for Windows
sda2 is extended where all the logical partitions will be included/exist
sda5 is FAT32 and I'm not sure if you created it or it's already there.
sda6 is Ubuntu's root partition.
sda7 is Ubuntu's swap partition.

If you want to have a shared partition between Windows and Ubuntu, you could keep sda5 as it's. Both Ubuntu and Windows can access FAT32 partition (just like an USB Flash drive).

---

### Post by Redmage913 on 2010-10-10
Hey,

I'm not trying to change anything currently, I'm just trying to mount one or both within Xubuntu.  Do I need to give one of the partitions a /dos designation or something?

I have very little experience with the GNU/Linux OS. I can follow someone's directions, but I don't know what to do to progress forward

---

### Post by amjjawad on 2010-10-10
> **Redmage913 said:**
> Hey,

I'm not trying to change anything currently, I'm just trying to mount one or both within Xubuntu.  Do I need to give one of the partitions a /dos designation or something?

I have very little experience with the GNU/Linux OS. I can follow someone's directions, but I don't know what to do to progress forward

If you want to "mount" sda5 which is the FAT32 partition, then you need to do that from inside Xubuntu itself. Go to  places and choose that partition the it should be mounted and an icon will be available on your desktop.

Edit:
As coffeecat said, GParted has nothing to do with mounting. You could do it from Ubuntu or whatever version of Linux you have ;)

---

### Post by Redmage913 on 2010-10-10
Neither are listed under places. I have the home, trash, desktop, file system, and the default 5 folders under my home folder listed under places.

---

### Post by srs5694 on 2010-10-10
You could create an /etc/fstab entry, as in:

```

/dev/sda5  /mnt/fat  vfat  uid=1000  0  0

```

You'll need to create the /mnt/fat partition, or change that value to whatever is convenient. When you've added this entry, type "sudo mount -a" and it should appear at the mount point you specify.

If necessary, you can tweak the entry in various ways. Mostly likely you'd want to change the "uid=1000" value or add other entries. Type "man mount" and pay particular attention to the "Mount options for fat" and "Mount options for vfat" sections. The dmask and fmask options are particularly likely to be useful.

---

### Post by Michael Dooley on 2010-10-10
Your fat32 partition can't be seen in "Places" because it has a hidden flag. Change that in Gparted and you will be able to see it in both OS's.

---

### Post by Redmage913 on 2010-10-10
Okay, I edited the fstab file, but how do I add the /mnt/fat?

---

### Post by Redmage913 on 2010-10-10
Michael,

Wrong partition. I'm talking about sda5, not sda3.

---

### Post by coffeecat on 2010-10-10
Let's take one thing at a time.

> **Redmage913 said:**
> I'm just trying to mount one or both within Xubuntu.

You didn't mention Xubuntu before. As your personal profile was showing an albeit nearly unsupported version of Ubuntu, I assumed you were using gnome. When I mentioned the Places menu I meant the gnome Places menu, not the Xfce one.

I don't know how to automount internal partitions in Xfce. The last time I tried Xubuntu - over a year ago - there was nothing to compare with the elegant simplicity of the gnome Places menu. Perhaps things have changed but from what you say I guess not.

Which, unless anyone can come up with a simple newbie-friendly way of mounting internal partitions in Xfce, then you are left with having to edit /etc/fstab as srs5694 mentions.

By the way, none of your FAT32 or NTFS partitions are mounted, so I don't know what you meant by them being locked.

---

### Post by Redmage913 on 2010-10-10
> Failed to mount "85G Volume".

The enclosing drive for the volume is locked.

I get this for the 85, 52, and 10G volumes every time I open or reload GParted.

---

### Post by Hakunka-Matata on 2010-10-10
[http://www.uluga.ubuntuforums.org/showthread.php?t=1115299]("http://www.uluga.ubuntuforums.org/showthread.php?t=1115299")

Can you perhaps Install Nautilus File manager into Xubuntu?  The thread above explains it quickly and easily.  Albeit they are using earlier versions of Ubuntu and I believe windows.

---

