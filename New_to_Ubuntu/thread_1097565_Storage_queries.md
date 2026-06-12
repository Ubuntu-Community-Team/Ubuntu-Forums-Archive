---
title: "Storage queries"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by nnjond on 2009-03-16
Hi,

Do hard disks run best when they'r only half used?

I have a 250Gb FAT 32 sdb1 which has 173Gb occupied.

---

### Post by acmeinc on 2009-03-16
I would use 'iostat' to view my hard disk speeds.  However I can not seem to find the iostat equivalent for Ubuntu.

---

### Post by orethrius on 2009-03-16
> **acmeinc said:**
> I would use 'iostat' to view my hard disk speeds.  However I can not seem to find the iostat equivalent for Ubuntu.
```
gksudo apt-get install sysstat
```

It won't display any messages other than the sudo password request, so give it a minute or two to complete (more if you're working from a base system).

```
xterm -e 'gksudo apt-get install sysstat'
```

That line will give you a nice xterm window that closes when the install finishes.  Both can be run from the Alt+F2 Run prompt. ;)

---

### Post by nnjond on 2009-03-16
Thanks for your interest. All I wanted to know is ; Should I buy a larger hd befoe i fill this one up?

---

### Post by orethrius on 2009-03-16
> **nnjond said:**
> Thanks for your interest. All I wanted to know is ; Should I buy a larger hd befoe i fill this one up?
Well, I've never heard of any research proving that an unfilled hard drive actually boosts hard drive performance - just RAM performance, as indexing services don't run so often - but correct me if I'm wrong here.  It sounds more like an excuse to push people into buying larger hard drives, which - IMO - is never a bad thing (just think how much MORE you can store!) :-D

---

