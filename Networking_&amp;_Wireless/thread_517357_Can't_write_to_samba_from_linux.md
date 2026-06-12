---
title: "Can't write to samba from linux"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Hase on 2007-08-04
This may be an easy fix but I sure can't find it.  I have a Debian server running samba, sharing with Windows works perfectly.  On my other linux boxes, I can't get write permission or, for certain shares, read permission.  Looking at the logs, the linux box is attempting to access as a guest, not under the username under which I am locally logged in.

```

[share]
path = /mnt/share
browsable = yes
public = yes
read only = no
guest ok = yes
directory mask = 0755
write list = HASE

[backup]
path = /mnt/backup
browsable = yes
public = yes
read only = no
write list = HASE

[test]
path = /usr/test
read only = no
guest ok = yes

```

When logged into the local machine as user HASE:
share - I can read but not write
backup - I cannot access at all
test - I can read and write

The logs indicate the local system is not trying to login as HASE but as a guest or "nobody"
```

[2007/08/04 11:35:17, 1] smbd/service.c:make_connection_snum(950)
  192.168.xxx.xxx (192.168.xxx.xxx) connect to service test initially as user nobody (uid=65534, gid=65534) (pid 8437)

```
Anyone know what I have screwed up?

---

### Post by noob12 on 2007-08-04
Do you have **security=share** in the smb.conf by any chance?

Is the username HASE in uppercase an actual unix user on the server?  are you using an smbpasswd file on the server?  

How are you connecting from the linux clients? via  Nautilus or smb mounts?  Are you getting prompted for a username/password (or keyring password)?  I'd suggest that you try using **smbclient** to see if the behavior is different.


What are the local unix directory permissions on /mnt/backup on the server?

Side note, but insignificant:  **public=yes** is a synonym for **guest ok = yes**.

---

### Post by Hase on 2007-08-04
Yes, under global, security = share. 

The unix username is something else, all lowercase.  I am using smbpasswd.  The server unix user, smb user and the local unix user names are all the same, spelled the same, all lower-case.

This is via nautilus.

The server's /mnt/backup is owned by the same user above, 755.

I'll try connecting via smbclient and smbfs.

---

### Post by noob12 on 2007-08-04
With **security=share**, you should read the docs (**man smb.conf**) very carefully about this mode and username mapping.  The client need not send username/password when the server is in this mode. You can probably use an explicit connection to get around this.  You may want to use the default **security=user**.

---

### Post by DugieHowsa on 2007-08-07
Try using cifs instead of smbfs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

