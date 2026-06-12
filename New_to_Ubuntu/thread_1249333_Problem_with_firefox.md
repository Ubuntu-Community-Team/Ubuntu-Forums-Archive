---
title: "Problem with firefox"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by manjotpahwa on 2009-08-25
I installed ubuntu on my computer which has Microsoft XP as well, and when it asked how much space to allocate (I installed via the CD they send) I checked the option of installing them side by side. I do not know how much disk space it got allocated.
Now when I try to use firefox, an error gets displayed saying that there is not enough disk space and that my application will not work. I cannot browse the internet but when I boot ubuntu using the CD via the live session user, Mozilla works just fine.
What should I do?

---

### Post by aktiwers on 2009-08-25
I would recommend resizing your partition or if that scares you off, simply do a new install, where you manually create your partitions.

Or open terminal (Applications => Accessories => Terminal) and type in:
```
df
```

And copy/paste the output here for us to see. Then we can see if you are out of diskspace or whats going on.

Welcome by the way :)

---

### Post by manjotpahwa on 2009-08-25
Thanks! Here's the message I got.
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              2403388   2351908         0 100% /
tmpfs                   221508         0    221508   0% /lib/init/rw
varrun                  221508        92    221416   1% /var/run
varlock                 221508         0    221508   0% /var/lock
udev                    221508       148    221360   1% /dev
tmpfs                   221508       512    220996   1% /dev/shm
lrm                     221508      2392    219116   2% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024        16      1008   2% /tmp
/dev/sr0                715732    715732         0 100% /media/cdrom0

The error message with Mozilla says some 'security issues', may be problem with the application. Same thing happens (disk space not enough) if I try to save a document in my folder File System. In Windows, the disk space available on C: is about 28GB and on D: is about 16GB. I don't know why this problem is coming.

---

### Post by aktiwers on 2009-08-25
/dev/sda6              2403388   2351908         0 100% /

That means your drive is full! Hmm.. 
You can also check it from Ubuntu with:
```
df -h
```

---

### Post by halitech on 2009-08-25
looks like the Ubuntu installer strikes again and only gave you 2.3gig of space (the bare minimum to install everything) so you will need to resize the partition to get more room.

You can use the Ubuntu Live cd to resize but I would suggest using the windows tools to defrag and shrink your windows partition first.

---

### Post by manjotpahwa on 2009-08-26
So, how am I supposed to allocate more space to Ubuntu?
How should I go to Gnome Partition Editor? There is no such option in my System icon.

---

### Post by manjotpahwa on 2009-08-26
Please help.

---

### Post by achase79 on 2009-08-26
use the liveCD (installer cd) to use the partition editor

---

### Post by manjotpahwa on 2009-08-26
you want me to run a live session or do you want me to install again?

---

### Post by Grenage on 2009-08-26
Indeed, and to elaborate, the partition tool is gparted.  Boot from the CD as a live CD (try without changing anything).

---

### Post by fanglinyong on 2009-08-26
go to your windows, and use the pq software to resize your disk(backup your important date first)!
i suggest that:
loacation    size
/ -----------10--15G;
swap       -------1-2G;
/home      ----->10G,or as much as you can give!

---

### Post by manjotpahwa on 2009-08-26
Can you tell me a solution which does not involve my using my Windows software because it is infected with virus (like it is after evry 2 months) which is why I shifted to Ubuntu. Whenevr I try to go to it, the computer hangs up or shows up a blue screen sayiong physical dump of memory...
So, I can't defragment my disk, even though I tried to, the same problem kept on happening. 
I have no problem in losing the data, I have backed up the important data I want.
Now can you tell me another way?
I do not want to uninstall Windows either.

---

### Post by manjotpahwa on 2009-08-26
I tried that but I can't resize. The option to unmount is disabled (ie I can't click on it).

---

### Post by mkvnmtr on 2009-08-26
What you need to do will be hard for you to understand with your level of experience. You seem to have installed on a very small partition. Working with partitions can give you a lot of problems if you do not understand what you are doing.
I would recommend that you boot from the live disk. Then open the partition manager and take a screenshot of it. Then using firefox on the disk post the screenshot in this thread. Then someone can see your problem and guide you through fixing it.

---

### Post by manjotpahwa on 2009-08-26
I tried that but there's no option to unmount so I am not able to do it. What should I do?

---

### Post by manjotpahwa on 2009-08-26
Thanks, here's the screenshot.

---

### Post by manjotpahwa on 2009-08-26
Please someone!!
Please!

---

### Post by manjotpahwa on 2009-08-26
Hello, anyone there?

---

### Post by fanglinyong on 2009-08-26
from the image ,i know that you used two system, one is windows, and the other is buntu,now
we said that you resized your /dev/sda5, the sda5 is drive D in your windows system!
you can use PQ software in windows to resize your drive D ,for example ,you can give ubuntu 15GIB,and left 20G for your windows system!this operation  will not delete your date on drive D,and then you can distribute your new partition to your new system--ubuntu.
remember :if you want to install and use ubuntu, you must have 20G at lest to install ubuntu!!!

---

### Post by manjotpahwa on 2009-08-27
Thanks, but now I have completely deleted Windows. In any case it was virus infected (which is why I shifted to Ubuntu). But I do not knwo much about Ubuntu. Hopefully I'll learn soon.

---

### Post by aktiwers on 2009-08-27
Okay I will give it a go and try to explain.
Do a clean install.

 If you want to dualboot with Windows, you need to install windows first, if you are going the happy way (only installing Ubuntu) Follow below.

Do a clean install.

Do as you normally do, but when it ask you to partition, pick manual partitioning.

Start off by deleting all the partitions you dont want(ie the Linux partitions).
Now you have some empty space to play with. 

 Start by creating a partition on min. 4gb (make it bigger if you want, I keep mine at 15gb to be sure there is enough). Its pick EXT4 in the filesystem spot and type in ```
/
``` in the "mount point" box.

Click OK.

Now create a new Partition on 1 gb. In filesystem, pick "SWAP".

And click OK. 

Now you are ready to go, if you want to create a home partition, go on create another partition, with filesystem EXT4 and type in the "mount point" box ```
/home
```
This last step i optional though.

Go through the rest of the install as usual.

Done.

Hope it helps :)

---

