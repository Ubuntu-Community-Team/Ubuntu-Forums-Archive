---
title: "File System Folders Window Keeps Automatically Launching"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by SimplyTed on 2011-06-22
Hi Everyone;

I've recently made the leap from Windows Vista to Ubuntu 11.4. 

Lately, a window displaying my main hard drive file system has started automatically launching itself (more than once an hour). Seems to happen when I'm using my computer, and the timing doesn't indicate any specific schedule. Why is it doing this and how do I stop it?

Thanks in advance,

Ted

---

### Post by Mr Stoozer on 2011-06-22
> **SimplyTed said:**
> Hi Everyone;

I've recently made the leap from Windows Vista to Ubuntu 11.4. 

Lately, a window displaying my main hard drive file system has started automatically launching itself (more than once an hour). Seems to happen when I'm using my computer, and the timing doesn't indicate any specific schedule. Why is it doing this and how do I stop it?

Thanks in advance,

Ted

Do you mean a nautilus window displaying the contents of / ?
the same as if you ran ```
nautilus /
```

If so, i think i had this bug a while ago. Seem to remember setting the mounted drives to show on the desktop fixed it.....that is of course if you have them hidden!

Show mounted drives on desktop:
```
gconftool-2 --type Boolean --set /apps/nautilus/desktop/volumes_visible 1
```

Hide mounted drives from desktop:
```
gconftool-2 --type Boolean --set /apps/nautilus/desktop/volumes_visible 0
```

Once you've set to show, logout & back in. If all is well try and set back to no show.

---

### Post by SimplyTed on 2011-06-22
It's exactly as if I clicked on my Filesystem icon from the left slideout menu. A window opens showing all the folder icons from my main drive, but without my clicking on it.

---

