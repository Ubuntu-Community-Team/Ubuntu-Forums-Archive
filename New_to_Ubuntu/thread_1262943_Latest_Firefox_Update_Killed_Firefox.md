---
title: "Latest Firefox Update Killed Firefox"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Her Ghost on 2009-09-10
I just ran the software update, which included several Firefox items.  Afterwards it said to restart Firefox, which I did.

And now, upon trying to start Firefox:

[Javascript Application]
Error launching browser window:no XBL binding for browser

How do I back out the last changes?
Anyone else affected?

(Ubuntu 9.04)

edit: Safe-Mode doesn't work either
edit2: renaming the Chrome folder to force it to rebuild doesn't work either

---

### Post by Soul-Sing on 2009-09-10
This happens because you have an incompatible [COLOR="Red"]extension[/COLOR] installed from a previous version....

---

### Post by Her Ghost on 2009-09-10
thanks - yes, I tried safe-mode but still got the same error.

---

### Post by kostkon on 2009-09-10
Give a
```
pkill firefox
```
in a terminal, and then try to run firefox again.

---

### Post by Her Ghost on 2009-09-10
kostkon - thankyou, that worked.  I can't believe it was that simple.  d'oh.

---

### Post by uncibex on 2009-09-10
I'm having this same problem.  I just disabled all of my extensions and restarted firefox, and it is still not working properly.  I am able to browse, but I lost all of my bookmarks and everything in my cache.  Is there any reason this would have been deleted? and any way I could get it back?

---

### Post by Excedio on 2009-09-10
> **uncibex said:**
> *snip*I lost all of my bookmarks*snip*
 
[Xmarks is your friend]("http://download.xmarks.com/download/all")

---

### Post by lovinglinux on 2009-09-10
> **uncibex said:**
> I'm having this same problem.  I just disabled all of my extensions and restarted firefox, and it is still not working properly.  I am able to browse, but I lost all of my bookmarks and everything in my cache.  Is there any reason this would have been deleted? and any way I could get it back?

Firefox profiles get corrupted frequently. That's why I recommend making automatic daily backups with FEBE extension. Nevertheless, you can still restore a bookmarks backup. Firefox makes them automatically. See the Backup section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for instructions.

---

