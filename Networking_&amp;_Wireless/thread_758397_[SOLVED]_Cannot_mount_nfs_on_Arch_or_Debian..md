---
title: "[SOLVED] Cannot mount nfs on Arch or Debian."
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by perlluver on 2008-04-18
I set up nfs on my Ubuntu machine, I set up the Arch machine to mount from fstab but it didn't.  I mounted it manually but since it has to be root, I cannot access the folder to write to it.  The same as the Debian machine, root mounted can't access the folder.  So my question is, how do I mount it so I can write to it from those computers?

---

### Post by MrFSL on 2008-04-18
The question concerning mounting nfs drives (and all drives for that matter) have been answered many times. Search the forums and you WILL find the answer SEVERAL places.

Let me help though if I can.

First off, on the server make sure that permissions are correct as well as the nfs server.

For instance, make sure that the UIDs of users on the server corresponds to the UIDs on the clients, or that you have the correct settings in /etc/exports so as to force or "squash" particular users. For instance, on my server I have a statement like this:
> /home/share     192.168.10.0/24(insecure,rw,sync,no_subtree_check,all_squash,anonuid=1000,anongid=1000)
Which is squashing all users and forcing UID and GID to 1000.

For more information type the following commands in terminal:
```
man nfs
```

On the client machine, if you want auto mounting you will probably want the 'auto' option, along with 'users' if you want this to automatically mount.

An example might be:
```
192.168.10.5:/home/share /media/share nfs auto,users,rsize=8192,wsize=8192 0 0
```

For more information type the following commands in terminal:
```
man nfs
man mount
man fstab
```

Hope this is helpful to you and others.

---

### Post by perlluver on 2008-04-18
Got it fixed, turned out I created both folders as root, instead of as a normal user.

---

