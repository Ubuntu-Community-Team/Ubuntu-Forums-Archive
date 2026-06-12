---
title: "System Restore??"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-06-16
Is there any way to save your current system setup, so if you try some change you can do a system restore as in windows, or like snapshot in virtualbox so you can revert to a prior state??  This would be real helpful because I have reinstalled my system a couple of times due to mess ups. I am dual booting but have been spending most of my time here in Linux Land, and my desktop is pretty much set, network is working, software packages are installed and I would not like to have to redo it all over again at this point!! Although I learn alot by fixing mistakes it gets tiresome!. 

Thanks,

 HCILL

---

### Post by xz124 on 2011-06-16
You could take a partition image and restore that if something bad happens. Depending on the size of your Ubuntu partitions, this could take a very long time. Plus, the image size would be the exact same size as your partition that you were imaging, so you'd need a lot of backup space. This is probably not an option for you, but oh well.

To backup:
```
sudo dd if=/dev/sdXY of=some_file.img bs=ZM conv=sync,noerror
```
X needs to be your disk, if you only have one disk, this is most likely 'a'. If you have more than one, substitute with the correct label. Y is the partition number, note that you do not want to backup the entire disk as that would be a pain to restore if other changes were made that you don't want to overwrite (like on your Window$). Z is a number, 1 is the minimum and there is theoretically no maximum, however, you probably do not want to go over 16 here. I don't know what the best number for Z is, it depends on your disk. Oh and you don't necessarily need sync and noerror, but I saw that somewhere it helps in case of disk read errors (which are possible, you don't see them because your disk transparently maps them to extra sectors). some_file should be a file, preferably on an external disk to speed things up, that you wish to backup to.

To restore:
```
sudo dd if=that_file.img of=/dev/sdXY bs=ZM conv=sync,noerror
```
All the variables mean the same things here.

Hope this helped.

---

### Post by Frogs Hair on 2011-06-16
That depends on what you want to restore . A desktop configuration can saved and restored with Ubuntu Tweak.

For files , check out some of the backup tools in the software center . For something more advanced see the links .

There is nothing like system restore on Linux , so be thoughtful about what you do. 

[http://clonezilla.org/](http://clonezilla.org/)  
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Mark Phelps on 2011-06-16
You should also check out CloneZilla.  While it does do full partition imaging (it's not System Restore), it doesn't require the same space as a partition to do the imaging.

It's also fairly quick -- only takes a few minutes.

---

### Post by jerrrys on 2011-06-16
"backintime" may be what your looking for.  its not a system restore.   its in the software center

---

### Post by tej1984 on 2011-06-16
> **jerrrys said:**
> "backintime" may be what your looking for.  its not a system restore.   its in the software center
[http://www.liberiangeek.net/2011/01/install-time-backup-suite-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2011/01/install-time-backup-suite-ubuntu-10-10-maverick-meerkat/)
 
hope this helps

---

### Post by Irony on 2011-06-16
Perform the following to a back up drive;
```
sudo cp -ax /. /media/backupfolder/.
```

---

### Post by JASONFUSARO on 2011-06-30
[ATTACH]196384[/ATTACH]> **JASONFUSARO said:**
> Is there any way to save your current system setup, so if you try some change you can do a system restore as in windows, or like snapshot in virtualbox so you can revert to a prior state??  This would be real helpful because I have reinstalled my system a couple of times due to mess ups. I am dual booting but have been spending most of my time here in Linux Land, and my desktop is pretty much set, network is working, software packages are installed and I would not like to have to redo it all over again at this point!! Although I learn alot by fixing mistakes it gets tiresome!. 

Thanks,

 HCILL




Finally found the answer



I installed Zorin 64 bit and it accomplishes everything with a simple click of a button

**Desktop Recovery list item within Ubuntu Tweak**


Simple, easy and straight forward


see attached screenshots


I have it installed on an 8GiB flash card. I have not installed it to my hard drive yet until I solve a current partitioning problem.

---

