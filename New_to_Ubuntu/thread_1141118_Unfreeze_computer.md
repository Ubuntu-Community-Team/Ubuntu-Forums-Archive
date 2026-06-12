---
title: "Unfreeze computer"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by eddski on 2009-04-28
Is there any way to unlock a frozen computer other than rebooting? Is there any way to tell what program locked my computer?

---

### Post by ndefontenay on 2009-04-28
You should check your logs. There must be something useful in /var
I don't have the file name in mind but there's not a thousand of them either so you should get something useful pretty quickly.

---

### Post by billgoldberg on 2009-04-28
> **eddski said:**
> Is there any way to unlock a frozen computer other than rebooting? Is there any way to tell what program locked my computer?

If you are on Ubuntu 8.10 or lower, you can try the shortcut:

ctrl+alt+backspace

to return to login.

It won't work on Ubuntu 9.04 by default.

Should that not work, try this:

```
    1. Hold down the Alt and SysRq (Print Screen) keys. 2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB 3. Watch your computer reboot magically. 

This sequence of keystrokes will kill all programs, unmount your drives and restart. FOSSwire recommends remembering this key sequence with the phrase "Raising Elephants Is So Utterly Boring." 
```

---

### Post by wizard10000 on 2009-04-28
> **eddski said:**
> Is there any way to unlock a frozen computer other than rebooting? Is there any way to tell what program locked my computer?

Second question first  :)

There *might* be something in the logs but it's been my experience that hard lockups don't usually leave log entries  ;)

A lot of the time you can do a graceful shutdown and restart by holding down the Alt and SysRq (that's the print screen) key and slowly typing REISUB - waiting a couple seconds seconds between letters.

Think BUSIER backwards.

---

### Post by eddski on 2009-05-01
Thank you all!

---

### Post by 3rdalbum on 2009-05-01
If it's a hard freeze, as in "the lights on my keyboard are flashing" then you probably won't get any data back from Gnome System Log. If the lights aren't flashing then you might get some useful information in "messages" or "kern.log" in Gnome System Log when you reboot.

---

