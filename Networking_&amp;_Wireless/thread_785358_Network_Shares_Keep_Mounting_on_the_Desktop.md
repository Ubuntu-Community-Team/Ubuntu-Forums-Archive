---
title: "Network Shares Keep Mounting on the Desktop"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by rocksolidsr on 2008-05-07
I just upgraded to 8.04 yesterday and everything seems to be working just fine except for one thing that is kind of weird.

I have a shortcut on my desktop to my winxp shared folders and that works fine, however when I open it and open a subdirectory it mounts that subdirectory on the desktop automatically and I can't figure out how to stop that from happening 

Does anyone know how to stop that.

Thanks

---

### Post by rocksolidsr on 2008-05-07
I found the solution else where thought i would post it in case someone else needed it

There is a setting in gconf-editor that allows volumes to be hidden/visible on the desktop. From a terminal, 

```
gconf-editor
```

Browse to /apps/nautilus/desktop and uncheck "volumes_visible"

---

