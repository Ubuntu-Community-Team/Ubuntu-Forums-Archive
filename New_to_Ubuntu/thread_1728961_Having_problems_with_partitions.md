---
title: "Having problems with partitions"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Musicmaker384 on 2011-04-14
Hello. I dual-boot Windows 7 and Ubuntu 10.10. I am trying to expand my Ubuntu partition so that it has more space. 18GiB won't cut it for much longer. I inquired about this some time ago, and someone was nice enough to explain to me that I had to shrink the Windows partition before I can expand the Ubuntu partition. I ran into a problem so I gave up on it for a while, but now that the 18GiB I gave Ubuntu is getting pretty full, I want to go ahead with it. Except, here's the problem - when I run GParted, the Ubuntu partition doesn't seem to show up. 
These are the four partitions that show up when I run GParted:

dev/sda1|ntfs|unmounted (SYSTEM)
dev/sda2|ntfs|host
dev/sda3|ntfs|unmounted (RECOVERY)
dev/sda4|fat32|unmounted (HP_TOOLS)
unallocated 1.00MiB

None of these are the Ubuntu partition from what I can tell. But then again, I am relatively new to Linux distros, so I suppose I could be wrong. However, when I run the Disk Utility in Ubuntu, it shows a 18GiB Linux loop which I assume is the Ubuntu partition (dev/loop0). It says it is mounted at "L". Do I need to unmount it so that it will show up in GParted? Or do I need to shrink the Windows partition first? Or both? I ask because I do not want to do anything that will harm my computer. I simply want more drive space for Ubuntu. Can anyone tell me the correct, safe way to do this?

---

### Post by Jerry N on 2011-04-14
The partitions as shown do not indicate that you are dual booting but rather that you installed Ubuntu with Wubi.  

Your gparted outputs shows that your Windows installation is using all 4 possible primary partitions and that to actually install as a dual boot you would need to remove one of these partitions.  I know nothing of Wubi so I can't help with that.

Jerry

---

### Post by seawolf167 on 2011-04-14
Wubi installs Ubuntu in a virtual partition, you won't be able to use GParted to edit its partition sizes (or the Windows partition editor for that matter). The virtual partition is actually a file on the Windows OS (think VirtualBox). See here for the [Wubi guide.]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

---

### Post by Mark Phelps on 2011-04-15
Just be aware that Windows needs some free space in order to work properly.  So, don't make the mistake of expanding your Ubuntu virtual disk to fill the entire available space in Windows -- or it won't boot or work anymore.

---

### Post by Rubi1200 on 2011-04-15
Can you post a screenshot from Disk Management of the current layout and sizes of your partitions please.

There is a way to resize the root.disk, but it has nothing to do with GParted. Using that will likely cause you problems that might be very hard, if not impossible, to fix without reinstalling.

Always providing full information in the future will help avoid being given advice that could potentially damage your system.

See here for information on how to resize the Ubuntu root.disk:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

As Mark Phelps already pointed out, make sure you do not run into issues with your Windows install (which is why the screenshot I asked for would be very helpful before you do anything).

Thanks.

---

### Post by union12011 on 2011-04-15
Your way ahead
Can you tell me how to find the partition
for windows I know it's loaded but have
no idea what version or how to open it
I think this follows this thread

---

### Post by seawolf167 on 2011-04-15
> **union12011 said:**
> Your way ahead
Can you tell me how to find the partition
for windows I know it's loaded but have
no idea what version or how to open it
I think this follows this thread

You should open a separate post with details of what you are trying to do and what is/isn't working so people can help you out.

---

### Post by union12011 on 2011-04-15
Did as told 
From reading forums
I know I should now delete this and
previous message but not sure how
thanx seawolf167

---

### Post by seawolf167 on 2011-04-15
You can always edit the post and say you removed the contents since you made a separate thread, but its probably not too big a deal since you posted a follow up saying your created your own thread.

---

### Post by Musicmaker384 on 2011-04-16
For some odd reason, the .jpg screenshot of the partitions and their sizes will not load. I uploaded to photobucket, clicked 'insert image', and pasted the URL, but it will not load.
[IMG]http://s1098.photobucket.com/albums/g370/Musicmaker384/?action=view&current=partitions.jpg[/IMG]

---

### Post by Rubi1200 on 2011-04-16
Try uploading it here to the forums if possible.

In a new post, click on the paperclip icon on the toolbar and attach to your post.

---

### Post by Musicmaker384 on 2011-04-17
Oh, excuse me. I tried to upload using the 'Insert Image' button instead of the 'Attachments' button. I am relatively new to Ubuntu Forums, so please forgive me.

I uploaded the requested screenshot. If this is not it, please let me know, and I will boot into Windows and take a screenshot of the Windows Disk Management screen.

---

### Post by Rubi1200 on 2011-04-17
According to the screenshot, sda2 is probably your C drive where you have Wubi installed. GParted reports there should be enough free space, so I would go ahead and resize the root.disk using the instructions in the link I gave you earlier.

If you have other questions, feel free to ask.

---

### Post by Musicmaker384 on 2011-04-17
Thank you very much Rubi1200, you have been very helpful.

---

### Post by Rubi1200 on 2011-04-18
No problem, you are more than welcome :-)

---

