---
title: "Sharing a shared folder through FTP"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by kyleflan on 2007-09-12
I'm trying to put all my server duties on to my Ubuntu machine. I have an FTP server set up and can access it. However, I'd like to be able to access a shared folder on another machine through the FTP server. I can access the shared folder through the network browser in Ubuntu.

Now, I'm not a total n00b at Linux, but I'm not an advanced user either. So what I'm trying to do may not be possible, but I figured I'd ask.

Here is what I've tried so far.

Let's say the folder I want to be shared on the FTP is on machine COMP and the folder is SHARED. The FTP directory is in /home/ftp on my Ubuntu machine. 

I tried
```
ln -s /smb://HOME/SHARED/ /home/ftp/
```
And whenever I try to access the link in the /home/ftp/ directory I get this:

> The link "SHARED" is Broken. Move it to Trash?
This link can't be used, because its target "/smb://HOME/SHARED/" doesn't exist.

Any other ideas? I welcome any suggestions.

-Kyle

---

### Post by kidders on 2007-09-14
Hi there,

> **kyleflan said:**
> ln -s /smb://HOME/SHARED/ /home/ftp/This symlink is meaningless (unless, I suppose, you really do have a directory called "/smb**:**" in your filesystem).

Network filesystems are no different than ones on CDs or hard disks ... if you want your system to be able to access them, mount them. I would be surprised if your FTP server (or any other application) gave you any trouble then, since it wouldn't be able to distinguish remote files from local ones.

---

