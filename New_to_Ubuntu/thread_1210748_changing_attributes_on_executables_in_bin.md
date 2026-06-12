---
title: "changing attributes on executables in bin"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by benny2 on 2009-07-11
I was reading a book trying to learn more about linux and in it they mention that you should check attributes set for your executables in /bin, /usr/bin, /sbin, and /usr/sbin.  Anyway I thought it said they should say -rwxr-xr-x but some of my stuff in /bin says lrwxrwxrwx.  First I tried to change the permissions recursively and when I listed it again it had not changed.  Then I tried to change the attributes with chattr -i -R and it gives this message:
chattr: Operation not supported while reading flags on ...
for a lot of things in bin.
I'm very confused-is it fine for some of the things in bin to say lrwxrwxrwx? or is this a bad sign? Thanks for any feedback!

---

### Post by Najand on 2009-07-11
Symbolic links usually have full permissions. Do a "ls -al /bin" or etc to see which one is really a file or a link.

---

### Post by jonobr on 2009-07-11
benny2 , you need to be really really careful what your doing,
your going to end up with an inaccessible system if you not only change permission , but do it recursively

The l indicates a symbolic link to another location, in other words a pointer to another file executable or so on.

the full permissions give full access to all users and groups meaning this is a link which is accessible to all.

The /bin does have files with full permissions so please be careful or you going to cause problem../

Im attaching the /bin folder from a basic install I have in case you changed anything.
You should change it basck as the /bin is a system directory

> -rwxr-xr-x 1 root root  729040 2009-03-02 06:22 bash
-rwxr-xr-x 1 root root   30140 2008-11-10 03:51 bunzip2
-rwxr-xr-x 1 root root   30140 2008-11-10 03:51 bzcat
lrwxrwxrwx 1 root root       6 2009-05-11 17:30 bzcmp -> bzdiff
-rwxr-xr-x 1 root root    2140 2008-11-10 03:51 bzdiff
lrwxrwxrwx 1 root root       6 2009-05-11 17:30 bzegrep -> bzgrep
-rwxr-xr-x 1 root root    4874 2008-11-10 03:51 bzexe
lrwxrwxrwx 1 root root       6 2009-05-11 17:30 bzfgrep -> bzgrep
-rwxr-xr-x 1 root root    3642 2008-11-10 03:51 bzgrep
-rwxr-xr-x 1 root root   30140 2008-11-10 03:51 bzip2
-rwxr-xr-x 1 root root    9524 2008-11-10 03:51 bzip2recover
lrwxrwxrwx 1 root root       6 2009-05-11 17:30 bzless -> bzmore
-rwxr-xr-x 1 root root    1297 2008-11-10 03:51 bzmore
-rwxr-xr-x 1 root root   30196 2008-06-26 17:31 cat
-rwxr-xr-x 1 root root   50784 2008-06-26 17:31 chgrp
-rwxr-xr-x 1 root root   46664 2008-06-26 17:31 chmod
-rwxr-xr-x 1 root root   50792 2008-06-26 17:31 chown
-rwxr-xr-x 1 root root    5472 2009-04-09 17:51 chvt
-rwxr-xr-x 1 root root   75492 2008-06-26 17:31 cp
-rwxr-xr-x 1 root root  118508 2009-02-15 09:39 cpio
-rwxr-xr-x 1 root root   87924 2008-11-04 23:51 dash
-rwxr-xr-x 1 root root   58960 2008-06-26 17:31 date
-rwxr-xr-x 1 root root    9620 2009-01-27 06:39 dbus-cleanup-sockets
-rwxr-xr-x 1 root root  297364 2009-01-27 06:39 dbus-daemon
-rwxr-xr-x 1 root root    5476 2009-01-27 06:39 dbus-uuidgen
-rwxr-xr-x 1 root root   50820 2008-06-26 17:31 dd
-rwxr-xr-x 1 root root   50812 2008-06-26 17:31 df
-rwxr-xr-x 1 root root   96216 2008-06-26 17:31 dir
-rwxr-xr-x 1 root root    5468 2009-02-18 11:43 dmesg
-rwxr-xr-x 1 root root    9652 2008-05-02 21:14 dnsdomainname
-rwxr-xr-x 1 root root   57884 2009-04-09 17:51 dumpkeys
-rwxr-xr-x 1 root root   26048 2008-06-26 17:31 echo
-rwxr-xr-x 1 root root   40440 2008-11-23 23:51 ed
-rwxr-xr-x 1 root root   96216 2008-11-04 13:16 egrep
-rwxr-xr-x 1 root root   26036 2008-06-26 17:31 false
-rwxr-xr-x 1 root root    9576 2009-04-09 17:51 fgconsole
-rwxr-xr-x 1 root root   55156 2008-11-04 13:16 fgrep
-rwxr-xr-x 1 root root   22536 2007-11-23 02:15 fuser
-rwsr-xr-x 1 root root   22064 2009-03-05 09:42 fusermount
-rwxr-xr-x 1 root root  100312 2008-11-04 13:16 grep
-rwxr-xr-x 1 root root      63 2008-10-15 00:32 gunzip
-rwxr-xr-x 1 root root    5874 2008-10-15 00:32 gzexe
-rwxr-xr-x 1 root root   57360 2008-10-15 00:32 gzip
-rwxr-xr-x 1 root root    9648 2008-05-02 21:14 hostname
-rwxr-xr-x 1 root root  207692 2008-11-04 19:11 ip
-rwxr-xr-x 1 root root    9572 2009-04-09 17:51 kbd_mode
-rwxr-xr-x 1 root root   13748 2009-03-18 15:17 kill
-rwxr-xr-x 1 root root 1374396 2009-02-10 08:13 ld_static
-rwxr-xr-x 1 root root   42564 2008-06-26 17:31 ln
-rwxr-xr-x 1 root root   82676 2009-04-09 17:51 loadkeys
-rwxr-xr-x 1 root root   35080 2009-04-03 22:49 login
-rwxr-xr-x 1 root root   96216 2008-06-26 17:31 ls
-rwxr-xr-x 1 root root    9452 2009-03-18 09:02 lsmod
-rwxr-xr-x 1 root root   34312 2008-06-26 17:31 mkdir
-rwxr-xr-x 1 root root   30220 2008-06-26 17:31 mknod
-rwxr-xr-x 1 root root    9552 2008-11-05 04:30 mktemp
-rwxr-xr-x 1 root root   30316 2009-02-18 11:43 more
-rwsr-xr-x 1 root root   76228 2009-02-18 11:43 mount
-rwxr-xr-x 1 root root    5400 2009-03-31 02:02 mountpoint
lrwxrwxrwx 1 root root      20 2009-05-11 17:30 mt -> /etc/alternatives/mt
-rwxr-xr-x 1 root root   30604 2009-02-15 09:39 mt-gnu
-rwxr-xr-x 1 root root   83732 2008-06-26 17:31 mv
-rwxr-xr-x 1 root root  153516 2009-03-30 03:23 nano
lrwxrwxrwx 1 root root      20 2009-05-11 17:30 nc -> /etc/alternatives/nc
-rwxr-xr-x 1 root root   22076 2008-06-21 15:40 nc.traditional
lrwxrwxrwx 1 root root      24 2009-05-11 17:30 netcat -> /etc/alternatives/netcat
-rwxr-xr-x 1 root root  109996 2008-11-11 09:11 netstat
-rwxr-xr-x 1 root root   34724 2009-04-09 15:46 ntfs-3g
-rwxr-xr-x 1 root root    5472 2009-04-09 15:46 ntfs-3g.probe
lrwxrwxrwx 1 root root       6 2009-05-11 17:30 open -> openvt
-rwxr-xr-x 1 root root   13776 2009-04-09 17:51 openvt
lrwxrwxrwx 1 root root      16 2009-05-11 17:30 pidof -> ../sbin/killall5
-rwsr-xr-x 1 root root   30856 2007-12-10 09:33 ping
-rwsr-xr-x 1 root root   26684 2007-12-10 09:33 ping6
-rwxr-xr-x 1 root root   79636 2009-03-18 15:17 ps
-rwxr-xr-x 1 root root   30200 2008-06-26 17:31 pwd
lrwxrwxrwx 1 root root       4 2009-05-11 17:30 rbash -> bash
-rwxr-xr-x 1 root root   38452 2008-06-26 17:31 readlink
-rwxr-xr-x 1 root root   50744 2008-06-26 17:31 rm
-rwxr-xr-x 1 root root   26052 2008-06-26 17:31 rmdir
lrwxrwxrwx 1 root root       4 2009-05-11 17:30 rnano -> nano
-rwxr-xr-x 1 root root   13940 2009-02-16 13:27 run-parts
-rwxr-xr-x 1 root root   42900 2008-05-02 23:53 sed
-rwxr-xr-x 1 root root   34440 2009-04-09 17:51 setfont
-rwxr-xr-x 1 root root    8794 2009-04-08 18:08 setupcon
lrwxrwxrwx 1 root root       4 2009-05-11 17:30 sh -> dash
lrwxrwxrwx 1 root root       4 2009-05-11 17:30 sh.distrib -> bash
-rwxr-xr-x 1 root root   26060 2008-06-26 17:31 sleep
-rwxr-xr-x 1 root root   48708 2008-06-26 17:31 stty
-rwsr-xr-x 1 root root   31012 2009-04-03 22:49 su
-rwxr-xr-x 1 root root   26044 2008-06-26 17:31 sync
-rwxr-xr-x 1 root root    9624 2009-02-18 11:43 tailf
-rwxr-xr-x 1 root root  252468 2008-05-03 00:40 tar
-rwxr-xr-x 1 root root    9516 2009-02-16 13:27 tempfile
-rwxr-xr-x 1 root root   46616 2008-06-26 17:31 touch
-rwxr-xr-x 1 root root   26036 2008-06-26 17:31 true
-rwxr-xr-x 1 root root    9664 2009-03-05 09:42 ulockmgr_server
-rwsr-xr-x 1 root root   55200 2009-02-18 11:43 umount
-rwxr-xr-x 1 root root   26052 2008-06-26 17:31 uname
-rwxr-xr-x 1 root root      63 2008-10-15 00:32 uncompress
-rwxr-xr-x 1 root root    2762 2009-04-09 17:51 unicode_start
-rwxr-xr-x 1 root root   96220 2008-06-26 17:31 vdir
-rwxr-xr-x 1 root root     946 2009-02-16 13:27 which
-rwxr-xr-x 1 root root      64 2008-10-15 00:32 zcat
-rwxr-xr-x 1 root root      69 2008-10-15 00:32 zcmp
-rwxr-xr-x 1 root root    4424 2008-10-15 00:32 zdiff
-rwxr-xr-x 1 root root      64 2008-10-15 00:32 zegrep
-rwxr-xr-x 1 root root      64 2008-10-15 00:32 zfgrep
-rwxr-xr-x 1 root root    2015 2008-10-15 00:32 zforce
-rwxr-xr-x 1 root root    4898 2008-10-15 00:32 zgrep
-rwxr-xr-x 1 root root    1733 2008-10-15 00:32 zless
-rwxr-xr-x 1 root root    2416 2008-10-15 00:32 zmore
-rwxr-xr-x 1 root root    4952 2008-10-15 00:32 zn

---

### Post by mike2357 on 2009-07-11
I would urge you not to change permissions on any of the files and directories in the directories you mentioned, such as /bin.  Many system commands need to run as the super-user, and permissions are set appropriately.  One way to wreck your system is to indiscriminately change permissions in these systems directories.  If you want to learn and experiment, make a directory in your home directory, and change permissions on it.

---

### Post by benny2 on 2009-07-12
Thank you for all your feedback.  My /bin file looks like the one you posted.  Luckily I don't think I changed anything with chmod and chattr. This is a big relief.  Thanks again.  And I will be more careful when I don't know what I am doing!

---

### Post by Copernicus1234 on 2009-07-12
> **benny2 said:**
> Thank you for all your feedback.  My /bin file looks like the one you posted.  Luckily I don't think I changed anything with chmod and chattr. This is a big relief.  Thanks again.  And I will be more careful when I don't know what I am doing!

Yes... what book did you read? Perhaps its outdated. Recently this book came out:

[http://www.newtorrents.info/torrent/63925/Ubuntu.Linux.Secrets.Apr.2009.eBook-BBL.html](http://www.newtorrents.info/torrent/63925/Ubuntu.Linux.Secrets.Apr.2009.eBook-BBL.html)

You have to decide if you want to download or buy it however, but it seems like a good book for beginners.

---

