---
title: "Need help understanding a command line"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by webwiller on 2009-10-14
Hi guys!
Days ago I opened a 3d because I have a problem regarding permissions about files on an external media station (external hdd vfat). Suddendly I could not delete or move files on my media-box cause they belong to root.
The last comment on that 3d (which you can see here: [http://ubuntuforums.org/showthread.php?t=1274494&page=2]("http://ubuntuforums.org/showthread.php?t=1274494&page=2"))
is the one below, which I did not execute in terminal cause I had to go and could not go back to my media-box issue till now.
Now I need to understand the command line that bloke gave me and see if that is the solution.
The line is as follows:
> mount -t vfat /dev/sdb1 /media/disk/chri -o uid=1000,gid=1000,dmask=000,fmask=111

-What does this line "says"?
-Would it change file permission from "root" to "user"?

Tyvm!;)

---

### Post by falconindy on 2009-10-14
The line the **admin** gave you is correct. The uid and gid flags set the **u**ser and **g**roup specified as owner of the drive. In this case, userid 1000 is the user who installs the OS, which is likely you.

In case you'd like the whole thing dissected:

```
-t vfat          -   type of drive to mount
/dev/sdb1        -   partition to mount
/media/disk/chri -    mount point
-o               -    specify the following additional options...
   uid=1000,     -    set userID 1000 as owner
   gid=1000,     -    set groupID 1000 as owner
   dmask=000,    -    permission mask on directories
   fmask=111     -    permission mask on files
```
You can think of masks as being the opposite of permissions. They're subtracted from the effective permissions. In this case, setting a file mask of 111 means that no one on the system has the ability to execute a file.

---

### Post by webwiller on 2009-10-14
tx a lot!
But...how do you get to know what these numbers (1000, 111, ect...) mean?

---

### Post by falconindy on 2009-10-14
I know what they mean because of context.
```
grep "1000:1000" /etc/passwd
```
Will show your user account. Every file is owned by a user and also a group. Rather than reinvent the wheel, I'll point you [here](http://en.wikipedia.org/wiki/File_system_permissions),for a fairly in depth article about POSIX file permissions. I would skip the first 2 sections and read the part about notation.

---

### Post by webwiller on 2009-10-14
> chriz@chriz-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/disk/chri -o uid=1000,gid=1000,dmask=000,fmask=111
[sudo] password for chriz: 
mount: /dev/sdb1 già montato o /media/disk/chri occupato
mount: secondo mtab, /dev/sdb1 è montato su /media/disk
chriz@chriz-laptop:~$ 


This is the "answer I got". Translated it means:
mount: /dev/sdb is already mounted or /media/disk/chri is busy
mount: in mtab opinion, /dev/sdb1 is mounted on /media/disk

Yes, it is mounted, but files on "chri" directory are owned by root and not by me! (???)

---

### Post by coldReactive on 2009-10-14
Also, **man mount** may help you in the future when figuring out what means what.

---

### Post by falconindy on 2009-10-14
> **webwiller said:**
> This is the "answer I got". Translated it means:
mount: /dev/sdb is already mounted or /media/disk/chri is busy
mount: in mtab opinion, /dev/sdb1 is mounted on /media/disk

Yes, it is mounted, but files on "chri" directory are owned by root and not by me! (???)
So you'll need to unmount it first with `sudo umount /dev/sdb1`

---

### Post by webwiller on 2009-10-14
I did:
> sudo umount /dev/sdb1

and than I did:
> mount -t vfat /dev/sdb1 /media/disk/chri -o uid=1000,gid=1000,dmask=000,fmask=111 

and I received the answer that "**mount point /media/disk/chri does not exist**"

How comes? If I mount /media/disk (my media-box) I can find a directory chri exactly under /media/disk! But if I unmount it, obviously is not there anymore! So...what is the issue?

---

### Post by falconindy on 2009-10-14
You need to create the directory (mount point) first.

---

