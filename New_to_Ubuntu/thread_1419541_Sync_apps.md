---
title: "Sync apps"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Arla on 2010-03-02
Does anyone know an app for this?

What I'd LIKE is something where I can specify to keep two directories in sync (and all subdirectories), but with a master/slave type relation, where, essentially, any new files in the master source will get copied to slave, any updated files in master will get copied to slave, but any deleted files would not get deleted from slave, so it's sort of a one-way syncing of data.

Anyone know anything that does this automatically, before I try to write something for myself.

---

### Post by switch10 on 2010-03-02
rsync does this.  you can set up a cron job to run your backup whenever you want

```
 man rsync 
```

there are so many options....

leave out the --delete option to keep files on your "slave" drive.

---

### Post by Arla on 2010-03-02
Much appreciated, now to try to read all the man pages

---

### Post by Temposs on 2010-03-02
If you want something with a GUI for this kind of thing, check out **grsync**, which is just a GUI on top of rsync. There's also an app called **Unison**, which makes things more user friendly than rsync.

---

### Post by fatality_uk on 2010-03-02
FYI. It is also possible using rsync to sync between windows and Linux. I had to write a we bit of a script, which of course I can't find now but it can work.

---

### Post by megamania on 2010-03-02
> **Arla said:**
> Anyone know anything that does this automatically, before I try to write something for myself.
```
rsync -av /source/path /dest/path/
```
should do. Test it with caution, however. :-)

Let me know if you need further help - I can post some simple scripts when I'm back home.

---

### Post by fatality_uk on 2010-03-02
Here's some of my rsync script, the bit that's relevant

```
rsync -r -t -v --delete --modify-window=10 /source/path/ dest/path
```

Lots of background on all the flags can be found here

[http://linuxmanpages.com/man1/rsync.1.php]("http://linuxmanpages.com/man1/rsync.1.php")

---

