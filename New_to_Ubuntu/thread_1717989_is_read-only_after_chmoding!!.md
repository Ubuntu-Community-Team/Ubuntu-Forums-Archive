---
title: "/ is read-only after chmoding!!"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Crazedpsyc on 2011-03-30
Hi, as it say in the title, my / partition appears to be Read-only.
It was not that way at first, but I was marking some files as executable from the terminal (my own files in my home folder).
Then I started to edit the file with gedit. For some reason it said it was read-only, after I just made it. Then I closed a running terminal app that writes to a file when it is done, and it said
```
readline.write_history_file(".dosprompt_history")
IOError: [Errno 30] Read-only file system
```
THen I tried to run "touch test" and it said my filesystem is readonly as well!
I found another thread with this issue here: IOError: [Errno 30] Read-only file system
But the only thing that looks like a solution is rebooting, and if ubuntu can't write to anything, won't it completely break?

I do have some info:
```
$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda7 on /media/BACKUP type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.
```

```
cat /proc/mounts                                     15:43:45
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=3974360k,nr_inodes=993590,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sda1 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/loop0 / ext4 ro,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
/dev/sda7 /media/BACKUP ext4 rw,relatime,barrier=1,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/mike/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
```

So that looks to me like it says, if there are errors, remount as read-only. If that is the case, rebooting sounds like the best thing to do, but if not, I need to know what to do

Any incredible geniuses out there who know for sure what to do?

** if I can fix it without rebooting (eg. umount -f / && mount /path/to/root.disk /)
btw, it is a wubi install

---

### Post by blind2314 on 2011-03-30
Rebooting won't totally *break* anything, but it could leave you in a nasty state (as a worst-case scenario). Definitely don't try to unmount and remount / while you're booted into the OS. It should scream and prevent you from doing that..but..well, just don't try it :)
 
 
I honestly don't know of many options other than rebooting, or using a live CD (although since you mention it being Wubi, I guess that idea is out as well). Save any data you have on there that you might need, and cross your fingers.
 
:popcorn:
 
 
P.S. That last bit was a joke, but seriously, rebooting likely needs to happen. If the filesystem is corrupted, the kernel will notice the dirty super block, and force a fsck.

---

### Post by Crazedpsyc on 2011-03-30
Thanks, before I even read that, I locked my screen, and it refused to unlock. So I switched over to tty6 (or whatever Ctrl+Alt+F6 is) and backed up some stuff.
Then I sudo shutdown -h 0 and rebooted. Plymouth came up nicely, then stayed there.
So I rebooted by holding the power button and got into recovery mode, where fsck nicely fixed a ton of stuff for me, and it rebooted itself this time. Finally, I booted back up normally and everything was(is) fine!

---

### Post by blind2314 on 2011-03-30
Great! :) Glad it worked for you.

---

