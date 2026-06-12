---
title: "Ubuntu can't update"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2009-06-03
I went to System --> Administration -->Update Manager

I got the following error message:


Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '81788964' '--update-at-startup' as user root.

Unable to copy the user's Xauthorization file.

Please Help!

Thanks,

Jpinson

---

### Post by YQ002lc2 on 2009-06-03
This is what I get when I try to open Synaptic package manager:

Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.


I should say that I recently did:
sudo apt-get install sbackup
and I backed up my system. I haven't tried to update since then, but now this is happening.

Thanks,

jpinson

---

### Post by YQ002lc2 on 2009-06-03
I just checked gnome system monitor. I don't know how, but my 15 GB root partition has filled completely up. Just recently it wasn't nearly that full. 

I have offline Gmail, GCalendar, Documents, etc, installed but these should be stored in the /home partition I thought?

There is room on my /home partition, but offline Gmail is not synchronizing now.

I disabled offline Google stuff now.

I will check the sbackup files in my root partition because I suspect this might be why my root partition filled up so quickly. 

The problem is that specified the backup to go to my External HDD. 

I will post any updates here just as soon as I get them. 

Thanks,

jpinson

---

### Post by YQ002lc2 on 2009-06-04
The problem is solved now. 

It seems that the sbackup software caused a lot of problems. When I mount my external HDD, one of the mounted partitions was /media/LinuxBackup but sbackup software actually created a folder on my local machine with this name and path. 

sbackup filled up my system to the point where I couldn't even do gksudo nautilus or anything requiring root permissions.

I finally went through a rigourous repartitioning of my system using an Ubuntu bootable USB I burned from the Ubuntu 9.04 image. 

If you want to do this, just go to System--> Administration --> USB Startup Disk Creator and select the USB drive you want as well as the location of the image you downloaded or had mailed.... 

I made enough space in my root partition and this seemed to fix the problem. 

Then, this morning, I noticed my root partition was growing crazily as time increased. I discovered through the gnome-system-monitor that sbackup was performing it's daily backup in the same flawed way it had before. 

I uninstalled the sbackup software using the synaptic package manager before it filled up my system again. 
I tried to delete the backed up files from my computer with gksudo nautilus, but this didn't seem to make a difference in the amount of space used on my root partition. 

Finally, using gksudo nautilus and "View-->Show Hidden Files" I skowered my computer for trash folders where the files might still be. 

I even used Applications--> Accessories--> Disk Usage Analyzer.

Finally, It occured to me and I found it. 
I should mention that my computer is setup with a separate partition for /, /home, and /swap.  

I went to  /root/.local/share/Trash
There were all my sbackup backup files and everything I'd ever deleted with root permissions. I deleted about 10 GB of files from this folder and now my system is back to it's normal size.

I think I will keep looking around for how to backup my system, but I don't think I will be using sbackup again. 

If anyone knows of some really good links on how to clone your ubuntu desktop, please let me know. Otherwise, I will keep searching the forums...

Thanks,

jpinson

---

