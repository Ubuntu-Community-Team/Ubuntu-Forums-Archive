---
title: "Separate partition for home?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Muffinabus on 2009-02-10
I'm growing bored with my perfectly working Ubuntu install (lol) and think I'm going to wipe this and try Kubuntu for a little while, learn something new, and have some more fun figuring out how to fix new problems!  

So to make things a little more advanced, I wanted to setup a separate partition for /home when I reformat this drive, but I'm unsure on the specifics on how big each partition should be when I do this.  I will be using the entire 120GB hard drive for the install.  Here's the output of my current fdisk -l:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33eb33ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

```

So how big should my /home partition be when I create it? (I realize this can vary given user preference and whatnot, but some recommendations would be nice)  Anything else I should know about before I proceed with the reformat/partitioning?

EDIT:  And yes I do know that I can boot KDE by installing the kubuntu-desktop package, but I've noticed some problems after doing this and feel I would get a better experience just installing KDE by itself.

---

### Post by philinux on 2009-02-10
I've got a 12 gig /, 2 gig /swap, and the rest is /home on a 250gig HD

---

### Post by TCSnyder on 2009-02-10
i got 
8 gb /
81 gb /home
1 gb /swap

---

### Post by tarps87 on 2009-02-10
I'm using 10GB for the / partition and the rest for /home. I think my netbook looks like this:
10GB Kubuntu
20GB /home
10GB Fedora
20GB /home
10GB Slackware
20GB /home
78GB(ish) share
2GB Swap
(A bit of a mess :))
While trying each distro I had some problems with sharing the same home so I setup a separate one for each, hence the mess. Anyway the I have not had any problems with the 10GB / partition.
Your best bet would be looking at the size of you /home directory and the workout what the rest uses and you should have some idea of size. The main use of the space will be the /var directory, this contains the download software installs and updates.
```
sudo apt-get autoclean
```
This will sort out the unneeded files

---

### Post by Therion on 2009-02-10
/Home is whatever is left after about 12-15GB for / and a 2GB /swap.

---

### Post by unutbu on 2009-02-10
Type
```

df -h /
```

You will see something like:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             115G   60G   54G  53% /

```
Note the amount of space used (e.g. 60GB)

Next type
```

du -sh /home
```

You might see something like
```

50G	/home
```

This shows your /home directory taking up 50GB.

So the difference between the total space used (60GB) and the space used by /home (50GB) is the minimum size you would need for your root partition after you've created a separate /home partition. (Most Linux OSs fit in 10GB, but if you like to install lots of extra packages, you should allow for room to grow as well.)

Since you are repartitioning, now would be the perfect time to set up some extra partitions. Here are some ideas:
[list]
[*]create an extra partition to install a second OS. Upgrading to the next Ubuntu (or other) distro is a risky process when you only have one OS. Having a second partition allows you to install the second distro without giving up your original distro first. Then you can check it out, play with it and then decide if it works for you.
[*]create a backup partition. Make it the same size as your /home partition. This allows you to backup your /home partition with one simple command:
```

sudo rsync -a --delete /home/ /backup/
```
[/list]

PS. Here are two guides on creating a separate home partition:
I've seen a lot of people use this one with success:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This one uses rsync, which I think is a good idea. It looks good, but I haven't studied it carefully.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Muffinabus on 2009-02-10
Cool, thanks for the suggestions and tips guys (:

---

