---
title: "Got 2 home folders"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by donniezazen on 2009-04-02
Hi all,

I just installed Jaunty Beta. I have a separate home partition. While installing i changed the user login name. Now i have got 2 home folder. Probably one if home folder and the old folder has all my data. How can i move my data from the old folder to new home folder? I am not able to copy as their is no space.

Thanks,
SK

---

### Post by rhcm123 on 2009-04-02
> **soham_1207 said:**
> Hi all,

I just installed Jaunty Beta. I have a separate home partition. While installing i changed the user login name. Now i have got 2 home folder. Probably one if home folder and the old folder has all my data. How can i move my data from the old folder to new home folder? I am not able to copy as their is no space.

Thanks,
SK

You can't really "move" the data as there is no space on your partiton.
Why are your home folders on different partitons?

---

### Post by taurus on 2009-04-02
You could have used the same $HOME when you installed jaunty.  Then, you don't have two $HOME's, one old and one new.  However, you can _move_ (not copy since sounds like you are running low on disk space) all the data from old $HOME to new $HOME.

---

### Post by donniezazen on 2009-04-02
> **rhcm123 said:**
> You can't really "move" the data as there is no space on your partiton.
Why are your home folders on different partitons?

No my home folders are in same partition. Instead of one home folder i have got 2 home folders. When i open HOME i have 4 folders 1. Guest 2.lost+found 3.New home folder 4.old home folder.  All my settings are new. May be because i did not import settings while installing. I do not want old settings i just want to move back my data to new home folder and delete old one.

Thanks.

---

### Post by rhcm123 on 2009-04-02
To copy the data in your old folder to a folder called "olddata" in your new home directory, run these commands

```
sudo mv -r /homepartition/oldfolder /homepartition/newfolder/olddata
```
```
sudo chown -R username:usergroup /homepartition/newfolder
```

Enjoy!

Edit: Also, be sure to change these examples to the proper directory/usernames. These aren't straight-away cut and paste commands.

---

### Post by kpatz on 2009-04-02
Just open both folders in Nautilus (File Browser) and then drag the files from one folder to the other.

When you're in the same partition, drag moves, when in different partitions (mounts), drag copies.

(EDIT: You'll have to change ownership of the files as rhcm123 explained above).

---

### Post by donniezazen on 2009-04-02
> **rhcm123 said:**
> To copy the data in your old folder to a folder called "olddata" in your new home directory, run these commands

```
sudo mv -r /homepartition/oldfolder /homepartition/newfolder/olddata
```
```
sudo chown -R username:usergroup /homepartition/newfolder
```

Enjoy!

Edit: Also, be sure to change these examples to the proper directory/usernames. These aren't straight-away cut and paste commands.

Thanks. I just cut pasted my data from old folder to new folder. And deleted old home folder using nautilus. What is this second command for? I am yet not sure if my new home folder is using all the space of the partition.


SK

---

### Post by rhcm123 on 2009-04-02
> **soham_1207 said:**
>  What is this second command for?
the second command changes ownership of the files to you. If the ownership is not changed, it will be left owned by the old user, and, because of the linux permissions system, you will probably not be able to run the files.

---

### Post by donniezazen on 2009-04-02
> **rhcm123 said:**
> the second command changes ownership of the files to you. If the ownership is not changed, it will be left owned by the old user, and, because of the linux permissions system, you will probably not be able to run the files.

I am able to use all my files. But its showing 38.5GB used and 23.5 free. And Gparted is showing the total disk space is 78GB. Where is the remaining disk space and how can i get it back?

Thanks.

---

### Post by rhcm123 on 2009-04-05
> **soham_1207 said:**
> I am able to use all my files. But its showing 38.5GB used and 23.5 free. And Gparted is showing the total disk space is 78GB. Where is the remaining disk space and how can i get it back?

Thanks.

how many partitions are on this drive? Sorry about the delay, this thread was lost in the flood, so to speak.

---

### Post by donniezazen on 2009-04-05
> **rhcm123 said:**
> how many partitions are on this drive? Sorry about the delay, this thread was lost in the flood, so to speak.

Thanks for the reply. I already formatted my laptop to try new ext4 file system and all new setting.

Thanks,
SK

---

### Post by rhcm123 on 2009-04-05
> **soham_1207 said:**
> Thanks for the reply. I already formatted my laptop to try new ext4 file system and all new setting.

Thanks,
SK

how is ext4, out of curiosity? Better on sudden shutdowns?

---

### Post by donniezazen on 2009-04-05
> **rhcm123 said:**
> how is ext4, out of curiosity? Better on sudden shutdowns?

I am not a tech guy but as a general user i can say that the file transfer is amazingly fast. I don't know what else to observe.

What do you mean by 'Better on sudden shutdowns'?

I want to mark this tread solved but couldn't see the tab in thread tools. Can you help?

SK.

---

### Post by rhcm123 on 2009-04-05
> **soham_1207 said:**
> 
What do you mean by 'Better on sudden shutdowns'?


ext3 has a bad habit of getting badly corrupted on a crash due to journaling errors. Not as bad as ext2 or other filesystems (cough ntfs cough), but still pretty bad - im working on fixing that in another thread here :). 

> **soham_1207 said:**
> 
I want to mark this tread solved but couldn't see the tab in thread tools. Can you help?
Actually, the forums removed the "SOVLED:" tag a few weeks ago due to some problems. The "thank user for this post" feature went with it. I don't know the exact reasoning.

---

