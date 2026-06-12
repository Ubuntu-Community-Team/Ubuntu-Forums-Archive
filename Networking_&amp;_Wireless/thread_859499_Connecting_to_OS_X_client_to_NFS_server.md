---
title: "Connecting to OS X client to NFS server"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by schauerlich on 2008-07-14
I have a home server with the nfs-user-server package installed, and I'm having trouble getting OS X to connect to it. Googling around, it seems that the UIDs on OS X and Ubuntu start at different places (OS X at 501, Ubuntu at 1000). I followed this thread ([http://ubuntuforums.org/showthread.php?t=696629](http://ubuntuforums.org/showthread.php?t=696629)) and the link in the second post to remap 501 to 1000. However, now when I try to connect, it says "incorrect username and password."

/etc/exports:
```

/shared 192.168.0.0/24(rw,no_root_squash,async,no_subtree_check,insecure,map_static=/etc/nfs/osx.map)

```

/etc/nfs/osx.map:
```

uid 501 1000
gid 501 1000

```

Any ideas?

---

### Post by schauerlich on 2008-07-15
Bump.

---

### Post by schauerlich on 2008-07-17
Last bump.

---

### Post by cyberdork33 on 2008-07-17
You might have more luck in another forum. I requested it moved.

---

### Post by Sef on 2008-07-17
Moved to Networking and Wireless.

---

### Post by hanzomon4 on 2008-07-18
I think I know what problem you're having you have to add an option to the cli option in OSX to mount an nfs share because it looks in the wrong port range or something I'll post the exact option when I boot back into OSX.

---

### Post by hanzomon4 on 2008-07-20
add the "-o resvport" option

---

