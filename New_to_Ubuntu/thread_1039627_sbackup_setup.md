---
title: "sbackup setup"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Matt26 on 2009-01-14
i'm trying to set sbackup to run a custom backup job to my USB drive- i have saved my settings and tried to run the backup job- sbackup notifies me that a backup has been initiated in the background with a process id of xxxxx... but when i go into process manager there is no such id listed- plus, there is no new data on my USB drive, so i am assuming the backup job is not running properly.

i have been able to run sbackup successfully with its default settings, but my custom backup job doesn't appear to be running.

does anyone know what i might be missing?  is there any way to view the progress of an active backup- it's a bit difficult to tell if one is running when there is no progress indicator to look at.

thanks.

---

### Post by blueridgedog on 2009-01-14
Have you tried it from the command line?
```

sudo sbackupd --config=/pathtomyconfig.conf
```

---

### Post by Matt26 on 2009-01-14
> **blueridgedog said:**
> Have you tried it from the command line?
```

sudo sbackupd --config=/pathtomyconfig.conf
```

where do i find the path to my config file?  i don't see any options for opening or accessing such a file in sbackup...

---

### Post by blueridgedog on 2009-01-15
The config file is typically located at /etc/sbackup.conf

You can try it from the command line with just 

```
sudo sbackup
```

When you select items via the gui interface, it simply build the config file which is a list of the items you want backed up.  My thought is perhaps you will get an error message when it attempts to run the backup.

---

### Post by Matt26 on 2009-01-16
> **blueridgedog said:**
> The config file is typically located at /etc/sbackup.conf

You can try it from the command line with just 

```
sudo sbackup
```

When you select items via the gui interface, it simply build the config file which is a list of the items you want backed up.  My thought is perhaps you will get an error message when it attempts to run the backup.

when i run the command *sudo sbackupd --config=/etc/sbackup.conf* or just *sudo sbackupd* i get the following output:

[B]File "/usr/lib/python2.5/posixpath.py", line 375, in normpath
    if path == '':
RuntimeError: maximum recursion depth exceeded in cmp[/B]

the first line shows up repeatedly, followed (eventually) by the last 2 lines... any ideas as to what this means?

---

### Post by blueridgedog on 2009-01-16
To stat, lets see what your path is (all of these are in a terminal):

```
echo $PATH
```
 
Mine is:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Secondly, lets see what your sbackup.conf looks like:

```
sudo cat /etc/sbackup.conf 
```

Mine is:

```
[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mpg,\.mkv,\.ogg,\.ogm,\.tmp,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/[^/]+?/\..+/[cC]ache,/home/[^/]+?/\.gvfs/
maxsize = 100000000

[places]
prefix = /usr

[dirconfig]
/proc/ = 0
/sys/ = 0
/tmp/ = 0
/var/cache/ = 0
/var/ = 1
/dev/ = 0
/home/ = 1
/var/tmp/ = 0
/usr/local/ = 1
/etc/ = 1

[general]
stop_if_no_target = 0
target = /var/backup
format = 1
purge = log
maxincrement = 21
lockfile = /var/lock/sbackup.lock
```

---

### Post by Matt26 on 2009-01-16
> **blueridgedog said:**
> To stat, lets see what your path is (all of these are in a terminal):

```
echo $PATH
```
 
Mine is:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Secondly, lets see what your sbackup.conf looks like:

```
sudo cat /etc/sbackup.conf 
```

Mine is:

```
[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mpg,\.mkv,\.ogg,\.ogm,\.tmp,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/[^/]+?/\..+/[cC]ache,/home/[^/]+?/\.gvfs/
maxsize = 100000000

[places]
prefix = /usr

[dirconfig]
/proc/ = 0
/sys/ = 0
/tmp/ = 0
/var/cache/ = 0
/var/ = 1
/dev/ = 0
/home/ = 1
/var/tmp/ = 0
/usr/local/ = 1
/etc/ = 1

[general]
stop_if_no_target = 0
target = /var/backup
format = 1
purge = log
maxincrement = 21
lockfile = /var/lock/sbackup.lock
```

echo $PATH:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

sbackup.conf:
```
[exclude]
regex = /home/[^/]+?/\.thumbnails/
maxsize = -1

[places]
prefix = /usr

[dirconfig]
// = 1
/home/matthew/ntfs/downloads/ = 1
/home/matthew/ntfs/stuff/ = 1

[general]
stop_if_no_target = 0
target = /home/matthew/NTFS/Backup/Central
format = 1
purge = log
maxincrement = 30
lockfile = /var/lock/sbackup.lock

```

---

### Post by blueridgedog on 2009-01-17
Why don't you try removing/commenting out this line:

```
// = 1
```

It looks like it may be related to the problem.

You can edit it with:

```
gksudo gedit /etc/sbackup.conf
```

If that still fails, then we can load a simplified config file and test it.

---

### Post by Matt26 on 2009-01-17
> **blueridgedog said:**
> Why don't you try removing/commenting out this line:

```
// = 1
```

It looks like it may be related to the problem.

You can edit it with:

```
gksudo gedit /etc/sbackup.conf
```

If that still fails, then we can load a simplified config file and test it.

i updated the sbackup.conf file as you suggested and this time when i run the command sudo sbackupd --config=/etc/sbackup.conf it creates a new backup folder with files in it, but the backup folder only contains about 35KB worth of data, and the directories that i have specified to be backed up in my config file have many GBs of data in them- so i don't think it's working properly.  does it matter that they are NTFS drives?

---

### Post by blueridgedog on 2009-01-17
Progress right?

Now lets see why it is not doing what you want.

Note in your file:

```
[exclude]
regex = /home/[^/]+?/\.thumbnails/
maxsize = -1

[places]
prefix = /usr

[dirconfig]
// = 1
/home/matthew/ntfs/downloads/ = 1
/home/matthew/ntfs/stuff/ = 1

[general]
stop_if_no_target = 0
target = /home/matthew/NTFS/Backup/Central
format = 1
purge = log
maxincrement = 30
lockfile = /var/lock/sbackup.lock
```

You refer to /home/matthew/NTFS and /home/matthew/ntfs

Which is is?  If it is NTFS, then you will backup nothing, as ntfs does not exist.  Case matters in Unix and therefore Linux.

---

### Post by Matt26 on 2009-01-17
> **blueridgedog said:**
> Progress right?

Now lets see why it is not doing what you want.

Note in your file:

```
[exclude]
regex = /home/[^/]+?/\.thumbnails/
maxsize = -1

[places]
prefix = /usr

[dirconfig]
// = 1
/home/matthew/ntfs/downloads/ = 1
/home/matthew/ntfs/stuff/ = 1

[general]
stop_if_no_target = 0
target = /home/matthew/NTFS/Backup/Central
format = 1
purge = log
maxincrement = 30
lockfile = /var/lock/sbackup.lock
```

You refer to /home/matthew/NTFS and /home/matthew/ntfs

Which is is?  If it is NTFS, then you will backup nothing, as ntfs does not exist.  Case matters in Unix and therefore Linux.

good catch- i changed the config to NTFS and my backup started!  unfortunately after it had been running for some time my PC froze completely- no mouse movement or keyboard response- Alt + Prt Scr + REISUB wouldn't even work... i wonder what would cause this to happen during the backup- i'm not sure if i should try running the backup until i figure this out for fear that my PC will freeze up like that again.

any suggestions?

---

### Post by blueridgedog on 2009-01-17
Try a simplified backup to start, select just one folder and test it in increments until you feel you have identified the problem.

---

