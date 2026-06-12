---
title: "Firefox problems"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-12-03
Hy all!

I have a problem with my browser. It takes ages to start and it freezes almost every time I quit it. Once it starts, it works very good, no issues here. But it's very annoying to wait 10-15 sec for it to start and to freeze when I exit. 
Can someone help?
I have an Asus laptop, 1.6 Mhz AMD Turion64 dual core processor, 2 GB RAM, nVidia GeForce Go 7600 video adapter.

---

### Post by llamabr on 2009-12-03
For trouble shooting, you can try:

```
mv .mozilla/ .mozilla.save
```

and then start firefox.  If it now works, you've got some weird setting somewhere in your preferences.  Something you're unlikely ever to find.

btw, 15 seconds isn't "forever".  That's about how long it takes routinely on my old g3 ibook.

---

### Post by arubislander on 2009-12-03
> **llamabr said:**
> btw, 15 seconds isn't "forever".  That's about how long it takes routinely on my old g3 ibook.

In all fairness to the OP... he did not say "forever" he said it took "ages", that's a tad shorter than "forever" ;)

---

### Post by Troll_the_Great on 2009-12-03
Thanks, that seems to work, at least for now. By the way, what happen? From that command I understand that I just moved my Mozilla folder into a new folder named mozilla-save. How did I improved my performance by doing that?

PS:I don't know what specs you old g3 ibook had, but for 1.6 MHz dual core and 2 GB of RAM, 15 seconds to start the browser seems alot.

---

### Post by RiceMonster on 2009-12-03
> **Troll_the_Great said:**
> How did I improved my performance by doing that

You didn't really improve the performance; there was an error with one of the config files and firefox just created a new one after you moved the director. Either that, or there was an add-on causing problems, and firefox is now running without it.

---

### Post by lovinglinux on 2009-12-03
> **Troll_the_Great said:**
> Thanks, that seems to work, at least for now. By the way, what happen? From that command I understand that I just moved my Mozilla folder into a new folder named mozilla-save. How did I improved my performance by doing that?

PS:I don't know what specs you old g3 ibook had, but for 1.6 MHz dual core and 2 GB of RAM, 15 seconds to start the browser seems alot.

The symptom you was experiencing is probably due to excess of junk in a Firefox database. Some extensions, and Firefox itself, need to read from databases upon start, so if the database is full of left-overs, it would take a lot of time to load. Sometimes extensions also perform database reading/writing upon closing Firefox, so this is why it takes more time to close.

Using a clean profile solves this issue, because you start with clean databases. But is not a good solution if you have a lot of bookmarks, extensions and personal Firefox settings, since you loose all of them. To solve the problem without deleting your profile, simply optimize the databases. To learn how to do that, visit the Database Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

