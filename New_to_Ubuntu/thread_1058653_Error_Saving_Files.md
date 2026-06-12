---
title: "Error Saving Files"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by flylehe on 2009-02-03
I have two systems on my laptop: Windows XP and Ubuntu 8.10

My C++ program is saved in the part of the hard drive for Windows and can be accessed from Ubuntu. Before yesterday everything was OK. Since then, any change made to my program under an IDE called code:blocks always fails to proceed, giving an Error Saving Files message saying "File could not be saved...". If I copy my program to the hard drive part of ubuntu, then change can be saved. Changes to my program made under gedit and other editors can still be saved. How can I fix this problem in code:blocks? 

Also from Ubuntu, I cannot extract tar.gz files on the part of hard drive for Windows. Neither can I delete or add files in "C:/Documents and Settings/flylehe/My Documents/My Pictures" of Windows. It seems like I don't have the permission.

Thanks!

---

### Post by flylehe on 2009-02-03
Help me please! Thanks!

---

### Post by Temposs on 2009-02-03
It seems like all of your issues are issues with permissions. Have you tried changing the permissions on these files manually in Ubuntu using the nautilus file browser or with chmod in terminal?

---

### Post by flylehe on 2009-02-03
Thanks! Can you give examples of how to by the browser and chmod?

---

### Post by handydan918 on 2009-02-03
there are a number of possibilities. Let's see the output of ```
mount
```

That should tell us if your ntfs partition is being mounted read-only, for example.

Also, if you don't give us terminal output it's really a guessing game. Try your copy operation from the cli and give us the whole shebang, errors and all.

---

### Post by flylehe on 2009-02-03
Thanks!
Here comes what mount tells about my system:

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sda2 on /windows-c type vfat (rw,utf8,umask=007,gid=46)
/dev/sda5 on /windows-d type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lehe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lehe)

---

### Post by flylehe on 2009-02-03
In the nautilus file browser, I don't see any special restriction on accessing the code files. It seems like different softwares are treated differently. It is just my IDE codeblocks cannot save the change, but gedit can.

---

