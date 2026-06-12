---
title: "Finding my smb share"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by ysr23 on 2011-09-08
Hi there - i have a FreeNAS server which i can connect to through nautilus under 'network' but what i cannot do is find the shares either in 'mnt' or 'media' or anywhere else for that matter or connect to it via command line.

in nautilus i can right click and see its at smb://freenas

any ideas how i can access this through /mnt/ or /media ? or from cli?

many thanks

---

### Post by snip3r8 on 2011-09-08
You need to use nfs if you want to mount shares like drives

[http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29]("http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29")

---

### Post by papibe on 2011-09-08
Usually smb shares are auto mounted on ~/.gvfs

If you really need to access your share using the command line, I would suggest to explicitly mount it where you need it. In order to do that, you will require to install a new package (not usually included with samba):
```
$ sudo apt-get install smbfs
```
Once that's installed you may be able to mount your shares, using a command similar like this:
```
$ sudo mount -t smbfs //freenas/sharename /media/myshare
```
or like this (preferred):
```
$ sudo mount -t cifs //freenas/sharename /media/myshare
```
If the share is user and password protected you would need to change it a little bit:
```
$ sudo mount -t cifs -o username=<name>,password=<passwd> //freenas/sharename /media/myshare
```
Hope it helps,
Regards.

---

### Post by ysr23 on 2011-09-08
> **snip3r8 said:**
> You need to use nfs if you want to mount shares like drives

[http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29]("http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29")


rly?  - its not possible to mount the cifs/smb freeNAS shares as a drive?  


yet i can through nautilus?  sorry i'm not quite with you here - could you perhaps expand?

---

### Post by ysr23 on 2011-09-08
> **papibe said:**
> Usually smb shares are auto mounted on ~/.gvfs

If you really need to access your share using the command line, I would suggest to explicitly mount it where you need it. In order to do that, you will require to install a new package (not usually included with samba):
```
$ sudo apt-get install smbfs
```

superb  - now i can see it in my 'media' folder - many thanks

---

