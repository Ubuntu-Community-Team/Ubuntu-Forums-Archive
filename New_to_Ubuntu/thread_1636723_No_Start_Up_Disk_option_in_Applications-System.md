---
title: "No Start Up Disk option in Applications-System"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-12-03
I d/l'd the .iso of Natty Alpha to put it on a [USB drive]("http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/") and start testing.

The instructions called for using Applications/System/Startup Disk Creator.

I opened Apps/System and LO! and Behold! I have NO Startup Disk Creator line in the pull down menu.

I opened a terminal and ran a variety of commands: startup, startupdisk, etc., to no avail. I tried 'locate' and that returned nothing related as well.

I'm running a stock 10.10 Maverick Meerkat

---

### Post by cariboo on 2010-12-03
Try System->Administration->Startup Disk Creator

The application can be started in a terminal with the following command:

```
usb-creator-gtk
```

---

