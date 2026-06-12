---
title: "Help trying to 'umount' a network drive (while server is down)"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by cahumphrey on 2007-07-25
I am trying to unmount my '/server' share, because I shut the server down.

When I attempt to do so, it gives me this error:

```
unmount error 16 = Device or resource busy
Refer to the umount.cifs(8) manual page (man 8 umount.cifs)

```

Here is the command I used to create the share:

```
sudo mount -t cifs -o username=chris //192.168.1.102/public /server/
```

Here is the command I am using to try to umount the share:

```
 sudo umount -f  //192.168.1.102/public /server
```

When the server is running I can easily umount and remount the shares, but since it is offline I am not able to get rid of the share. When I try to open my nautalis browser (which has a link to '/server') it doesn't respond. 

Any suggestions to force a umount?

---

### Post by kidders on 2007-07-27
Hi there,

Unmounting a network filesystem while the server is unavailable isn't necessarily wise ... especially if I/O is being done asynchronously! (Think of it as being similar to whipping out a USB disk without telling your OS first.) Unfortunately, there *are* times when you just don't have a choice.

You could try a "lazy" umount (see umount's man page). That might do the trick.

---

