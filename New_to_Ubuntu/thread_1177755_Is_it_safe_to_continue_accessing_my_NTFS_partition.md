---
title: "Is it safe to continue accessing my NTFS partition?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by kickwin on 2009-06-03
I have a dual-boot WinXP/Ubuntu (ubuntu recent) and I have most of my files - music, docs etc. on one of my Windows NTFS partitions. Since Ubuntu mounted these partitions by default, I have had no problem accessing/editing the files present there. Is it okay to keep accessing these files and not move the stuff over to my ubuntu partition? Any demerits?

I found in some posts that creating a FAT partition is the right thing to do. But being a newbie, I am a bit apprehensive of the task of re-partioning and stuff. Thanks!

---

### Post by Paqman on 2009-06-03
> **kickwin said:**
> 
I found in some posts that creating a FAT partition is the right thing to do.

Probably only reeeeaaaally old ones. Linux didn't used to have write support on NTFS partitions built-in, so nasty old FAT32 partitions used to be popular. No need for them at all now.

About the only problem you're going to strike with using an NTFS partition on Linux is that it'll get fragmented (eventually). That's less of an issue on a data partition than one that has an OS, as you (probably) aren't changing the contents as much.

Since you've still got a copy of Windows, just boot up into it and let Windows defrag it every once in a while.

---

### Post by DGortze380 on 2009-06-03
> **Paqman said:**
> Probably only reeeeaaaally old ones. Linux didn't used to have write support on NTFS partitions built-in, so nasty old FAT32 partitions used to be popular. No need for them at all now.

About the only problem you're going to strike with using an NTFS partition on Linux is that it'll get fragmented (eventually). That's less of an issue on a data partition than one that has an OS, as you (probably) aren't changing the contents as much.

Since you've still got a copy of Windows, just boot up into it and let Windows defrag it every once in a while.

Agreed, no issues using NTFS. 
Keep good backups.
Defrag occasionally.

---

### Post by kickwin on 2009-06-03
Thanks guys. That's a relief :grin:

---

### Post by bodhi.zazen on 2009-06-03
So long as you are dual booting with windows , accessing your ntfs file system should be fine.

The problem with NTFS is that there are no tools to fix the NTFS file system in linux , so if yo have problems you need windows to repair it.

Once (if) you leave windows, I suggest FAT. FAT is popular and is the default file system on Flash drives (mainly due to compatibility).

---

### Post by hovzio on 2009-06-04
I have no problems accessing files, the problem arises when I change anything on my C drive. Windows doesnt seem to like this to much, its like it takes a snapshot of things before it powers down and things run very funny after rebooting to windows. Copying has been no problem but as soon as I go changing files vista starts complaining. This is just my experience, but it has happened a few times so after googleing a little this is the conclusion I have come to, please correct me if I'm wrong.;)

---

### Post by listener on 2009-06-04
I'll add the (probably) obvious:
You have access in Ubuntu to parts of your Windows
filesystem which Windows will protect.  Don't go
places like 'System Volume Infomation' etc while
in Ubuntu, as that will surely cause problems
On the other hand, as I've been moving to Linux
filesystems, I've discovered that if you no
longer need to use it in Windows, you can delete
System Volume Information possibly regaining
several gigs of drive space.  I've never had a
problem with this, but I'm not certain Linux never
uses it.  Vista, I know, keeps a lot of backups
(system restore points, shadow copies, etc) in
there which you cannot access from Ubuntu anyway.

---

### Post by Paqman on 2009-06-04
> **bodhi.zazen said:**
> 
Once (if) you leave windows, I suggest FAT. FAT is popular and is the default file system on Flash drives (mainly due to compatibility).

I wouldn't bother with FAT. If you're no longer needing compatibility with Windows then switch to EXT.

---

### Post by hovzio on 2009-06-05
> **Paqman said:**
> I wouldn't bother with FAT. If you're no longer needing compatibility with Windows then switch to EXT.

For a filesystem etc ext is great.. I personlly use ext2 for a filesystem on a ssd, thumbs drives etc. Nevertheless, imho there is no great advantage in this... I'm at work and need somthing that compatible with "the rest of the world"; hence fat32 is indeed a fine option (Ask tomtom) because it just works and is fur sure compatible.

---

### Post by anjilslaire on 2009-06-05
Also, bear in mind FAT32 partitions that are very large can actually perform slower than other file systems:
[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)
> 
many tasks on a very large FAT32 file system become slow and inefficient.
 
If you're using large data drives, FAT may not be the best option performance-wise.

---

### Post by Paqman on 2009-06-05
> **anjilslaire said:**
> 
If you're using large data drives, FAT may not be the best option performance-wise.

It also suffers from heavy fragmentation, and has a maximum file size of 4GB. It's only real good point is it's universal compatibility, but these days pretty much anything can read/write NTFS anyway.

---

### Post by kickwin on 2009-06-05
Thanks for all your replies. I am more educated on the different file systems now.

---

### Post by Shadowking on 2009-06-05
It's frustrating that windows cannot access ext3. Anyway, I have 3 questions...

1. Can Ubuntu automount my NTFS partitions on startup? 
2. The NTFS drives to not be displayed on desktop when mounted? It's annoying.
3. Why can't I adjust the location of my Desktop Icons (I can't maximize my desktop space there's a lot of corner space being wasted)? and why are they so large? I can only resize them by right-clicking and resizing them manually.

---

### Post by VCoolio on 2009-06-05
1. yes, read elsewhere the forums or search with keywords 'ntfs' 'automount' 'fstab' (/etc/fstab is the file to edit).
2. you can set what you want to see on your desktop in the configuration editor (alt+F2, type gconf-editor and it will show up); navigate to apps/nautilus/desktop and tweak (uncheck volumes_visible to prevent partitions show up).

---

### Post by Shadowking on 2009-06-05
> **VCoolio said:**
> 1. yes, read elsewhere the forums or search with keywords 'ntfs' 'automount' 'fstab' (/etc/fstab is the file to edit).
2. you can set what you want to see on your desktop in the configuration editor (alt+F2, type gconf-editor and it will show up); navigate to apps/nautilus/desktop and tweak (uncheck volumes_visible to prevent partitions show up).
cool...Thanx!

---

### Post by markharding557 on 2009-06-05
if you want to be ultra safe you could set the ntfs partition to be read only

---

### Post by kickwin on 2009-06-05
> **Shadowking said:**
> 
1. Can Ubuntu automount my NTFS partitions on startup? 


I recently installed Ubuntu 9.04 Jaunty Jackalope and my Windows drives were automatically mounted.

---

### Post by Paqman on 2009-06-07
> **Shadowking said:**
> 
1. Can Ubuntu automount my NTFS partitions on startup? 


Yes, install the package ntfs-config for an easy way to set this up.

> 
2. The NTFS drives to not be displayed on desktop when mounted? It's annoying.


Anything mounted to a mount point in /media shows on the desktop. You can put your mount point somewhere like /mnt if you don't want it to show.

> 
3. Why can't I adjust the location of my Desktop Icons (I can't maximize my desktop space there's a lot of corner space being wasted)? and why are they so large? I can only resize them by right-clicking and resizing them manually.

To change your icon sizes open Nautilus and go to Edit > Prefs > View > Icon View Defaults and change the level of zoom.

---

