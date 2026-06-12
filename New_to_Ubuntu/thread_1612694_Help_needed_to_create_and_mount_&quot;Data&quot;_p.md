---
title: "Help needed to create and mount &quot;Data&quot; partition"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by jaycee23 on 2010-11-03
For a while now I have done a separate root and home partition whenever I do a fresh install. This has worked well but I wanted something cleaner.

After some thought and reading around I would now like to create a separate "Data" partition which I would like to mount at boot.

I propose storing all my music, documents and videos on this partition and then edit the bookmarks to point to my "Data" partition.

I would leave the Data partition untouched at any further installations and just mess with the root and home partition. I would share the Data partition with my various distro installations. 

Has anyone got some simple instructions on how to do this.

Thoughts welcome.

---

### Post by amjjawad on 2010-11-03
> **jaycee23 said:**
> For a while now I have done a separate root and home partition whenever I do a fresh install. This has worked well but I wanted something cleaner.

After some thought and reading around I would now like to create a separate "Data" partition which I would like to mount at boot.

I propose storing all my music, documents and videos on this partition and then edit the bookmarks to point to my "Data" partition.

I would leave the Data partition untouched at any further installations and just mess with the root and home partition. I would share the Data partition with my various distro installations. 

Has anyone got some simple instructions on how to do this.

Thoughts welcome.


[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you're Dual Booting Ubuntu with Windows, it's good idea to have NTFS "Data" Partition so that both Ubuntu and Windows can access that partition. Otherwise, if you have Ubuntu only, use ext4 or ext3 (in case you'll install another Distribution later on).

---

### Post by sikander3786 on 2010-11-03
What is your current partitioning setup? Have you got a free partition on your HDD or you need to shrink an existing partition and then create a new partition in that space?

As mentioned by amjjawad, you can format it to ext3/ext4/NTFS, depending on your needs.

It will be better to post the output of

```
sudo fdisk -l
```

so we have a better idea of your setup and therefore are able to advise more efficiently.

---

### Post by oldfred on 2010-11-03
I mount and then link folder from /data directly into /home. Since I reinstall regularly I converted my first effort from a history list of commands into a bash script.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
Suggestion by srs5694 on /shared or /mnt as location to mount data partitions to:
[http://ubuntuforums.org/showthread.php?t=1594622](http://ubuntuforums.org/showthread.php?t=1594622)

---

### Post by Gone fishing on 2010-11-03
That what I do (only I call it storage). You can then add the partition to your fstab file if you want it mounted on boot - however there is a gui tool to help called Mount Manager.

---

### Post by jaycee23 on 2010-11-04
Thanks for all your help. Found exactly what I was looking for here.

[http://ubuntuforums.org/showthread.php?t=1490708](http://ubuntuforums.org/showthread.php?t=1490708)

---

