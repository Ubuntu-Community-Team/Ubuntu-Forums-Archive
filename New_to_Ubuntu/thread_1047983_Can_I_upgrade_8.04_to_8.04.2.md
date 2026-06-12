---
title: "Can I upgrade 8.04 to 8.04.2"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Lupgaru on 2009-01-22
Instead of upgrading to 8.10, can I upgrade my current 8.04 to the new LTS 8.04.2?
   I don't want to download and reinstall the entire system if possible. Anyone know how to do this?

SOLVED!

---

### Post by jimmy the saint on 2009-01-22
It is already done!  When you install ubuntu, there are usually a LOT of updates that have been commited between when the iso was created and you choose to install.  All the point releases do is update the iso to cut down on this.  As long as you are updating your system, you already have it plus some!

---

### Post by bodhi.zazen on 2009-01-22
yes. If you are doing a fresh install less bandwidth to DL 8.04.02

If you installed 8.04 and have been doing updates with any regularity you are alrady there or very close.

The idea of 8.04.0x is to save on bandwidth on a fresh install, why dl 8.04 and then update ?

Other the updates there should be no major differences between the 2 versions.

---

### Post by Lupgaru on 2009-01-23
Thank You!

---

### Post by ibuclaw on 2009-01-23
You can get 8.04.2 fresh from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

If you are already on 8.04/+ and you have been keeping up-to-date with current releases of software updates, then you probably already are running 8.04.2 without you realising it.

Open a terminal and type in:
```
lsb_release -a
```
and you will be told what version of Ubuntu you are running.

Regards
Iain

---

### Post by kansasnoob on 2009-01-23
On one of my partitions, the one I'm on right now, I have 8.04.2 and it began as 8.04 Release Candidate. Look at the top line here:

[ATTACH]100779[/ATTACH]

---

### Post by kansasnoob on 2009-01-23
> **tinivole said:**
> You can get 8.04.2 fresh from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

If you are already on 8.04/+ and you have been keeping up-to-date with current releases of software updates, then you probably already are running 8.04.2 without you realising it.

Open a terminal and type in:
```
lsb_release -a
```
and you will be told what version of Ubuntu you are running.

Regards
Iain

Or just:

```
cat /etc/issue
```

Or to see what kernel version you're running:

```
uname -r
```

---

