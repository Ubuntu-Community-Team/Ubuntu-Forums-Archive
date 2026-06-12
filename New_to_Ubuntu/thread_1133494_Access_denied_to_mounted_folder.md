---
title: "Access denied to mounted folder"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Phil Doomen on 2009-04-23
I have searched quite a bit but I presume I am not using the right search words as I'm sure this has been asked a million times but I just can't find it..... so here goes...

If I use the mount command I have to do so as sudo but if I use sudo I don't have access to the folder as I'm not root.  I have tried adding myself to the root group and tried to change the permissions using sudo nautilus but it won't let me change them from root.  How can I mount a filesystem and have access to it as myself?  I'm trying to access a shared folder on the host (8.10) using a VirtualBox guest of 9.04 beta.

Your expertise and patience would be greatly appreciated.

Phil

---

### Post by Ticketoride on 2009-04-23
See here ---> [https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by andrew.46 on 2009-04-23
Hi Phil Doomen,

I ran in to this problem recently and rather than mount *manually* I added the following to fstab:

```
share /home/andrew/Desktop/share vboxsf uid=andrew,gid=users 0 0
```

Here you can see that my shared folder is:

```
/home/andrew/Desktop/share
```

and I have set owner to 'andrew' and group to 'users':

```
uid=andrew,gid=users
```

and this has worked well for me and has ensured that my shared folder is automatically ready for use when I logon. Perhaps this might work better for you as well?

Andrew

---

