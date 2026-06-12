---
title: "mounting at startup drives and hiding them from desktop"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by dyyyy on 2009-02-14
hi,
i have two questions 
-how can i mount automatically drives at startup.
-can i hide the mounted drives from my desktop.
thx

---

### Post by cerealtx on 2009-02-14
> **dyyyy said:**
> hi,
i have two questions 
-how can i mount automatically drives at startup.
-can i hide the mounted drives from my desktop.
thx

[http://lloydpuckitt.wordpress.com/2007/10/10/mount-drive-at-startup/](http://lloydpuckitt.wordpress.com/2007/10/10/mount-drive-at-startup/)
got 1/2 of your answer

---

### Post by drs305 on 2009-02-14
If you are using the normal gnome desktop (i.e. don't have it turned off with compiz), you can edit display settings with gconf-editor. You can manually start "gconf-editor" or just run the following to hide mounted volumes. You can reverse the setting by changing the setting to *true*
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible '**false**'
```

---

### Post by Ben Page on 2009-02-14
Use these tools, ntfs config (NTFS configuration tools), witch will mount the volumes you want at startup - note, unmount any volumes you have mounted and then run the tool, and use ubuntu tweak to set up desktop icons. Both of these tools can be found in synaptic.

---

### Post by Andy06 on 2009-02-14
Disk Manager does an even better job than NTFS config and has more features. It is also more powerful in that it can mount "dirty" drives (those that weren't "safely" removed from windows).

---

