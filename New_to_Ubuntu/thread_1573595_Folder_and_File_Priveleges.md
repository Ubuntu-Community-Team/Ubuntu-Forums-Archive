---
title: "Folder and File Priveleges"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Steveplanetary on 2010-09-12
[SIZE=2]I've installed Ubuntu a number of times in the last two weeks or so, since I've abandoned MS Windows, but this time I noticed that root has all the privileges over every folder and file.  This is even true of two folders I created as subdirectories of /usr at the time of installing the system.  These subdirectories are /usr/local1 and /usr/local2, which I created to be the mount points of other Ext4 partitions on the same hard drive.  Maybe I don't understand what it means to be a 'mount point', but I thought of it as a wormhole into the other partition.  But since root has all the privileges I can't create folders and move files into and out of the other partitions.  And since root has all the privileges, I can't change that.  What am I to do?

Thanks in advance.
[/SIZE]

---

### Post by BugBuster on 2010-09-13
I think you should consider mounting the partitions under /mnt or /media as these are more conventional and go well with the linux file hierarchy.

Also in linux, "root" user is the 'almighty'!! Hence is it quite obvious that it has all the permissions.
What you can do is after mounting your ext2/3/4 partitions you can change the permissions using the chown & chmod utilities.

---

### Post by Bucky Ball on 2010-09-13
Simply, EVERYTHING in Ubuntu is a Directory. A mount point is simply a directory. Create, for instance:

/media/local1

You then mount the appropriate partition into the DIRECTORY (or mount point if you like!) /media/local1.

This can be done very quickly on the fly or you can mount at boot by adding a line to /etc/fstab (in 8.04 - this might be different in other versions). Remember, anyt line you add in fstab MUST refer to an existing mount point (directory). Consequently, you can mount local partitions this way OR network partitions from other machines. Just remember; you MOUNT your partition into a DIRECTORY.

---

### Post by 3rdalbum on 2010-09-13
Open the file browser as root:

gksudo nautilus

And right-click the directory you want to change, go to Properties and then change the owner to yourself.

Only do this where absolutely necessary.

---

