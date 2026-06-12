---
title: "mount smb share (windows 2000 server)"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by rjchute on 2007-08-30
My Ubuntu machine is on a network with a domain controlled by a Windows 2000 Server box.  I can seemingly successfully mount a (smb) share found on the Windows 2000 Server box, however when I attempt to browse or ls the contents of the mounted directory, there is nothing there (not even the typical . and ..).  It seems as though I am authenticating correctly to the server, as when it asks me for a password (i am not using the password= directive) if I were to type in the incorrect password, it would give an authentication error (however typing in the correct password gives no error at all).  To top it off, if I go through the Gnome menus Places > Connect to Server... and do it that way, it works and I can successfully browse the windows share with all of the privileges of the username i am using to connect -- however most applications don't like this method and (i included) would prefer to have it mounted in a directory.  Any suggesstions as to why I would not be seeing any files in the mounted share?

---

### Post by f00buntu on 2007-08-30
Please post the mount command you used. Maybe you mounted the share using sudo and you don't see any files using nautilus/terminal as a regular user. 
Use the uid option in your mount command to give a regular user ownership of the mounted share, for example:

```
sudo mount -t smbfs -o username=YourWindowsUsername,uid=yourlocalusername //SERVERNAME/ShareName /mount/point
```

---

### Post by rjchute on 2007-08-30
That thought occurred to me, however ```
sudo ls
``` and ```
sudo su -
ls
``` produces the same results as simply running ls as my current user.  I will definately give your uid suggestion a go and let you know the outcome.

---

### Post by rjchute on 2007-08-30
No such luck :confused:

```

~$ sudo mount -t smbfs -o credentials=/home/linuser/smbshareJobs,uid=linuser //winserver/Jobs /media/Jobs 
~$ cd /media/Jobs/
/media/Jobs$ ls -a
/media/Jobs$ 

```

as well, to be sure,

```

~$ sudo umount /media/Jobs
~$ sudo mount -t smbfs -o username=winuser,uid=linuser //winserver/Jobs /media/Jobs
Password: 
~$ cd /media/Jobs/
/media/Jobs$ ls -a
/media/Jobs$

```

and again, through Gnome,  Place > Connect to Server... works as expected.

---

### Post by f00buntu on 2007-08-31
try to mount the share using cifs instead of smbfs, see what happens

```
sudo mount -t cifs -o credentials=/home/linuser/smbshareJobs,uid=linuser //winserver/Jobs /media/Jobs
```

---

### Post by rjchute on 2007-08-31
Worked like a charm =D>  I should have tried CIFS sooner....

---

