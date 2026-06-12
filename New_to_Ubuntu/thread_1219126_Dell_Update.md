---
title: "Dell Update"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by John F on 2009-07-21
I have an EEE and a Dell Mini 12 both running Ubuntu.  Suddenly, for no clear reason and after no system alterations, the Dell gives me a message that it cannot download all reppository indexes to do an update.  The EEE updates just fine.

Is this likely to be a problem with Dell's server, or should I be looking at something on the Mini 12 (or should I just wait and see if it is the kind of problem that can fix itself)?


John F

---

### Post by philcamlin on 2009-07-21
can you post the output when it does that

---

### Post by John F on 2009-07-21
I got the message "Could not download all repository indexes" (I have corrected the wording in the original post).  I guess Dell has its own Ubuntu repository.

John F

---

### Post by sandyd on 2009-07-21
can you
```

cat /etc/apt/sources.list

```

---

### Post by John F on 2009-07-21
This is what I get:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe multiverse
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted



John F

---

### Post by mikechant on 2009-07-22
It's probably a temporary problem with Dell's repository servers.

Might take a day or two to get sorted.

---

### Post by ukripper on 2009-07-22
Server might be down or having problem communicating

---

### Post by John F on 2009-07-22
Many thanks.  I will keep trying.

---

