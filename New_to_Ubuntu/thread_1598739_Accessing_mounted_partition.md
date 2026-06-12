---
title: "Accessing mounted partition"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Steveplanetary on 2010-10-16
I have Ubuntu 10.04 on /dev/sda5 ext4, and another ext4 partition (/dev/sda6) I created for the purpose of backing up important files and directories, which is mounted at /mnt of /dev/sda5.  But I don't know how to access /sda5.  The only subdirectory on /mnt is /lost+found.  How do I back up my files?  Thanks in advance.

---

### Post by rogueleader12345 on 2010-10-16
use the graphical manager, in the "places" menu, then just copy and paste

---

### Post by Steveplanetary on 2010-10-17
I just noticed an error in my original post: I said I didn't know how to access /sda5, but I really meant I don't know how to access /sda6.  You probably understood what I meant, and thanks for the reply.

With regard to a graphical manager, I don't know what you mean.  I boot into /dev/sda5, but there is no graphical manager explicitly stated under Places.  Could you please elaborate?

Thanks

---

### Post by Verbeck on 2010-10-17
can you see the drive listed in Disk Utility ? its in the System>administration menu


try:
cd /media
sudo mkdir backup
sudo mount /dev/sda6 backup -o force

---

### Post by Steveplanetary on 2010-10-17
Yes, I can see the disk and all it's partitions in Disk Utility, exactly as I set it up.

I performed the following, except that instead of using /media I used /mnt, since that is the directory that, by default, mounts /sda6:

```
cd /media
sudo mkdir backup
sudo mount /dev/sda6 backup -o force
```I set up /mnt to be the default when I was specifying the parameters to format /sda6.  /mnt wasn't in the drop down list, so I typed it in.  If that was a bad choice please tell me.  /media wasn't in the drop down list either.

I experimented with the [SIZE=2]mount [SIZE=1]and [SIZE=2]umount[SIZE=1] commands, as well as [SIZE=2]cp[SIZE=1] with help from [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]http://www.tuxfiles.org/linuxhelp/dirman.html.[SIZE=2][SIZE=1][SIZE=2][SIZE=1][SIZE=2][SIZE=1]  I can mount and unmount /dev/sda6 with any directory.  [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]I also created /bkp in /var, and typed:

stephen@Presario:/usr/share$ sudo cp -r example-content /var/bkp
stephen@Presario:/usr/share$ cd /var/bkp
stephen@Presario:/var/bkp$ ls
example-content
stephen@Presario:/var/bkp$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stephen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stephen)
/dev/sda6 on /mnt type ext4 (rw)
stephen@Presario:/var/bkp$ sudo umount /dev/sda6
stephen@Presario:/var/bkp$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stephen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stephen)
stephen@Presario:/var/bkp$ cd /mnt/backup
stephen@Presario:/mnt/backup$ sudo mount /dev/sda6
stephen@Presario:/mnt/backup$ cd /var/bkp
stephen@Presario:/var/bkp$ sudo cp -r example-content /dev/sda6
[sudo] password for stephen: 
cp: cannot overwrite non-directory `/dev/sda6' with directory `example-content'
stephen@Presario:/var/bkp$ sudo cp -r example-content /mnt/backup
stephen@Presario:/var/bkp$ cd /mnt/backup
stephen@Presario:/mnt/backup$ ls
example-content

Sorry about all the code.  Here's what I did:

Lines 1-4: copied /example-content from /usr/share to /var/bkp
Lines 5-20: /dev/sda6 is mounted on /mnt, the default
Lines 21-36: /dev/sda6 unmounted
Lines 37-38: /dev/sda6 mounted on /mnt/backup
Lines 39-42: unsuccessful attempt  to copy /example-content to /dev/sda6
Lines 43-46: copied /example-content from /var/bkp to /mnt/backup

This is at the heart of my problem.  I can mount /dev/sda6 anywhere I want, but I don't know how to back up files to it.  Help!

EDIT: BTW after I executed the code in the box I typed umount, which resulted in a message stating that it appeared /dev/sda6 was mounted multiple times.  Rebooting and executing the mount command again showed that /dev/sda6 mounted automatically at startup.

---

### Post by Verbeck on 2010-10-18
> I set up /mnt to be the default when I was specifying the parameters to  format /sda6.  /mnt wasn't in the drop down list, so I typed it in.  If  that was a bad choice please tell me.  /media wasn't in the drop down  list either.> /dev/sda6 on /mnt type ext4 (rw)from what i see, you set up the mount point of dev/sda6 as /mnt while installing. this means *_/mnt is /dev/sda6_* . the partition was formatted as ext4, that why there is a /lost+found in /mnt.

Edit: since /mnt is owned by root, you might not be able to copy any files there. so run *sudo chown -R stephen:stephen /mnt*
however i suggest that you mount it in another place, not at /mnt ,its confusing....

---

### Post by Stephen Morgan on 2010-10-18
> **Steveplanetary said:**
> Lines 1-4: copied /example-content from /usr/share to /var/bkp
Lines 5-20: /dev/sda6 is mounted on /mnt, the default
Lines 21-36: /dev/sda6 unmounted
Lines 37-38: /dev/sda6 mounted on /mnt/backup
Lines 39-42: unsuccessful attempt  to copy /example-content to /dev/sda6
Lines 43-46: copied /example-content from /var/bkp to /mnt/backup

This is at the heart of my problem.  I can mount /dev/sda6 anywhere I want, but I don't know how to back up files to it.  Help!

Once /dev/sda6 is mounted on /mnt/backup copying something to /mnt/backup is equivalent to copying it to /dev/sda6. You can't copy things to /dev/sda6, only to the mount point you've assigned for it, in this case /mnt/backup. example-content should now be visible whereever you mount /dev/sda6

> EDIT: BTW after I executed the code in the box I typed umount, which resulted in a message stating that it appeared /dev/sda6 was mounted multiple times.  Rebooting and executing the mount command again showed that /dev/sda6 mounted automatically at startup.

If you don't want it to edit /etc/fstab and add the noauto option to the line referring to /dev/sda6

---

### Post by Steveplanetary on 2010-10-23
You have all been very helpful.  I now have full access to /dev/sda6.  Thanks a bunch! :P

---

