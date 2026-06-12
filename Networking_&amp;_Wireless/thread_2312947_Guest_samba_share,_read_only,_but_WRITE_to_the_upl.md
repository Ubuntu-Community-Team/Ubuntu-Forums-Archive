---
title: "Guest samba share, read only, but WRITE to the uploads folder"
date: 2016-02-08
forum: Networking &amp; Wireless
---

### Post by nyktovus on 2016-02-08
I am running Ubuntu server 14.04 with a samba share. 


i have a user Timmy. 
Timmy groups : users

It works great, but the guest users cant write to the uploads folder.. everything shows up as read only. 

==================

Here is the ls of the shared directory. 
$$ls -l

drwxrwsr-x 522 own3r users 36864 Jan 11 11:31 music
drwxrwsr-x  94 own3r users 36864 Jan 11 11:31 pics
drwxrwxr-x  24 own3r users  4096 Feb  7 23:59 reads
drwxrwsr-x  15 own3r users  4096 May 19  2015 software
drwxrwsr-x   7 own3r users  4096 Feb  7 10:44 uploads
drwxrwxr-x  19 own3r users 32768 Jan 25 10:45 video

Smb.conf::

#======================= Global Settings =======================

[global]
        path = /data/trunk
        hosts allow = 192.168.2.
        netbios name = trunk
        security = user
        map to guest = bad user
        os level = 20
        server string = Trunk
        workgroup = COALITION
        socket options = TCP_NODELAY

#======================= Share Definitions =======================


[data]
        create mask = 2775
        directory mask = 2775
        browsable = yes
        force user = timmy
        public = yes

---

### Post by bab1 on 2016-02-08
By default the guest user (and group) is nobody:nogroup.  I would think that the guest user will have access with this line in the share definition```
force group = users
```  Of course, if the files in the directory are owned by any other group or owner the access to those files will be restricted to read only.

I notice you have defined the path to the share globally.  Instead you should add the path to each share you define and remove the path parameter from the global section.

---

### Post by nyktovus on 2016-02-08
FIXED!
that helped alot. 
Turns out i needed to add 
read only = no

then it all worked as planned !

---

