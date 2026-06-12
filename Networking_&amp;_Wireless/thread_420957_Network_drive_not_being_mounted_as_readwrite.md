---
title: "Network drive not being mounted as read/write?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Kimppa on 2007-04-24
Hi

I'm having problems with mounting a network drive as read/write. Here's what I have:
I have a server running ubuntu 7.04 server edition. The local directory which I'm trying to share is "/projects"
```

drwxr-xr-x  4 kimppa kimppa  4096 2007-04-24 09:25 projects

```

The content of the projects folder is the following
```

drwxr-xr-x  4 kimppa kimppa 4096 2007-04-24 09:25 .
drwxr-xr-x 22 root   root   4096 2007-04-24 09:25 ..
drwxr-xr-x  3 kimppa kimppa 4096 2007-04-24 09:25 mdt
drwxr-xr-x  3 kimppa kimppa 4096 2007-04-24 09:25 pvp

```

Samba configs are the following
```

[projects]
  comment = Projects root directory
  path = /projects
  public = yes
  writable = yes
  valid users = kimppa
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

```


The computer I'm trying to mount with has kubuntu 7.04 desktop edition. I've created a mount point to /media/develop

```

drwxr-xr-x  2 root   root     4096 2007-04-24 09:28 develop

```

I'm mounting the network drive with the following command
```

sudo mount //192.168.11.4/projects /media/develop/ -o username=kimppa,dmask=777,fmask=777

```

The network drive is being mounted, but as read only?? 
```

kimppa@kleppane:/media/develop$ ls -al
total 16
drwxrwxrwx 1 root root 4096 2007-04-24 10:12 .
drwxr-xr-x 8 root root 4096 2007-04-24 09:48 ..
drwxrwxrwx 1 root root 4096 2007-04-24 09:25 mdt
drwxrwxrwx 1 root root 4096 2007-04-24 09:25 pvp
kimppa@kleppane:/media/develop$

```

I'm not able to write anything to the network drive, not with the username "kimppa", not even with sudo. What am I doing wrong? How can I get it to mount the network drive as read/write for all users?

- Kimppa

---

### Post by lassegs on 2007-04-24
How about setting file permissions on the server? 
```
 sudo chmod 777 ../projects 
```
(you should maybe find a better permission setting than 777?

---

### Post by Kimppa on 2007-04-24
Thank you for your very quick reply!
Yes, that helped, however, it's not quite secure :/ Anything else I could use, so that only "kimppa" would have read/write access.

... especially when it should be recursive to all files.

---

### Post by lassegs on 2007-04-24
Maybe: 

```
 sudo chown -R kimppa ../projects/ 
```
This would change it so you are the owner of /projects and all subdirs. The -R makes it recursive (all subdirs).
then set read write to you and your group, only read to others, execute to none. 
```
 chmod -R 664 ../projects/ 
```

Im not sure that these are the permissions you want, just try it out a bit. :)

---

### Post by Kimppa on 2007-04-24
Nope, already tried that, it will only cause the mount point to be unaccessable after mounting.

---

### Post by Kimppa on 2007-04-24
Ok, I got it sorted out. In samba configurations I changed "force group = nogroup" to "force group = kimppa"

---

### Post by lassegs on 2007-04-24
Goodie.

---

