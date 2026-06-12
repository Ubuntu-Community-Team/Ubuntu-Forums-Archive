---
title: "TwinView for me but not other users"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by linux_believer on 2009-09-08
I dual monitors set up. 1 desktop monitor and 1 connected rgb to my LCD tv. Is there a way to disable twinview for other users. Since the desktop extends i'm worried that my wife may somehow drad a window over to the tv or when the mouse gets over there it will be hard for her to get it back since you would have to know it extends to the right.

I have a use for using my tv but she does not. Can i disable it just for her user?

---

### Post by Hospadar on 2009-09-08
Not really.

This is all set up in the xorg.conf file which is system-wide, and there's no real way to make it per user.

If you don't always use your second desktop, you could just open nvidia-settings and enable twinview when you need the tv (but don't save your config to the xorg.conf file)

I think there may be a way to script this as well through the use of nvidia's own tools.

---

