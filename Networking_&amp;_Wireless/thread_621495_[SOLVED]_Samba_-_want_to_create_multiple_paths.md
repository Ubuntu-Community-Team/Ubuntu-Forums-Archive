---
title: "[SOLVED] Samba - want to create multiple paths"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by nickpaton on 2007-11-23
Gutsy 7.10 i386 desktop

My smb.conf file is set up to successfully link to any path or HDD I want, by altering path =  /xyz/abc/jkl, for example to the Public folder on my home directory on my Ubuntu PC:

```
[MyFiles]
    path = /home/myname/Public
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = 
    force group = 
    available = yes
    public = yes
    writable = no
```

or to the Media directory on another HDD on the Ubuntu PC:

```
[MyFiles]
    path = /media/sda1/Media
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = 
    force group = 
    available = yes
    public = yes
    writable = no
```

Currently I can only access a single location from another Windows PC on the network.

I would like to access a number of different locations and HDD's on the Ubuntu PC at any time via a series of shortcuts on the Windows desktop.

Is it possible to do this in samba or is there another way?

---

### Post by JKyleOKC on 2007-11-23
Yes, it's quite possible. The trick is to have one definition for each path you want, like this:

```
[Path1]
    path = /media/sda1/path1
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = 
    force group = 
    available = yes
    public = yes
    writable = no

[Path2]
    path = /media/sda1/path2
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = 
    force group = 
    available = yes
    public = yes
    writable = no
```

Each of these will show up in Windows as a separate folder on the system. My little LAN has four Linux boses and two running Win98SE, and some of the Linux boxes have as many as a half dozen such definitions for their copy of Samba (each of them runs its own Samba server to communicate with each other and with the Windows boxes). If you want to be able to write to the Linux files from Windows, be sure to put your Linux user name into the "force user" line for that path, and set the create and directory masks to 033 so that you as the owner have write permission.

Hope this helps!

---

### Post by nickpaton on 2007-11-24
Many thanks - works perfectly!

Nick

---

