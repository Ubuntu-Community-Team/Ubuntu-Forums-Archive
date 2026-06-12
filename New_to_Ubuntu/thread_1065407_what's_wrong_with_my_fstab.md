---
title: "what's wrong with my fstab?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by lapubell on 2009-02-09
I'm trying to add a new partition to my fstab and it's not giving me user rw permissions!  I'm not running ubuntu, but i'm pretty sure that this is linux wide, and this is the best support forum ever.

Here's the line that i added to /etc/fstab:

/dev/sda4    /media/stuff    ext3     exec,rw,user,auto    0      0

the device is correct, the mountpoint is there, the mount point is owned by me but when it mounts, i have read only permissions...

arg!

---

### Post by beno1990 on 2009-02-09
```

ls -l /media

```

Will show the permissions of the mount point.

After this, if the permissions settings are undesirable, you might want to do the following:

```

sudo chgrp <yourusername> /media/stuff
sudo chmod g=rwx /media/stuff

```

Tell me if this works for you.

---

### Post by lapubell on 2009-02-09
well, no good.

/media/stuff is owned by me and it's group is me also.

> 
lapubell@klaptop:/media$ ls -l /media
total 16
drwxr-xr-x 2 root     root     4096 2008-09-01 15:00 cdiso
drwxr-xr-x 2 root     root     4096 2008-08-29 02:04 cdrom
drwxr-xr-x 2 lapubell lapubell 4096 2008-08-31 15:06 lapubell.com
drwxr-xr-x 2 lapubell lapubell 4096 2009-02-09 18:05 stuff


any other ideas?

---

### Post by beno1990 on 2009-02-09
Ok, if you go into users and groups from the administration menu, double-click on your username and go to the advanced tab, note your user ID number. This will probably be 1000 if your user account is the default which Ubuntu creates on installation.

Assuming it's 1000, you can try changing your fstab line to this:

```

/dev/sda4 /media/stuff ext3 exec,rw,user,auto,uid=1000,gid=1000 0 0

```

---

### Post by egalvan on 2009-02-09
> **lapubell said:**
> I'm trying to add a new partition to fstab, it's not giving me user rw permissions!  I'm not running ubuntu, i'm pretty sure that this is linux wide, this is the best support forum ever.

Here's the line that i added to /etc/fstab:

[B]/dev/sda4    /media/stuff    ext3     exec,rw,user,auto    0      0
[/B]
the device is correct, the mountpoint is there, the mount point is owned by me but when it mounts, i have read only permissions...


try:

**/dev/sda4 /media/stuff ext3 defaults,user,exec,uid=1000,gid=100,umask=000 0 0**

---

### Post by spiderbatdad on 2009-02-09
/dev/sda4 /media/stuff ext3 defaults 0 0

---

### Post by lapubell on 2009-02-09
well, i'm not running ubuntu.  I'm running a debian derived disto called sidux.  my uid is 1000 so i tried those options, but got this lovely message...

> 
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and dmesg | tail gives me this tidbit...

> 
lapubell@klaptop:/media$ dmesg | tail
EXT3 FS on sda4, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda4, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda4, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
EXT3-fs: Unrecognized mount option "uid=1000" or missing value
EXT3-fs: Unrecognized mount option "uid=1000" or missing value


so, thanks but still arg...

---

### Post by lapubell on 2009-02-09
ok so i don't know exactly what the reason behind this is, but i can't write into the main dir where it's mounted.  i can write to a directory that i own inside that dir (for example, /media/stuff/junk) so this will work for me for now.

thanks again for all the help!

---

### Post by egalvan on 2009-02-13
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

[http://news.softpedia.com/news/How-To-use-your-partitions-in-Linux-33260.shtml](http://news.softpedia.com/news/How-To-use-your-partitions-in-Linux-33260.shtml)

---

### Post by Alterax on 2009-02-13
I'll run the risk of sounding like an idiot here, but can you write files to the drive using sudo?  The bit about the wrong fstype or superblock makes me wonder...was the drive formatted with ext3 to begin with?

> **lapubell said:**
> well, i'm not running ubuntu.  I'm running a debian derived disto called sidux.  my uid is 1000 so i tried those options, but got this lovely message...



and dmesg | tail gives me this tidbit...



so, thanks but still arg...

---

