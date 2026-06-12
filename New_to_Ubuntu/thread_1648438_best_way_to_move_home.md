---
title: "best way to move home"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by bj218 on 2010-12-18
What is the best way to move /home/bill to a partition /media/homeu?

---

### Post by JKyleOKC on 2010-12-18
The **best** way is not at all; if you move that directory out of /home then none of bill's programs will work properly and he may not even be able to log into the system at all.

Tell us what you're trying to accomplish and we may be able to help you get there. Moving a home directory, however, is a guaranteed way to get a broken system!

---

### Post by bj218 on 2010-12-18
> **JKyleOKC said:**
> The **best** way is not at all; if you move that directory out of /home then none of bill's programs will work properly and he may not even be able to log into the system at all.

Tell us what you're trying to accomplish and we may be able to help you get there. Moving a home directory, however, is a guaranteed way to get a broken system!

I do not want to loose all my data ie screen saver printer driver & many others every time I install a new version of ubuntu.

---

### Post by hwychld on 2010-12-18
What you want then is to make a copy, not move.  This can be done from Nautilus by going to Places->Home, then go back one directory so that your home directory is shown in the right pane.  Highlight it and right click, choose copy and then paste in media/homeu (or whatever you have mounted where you are trying to place your backup - I assume some sort of removable media).

Or perhaps more direct, from the command line

```

cp -r ~/ /media/homeu

```

If this is something you will want to do routinely, then look into rsync.

Or if you want to eliminate the problem, create a new partition for your home directory.  There are tutorials on the web for this (I have done it but it does require some knowledge of using gparted and partitions, and there is a risk of messing up your install - so make a backup before you do this.  Clonezilla would be a good tool to use for the backup).  With home on its own partition a new install won't affect the home directory.

---

### Post by cipherboy_loc on 2010-12-18
Just a note: to save file permissions when you copy (assuming you are copying to a regular Linux drive, ie Ext*, XFS, etc):


```
cp /home/user -prv /external/drive
```



Cipherboy

---

### Post by bj218 on 2010-12-20
> **hwychld said:**
> What you want then is to make a copy, not move.  This can be done from Nautilus by going to Places->Home, then go back one directory so that your home directory is shown in the right pane.  Highlight it and right click, choose copy and then paste in media/homeu (or whatever you have mounted where you are trying to place your backup - I assume some sort of removable media).

Or perhaps more direct, from the command line

```

cp -r ~/ /media/homeu

```

If this is something you will want to do routinely, then look into rsync.

Or if you want to eliminate the problem, create a new partition for your home directory.  There are tutorials on the web for this (I have done it but it does require some knowledge of using gparted and partitions, and there is a risk of messing up your install - so make a backup before you do this.  Clonezilla would be a good tool to use for the backup).  With home on its own partition a new install won't affect the home directory.

I have attached 2 screenshots which I hope will help a little!! Screenshot 2 shows the partitioning of my 250GB drive & the second 
screenshot shows homeu beside home I do not understand this? I think there should only be 1 ie homeu which has my data plus the data the was in home? Any way I hope this helps a little.

---

### Post by JKyleOKC on 2010-12-20
> **bj218 said:**
> I think there should only be 1 ie homeu which has my data plus the data the was in home? Any way I hope this helps a little.We must not have made it clear that the system is going to look in /home/bill for the configuration files, not anywhere else. The instructions given you are making a **COPY** of everything in your home directory, so that you can restore it after doing anything that damages the original.

Also, if the directory /media/homeu is NOT an external device such as a thumb drive or an external disk, your copy will NOT survive a destructive update that reformats everything in / and below. To accomplish your goal, the copy absolutely has to be on an external medium, and should be kept reasonably up to date as well.

Creating a separate partition and filesystem for /home, as suggested by several messages above, can do what you want, and it can be on the same drive as / to keep things a bit simpler. If you go this route, then there will be only one home directory, no copy, and it will always be up to date. However doing this after you've already installed and used the system is a bit complicated; it's easiest to do on the initial install. If you do choose this route, you still need to do a full backup copy of your home directory just in case something should go wrong during the process.

Hope this helps! Your goal is a good one; you just need to achieve it in a way that the system understands and will handle properly.

---

