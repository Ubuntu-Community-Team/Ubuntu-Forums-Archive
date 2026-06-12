---
title: "mount cifs drive without sudo or fstab"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by lp.descamps on 2017-02-11
hi

i try to mount this

```
mount.cifs //10.11.12.13/shared /home/linux/nas -o user=username,pass=password,uid=pi,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm
```

i get error

```
mount.cifs: permission denied
```

if i run this 
```
sudo mount.cifs //10.11.12.13/shared /home/linux/nas -o user=username,pass=password,uid=pi,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm
```

it's working ok.

i dont want to use fstab or sudo to mount this drive as i want to add it in a bash script.

any idea?

thanks

---

### Post by TheFu on 2017-02-11
The power to mount is the power to destroy, so it needs to be managed specifically by a root account. That's why **sudo** is necessary.

However, you can pre-configure it to mount to a specific location when accessed (provided the storage is available) using **autofs**.

Or you can just put the 
```
sudo mount -t cifs //10.11.12.13/shared /home/linux/nas -o user=username,pass=password,uid=pi,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm
``` into a file, make the permissions eXecutable and run it that way. That would be *a script*.

If you want anyone to be able to do this, you'll want to modify the **sudoers** file and specify this exact, specific, command carefully to be available for anyone on the system to run. I would have to lookup how to do it, but sudo HAS the ability to allow 1 userid, a group or all userids to run exact, specific, commands with strictly controlled options.  777 permissions is also not a smart choice.  664 and 775 would be better to prevent anyone who happens onto the box from being able to delete files.  Just sayin'. Permissions are the cornerstone of all Unix security. Allowing "other" to have write access undermines this. If you've ever been hacked, and I have, you'll appreciate why not allowing "other" write outside of /tmp/ is a good idea.

BTW, it would be smarter to put the credentials into a separate file and pass that in as **credentials=** in the options. Anything put on a command line can be seen by anyone on the system by listing the process list, as can the /etc/fstab file contents. Best to put credentials somewhere that only the userid doing the mounting or only root can view.  I put them in /root/. Just be certain to back that up with your normal backups of /home/ and /etc/ and all the other data in DBs and servers running on the box.

I wouldn't mount network storage for general use under a HOME directory for a few reasons. Got burned doing that about 20 yrs ago and learned my lesson.  I don't use /media/ for manually mounted storage either - been burned there too.  It is a "too many cooks in the kitchen issue."

So - you have a few different options. Quick script with sudoers or autofs. They are about equally complicated the first time, but autofs is *bonehead simple* after that.  autofs is really, really convenient too.  Storage gets mounted automatically when you want it. Just access the location and the first use mounts it.  After 5 minutes of non-use, it is automatically unmounted, saving resources and connections.  Plus, I've had issues with long connected mounts to Windows systems. Autofs seems to solve that.  I find autofs handy for USB storage too.  The only real trick is to remember which storage is and isn't available.  Looking for unavailable storage will lock up the process until the timeout is reached. Definitely set the timeout.

---

### Post by Morbius1 on 2017-02-11
I can give you an alternative but it violates one of your requirements - adding something to fstab:

This would be the fstab statement:
```
//10.11.12.13/shared /home/linux/nas cifs user=username,pass=password,uid=pi,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm,noauto,user 0 0
```
When the system boots the share will not mount ( the "noauto" option ). But you can mount it without using sudo with a:
```
mount /home/linux/nas
```

---

### Post by DuckHook on 2017-02-11
Another alternative is to use FUSE: [http://manpages.ubuntu.com/manpages/precise/man8/mount.fuse.8.html](http://manpages.ubuntu.com/manpages/precise/man8/mount.fuse.8.html)

TheFu is correct. By default, the mount subsystem assumes that any mounted disk should be available, at least in principle, to all users. FUSE makes the opposite assumption: that, by default, FUSE mounts should be available only to one specific user. *Provided your source filesystem has the right permissions* FUSE will not require root. However, it will mount into a subdirectory under your /home directory, so only you will be able to use it.

---

### Post by lp.descamps on 2017-02-19
Thank you all for the great tips

---

