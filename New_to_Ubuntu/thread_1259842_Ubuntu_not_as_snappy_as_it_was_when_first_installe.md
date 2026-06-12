---
title: "*Ubuntu* not as snappy as it was when first installed? why not?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-06
when i first installed ubun, wow was it fast took mearly a second to open the web browser, but now... about 20 idk what i did to make it so slow, maby the compiz animation add ons? or the cube? or the virtualbox... i did give virturalbox 1/4 of my memory to run vista... is that it dose it reserve that ALL the time or just when VB is open? idk what it is but i did the janator clean up and not much faster. most of my programs are still snappy, just the time between when i log in and and when my desktop is finaly loaded (30 sec), and the time it takes for my firefox browser to open (20 sec) any help would be greatly appreciated
thanks!

---

### Post by nandemonai on 2009-09-06
> **R3fr4cti0n said:**
> when i first installed ubun, wow was it fast took mearly a second to open the web browser, but now... about 20 idk what i did to make it so slow, maby the compiz animation add ons? or the cube? or the virtualbox... i did give virturalbox 1/4 of my memory to run vista... is that it dose it reserve that ALL the time or just when VB is open? idk what it is but i did the janator clean up and not much faster. most of my programs are still snappy, just the time between when i log in and and when my desktop is finaly loaded (30 sec), and the time it takes for my firefox browser to open (20 sec) any help would be greatly appreciated
thanks!

Search this forum for the 'speed up firefox' threads. It's likely the sqlite db for firefox is getting rather large. 

```
find ~/.mozilla/firefox/ -type f -name "*.sqlite" -exec sqlite3 {} VACUUM \;
```

The above code should clean it up for you. Run that maybe once a month.

As far as slow login goes, check your startup apps / services.

---

### Post by R3fr4cti0n on 2009-09-06
"no such file or directory"  ??? im clueless

---

### Post by pi.boy.travis on 2009-09-06
Firefox's history and cache is getting too big for it's own good.  Just go into Tools>Clear Private Data, and delete your history, cache, cookies, and offline website data.  That should do the trick.

---

### Post by winotree on 2009-09-07
> **R3fr4cti0n said:**
> "no such file or directory"  ??? im clueless
The instructions **nandemonai **offered presupposed that you had the file *sqlite3* already installed.  You can get it from the repository, copy the command into terminal, *close Firefox*, then run the command if you still want -- might be interesting to do a *df* in terminal before and after...  ;)

---

### Post by nandemonai on 2009-09-07
> **winotree said:**
> The instructions **nandemonai **offered presupposed that you had the file *sqlite3* already installed.  You can get it from the repository, copy the command into terminal, *close Firefox*, then run the command if you still want -- might be interesting to do a *df* in terminal before and after...  ;)

Dang, I knew I was missing something...

---

### Post by TenPlus1 on 2009-09-07
Install BleachBit to tidy up Firefox as well as many other applications:

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by nandemonai on 2009-09-07
> **TenPlus1 said:**
> Install BleachBit to tidy up Firefox as well as many other applications:

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

Good call ;)

---

### Post by howefield on 2009-09-07
> **R3fr4cti0n said:**
> i did give virturalbox 1/4 of my memory to run vista... is that it dose it reserve that ALL the time or just when VB is open?

Your virtual machine will use the allocated resources only when loaded, closing the virtual machine releases the resources back to the host.

---

