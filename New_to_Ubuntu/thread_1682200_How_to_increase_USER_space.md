---
title: "How to increase USER space?"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by jokumar on 2011-02-05
Hi, I am newbie to Ubuntu but i am running it for the last 3 months, I have installed Ubuntu 10.10 inside win 7, Recently i have D/L Kile (LaTex) software which is around 1 gb. n since then my USER space has become "O", I do no where n how to increase the Space as i have installed Ubuntu on 80gb. HD, n my win. 7 runs on 320 gb. SATA HD.
I am unable to install updates due "0" space avlble. in USER, i have attached Gparted screen shot
Thx. in advance

---

### Post by Stephen Morgan on 2011-02-05
That's a wubi install which often seems to have this problem. It also doesn't maintain reserved system blocks to allow root functions while you're low on disk space.   ```
sudo apt-get clean
```  should remove at least some old files, at least enough to allow a bit of updating.  ```
sudo apt-get autoremove
```  will also remove unnecessary packages, and should normally free up a little bit of space.  Looks like there's some space in /host too, if you can move some user files out of your userspace.

---

### Post by jokumar on 2011-02-06
I have done as per the instrn.it did`nt help,

---

### Post by bcbc on 2011-02-06
You can probably customize the instructions [here]("http://ubuntuforums.org/showthread.php?t=1625371") to create a bigger root.disk while booted from a live CD (if your current install is too full to handle it). Either create a new virtual disk for and copy the entire root.disk to it, or create a separate home.disk and move your home to it.

Also look in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide") - there is a script to create a separate home.disk. Between the two you should be able to figure out something. (consider making a backup of your current root.disk before making these sorts of changes).

---

### Post by jokumar on 2011-02-08
Is there any other option avlbl.? b`cause i am unfamiliar with commands n so on.

---

### Post by bcbc on 2011-02-08
I don't know what to suggest. If your Wubi install isn't functioning normally due to the root.disk being full, then you have limited options. But if you can download and run the scripts to resize or create a separate /home virtual disk - that's an option.
Another option is to backup important data and reinstall.

It's also possible to migrate a wubi install to partition as well. I've released a new version of the [script]("http://ubuntuforums.org/showthread.php?t=1519354") to allow this to run from a live CD (just using the root.disk). That's another option, but you'd have to create the partitions first.

---

### Post by vanadium on 2011-02-08
You probably should move all your user data out of your wubi partition.

You could store all your folders such as Documents, Pictures, Videos, Downloads etc. on your Windows partition. Then replace these folders with symbolic links to their new locations.

-> Your have again plenty of room for the system on your wubi partition
-> You can access your Documents, Pictures, Videos as before: from a users perspective, they stay on the same location
-> You can access the same Documents, Pictures, Videos ... from your Windows partition.

Feel free to ask more hands on guidance if needed.

---

