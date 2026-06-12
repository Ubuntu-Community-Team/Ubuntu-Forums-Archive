---
title: "Installing Ubuntu 9: Partitioning"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by iamleaf on 2009-05-19
Hey everyone, me so confused :S

Upgrading from Ubuntu Hardy. Still a noob. 
I want to partition manually but I don't know which to choose: EXT3, FAT32, NTFS etc.

I have two disks: a 40 GB one and an 160 GB one.
I want to make a new partition for my Home folder and the rest of it can all go to another partition. 

Is it possible to make my home folder on the other disk and the rest of it on the 40 GB one?

Also please help me in choosing the  [LIST]
[*]type
[*]mount point
[/LIST]
for each of the partitions.

Thanks!!! xD

---

### Post by Elfy on 2009-05-19
Yea you can do that - choose manual

Select the partition you want the install to go on - Edit partition - choose mountpoint / you can't use fat or ntfs as filetype - I would pick ext4 but ext3 is the default type - there have been some issues it seems with ext4 but I have had no problems.

Select the partition you want to use for your home - edit partition - chhose mountpoint /home - again I would use ext4 but ...

Read this regarding ext3/4 [http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

---

### Post by iamleaf on 2009-05-19
What mount point should I choose for disk storage? (not home folder, not root either... just other stuff) ?

---

### Post by timcredible on 2009-05-19
i would do:

40gb drive:
   partition 1: 10gb mounted at /
   partition 2: 1gb mounted as swap
   partition 3: the rest mounted at /home

160gb drive:
   entire disk mounted at /data (the old unix standard was /opt, but i wouldn't do that anymore)

then make symlinks from your home directory to /data for your data storage needs.  keep in mind that the defaults are Music, Pictures, Videos in your home directory```
rmdir Music
``` etc.  

if you want those to be in /data, then delete those directories in your home directory, then make symlinks to them in /data like: ```
sudo mkdir /data/<yourloginname>
sudo chown <yourloginname> /data/<yourloginname>
sudo chgrp <yourloginname> /data/<yourloginname>
mkdir /data/<yourloginname>/Music
ln -s /data/<yourloginname>/Music Music
```
and repeat the last 2 lines for Pictures, Videos, etc.

---

