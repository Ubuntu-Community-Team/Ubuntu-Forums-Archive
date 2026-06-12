---
title: "dvd drive help"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by mike941 on 2010-01-20
I disabled polling on my dvd drive with this command:
```
sudo hal-disable-polling --device /dev/cdrom
```
I'm suppose to be able to renable it with this command:
```
hal--enable-polling --device /dev/cdrom
```
But for some reason that re-enable command isn't working. Whenever i enter the re-enable command it says something like command deosn't exist. When i enter the disable command it tells me it's aready been used though. I also can't open the man page for hal. So how do i get my dvd drive polling again?

---

### Post by linux nut on 2010-01-20
If i can rember correctly I think its this: sudo hal-disable-polling --enable-polling --device /dev/cdrom

---

