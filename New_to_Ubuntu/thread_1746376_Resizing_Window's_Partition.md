---
title: "Resizing Window's Partition"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by sheldonhuelin on 2011-05-01
Hi;
Here is my problem: My hard disk drive size is 320 GB, I originally allocated just 100 GB to Ubuntu, and left the rest for Windows 7. I am really enjoying Ubuntu (espcially 11.04) and would like to increase the partition size of it but I am not sure how. I have done some reading on this forum and the web but am still really confused. Could someone please help. Thanks
Sheldon

---

### Post by josephmills on 2011-05-01
> **sheldonhuelin said:**
> Hi;
Here is my problem: My hard disk drive size is 320 GB, I originally allocated just 100 GB to Ubuntu, and left the rest for Windows 7. I am really enjoying Ubuntu (espcially 11.04) and would like to increase the partition size of it but I am not sure how. I have done some reading on this forum and the web but am still really confused. Could someone please help. Thanks
Sheldon

look into gparted google it watch some videos you will be done in no time. Glad that you like ubuntu :)

---

### Post by wilee-nilee on 2011-05-01
> **sheldonhuelin said:**
> Hi;
Here is my problem: My hard disk drive size is 320 GB, I originally allocated just 100 GB to Ubuntu, and left the rest for Windows 7. I am really enjoying Ubuntu (espcially 11.04) and would like to increase the partition size of it but I am not sure how. I have done some reading on this forum and the web but am still really confused. Could someone please help. Thanks
Sheldon

It is best to use the disk manager in W7 to resize it, it is a virtual partitioner and is done from a admin account.

Really though give us a picture of the HD with gparted though if you want a exact description.

Gparted can be used to resize W7 but you risk things by doing this in that if you shrink it to far=past the non-movable paging files and haven't defragged it your a lot closer statistically to a bricked set up then a disk manager resizing.

---

### Post by jprobe on 2011-05-01
> **sheldonhuelin said:**
> Hi;
Here is my problem: My hard disk drive size is 320 GB, I originally allocated just 100 GB to Ubuntu, and left the rest for Windows 7. I am really enjoying Ubuntu (espcially 11.04) and would like to increase the partition size of it but I am not sure how. I have done some reading on this forum and the web but am still really confused. Could someone please help. Thanks
Sheldon
  
I did this just last month:

BACK UP EVERYTHING.  Defrag your Windows drive.  In W7 right click on your My Computer icon in the start menu, and say manage.  Type in your password.  It'll show you the partitions on your drive.  I am assuming that it looks like this (_**if not, then please don't do what I am saying**_ and post how it does look):

| Windows | Windows C drive | Ubuntu 11.04 | Ubuntu Swap | Windows 

Right click the one you want to reduce (windows c more than likely) and hit resize.  Reduce it however much you want to increase your Ubuntu partition.  

| Windows | Windows C | xx Unpartitioned xx | Ubuntu | Swap | Windows

Restart using your gparted live cd (found here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)).  Your windows partition is in front of your Ubuntu partition, so you need to first move Ubuntu next to the windows partition, 

| Win | Win | Ubuntu | xxxx | Swap | Win

and then, second, resize it to where it was.  

| Win | Win | Ubuntu ------> | Swap | Win

I also took this opportunity to increase the size of my swap.  Now just apply these settings and make yourself a pot of tea (if you want to do exactly what I did, I made a nice pot of Lapsang Souchong).  This process took FOREVER to complete (just around an hour).  But if all goes well, you should have plenty of room to enjoy your new 11.04!  Cheers, and let everyone know how you did!

---

### Post by drs305 on 2011-05-01
Here is some info and tips for resizing /.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")
Also take a look at the link to srs5694's offering in the links section of the first post above.

---

### Post by jprobe on 2011-05-01
> **drs305 said:**
> Here is some info and tips for resizing /.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")
Also take a look at the link to srs5694's offering in the links section of the first post above.


Right on drs305! Superb walk-through pictures and all! =D>

---

### Post by beew on 2011-05-01
> **jprobe said:**
> 

so you need to first move Ubuntu next to the windows partition, 

| Win | Win | Ubuntu | xxxx | Swap | Win

and then, second, resize it to where it was.  




Instead of moving the Ubuntu partition why not just move the left end to become 
 Win | Win | Ubuntu | xx| Swap | Win
 and then move the right end to 
Win | Win | Ubuntu  Swap | Win?

---

### Post by jprobe on 2011-05-01
> **beew said:**
> Instead of moving the Ubuntu partition why not just move the left end to become 
 Win | Win | Ubuntu | xx| Swap | Win
 and then move the right end to 
Win | Win | Ubuntu  Swap | Win?

That was what I tried first, but I don't think that you can move the front end of a partition like that.  In any case, I had to make the move (kb at a time) and then the resize.  If you can move your front end (left side) over, then by all means that would save time.  I just don't think that you will have that option.

---

### Post by remarkrab on 2011-05-01
On a side note Easeus partition manager is my favorite on windows and the home edition is free at w ww.partition-tool.com

---

