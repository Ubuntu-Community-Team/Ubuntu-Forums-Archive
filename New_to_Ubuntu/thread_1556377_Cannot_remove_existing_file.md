---
title: "Cannot remove existing file"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Onur Cobanoglu on 2010-08-19
Hi,

Apologies if duplicates of this question exist, in a quick search I couldn't find any. I cannot remove existing files on the disk. Both on Gnome and command line (doing an ls) I can see them, and when I issue an rm command on the command line for them system even auto-completes their names when I hit the tab, but I always get the same error:

rm: cannot remove `<the name of the file here>`: No such file or directory

Trying with sudo doesn't change the result either. Trying to delete them on GUI doesn't work for the same reason.

I am using 64-bit Ubuntu 9.04. One extra information: These files reside on the disk partition onto which Vista is installed (actually I am accessing the Vista users' home directories), hence it is formatted in NTFS.

Any help will be appreciated.

Thanks,
Onur

---

### Post by lukeiamyourfather on 2010-08-19
Check the file system for errors with the utilities in Windows (since its NTFS).

---

### Post by Ampi on 2010-08-19
I had this problem years ago so I dont remember well. 

For reading and writing NTFS files from Ubunt you need ntfs-3g support. You can not 'just' share this filesystem with Windows. More on this you can find in this thread:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

As things have changed the last couple of years I wont give you any more information as it might be incorrect..

---

### Post by lukeiamyourfather on 2010-08-19
> **Ampi said:**
> I had this problem years ago so I dont remember well. 

For reading and writing NTFS files from Ubunt you need ntfs-3g support. You can not 'just' share this filesystem with Windows. More on this you can find in this thread:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

As things have changed the last couple of years I wont give you any more information as it might be incorrect..

That's no longer applicable because Ubuntu comes with read and write NTFS support by default now. There's likely a file system issue on the NTFS partition. Or a permission issue depending on how the user directories are setup on the Windows side.

---

### Post by Ampi on 2010-08-19
In that case, sorry for my outdated information! Haven´t used windows in a while...

Also, knowing this it looks liek Lukeiamyourfather is right!

---

### Post by AlphaLexman on 2010-08-19
In a terminal, and in the [ntfs] directory of the file you want to delete, please post the result of:
```
ls -l file_to_delete.ext
```

---

### Post by Onur Cobanoglu on 2010-08-19
Here is the result:

```
-rwxrwxrwx 2 root root 2 2010-08-13 16:33 Autonomic Multi-Agent Management of Power and Performance in Data Centers.pdf
```Thanks for all the answers and reply backs.

Onur

> **AlphaLexman said:**
> In a terminal, and in the [ntfs] directory of the file you want to delete, please post the result of:
```
ls -l file_to_delete.ext
```

---

### Post by AlphaLexman on 2010-08-19
You can 'ls' the file (and it exists), but you can't 'rm' the file?

Is the partition (Vista) in a 'hibernate' mode or 'suspend' mode? If yes, go back to Win, and shutdown properly.

If not, it may be mounted read-only, post the result of ->
```
mount
```
and let us know which 'device' is the Win partition, i.e., [/dev/sdb1] or something.

---

### Post by jaxxm on 2010-08-19
What is the exact command you are typing? 

Are you making sure you are escaping the spaces in the name or quoting the file name?

---

### Post by Vaphell on 2010-08-19
seeing as the file is root owned
```

sudo rm Autonomic\ Multi-Agent\ Management\ of\ Power\ and\ Performance\ in\ Data\ Centers.pdf

```
should work

maybe your partition is umasked to be readonly?

---

### Post by Onur Cobanoglu on 2010-08-19
I booted Vista and properly shut it down. The problem still exists. Here is the output of mount:

```

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/onur/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=onur)
/dev/sda2 on /media/VistaOS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```Looking at this output, I guess /dev/sda2 is the Windows partition (since it is the one mounted on /media/VistaOS).

Thanks,
Onur

> **AlphaLexman said:**
> You can 'ls' the file (and it exists), but you can't 'rm' the file?

Is the partition (Vista) in a 'hibernate' mode or 'suspend' mode? If yes, go back to Win, and shutdown properly.

If not, it may be mounted read-only, post the result of ->
```
mount
```and let us know which 'device' is the Win partition, i.e., [/dev/sdb1] or something.

---

### Post by AlphaLexman on 2010-08-19
You have read-write permissions, the 'rw' tells us that ->
> /dev/sda2 on /media/VistaOS type fuseblk (**rw**,nosuid,nodev,allow_other,blksize=4096)My Win XP partition is 'slightly' different...
> /dev/sda1 on /media/Sata_Disk_0 type fuseblk (rw,nosuid,nodev,allow_other,**default_permissions**,blksize=4096)with the 'default_permissions' part. We could look at your /etc/fstab file but I don't think that is the issue, because you still have 'rw' permissions.

So, let's check what lukeiamyourfather said about ntfs-3g support ->
```
whereis ntfs-3g
```and post the results.

---

### Post by jtarin on 2010-08-19
Have you tried renaming the file from Linux then removing?

---

### Post by Onur Cobanoglu on 2010-08-28
Here is the output:

```
ntfs-3g: /bin/ntfs-3g.probe /bin/ntfs-3g /usr/share/man/man8/ntfs-3g.8.gz
```

Thanks,
Onur

> **AlphaLexman said:**
> You have read-write permissions, the 'rw' tells us that ->
My Win XP partition is 'slightly' different...
with the 'default_permissions' part. We could look at your /etc/fstab file but I don't think that is the issue, because you still have 'rw' permissions.

So, let's check what lukeiamyourfather said about ntfs-3g support ->
```
whereis ntfs-3g
```and post the results.

---

### Post by Onur Cobanoglu on 2010-08-28
When I try to rename, the system says that no such file exists.

Thanks,
Onur

> **jtarin said:**
> Have you tried renaming the file from Linux then removing?

---

