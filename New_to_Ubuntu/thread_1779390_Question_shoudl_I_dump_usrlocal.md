---
title: "Question shoudl I dump /usr/local?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by iconoclast hero on 2011-06-10
I don't want to wade into the argument about whether or not it is wise  to partition, but I just dumped the Natty partition that I had and I'm  trying to optimize my /home partition.  For some reason, I have a  separate partition for /usr/local.  I am fairly certain that I didn't  put it there and /etc/fstab says of it 
```
# /usr/local was on /dev/sda6 during installation
```I was  thinking I might be able to use that for both /home and /usr/local but  I'm finding that is probably not going to work.  That said, I have no  idea where it came from and I rarely compile from source (I think I've  done it twice or three times, with great difficulty, and with ruby  scripts).  Would it make sense just to reformat it to ext4 (as it is  now) to remove the /usr/local data and then to copy my /home info to  that and call it a day?  The partition is just about 21 GiB according to  gparted.

```
Disk /dev/sda: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d64e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54262   435853953   83  Linux
/dev/sda2           54262       60802    52531201    5  Extended
/dev/sda5           60667       60802     1079296   83  Linux
/dev/sda6           57634       58048     3333456   82  Linux swap / Solaris

Partition table entries are not in disk order

```(There are also 25 GiB unallocated that are going back to /dev/sda1 as soon as I get around to booting from disc).

---

### Post by Joe of loath on 2011-06-10
/dev/sda6 is your swap partition.

---

### Post by psusi on 2011-06-10
You must have chosen to create it when you installed.  Are there any files in there?  If not, then you certainly can reuse it for /home if you want.  Just copy everything from /home to /usr/local, then edit your /etc/fstab to mount it in /home instead of /usr/local.  Reboot and make sure it is working correctly, and if it is, boot the livecd, mount the / partition, and delete everything in /home ( since you now have a copy of it on the other partition ).

---

### Post by iconoclast hero on 2011-06-14
> **psusi said:**
> You must have chosen to create it when you installed.  Are there any files in there?  If not, then you certainly can reuse it for /home if you want.  Just copy everything from /home to /usr/local, then edit your /etc/fstab to mount it in /home instead of /usr/local.  Reboot and make sure it is working correctly, and if it is, boot the livecd, mount the / partition, and delete everything in /home ( since you now have a copy of it on the other partition ).

I don't think I actually selected it during installation (or at least I don't remember doing so).  For some  reason it seems that the installer partitioned it automatically.  

There was stuff in it, but what I'm realizing is that if I have both a /usr/local and a /home as separate partitions than things like rubyripper will be preserved if something happens to /dev/sda1 or I reinstall when 12.04LTS comes out.  What I was wondering is if there is some way to use the same partition for both /home and /usr/local...

I am going to partition and mount a /home directory of about 48 gb...  If there is a way to put the /usr/local on that partition I would appreciate how to mount it via fstab (my attempts have been for naught)...otherwise, what is a good size for /usr/local/ considering I don't really compile much...  All I've done so far is rubyripper and e4rat.  I think ubuntu defaulted to 2gb with the standard 5% holdback.

Thanks

---

### Post by Joe of loath on 2011-06-14
What's your output for mount and df -h, first up?

---

### Post by iconoclast hero on 2011-06-14
> **Joe of loath said:**
> What's your output for mount and df -h, first up?

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/icon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=icon)

```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             410G  155G  255G  38% /
none                  1.5G  320K  1.5G   1% /dev
none                  1.5G  2.7M  1.5G   1% /dev/shm
none                  1.5G  220K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda6              48G  180M   45G   1% /home2

```

---

### Post by Joe of loath on 2011-06-14
Well, you don't have a separate mount point for /usr/local, so it's currently on /dev/sda1 with the rest of /, as it should be :p

---

### Post by iconoclast hero on 2011-06-14
> **Joe of loath said:**
> Well, you don't have a separate mount point for /usr/local, so it's currently on /dev/sda1 with the rest of /, as it should be :p
No, I know that...  What I am asking is, can I set both /home and /usr/local up on /dev/sda6 or do I need a separate partition for /home and  /usr/local

---

### Post by Joe of loath on 2011-06-14
Why not leave /usr/local where it is, though?

---

### Post by psusi on 2011-06-14
I suppose you can create a mount point ( maybe in /media ) for sda6, then create both home and local directories in there, and then bind mount those directories to /home and /usr/local.

---

### Post by iconoclast hero on 2011-06-14
> **psusi said:**
> I suppose you can create a mount point ( maybe in /media ) for sda6, then create both home and local directories in there, and then bind mount those directories to /home and /usr/local.

I guess I see the point of why ubuntu would have set up a /usr/local partition separate for much the same reason as to why you would want to set up a separate /home...  if something happens to the main file system, you can preserve what is in /usr/local.  the reason i want both on /dev/sda6 is because that way I don't have to guess as to how big a partition for /usr/local I should create.

psusi, i think that is what I am trying to do...

So what about making mounting /dev/sda6 to /media/local and then create /media/local/home and /media/local/usr/ and then do the bind mount?  My problem is I have not been able to get the bind mount to work properly from fstab.

On /dev/sda6 I suppose I should make a /home and a /local (for /usr/local) then copy my /home to the /dev/sda1/home to /dev/sda6/home...

am I on the right track here?

---

### Post by Joe of loath on 2011-06-14
The problem is, everything in /usr/local is specific to your install, it would be problematic if you were to install a different distro.

---

### Post by iconoclast hero on 2011-06-14
> **Joe of loath said:**
> The problem is, everything in /usr/local is specific to your install, it would be problematic if you were to install a different distro.

So when I move to 12.04 LTS, rubyripper will need to be recompiled?  Then I guess the only advantage would be if something were to happen to my 10.10 install on /dev/sda1 and I had to reinstall 10.10.

---

### Post by psusi on 2011-06-14
Sure, that should work.

---

### Post by iconoclast hero on 2011-06-14
> **psusi said:**
> Sure, that should work.

Is there some guide how to do a bind mount in fstab?

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) doesn't have "bind" mentioned once.

I started [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) but didn't get very far (although it doesn't have "bind" in it either.

---

### Post by psusi on 2011-06-14
Simply add "bind" to the options, and of course, you specify the already mounted directory as the source instead of a dev node.

---

### Post by Joe of loath on 2011-06-14
I can see compiled applications behaving badly when you change distros or versions, they were compiled with certain libraries, and suddenly these libraries change version, included features, and locations between releases.

---

### Post by iconoclast hero on 2011-06-14
Ok, thanks, I think I got it.  It appears that /home and /usr/local are both on /dev/sda6 mounted from /media/local...  I suppose there is probably a better descriptor than local so I don't end up with /media/local/local...  perhaps /media/usr/local and /media/usr/home but whatever.

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1

# swap is on /dev/sda5
UUID=82b4a03f-9aba-462c-963f-40d45afd35ca none            swap    sw           $

# /dev/sda6 with /home and /usr/local
UUID=b7877ac1-450e-4a63-ad74-6417bdf1c79c /media/local ext4 nodev,nosuid 0 2

# mount /home from /dev/sda6
/media/local/home /home ext4 bind 0 2

#mount /usr/local from /dev/sda6
/media/local/local /usr/local ext4 bind 0 2

```

---

