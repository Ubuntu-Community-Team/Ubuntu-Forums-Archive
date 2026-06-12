---
title: "Can't see startup messages or shutdown messages"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by skinks on 2009-12-18
I just reinstalled Ubuntu 9.04, and got boot working after help here.  For first install, I saw startup screen with Ubuntu logo and startup messages.  It was useful for troubleshooting.  Likewise, I would see the shutdown messages.  Now, with this install, the screen is blank until the mouse icon arrives.  What do I change in order to see the startup and shutdown messages again?

---

### Post by lidex on 2009-12-18
Go to "System>Administration>StartUp-Manager". On the "Boot" tab, at the bottom under "Misc." untick the "Show Boot Splash" option. Tick the third option: "Show text during boot".



BTW you can see all those messages in dmesg. Simply run in a terminal:
```
dmesg
```
or
```
dmesg | less
```

---

### Post by sgosnell on 2009-12-18
Install either bootup manager or startupmanager.  Either should work, but I have been unable to get startupmanager to install, because it list an obsolete version of python as a dependency, and I haven't had enough interest to chase down a fix for that.  Bootup manager works for me.  Install it, run it, and uncheck usplash, and you should see the text instead of the splash screen.

---

### Post by joes7 on 2009-12-18
> **lidex said:**
> Go to "System>Administration>StartUp-Manager". On the "Boot" tab, at the bottom under "Misc." untick the "Show Boot Splash" option. Tick the third option: "Show text during boot"
That is the best way to fix it. Alternately, you can update your GRUB by opening a terminal and writing the following command:
```

update-grub

```

For that to work, you must log in as "root".

---

