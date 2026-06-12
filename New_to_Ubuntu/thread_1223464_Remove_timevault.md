---
title: "Remove timevault"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by okey666 on 2009-07-26
Looking for a backup program, I tried timevault using instructions which forced it to install on my 64-bit machine. After using it for a bit I decided I preferred sbackup for now so I wanted to get rid of timevault. I disabled it in "start up programs" and then went looking for a way to uninstall it, which I can't work out for the life of me, as it was installed from a .deb and not from the repros. As I couldn't work it out I left it, but then found a few days later that it was filling up my backup drives with backups even though sbackup was doing the same job.

Can anyone tell me how to remove it and stop the process which is backing up? (I'm on 9.04)

---

### Post by wojox on 2009-07-26
In terminal:

```
top
```

Find the PID

```
kill <thePID>
```


```
sudo dpkg -r timevault
```

---

### Post by okey666 on 2009-07-26
Thanks that seemed to work. One slight worry:
```
update-rc.d: /etc/init.d/timevault exists during rc.d purge (use -f to force)

```

Do I need to force that? No errors were given.

---

### Post by wojox on 2009-07-26
yes that what keeps starting it.

---

### Post by colau on 2009-08-16
> **okey666 said:**
> Thanks that seemed to work. One slight worry:
```
update-rc.d: /etc/init.d/timevault exists during rc.d purge (use -f to force)

```

Do I need to force that? No errors were given.
As you removed timevault,nothing to worry to stop running at boot time.

---

### Post by rmcellig on 2009-09-10
I am new to all this stuff. When I type top, I don't see Timevault in the list so I don't know what the PID is. Is there another way I can find out what it is so that I can kill it and remove it for good?

---

