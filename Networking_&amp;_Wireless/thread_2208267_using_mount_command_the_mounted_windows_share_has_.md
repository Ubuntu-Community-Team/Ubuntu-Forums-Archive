---
title: "using mount command the mounted windows share has no write permission"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2014-02-27
The share shows up in nautilus browse network with read and write permissions.

but when I do this

 sudo mount -t cifs -o username=lr //192.168.1.7/'users/lr/testshare' /home/scott/testrecord

I cant write to that location  /home/scott/testrecord
I made that folder from ubuntu browsing the network in nautilus, but my mount at  /home/scott/testrecord  shows these files locked
running this sudo chmod -R 777 /home/scott/testrecord did not help


If I run nautilus as root, I can write to the folder /home/scott/testrecord

picture

---

### Post by sdowney717 on 2014-02-27
I have no idea what to do.
Anyone ?

```
scott@scott-P5QC:~/testrecord$ ls -l
total 3742720
-rwxr-xr-x 1 root root 3832545280 Feb  7 19:10 Leverage_WPXVDT_2014_02_07_18_00_00.wtv
drwxr-xr-x 2 root root          0 Feb 27 11:03 Untitled Folder
drwxr-xr-x 2 root root          0 Feb 27 11:13 Untitled Folder 2

scott@scott-P5QC:~/testrecord$ sudo chmod -R 777 *

scott@scott-P5QC:~/testrecord$ ls -l
total 3742720
-rwxr-xr-x 1 root root 3832545280 Feb  7 19:10 Leverage_WPXVDT_2014_02_07_18_00_00.wtv
drwxr-xr-x 2 root root          0 Feb 27 11:03 Untitled Folder
drwxr-xr-x 2 root root          0 Feb 27 11:13 Untitled Folder 2

scott@scott-P5QC:~/testrecord$ chown -R scott *
chown: changing ownership of ‘Leverage_WPXVDT_2014_02_07_18_00_00.wtv’: Operation not permitted
chown: changing ownership of ‘Untitled Folder’: Operation not permitted
chown: changing ownership of ‘Untitled Folder 2’: Operation not permitted

scott@scott-P5QC:~/testrecord$ ls -l
total 3742720
-rwxr-xr-x 1 root root 3832545280 Feb  7 19:10 Leverage_WPXVDT_2014_02_07_18_00_00.wtv
drwxr-xr-x 2 root root          0 Feb 27 11:03 Untitled Folder
drwxr-xr-x 2 root root          0 Feb 27 11:13 Untitled Folder 2

scott@scott-P5QC:~/testrecord$ sudo chown -R scott *

scott@scott-P5QC:~/testrecord$ ls -l
total 3742720
-rwxr-xr-x 1 root root 3832545280 Feb  7 19:10 Leverage_WPXVDT_2014_02_07_18_00_00.wtv
drwxr-xr-x 2 root root          0 Feb 27 11:03 Untitled Folder
drwxr-xr-x 2 root root          0 Feb 27 11:13 Untitled Folder 2
scott@scott-P5QC:~/testrecord$ 

```

---

