---
title: "user does not exist..."
date: 2010-03-06
forum: New to Ubuntu
---

### Post by switch10 on 2010-03-06
I just put /home in its own partition, everything works fine except "users and groups" does not list my name.  See screen shot.  I tried adding my user name, and /home/dave, it said that the name and /home/dave already exists.  Why won't it show me then?

I've tried 
```
useradd -G <groupname> dave
```
as well...


how do I get my name in this list???

thanks 

dave.

---

### Post by spiderbatdad on 2010-03-06
if the /home/user directory exists...then something like this should work:
```
sudo useradd switch
chown -R switch:switch switch
sudo passwd switch
``` If your user name was switch.

---

### Post by SoFl W on 2010-03-06
I had trouble with this "moving your home partition" but this might help you:
[http://ubuntuforums.org/showthread.php?t=1411215](http://ubuntuforums.org/showthread.php?t=1411215)

---

### Post by switch10 on 2010-03-06
> **spiderbatdad said:**
> if the /home/user directory exists...then something like this should work:
```
sudo useradd switch
chown -R switch:switch switch
sudo passwd switch
``` If your user name was switch.

I get 'user already exists' when I try to add the user again.

The ownership of all of the files, hidden and all, are dave:dave.

> I had trouble with this "moving your home partition" but this might help you:
[http://ubuntuforums.org/showthread.php?t=1411215](http://ubuntuforums.org/showthread.php?t=1411215)

Thanks, but I've already successfully made a separate partition for my /home.  Everything works fine, except that I cant add myself to groups.  It might not even have anything to do with the fact that I have a separate /home partition.

Any other ideas?

---

### Post by switch10 on 2010-03-06
any clues as to what would cause this anyone??

---

### Post by falconindy on 2010-03-06
Please post the output of the following:
```
grep dave /etc/passwd
groups dave
ls -l ~dave
```

---

### Post by switch10 on 2010-03-06
```
dave:x:999:999:dave,,,:/home/dave:/bin/bash

```


```
dave : dave adm dialout cdrom plugdev lpadmin admin sambashare

```


```
total 144
-rw-r--r-- 1 dave dave    65 2010-03-05 17:18 backup_fstab.sh~
drwxr-xr-x 2 dave dave  4096 2010-03-06 10:42 bin
-rw-r--r-- 1 dave dave 60094 2010-03-06 10:32 bt4-final.iso
drwxr-xr-x 2 dave dave  4096 2010-02-26 18:00 Calibre Library
-rwxrwxrwx 1 dave dave   373 2010-03-04 18:03 conky
drwxrwxrwx 5 dave dave  4096 2010-03-05 18:07 conky_colors
drwxr-xr-x 3 dave dave  4096 2010-03-06 18:27 Desktop
drwxr-xr-x 5 dave dave  4096 2010-03-01 12:04 Documents
drwxr-xr-x 8 dave dave  4096 2010-02-27 11:37 Downloads
-rw-r--r-- 1 dave dave   167 2010-03-04 18:03 examples.desktop
drwxr-xr-x 5 dave dave  4096 2010-02-27 11:39 gtk-gnutella-downloads
-rw-r--r-- 1 dave dave    78 2010-03-04 18:03 mar_3_2010
drwxr-xr-x 2 dave dave  4096 2010-02-26 18:00 Music
drwxr-xr-x 5 dave dave  4096 2010-03-02 23:59 Pictures
drwxr-xr-x 2 dave dave  4096 2010-02-26 18:00 Podcasts
drwxr-xr-x 2 dave dave  4096 2010-02-26 18:00 Public
drwxr-xr-x 2 dave dave  4096 2010-03-05 15:37 Scripts
drwxr-xr-x 2 dave dave  4096 2010-02-26 18:00 Templates
drwxr-xr-x 4 dave dave  4096 2010-02-27 11:38 Test
drwxrwxr-x 7 dave dave  4096 2010-03-05 23:02 Ubuntu One
drwxr-xr-x 2 dave dave  4096 2010-03-05 15:26 upgrade
drwxr-xr-x 2 dave dave  4096 2010-03-06 14:45 Videos

```

If this is not an easy fix, its OK.  I may just do a reinstall.  I had a slackware install in another partition that shared the /home.  Every time I reboot Ubuntu, I have to restart x as well.  Ever since I've been sharing my /home with slackware, I've had problems.

---

### Post by falconindy on 2010-03-07
Just for grins, create another user, and assign him UID 998 -- or anything else below 1000 that isn't taken. I bet that isn't displayed either. Then create a new user above UID 1000 and I'll bet that they **are** displayed.

Similar behavior is exhibited by GDM's login screen, wherein any user below UID 1000 will not be displayed, in order to keep things clean. The users & groups applet must be doing something similar, but making an exception for root (UID = 0).

---

### Post by switch10 on 2010-03-07
hmm.  I made a new user; Dave, and it assigned 1000 as UID. I wonder how mine got switched to 999?

Anyway I got it sorted now, thanks for the help.

---

