---
title: "My /var/cache dirctory tree has become corrupted"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by frOOgz on 2009-04-19
My /var/cache directory tree has become corrupted.  I have been getting some strange errors today and they point to directories in /var/cache not being available.

How can I go about fixing this without a backup and what are the implications of directories and probably files being missing?

This is my directory tree from /var/cache.  Is there anything obvious missing?

./cups
./cups/rss
./fontconfig
./man
./jockey
./hwtest
./apt
./apt/archives
./apt/archives/partial
./hald
./debconf

---

### Post by ptn107 on 2009-04-20
This is the contents of my /var/cache (from a fresh 9.04 installation):

```
user@user-desktop:/var/cache$ ls -la
total 60
drwxr-xr-x 15 root root  4096 2009-04-14 12:28 .
drwxr-xr-x 15 root root  4096 2009-04-14 12:33 ..
drwxr-xr-x  2 root root  4096 2009-04-14 12:32 app-install
drwxr-xr-x  3 root root  4096 2009-04-19 22:26 apt
drwxrwxr-x  4 root lp    4096 2009-04-15 10:22 cups
drwxr-xr-x  2 root root  4096 2009-04-17 16:21 debconf
drwxr-xr-x  2 root root  4096 2009-04-14 12:38 dictionaries-common
drwxr-xr-x  2 root root  4096 2009-04-15 10:15 fontconfig
drwxr-xr-x  3 root root  4096 2009-04-14 12:26 gnome-system-tools
drwxr-xr-x  2 root root  4096 2009-04-15 05:46 hald
drwxrwsr-t  2 root admin 4096 2009-04-15 10:25 jockey
drwx------  2 root root  4096 2009-04-19 13:35 ldconfig
drwxr-sr-x 42 man  root  4096 2009-04-19 13:35 man
drwxr-xr-x  2 root root  4096 2009-02-20 12:56 pppconfig
drwxr-xr-x  2 root root  4096 2009-04-19 21:48 samba
```

---

### Post by frOOgz on 2009-04-20
Thanks for this.  It would be useful if all the sub directories were also listed as I have had to recreate these.

---

### Post by sisco311 on 2009-04-20
Please post the error message.

---

### Post by frOOgz on 2009-04-20
One of the problems was that HAL wouldn't initialize.  I tracked down the problem to directories being missing under /var/cache

I would like to recreate a directory tree to safe guard against other problems.  I can see from ptn107 post that I am missing app-install.

---

### Post by ptn107 on 2009-04-20
The complete listing is linked*.  Ignore whats in /var/cache/apt/archives/.  You will probably need to copy the files from a working Ubuntu to get it working correctly and hope there are no problems.

*[http://ubuntu.pastebin.com/m25fc3f9c](http://ubuntu.pastebin.com/m25fc3f9c)

**Also, I could compress the contents of my /var/cache for you to have, but I'm running Ubuntu 9.04 and I don't know what version your using.

---

### Post by sisco311 on 2009-04-20
> **frOOgz said:**
> One of the problems was that HAL wouldn't initialize.  I tracked down the problem to directories being missing under /var/cache

I would like to recreate a directory tree to safe guard against other problems.  I can see from ptn107 post that I am missing app-install.

check the partition for errors(fsck)
```
tune2fs -C 40 /dev/sdXY
reboot
```

```
dpkg-query -L hal | grep /var/cache/
```
shows that only /var/cache/hald is created by the hal package, 

but try to reinstall hal:
```
apt-get install --reinstall hal
```

/var/cache/app-install is created by gnome-app-install (*dpkg-query -S /var/cache/app-install*), try to reinstall the package:
```
apt-get install --reinstall gnome-app-install
```

---

