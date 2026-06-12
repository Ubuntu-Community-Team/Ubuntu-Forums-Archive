---
title: "Mounting a Windows Share Drive"
date: 2005-07-12
forum: Networking &amp; Wireless
---

### Post by ux5b2 on 2005-07-12
Hello,  
I need to mount a windows share drive at work on Ubuntu and be able to modify and save within that mount.  When I used to use windows I successfully connected to the computer by //ip/folder and then mapping the drive and entering my username and password.  I could then modify files in the shared folder.  However with Ubuntu, I successfully mounted the drive but do not have permissions to modify and save files in the mount.  This is the command I used to mount the drive:

sudo mount -t smbfs -o username=xxx,password=xxx //128.227.16.140/web /home/a/Desktop/mount

This successfully mounted the drive however, like I said I cannot modify files.  Any help is greatly appreciated.  Thanks!

---

### Post by Dogmeat on 2005-07-12
nevermind I misread your post, thought you were sharing with samba  :-#

---

### Post by Dogmeat on 2005-07-12
Try this in a terminal:

```
umount /home/a/Desktop/mount
cd /home/a/Desktop
ls mount -l
```

See if you own the mount directory and / or you have write permissions to it. If not, set your permissions and try mounting again!

---

### Post by ux5b2 on 2005-07-12
After I mount the drive the ownership is changed to root:root.  When I try to chown so that I own the folder, it gives me the error: chown: changing ownership of `mount': Operation not permitted.   Any ideas? 

Thanks

---

### Post by geearf on 2005-07-12
you have to tell the system a user can go in
i use this in fstab to do so
/dev/hde1       /home/gee/c    ntfs    nls=utf8,ro,user,exec,auto,uid=1000,gid=100

---

### Post by ux5b2 on 2005-07-12
Could you please elaborate on how that works and what I actually have to type in.  Im pretty new to linux so I dont quite understand how do to that.  Thanks.

---

### Post by Dogmeat on 2005-07-12
[QUOTE=geearf]you have to tell the system a user can go in
i use this in fstab to do so
/dev/hde1       /home/gee/c    ntfs    nls=utf8,ro,user,exec,auto,uid=1000,gid=100[/QUOTE]
 Edit /etc/fstab as super user:

```
sudo gedit /etc/fstab
```

Now at the bottom of this file, add this:
```

//128.227.16.140/web /home/a/Desktop/mount /home/a/Desktop/mount uid=1000,gid=1000,username=xxx,password=xxx,dmask=700,fmask=700 0 0 0 0
```

Adding this line to fstab will make samba mount your share everytime you boot!

Note: You have to add all this in a single line. And please remove the blank space after dmask, I guess the line was too long, its a forum bug. In your fstab, it should read "dmask=700" without the quotes.

If you use an international keyboard like me, you might want to add "utf8," before uid to enable special keys (like é or ö) in the mounted system.

- uid is your user id (1000 is the default user ubuntu creates on install).

- gid is the group id (again ubuntu puts the default user in group 1000).

- dmask is the permissions of the mount directory (700 means owner has read/write/execute)

- fmask is the permissions of the files in the mount directory (700 means owner has read/write/execute)


After you add the line, save the file, close gedit. and go to the terminal and type:

```
sudo umount /home/a/Desktop/mount
sudo mount -a
```

to re-mount all the filesystems in fstab. You should now have read and write permissions!

---

