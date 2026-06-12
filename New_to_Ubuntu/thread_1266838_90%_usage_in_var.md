---
title: "90% usage in /var"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by eddski on 2009-09-15
Not sure why its at 90% usage, but I wanted to know if I can delete the contents of lost+found as it 4x the data of any other dir.

---

### Post by NoaHall on 2009-09-15
What do you mean by 90 % usage? Your disk space is being taken up by it? Have you, by any chance, installed bootchart?

---

### Post by eddski on 2009-09-15
partial outpout from df -h :
/dev/sda3             175M   43M  124M  26% /boot
/dev/sda5             3.4G  1.6G  1.7G  49% /home
/dev/sda8             1.3G   35M  1.2G   3% /tmp
/dev/sda7             7.4G  2.4G  4.7G  34% /usr
/dev/sda10            1.3G  1.1G  129M  90% /var

output from ls -la for /var :
drwxr-xr-x 16 root root   4096 2008-10-29 16:12 .
drwxr-xr-x 21 root root   4096 2009-09-15 00:19 ..
drwxr-xr-x  2 root root   4096 2009-09-14 22:34 backups
drwxr-xr-x 19 root root   4096 2009-09-15 00:14 cache
drwxr-xr-x  2 root root   4096 2008-10-23 22:57 crash
drwxr-xr-x  2 root root   4096 2008-10-29 16:12 games
drwxr-xr-x 59 root root   4096 2009-09-15 00:43 lib
drwxrwsr-x  2 root staff  4096 2008-10-20 05:27 local
drwxrwxrwt  2 root root     60 2009-09-15 01:09 lock
drwxr-xr-x 13 root root   4096 2009-09-15 01:09 log
drwx------  2 root root  16384 2009-05-17 08:52 lost+found
drwxrwsr-x  2 root mail   4096 2008-10-29 15:53 mail
drwxr-xr-x  2 root root   4096 2008-10-29 15:53 opt
drwxr-xr-x 17 root root    720 2009-09-15 02:00 run
drwxr-xr-x  6 root root   4096 2009-09-15 00:03 spool
drwxrwxrwt  2 root root   4096 2009-09-15 01:14 tmp

---

### Post by louieb on 2009-09-15
lost+found is the place fsck puts stuff it has found. 
see whats in it - if you don't want it get rid of it. 
```
sudo ls- l /var/lost+found
```

You can delete the whole lost+found  directory - fsck will create a new empty one next time it is run.

---

### Post by niteshifter on 2009-09-15
Hi,

No. don't delete it. It needs to be there. It's purpose is to store the results of a fsck run when/if fsck fixes a corrupt file system. IIRC, even if you delete it will come back on a restart or fsck run.

I can almost promise it's not lost+found that's eating up space. Let's decode the output of ls -la /var:

```
drwxr-xr-x 2 root root 4096 2009-09-14 22:34 backups
|---+----| |   |    |    |  |------+-------|    |
    |      |   |    |    |         |            +- filename
    |      |   |    |    |         +- date time
    |      |   |    |    +- size (in bytes)
    |      |   |    +- group name
    |      |   +- owner name
    |      +- number of hard links
    +- permissions

```

This:
```
drwx------ 2 root root 16384 2009-05-17 08:52 lost+found
```
is telling that there are 16384 **bytes** used just for the directory. This is a normal size for lost+found.

Most likely culprits for eating space are /var/log or /var/cache. Try the du command:
```
sudo du -h /var | less
```
pipes the output to a "paginator" (less), use pagedup & page down keys to view.
Or if you like put the output to a file and use an editor to view:
```
sudo du -h /var > ~/var-usage.txt
```

---

### Post by anaconda on 2009-09-15
apt cache is also in /var.

to clean it you can type
```
sudo apt-get clean
```
in terminal.

(apt cache has all the install files of the programs you have downloaded using apt or synaptic, or add/remove or update)
and you dont need those install files after you have used them....

---

