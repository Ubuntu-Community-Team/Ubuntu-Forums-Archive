---
title: "Samba\file permissions"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Tsu on 2009-07-24
I have set “guest ok = yes” under a share in the samba configuration file.

I then mad the following changes

chmod -R 775 /srv/samba/share
chown -R nobody:nogroup /srv/samba/share

Yet some of the files seem to be read only.

I note that some folder will not let me save files to them. Even then the ls -l shows that the folder have the following read/write permissions.

drwxrwxr-x

I also note that some of the files have the following permissions set.

-rwxrwxr-x

Is there a guide to understanding file permission on a windows network share. As I tried turning “guest ok = no”. Then made a user account using “sudo adduser test”. Then setting “admin users = test”

[https://help.ubuntu.com/9.04/serverg...-security.html](https://help.ubuntu.com/9.04/serverg...-security.html)

This still failed. I could not log onto the share using the user account and password I had created.

Is there a guide that explains file permissions and how they work for file sharing from a ubuntu file server to windows machines?

---

### Post by swerdna on 2009-07-24
I assume you made the share in smb.conf, not with the sharing tool in Nautilus, is that correct?

Can you print here please the filtered version of smb.conf that you get when you run this terminal command:```
testparm -s
```and also the ls -l for the shared directory and for the directory itself; i.e. run these two:
[LIST]
[*]ls -l /path_to/shared_directory
[*]ls -l /path_to/
[/LIST]

PS the link is broken in your post.

---

