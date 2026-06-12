---
title: "usb drive help"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-06-05
is there someway to configure ubuntu so that it writes to usb drives straight away so that i dont have to unmount them as its really annoying when i create a folder but forget to unmount the drive and just remove it straight away.?

---

### Post by 123456789123456789123456 on 2009-06-05
In order for any OS to use a device, it must first mount it.
Ubuntu should mount USB disks, as soon as they are incerted.  I don't know of any way to have Ubuntu automatically unmount the drive, except when you restart, or shutdown the computer, the drive are unmounted at that time.

---

### Post by anewguy on 2009-06-05
I believe what you are asking is if there is a way for Ubuntu not to use caching on writes to a USB drive or stick.  I don't know how to do it without doing some digging, but I'm sure there must be a way to turn off caching on a USB device.  I would suggest doing a google search with the following:

ubuntu usb drive disable cache

See if something turns up.

I think it will have something to do with the mount and the sync parameters, but I'm not sure.

Dave :)

---

