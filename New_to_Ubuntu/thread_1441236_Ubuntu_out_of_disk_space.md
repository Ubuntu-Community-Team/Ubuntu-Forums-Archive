---
title: "Ubuntu out of disk space"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by ynnojC on 2010-03-28
I am running ubuntu on a mac book pro(13 inch) and i ran out of space on ubuntu. I cant resize the partition through boot camp though, and i dont know how to use gparted. any suggestions?

---

### Post by r-senior on 2010-03-28
How have you partitioned the disk? One large partition for everything, or separate partitions for / and /home? Or something else?

How much space did you allocate?

As a start, this might free some space:

$ sudo apt-get update
$ sudo apt-get autoclean
$ sudo apt-get autoremove

---

### Post by ynnojC on 2010-03-28
> **r-senior said:**
> How have you partitioned the disk? One large partition for everything, or separate partitions for / and /home? Or something else?

How much space did you allocate?

As a start, this might free some space:

$ sudo apt-get update
$ sudo apt-get autoclean
$ sudo apt-get autoremove

I use 1 large partition for everything. I allocated only 4GB of space (probably why I ran out.)

How do you use separate partitions for / and /home?

---

### Post by r-senior on 2010-03-28
The easiest way to use multiple partitions is from the installer. It pretty much walks you through the whole thing. 

You can do it after installation if you have free space to make another partition. In short, you make the partition, format it, mount it onto a temporary mount directory, move your /home folder to it and remount it as /home.

But if you've no spare space, you can't do that as a quick fix.

Did you get anywhere with the apt-get cleaning up? Did it make any space? I guess the next step, assuming you've deleted any of your own files that you don't need, is to remove software you don't use. Ideally go for the bigger things like OpenOffice, GIMP?

Might also be worth looking in /var/logs. You can remove the archived logs:

$ sudo rm /var/log/*.[1-9].gz

---

### Post by ynnojC on 2010-03-28
How do i make the mac os x partition smaller to make a new partition in gparted? also, where is Gparted in the menu. i cant find it. 

Also, thanks for the help:p

---

### Post by llamabr on 2010-03-28
Have you tried just cleaning up your space?  Look in ~/.local/share/Trash/ and see if there's anything big in there.  Also look in /tmp/  then do a 

```
sudo apt-get clean
```

you can also clean up some log files, but those ususally aren't that big.

Post your:

```
df -h  
```

after that, and we can get a feel.

---

### Post by BikeHelmet on 2010-03-28
You need to install the Gnome Partition Editor first.

I would install [Ubuntu Tweak]("http://ubuntu-tweak.com/"), too. It has handy options that free up quite a bit of space.

---

### Post by ynnojC on 2010-03-28
okay, so i use Gparted to create an empty partition, now how do i mount it to copy /home to it? Basicely, i need to know how to format and set where to mount the drive.

---

### Post by ynnojC on 2010-03-28
okay, i formated it as "jonny cash!":p, and can now acces it. how do i mount it to the /home directory?

(PS my name is jonny, so i thought the name would be funny)

---

### Post by ynnojC on 2010-03-29
Solved! Heres what i did, I backed up ubuntu by copying /home to an SD card, backed up Mac os x using time machine, created a new partition table using mac os x install disk, and reinstalled mac and ubuntu. then i used ubuntu live CD to copy /home (from the SD card) to the hard disk.:popcorn:

---

### Post by lavinog on 2010-03-29
bleachbit is a handy program for freeing up some wasted space btw.

---

