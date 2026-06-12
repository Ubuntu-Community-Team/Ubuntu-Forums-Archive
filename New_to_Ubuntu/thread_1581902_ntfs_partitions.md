---
title: "ntfs partitions"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by rre12 on 2010-09-25
Currently I am still using Windows and I have a storage partition where I put all of my music, movies, etc. I am wondering once I start using kubuntu, can I freely navigate my storage partition as well as read/write new files to it within kubuntu? Or do I need to create another partition for storage with the ext2 or ext3 file system?

---

### Post by Jitse on 2010-09-25
You don't have to create a different partition. Kubuntu can navigate, read from and write to ntfs filesystems without any problems. Just make sure you don't remove any important Windows files while you're using Kubuntu, though.

---

### Post by tonsil on 2010-09-25
You can use your ntfs storage partition just fine under Ubuntu/Kubuntu. You will just have to mount it to be able to use it.

---

### Post by rre12 on 2010-09-26
Since I am planning to use a big NFTS partition(250 Gb) to share between Windows and Kubuntu, is there a need for me to create a separate partition for my /home? I have not installed Kubuntu yet so I have no idea what exactly goes inside the /home directory. I also have a 2 TB internal HD, so space is not an issue.

---

### Post by adit on 2010-09-26
```
what exactly goes inside the /home directory
```
You said that you are going to store all your documents in a separate ntfs partition.  Then there is no need to create a separate /home partition for kubuntu.  The /home partition contains user specific settings for various applications you use.  This /home partition will occupy only a few megabytes

---

### Post by Paqman on 2010-09-26
/home contains all your settings for your apps, and has pre-made folders for photos, videos, documents, etc. But you don't have to store your data in them if you don't want to.

The advantage of creating a separate /home partition is that you can do a full reinstall without wiping your user accounts and all the settings. Once you finish the install the system is totally ready to go. It's a pretty popular way to set up your system, but by no means compulsory, especially since you can always do an in place upgrade between versions without having to do a reinstall anyway.

---

### Post by srs5694 on 2010-09-26
I'd like to clarify what Paqman and adit have written: *User home directories* contain the settings for individual users; the /home directory *contains user home directories.* For instance, my own user home directory on most of my computers is /home/rodsmith; the /home directory doesn't belong to the user rodsmith, but /home/rodsmith does. Putting /home on a separate partition is a common practice, but putting individual users' home directories (such as /home/rodsmith) on separate partitions is less common (but perfectly legal).

Many Ubuntu users are a bit imprecise when describing this issue, I suspect because so many Ubuntu computers have just one user, so /home contains just one subdirectory. Ubuntu is, however, a multi-user OS; a single computer can support a huge number of users. Even a home computer might have a handful, for different family members; or you might want to create multiple accounts or home directories for yourself, so you can use one or more for experimentation or to hold different settings for different distributions or versions of Ubuntu. In any of these cases, if /home is on a separate partition, it will hold all the ordinary users' home directories (unless you set up an account to have a directory in an odd location or put a particular user's home directory on its own partition).

As to the main question, the benefit of putting /home on a separate partition depends on a number of factors, the biggest probably being how much user data will be Linux-specific. That is, if everything but configuration files and perhaps a handful of small files will be shared between OSes, there's little benefit to putting /home on its own partition; that partition will have users' home directories with just a few files. OTOH, if you plan to store much Linux-specific data, having a separate /home partition can simplify certain types of re-installations and upgrades, since you can wipe the root (/) partition without affecting the user data in /home.

---

### Post by rre12 on 2010-09-26
Thanks for the helpful information. I just installed Kubuntu, but have a problem. I'll make a new thread about it.

---

