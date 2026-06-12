---
title: "A little help if you will..."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Toneh on 2008-12-30
Well, a dell mini netbook  with Ubuntu 8.04 hard heron edition.
Since it doesn't have a CD-ROM drive, I have to upgrade using the terminal, or the upgrade manager. Problem: I followed the tutorial on the ubuntu.com thingy, and when I download upgrades, it says this:
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://mirror.imbrandon.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.



ps I used the find the best server thingy, so my links may look a little weird.

---

### Post by adult swim on 2008-12-30
are you using a proxy?

---

### Post by oilchangeguy on 2008-12-30
this probably should be posted in main support, dell ubuntu support.

---

### Post by Toneh on 2008-12-30
Well, a dell mini netbook with Ubuntu 8.04 hard heron edition.
Since it doesn't have a CD-ROM drive, I have to upgrade using the terminal, or the upgrade manager. Problem: I followed the tutorial on the ubuntu.com thingy, and when I download upgrades, it says this:
Failed to fetch [http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz](http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz) 404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz](http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz) 404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz](http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz) 404 Not Found
Failed to fetch [http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz](http://mirror.imbrandon.com/ubuntu/d...ia/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ia/Packages.gz](http://security.ubuntu.com/ubuntu/di...ia/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ia/Packages.gz](http://security.ubuntu.com/ubuntu/di...ia/Packages.gz) 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.



ps I used the find the best server thingy, so my links may look a little weird.

---

### Post by Toneh on 2008-12-30
> **adult swim said:**
> are you using a proxy?
I dont think so, how can I tell?

---

### Post by taurus on 2008-12-30
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by adult swim on 2008-12-30
if you didnt set up a proxy then you arent using one.  have you tried changing the download server to the main server?

---

### Post by Toneh on 2008-12-30
> **taurus said:**
> Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
sure here you go:
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://mirror.imbrandon.com/ubuntu/](http://mirror.imbrandon.com/ubuntu/) hardy main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main universe
deb [http://mirror.imbrandon.com/ubuntu/](http://mirror.imbrandon.com/ubuntu/) hardy-updates main universe
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

---

### Post by Rocket2DMn on 2008-12-30
Threads merged.

---

### Post by hansdown on 2008-12-30
Hi Toneh.

A 404 error simply means the server could not be found.
Try changing mirrors, even if they are farther away from you. They still may be better.
Quick question though. Why do you wish to upgrade? 8.04 hh is a long term support version.

---

### Post by Toneh on 2008-12-30
> **hansdown said:**
> Hi Toneh.

A 404 error simply means the server could not be found.
Try changing mirrors, even if they are farther away from you. They still may be better.
Quick question though. Why do you wish to upgrade? 8.04 hh is a long term support version.

I tried 8.10 and I like it better.

---

### Post by abn91c on 2008-12-30
connect the netboot by wire to your modem/router then try the updates again

---

### Post by Toneh on 2008-12-30
> **abn91c said:**
> connect the netboot by wire to your modem/router then try the updates again

how do I do that?
Im such a n00b.

---

### Post by abn91c on 2008-12-30
> **Toneh said:**
> how do I do that?
Im such a n00b.
run the RJ45 cable from your modem and plug into the ethernet port in back or side of the laptop(looks like a large phone plug)

---

### Post by Toneh on 2008-12-30
> **abn91c said:**
> connect the netboot by wire to your modem/router then try the updates again

Ok I'll try it.

---

### Post by Toneh on 2008-12-30
> **Toneh said:**
> Ok I'll try it.
It said the same thing...

---

