---
title: "gvfs and Vista shell folders"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by NTolerance on 2008-10-07
I've got a shared drive on my Vista PC that contains a few of the Windows "shell folders" (Documents, Downloads, Pictures, etc...).  gvfs seems unable to give me write access to these shell folders but grants write access to any other folders.  If I access the Vista shared drive with Windows XP I can write to the shell folders fine, but not from Ubuntu.  You can see the lack of write access here:

```
nt@dv6000t:~/.gvfs/d_files on meganuke$ ls -la
total 0
drwx------ 1 nt nt   4096 2008-10-03 13:28 .
dr-x------ 3 nt nt      0 2008-10-06 01:53 ..
drwx------ 1 nt nt  65536 2008-10-04 12:51 Apps
dr-x------ 1 nt nt  20480 2008-09-29 13:08 Docs
drwx------ 1 nt nt   4096 2008-09-15 20:32 Drivers
drwx------ 1 nt nt   4096 2008-09-29 13:07 Games
dr-x------ 1 nt nt 163840 2008-10-04 02:35 Pictures
drwx------ 1 nt nt      0 2008-09-17 08:15 $RECYCLE.BIN
drwx------ 1 nt nt      0 2008-09-17 19:52 System Volume Information
dr-x------ 1 nt nt   8192 2008-10-04 14:27 Temp

```

I tried to chmod those folders to 700 but I get this error:

```
chmod: changing permissions of `Docs': Operation not supported
```

Is there any way to get gvfs to give me the proper permissions for this network share?

---

### Post by NTolerance on 2008-10-10
bump

---

### Post by NTolerance on 2008-10-27
bump

---

### Post by NTolerance on 2008-11-03
After reformatting and upgrading to Intrepid I gave up on gvfs altogether and mounted my Windows share in fstab.  I found the same issue with the Vista shell folders, only this time I was able to chmod +w them to allow write access.  This is all very weird.

---

### Post by nomizzz on 2008-11-19
I'm having an extremely similar issue, but the folder whose permissions I cannot change is a Windows XP folder that resides on a FAT32 partition whose other files can be chmod-ed or chown-ed without problems.  When I try to play around with this one, I get a ```
chmod: changing permissions of `/media/d/Shared Documents': Operation not permitted
``` error without further explanation.

Update: I can now chmod without issue, but even when I add read, write and execute permissions to all, I still cannot make directories or files, and there's still a lock on the folder in nautilus.  "chown" also still yields the same "Operation not permitted" error message.

---

