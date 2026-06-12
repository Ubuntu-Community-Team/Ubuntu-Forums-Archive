---
title: "clean install of"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-11
I want to clean install LM9 on a hardy/vista
manual partition reformat the hardy partition happens to be sda3
leave swap same leave ntfs same 
should i make it the sda3 / or /home???? i will make it ext4
there will be no separate home partition ????

---

### Post by nhasian on 2010-06-11
yes make sure your new partition is EXT4, instead of hardy's EXT3.  making a separate /home partition is optional.  you can have up to four primary partitions on a hard disk.  if you want you can have the fourth one be an extended partition so you can make additional logical volumes.

---

### Post by DarinB on 2010-06-11
thank you very much. i am upgrading a friends pc from hardy to lucid with a clean install
what i do need to do is..... i have a home folder from hardy with many issues and i would like to copy over the theme and desktop fonts etc. so it looks like it did before when she was using hardy.
therefore what files do i need to copy over from the old home folder with out copying the entire thing.
I also can't find the .thunderbird folder to copy over the old emails. and .prf files

---

### Post by tjk on 2010-06-11
I am also wanting to do a "clean install", but want to preserve all my settings and data.  I know that the normal response is to just backup and restore your existing /home folder, but are you sure that there isn't more to this?  As well, what app is recommended for backing up the entire harddrive (includes fat32 and other types of formated partitions) -- I would like it so that I can revert to my original system if the clean install doesn't work, but also want to be able to pull out the /home partition or individual files for the upgrade (so an image won't work).

---

### Post by DarinB on 2010-06-11
on my pc i did that when i went from intrepid to linux mint 
and it is excellent...on the pc i am doing was running hardy and she had a lot of files that would not open and flash codecs that did not run
but copying the entire home folder is a great way to upgrade.

---

### Post by -kg- on 2010-06-11
> **DarinB said:**
> I want to clean install LM9 on a hardy/vista
manual partition reformat the hardy partition happens to be sda3
leave swap same leave ntfs same 
[COLOR="Red"]should i make it the sda3 / or /home????[/COLOR] i will make it ext4
there will be no separate home partition ????

I didn't see this issue addressed.  If you intend to use sda3 as your installation partition, then you should select "/" (root) as your mount point in the installation process.  If you wish to have a separate "/home" partition, you'll need to create it separately or select another existing partition and mark its mount point as "/home"..

---

