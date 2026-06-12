---
title: "permission for data partition"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by beew on 2011-01-25
Hi,

I made a multi-system with several Linux OS's (right now only Ubuntu 10.10 and Fedora 14). I created a separate partition for shared data on the same drive. Now it seems that I need root privilege to create folder or move things to or from this partition. Since I am planning to use it to store media files and documents it is rather cumbersome. I am wondering if there is a way to change its permission that I can access its content like I would in the home directory? It may be a bit different for Fedora or other OS's I plan to install in future, but what should I do in Ubuntu?

Thanks.

---

### Post by sikander3786 on 2011-01-25
You need to chown your mount folder.

```
sudo chown <username>:<username> /place/to/mount
```

If you want to mount that data partition in /etc/fstab, this might help.

[http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html](http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html)

---

### Post by beew on 2011-01-25
What should I put in /place/to/mount?

It just mounts automatically when I go to system > places and click the icon.

Thanks.

---

### Post by Morbius1 on 2011-01-25
Is there a religious or philosophical reason why you didn't format the data partition in NTFS?

Here's the problem. Let's say you change ownership of the mounted partition to "bart" on Ubuntu: sudo chown bart /media/Data. Now bart can add a file to the data partition.

Now you reboot into Fedora and let's say your username in Fedora is also bart. The problem is "bart" in Fedora is not the same as "bart" in Ubuntu because their uid's are different. Bart in Ubuntu has a uid = 1000 whereas bart in Fedora is 500 ( I think - it's been a while ) and bart in Suse may be something else. 

You could leave the ownership as root but change permissions to 777: sudo chmod 0777 /media/Data. Then everyone in every OS can add to the partition. 

But there's a bigger problem ahead. When bart on ubuntu saves a file to the data partition it will save as owner:group = bart:bart and with permissions of 644.  bart can read and write to the file in ubuntu but everyone else in  ubuntu can only read. Since bart on Fedora has a different uid he can read the file but cannot edit the file.

You've got some options at this point. You could change the uid's of bart in every system to the same value so that bart = bart. You could change the umask in bashrc in every OS to 000 instead of 022 so that every file saved saves with permissions of 666 - which is the sign of the devil and is frowned upon. There are more complex solutions as well.

Or you could format the partition as NTFS. Then every OS will mount the partition thinking they own it - sort of like a usb stick - only internal.

---

### Post by beew on 2011-01-25
Morbius1

That is very informative. I will wait a while and if there is no better suggestion I would reformat the partition to ntfs. But then I may try a more complicated solution without ntfs.  Though I am not religious, I try not to use ntfs  because there seems to be no good reason why I would need to make a partition using a Windows file system while I have no Windows (and I am not planning to install it here)!

---

### Post by beew on 2011-01-26
So is there any other suggestion beside formatting the data partition in ntfs? It is practical but not very elegant as everything is Linux in my dual boot system and it seems odd to have to use a "windows solution" for a Linux problem.

Thanks.

---

### Post by JKyleOKC on 2011-01-26
I believe there's options available for the fstab entry of that disk/partition to always mount it as owned by uid xxx and gid xxx where the "xxx"s are a specific uid/gid. Thus if bart on one system is uid=1000 and on another is uid=500, the first system's fstab could mount for uid=1000 and the second as uid=500.

This, however, might work only for one user and not for a group of users. I'm not sure whether writing a file to such an area would automagically take the owner and group from the mount data, or from the logged-in user, if they differ...

At any rate it might be worth looking into; it's a question that comes up fairly often and will probably become even more frequent as more entire families convert to *nix use!

EDIT: It may also be worthwhile to look more deeply into the usage of "group" permissions rather than setting permissions to 777 or umask to 000. The whole purpose of the group permission is to allow different users, with unique user ID, to have access to some files but not allow everyone that same access...

---

### Post by Morbius1 on 2011-01-26
I'm fairly certain the uid and gid in fstab are only used for Windows filesystem not linux filesystems.

If you want an old school method the general procedure is something like this - it's been a very long time since I've done this but:
(1) Create a new group - sharedata with a group id that is the same for every OS you have making sure it doesn't conflict with an existing gid.
(2) Make the default umask for each user on each OS = 002
(3) Change the group of the shared directory to sharedata
(4) Change permissions of the shared directory to allow all members of the sharedata group to have access and so that all new files / directories will inherit the sharedata group:
```
sudo chmod 2775 /media/Data
```Or you can use bindfs: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

The implementation of bindfs may be different for each OS but it will make every user on every OS think he owns the partition and it's contents. Essentially making a Linux partition appear to be an NTFS partition.

---

