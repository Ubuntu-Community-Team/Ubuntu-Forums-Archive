---
title: "Davfs2: Cannot connect to secure WebDav Server!"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Pancake8989 on 2008-04-18
Hello all.

I have spent a bit of time researching this issue. When I attempt to mount a webdav server using davfs2, I get the following error:
```
/sbin/mount.davfs: Mounting failed.
GSSAPI authentication error (Unspecified GSS failure.  Minor code may provide more information: No credentials cache found)
```

I know it is making a connection because it asks me to accept the certificate.

And in my **/etc/fstab** folder:
```
#WebDav Server
https://example.com/folder /home/pancake/mnt/vdrive davfs rw,noauto,user 0 0
```

Thanks.

---

### Post by brpege on 2008-04-20
I'm having the same issue.  I'm connecting to a M$ server with the webdav folder served by IIS,  I wonder if this could be the source of my troubles...
Do you know if the webdav you're trying to connect to is also Microsoft?

---

### Post by Pancake8989 on 2008-04-21
Sure is :(

And fyi, opening it in Firefox under Windows works fine, but Firefox under Ubuntu doesn't work :'(

Also, I deleted the content in my ~/.davfs2/davfs2.conf file

---

### Post by gkffjcs on 2008-04-28
I'm having the same problem mounting my University webdav folder. However, I have found quite by accident that using the webdavs:// protocol in the kde konqueror filemanager/web browser I was actually able to access my webdav folder and read/write to/from it, with no issues at all. So if you want access, konqueror works. Just type in webdavs://example.server.com/somefolder, that will open up a password prompt, enter your password and user name, and it should work fine.

---

### Post by Pancake8989 on 2008-04-28
> **gkffjcs said:**
> I'm having the same problem mounting my University webdav folder. However, I have found quite by accident that using the webdavs:// protocol in the kde konqueror filemanager/web browser I was actually able to access my webdav folder and read/write to/from it, with no issues at all. So if you want access, konqueror works. Just type in webdavs://example.server.com/somefolder, that will open up a password prompt, enter your password and user name, and it should work fine.
Yea I just discovered that :)

However, when I try to add a file, it just hangs at 100% for a while :(

---

