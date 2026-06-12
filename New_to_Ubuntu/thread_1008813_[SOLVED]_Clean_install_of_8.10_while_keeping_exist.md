---
title: "[SOLVED] Clean install of 8.10 while keeping existing partitions.."
date: 2008-12-11
forum: New to Ubuntu
---

### Post by akelsall on 2008-12-11
I'm currently running 8.04 and want to upgrade to 8.10. I have separate /, swap, and /home partitions. In addtion to these, I have several other partitions, (e.g. /music, /photos, /computer) and I don't want to wipe these out during the clean install. 

What is the safest way to do a **fresh** install (not an upgrade from 8.04, but a fresh install of 8.10) to prevent my other partitions from getting wiped out?

Thanks,

Andy

---

### Post by aheckler on 2008-12-11
When you go to install, make sure the "Format" box for those partitions is **unchecked**.

---

### Post by cariboo on 2008-12-12
Just to expand on what the PP said, when you get to the partitioning section choose Manual and only format /, make sure you set mount points for the rest of the partitions and you should be OK.

Jim

---

### Post by mdebusk on 2008-12-12
> **akelsall said:**
> What is the safest way to do a **fresh** install (not an upgrade from 8.04, but a fresh install of 8.10) to prevent my other partitions from getting wiped out?

Print out the output of: ```
sudo fdisk -l
```
Keep it handy. It might save your butt. (It's saved mine.) You'll be able to tell which partitions to leave unchecked when the install wants to format.

---

### Post by akelsall on 2008-12-12
> **cariboo907 said:**
> ...when you get to the partitioning section choose Manual and only format /, make sure you set mount points for the rest of the partitions and you should be OK.


Thanks Jim. I have a few follow-up questions if you don't mind. 

So, what happens with my /home and swap partitions? Will they be left intact? 

Concerning your comment about setting the mount points, I'm not 100% clear on this. If I have several other partitions currently in use (e.g. /photos, /music, etc), when I set those mount points, is the data currently on those partitions left intact, or is it wiped out? 

Am I correct in saying the the new kernal (8.10) will be installed in it's entirety on just the / then? 

Thanks,

Andy

---

### Post by akelsall on 2008-12-17
Well, I completed the upgrade and it only took about 25 minutes. For details on the upgrade, please see my posting under Installs and Upgrades:

[http://ubuntuforums.org/showthread.php?p=6387248#post6387248](http://ubuntuforums.org/showthread.php?p=6387248#post6387248)

Here are my general impressions so far (after a week of running 8.10):

>  Boots a LOT faster than Hardy. 

         Fixed my video card, so I can now use Compiz!!

         Fixed my issue with VirtualBox (couldn't access the 'Net from my WinXP guest before upgrading to 8.10). 

         Tabs in Nautilus!! Great idea!!!


---

### Post by akelsall on 2008-12-18
Bit the bullet and went forward with the upgrade. All went well. See the link below for all the details:

[http://ubuntuforums.org/showthread.php?t=1013990](http://ubuntuforums.org/showthread.php?t=1013990)

---

