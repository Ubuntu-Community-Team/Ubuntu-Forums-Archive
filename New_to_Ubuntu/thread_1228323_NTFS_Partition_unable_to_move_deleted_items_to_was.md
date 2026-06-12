---
title: "NTFS Partition unable to move deleted items to wastebasket"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Dangger on 2009-07-31
Hi all,

This is my first post and also my first experience with Ubuntu (first successful experience). I am completely thrilled by the performance, resources and community. I have a question though. 

I have a problem with my NTFS partition. This is the way I have organized my disk:

partition 1: windows
partition 2: Documents
partition 3: Ubuntu

So I have everything on Documents and it is a NTFS partition. Now Ubuntu can access it, I've already created a mountpoint for it and everything looks swell, except... 

Every time I erase something on the NTFS partition it says exactly the following:

> "Cannot move file to the Deleted Items folder, do you want to delete permanently?
The file "example" cannot be moved to the wastebasket.Although I rarely rescue items from the wastebasket I'm afraid that I could accidentally delete my files without being able to rescue them. 

I am using Ubuntu 9.04 and any help will be greatly appreciated.

---

### Post by kansasnoob on 2009-07-31
Try installing ntfsprogs from Synaptic.

More about ntfsprogs here:

[http://gnuwin32.sourceforge.net/packages/ntfsprogs.htm](http://gnuwin32.sourceforge.net/packages/ntfsprogs.htm)

---

### Post by drs305 on 2009-07-31
The reason for the message is that the folder is mounted and owned by root. In linux, non-linux filesystems such as fat and ntfs have their permissions set at the time of mounting and can't be changed. To get the behavior you desire you have to make yourself the owner of the mountpoint at the time of mounting.

You can either use this command (this assumes you are user 1000 with a mount point of "/media/Documents", change sdXX to the correct designation):
```

sudo mount /dev/sdXX -t ntfs /media/Documents -o uid=1000

```
or place an entry in fstab that mounts the partition with you as the owner.

If you do this, the first time you delete a file or folder a trash bin called .Trash-1000 will be created and deletions will go there until you empty it. (in the .Trash-1000/files folder, to be precise).

---

### Post by Dangger on 2009-07-31
Thanks, 

> **drs305 said:**
> The reason for the message is that the folder is mounted and owned by root. In linux, non-linux filesystems such as fat and ntfs have their permissions set at the time of mounting and can't be changed. To get the behavior you desire you have to make yourself the owner of the mountpoint at the time of mounting.

You can either use this command (this assumes you are user 1000 with a mount point of "/media/Documents", change sdXX to the correct designation):
```

sudo mount /dev/sdXX -t ntfs /media/Documents -o uid=1000

```
or place an entry in fstab that mounts the partition with you as the owner.

If you do this, the first time you delete a file or folder a trash bin called .Trash-1000 will be created and deletions will go there until you empty it. (in the .Trash-1000/files folder, to be precise).



I installed ntfs-config, that created a file with some info like:

> /dev/sda3 /media/Documents ntfs-3g defaults,locale=en_GB.UTF-8 0 0

How exactly should I change it? :S, sorry for my inexperience.

---

### Post by drs305 on 2009-07-31
> **Dangger said:**
> 
I installed ntfs-config, that created a file with some info like:

How exactly should I change it? :S, sorry for my inexperience.

Just amend the line. Open fstab with:
```
gksudo gedit /etc/fstab
```
> 
/dev/sda3 /media/Documents ntfs-3g defaults,[COLOR="DarkRed"]**uid=1000**[/COLOR],user,locale=en_GB.UTF-8 0 0 

 You can check to make sure you are user 1000 by running the command "id".

And welcome to the Ubuntu forums. We were all beginners once. ;-)

Added: Once you have made the entry, you can unmount it and remount it with the following command. If nothing happens (no error messages), it mounted with you as the owner:
```

sudo umount /dev/sda3
sudo mount /dev/sda3

```

I also added "user" to the options so a user, and not just root, could mount the partition.

---

### Post by Dangger on 2009-07-31
Ah Thanks! It worked!! I was user 1001. Would you happen to know if my timestamps will be preserved?

---

### Post by drs305 on 2009-07-31
> **Dangger said:**
> Ah Thanks! It worked!! I was user 1001. Would you happen to know if my timestamps will be preserved?

As far as I know they will.

Glad it's working for you.

---

