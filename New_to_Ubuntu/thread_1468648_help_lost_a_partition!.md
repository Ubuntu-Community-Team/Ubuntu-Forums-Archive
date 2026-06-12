---
title: "help lost a partition!"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by natman on 2010-05-01
Hi,
I am after doing a fresh install of 10.04, when i was manually giving the partition table, i asked for a 43GB fat32 as well as / and /home and /swap, now when i go to computer i dont see it anywhere? but its visible in windows. I presume i need to mount it? Can someone tell me how?
Here is the output:
> natman@natman-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System                         
/dev/sda1               1         192     1536000   27  Unknown                        
Partition 1 does not end on cylinder boundary.                                         
/dev/sda2   *         192       19628   156122112    7  HPFS/NTFS                      
/dev/sda3           19628       38914   154910721    5  Extended                       
/dev/sda5           19628       21164    12332032   83  Linux                          
/dev/sda6           21164       33321    97654784   83  Linux                          
/dev/sda7           33321       38549    41992192    b  W95 FAT32
/dev/sda8           38549       38914     2928640   82  Linux swap / Solaris
natman@natman-laptop:~$ 


---

### Post by -humanaut- on 2010-05-01
You need to setup the mount point in fstab sudo nano /etc/fstab if you wrote **_new_** partitions and had windows on that partition you overwrite it.

---

### Post by srs5694 on 2010-05-01
Try editing /etc/fstab, and add an entry like this:

```

/dev/sda7   /home/yourname/shared   vfat    uid=1000,gid=100    0 0

```

You should change /home/yourname/shared to an empty directory in some convenient location. (The idea in this example was to put the partition in a subdirectory of your home directory (/home/yourname), but you could put it somewhere else, if you like.) You must create this empty directory (known technically as a *mount point*) before you go further. The "uid=1000,gid=100" entries set two filesystem mount options that give ownership of all files to whoever has user ID (UID) 1000 (normally the first user created), with group ownership going to group ID (GID) 100 (normally "users"). You can change these options or add others, as you see fit; type "man mount" and search for vfat options to learn about them all.

When your mount point exists and you've made the /etc/fstab changes, type "sudo mount -a". The files in the directory should now be available at your mount point, and will be available there whenever you reboot.

---

### Post by natman on 2010-05-01
The problem is i have no idea how to do that.

---

### Post by -humanaut- on 2010-05-01
> **srs5694 said:**
> Try editing /etc/fstab, and add an entry like this:

```

[B][U]/dev/sda7   /home/yourname/shared   vfat    uid=1000,gid=100    0 0
[/U][/B]
```

You should change /home/yourname/shared to an empty directory in some convenient location. (The idea in this example was to put the partition in a subdirectory of your home directory (/home/yourname), but you could put it somewhere else, if you like.) You must create this empty directory (known technically as a *mount point*) before you go further. The "uid=1000,gid=100" entries set two filesystem mount options that give ownership of all files to whoever has user ID (UID) 1000 (normally the first user created), with group ownership going to group ID (GID) 100 (normally "users"). You can change these options or add others, as you see fit; type "man mount" and search for vfat options to learn about them all.

When your mount point exists and you've made the /etc/fstab changes, type "sudo mount -a". The files in the directory should now be available at your mount point, and will be available there whenever you reboot.

Copy the bold and underlined part in to your /etc/fstab file. its easy open a terminal and type sudo nano /etc/fstab those are great instructions. honestly.

---

### Post by srs5694 on 2010-05-01
There are also lots of GUI text editors that will do the job. For instance, "gksudo gedit /etc/fstab" will probably work. (If gedit doesn't work, substitute nedit, xedit, or emacs, to name just a few.)

---

