---
title: "separate home partition"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by senorian on 2008-12-04
It is frequently suggested to have a separate home partition; but the following comment seems to say that each OS will have its own entries in the single home partition and the entries may conflict:

You shouldn't share a /home partition with different systems - most applications store their per-user settings in the users /home directory.
If you've got 2 systems sharing the same /home partition then they're both going to try to edit / add config files etc. into the /home directory and clash with the other system. (For example, if you've got KDE 3.5.2 on system A, and KDE 3.4.1 on system B and they share the same /home directory, system A will make its KDE config file, complete with things only applicable to the updated KDE. System B tries to load this file, but finds things which don't work in the old KDE, so it fails).

So should each OS have its own home partition; i.e. OS A will have home partition A,and OS B will have home partition B?
Thanks

---

### Post by handydan918 on 2008-12-04
I think you have a pretty good handle on the situation. It is possible to share /home if done carefully, but at the price of drive space these days, why bother? It is easiest to keep them segregated.

---

### Post by unutbu on 2008-12-04
One way to set up a multi-OS system is for each OS partition to also contain a small home directory. That home directory can have symlinks to a separate data partition, however.

Share data between OSes, but leave OS config files and apps separate.

For example,
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661        3210    20482875   83  Linux
/dev/sda4            3211       38913   286784347+   5  Extended
/dev/sda5            3211        5760    20482843+  83  Linux
/dev/sda6            5761       22209   132126561   83  Linux
/dev/sda7           22210       38658   132126561   83  Linux
/dev/sda8           38659       38913     2048256   82  Linux swap / Solaris

```
sda3 (Gutsy) and sda5 (Intrepid) are two OS partitions.
sda6 is a data partition mounted at /data

sda3 contains a /home/user directory, but it quite small because it contains mostly symlinks:
```

  lrwxrwxrwx  1 user user    20 2008-12-02 17:22 ebooks -> /data/user/ebooks
```

From the user's point of view, files can be read and written to /home/user/ebooks as if it were a regular directory. The files get stored, however, on the data partition.

To create the symlinks you can use the command "ln":
```

ln -s /data/user/ebooks /home/user/ebooks
```

Similarly, sda5 (Intrepid) also has a /home/user directory, 
and it also has symlinks to /data/user.

This way, data can be shared, but config files remain OS-specific.

---

### Post by bumanie on 2008-12-04
What you are saying is correct, however, from personal experience, running 2 ubuntu's at once, sharing /home, I have yet to have an issue. They have been consecutive distro's. The potential for conflict is there and if one decides to share /home, one needs to appreciate that conflicts may occur, but as said, I've not had an issue when I have done this previously. You could do a backup of your present installation and try it out. If something goes wrong later, reinstall the backup.

---

### Post by senorian on 2008-12-05
Many thanks to all three.
Unutbu:
My ignorance of cli(and linux in general) let's me wonder if items that are (apparently) posted to the user's home directory are automatically segregated as to those which are symlinked to the data partition and those which must not be sent there.Your statement:

From the user's point of view, files can be read and written to /home/user/ebooks as if it were a regular directory. The files get stored, however, on the data partition.

This seems to assert that the process is automatic. That is, I do not have to recognize which is which?
Many thanks

---

### Post by Paqman on 2008-12-05
> **senorian said:**
> 
If you've got 2 systems sharing the same /home partition then they're both going to try to edit / add config files etc. into the /home directory and clash with the other system.

No, that would only happen if you were also sharing a single username and UID. Config files are stored in /home/*username* not /home, so if you have different user accounts on the different OSes, they will never clash.

I've had a single /home partition shared between different distros for years, and i've never had an problems.

---

### Post by unutbu on 2008-12-05
Since a number of users have used a common home partition with no problems, you may want to try that. I recently set up a multi-OS system using the symlink idea described above, and it works just fine. However, I might be fighting a theoretical problem which doesn't arise often in actuality. I just want to make that clear.

If you'd like to learn more about symlinks before deciding, then I think the best way to understand symlinks is to make a symlink and then play around a bit with it.

There is a way to make symlinks using nautilus: Here are instructions:
[http://linux.about.com/library/gnome/blgnome6n6l.htm](http://linux.about.com/library/gnome/blgnome6n6l.htm)


The syntax for making symlinks using the CLI is
```

ln -s TARGET SOURCE
```

TARGET is the path that already exists. 
SOURCE is the symlink you wish to make.
The symlink will point from SOURCE to TARGET.

For the full story on symlinks, type
```

man symlink
```

---

### Post by senorian on 2008-12-07
Thanks Paqman for pointing out the necessity of having a different user name for each OS if they are sharing a common home partition.
Thanks unutbu for the info re symlinks.
I will check out  "man symlink"

---

