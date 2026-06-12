---
title: "Trouble changing permissions on external HDD"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by swarup on 2009-09-10
I've got a 1 TB external HDD (brand: "FantomDrives"), and can connect to my laptop via either USB or 800FW. Either way, the ext3 partition on it mounts fine but with no read or write permission. If I open nautilus to root (gksudo), then I can read and write just fine to it. But I'd like to be able to open nautilus in the normal way and have permissions to do my work.

I tried using chmod:

```
:~$ chmod -R +w /media/disk
chmod: changing permissions of `/media/disk': Operation not permitted
chmod: changing permissions of `/media/disk/lost+found': Operation not permitted
chmod: cannot read directory `/media/disk/lost+found': Permission denied
```

That obviously didn't work, so I tried the same command, using sudo:

```
:~$ sudo chmod -R +w /media/disk
[sudo] password: 
:~$ 
```

It accepted the command, but still had no effect on changing the permissions.

At least the way I've done chmod, it didn't work as you see. Guidance? Suggestions?

---

### Post by nothingspecial on 2009-09-10
```
sudo chown -R username:username /media/disk/
```
```

sudo chmod -R (permissions you want maybe 755) /media/disk/
```

---

### Post by DaithiF on 2009-09-10
Hi, prefix your chmod command with sudo ... since root owns the files then only root can change their permissions.

alternatively (and probably better approach), is to change the owner of the files to be you rather than root, that way you can keep write permissions just for yourself rather than having the drive globally writeable.

```
sudo chown -R yourname.yourgroup /media/disk
```

---

### Post by swarup on 2009-09-10
Thanks-- it worked great. :)

---

### Post by ayenack on 2009-09-10
I would just make a folder on the drive owned by you and use that rather than changing the permission on the whole drive.

[B]sudo mkdir /media/data-rw/drop-box (where data-rw is the name of the drive and drop-box is the name of the folder.)
sudo chown your_username:your_username /media/data-rw/drop-box[/B]

That way you're not changing the root of the hard drive.

---

### Post by swarup on 2009-09-10
> **ayenack said:**
> ...That way you're not changing the route of the hard drive.

What you do mean by "changing the route of the hard drive"? My read/write permissions are now working, and the route (location?) of the drive is still /media/disk.

---

### Post by ayenack on 2009-09-10
It was a quick reply didn't really explain myself well.

What I mean is that the drive was originally owned by root user I would say it's better to leave the drive owned by root and just create a folder owned by you then put files into that.

Others will most likely will beg to differ but I would say it's more secure to do it that way.

---

### Post by thinking2loud on 2009-09-10
Happy homonyms, everybody!!!

You want the **root** directory of the drive owned by the **root** user.  You probably want the mount point owned by the root user too.  You should have a directory on your external drive owned by [username], and you should put your stuff in that directory.

---

### Post by ayenack on 2009-09-10
You're right. Not sure what I was thinking. I'll change it.

Spelling never been a good point for me especially when I'm tired. LOL. Route instead of root emmm...

---

