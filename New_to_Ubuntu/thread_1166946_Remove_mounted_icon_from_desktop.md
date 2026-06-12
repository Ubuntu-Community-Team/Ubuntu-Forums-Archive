---
title: "Remove mounted icon from desktop"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by GXice on 2009-05-22
Hi guys, I have an iPod icon on my desktop from when my ipod was plugged in last week. I've disconnected the USB cable but the icon doesnt disappear. Right clicking doesn't offer an option to remove.

I've also got another icon for a mounted hard drive that I recently bought. I dont need the icon on the desktop. How can I get rid of the icon without unmounting the hard drive?

Thanks ;)

---

### Post by nandemonai on 2009-05-22
> **GXice said:**
> Hi guys, I have an iPod icon on my desktop from when my ipod was plugged in last week. I've disconnected the USB cable but the icon doesnt disappear. Right clicking doesn't offer an option to remove.

I've also got another icon for a mounted hard drive that I recently bought. I dont need the icon on the desktop. How can I get rid of the icon without unmounting the hard drive?

Thanks ;)

ALT-F2 to bring up a run prompt.

```
gconf-editor
```

Apps -> Nautilus -> Desktop then uncheck 'volumes visible'.

---

### Post by GXice on 2009-05-22
Sweet, thanks for that :)

---

