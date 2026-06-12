---
title: "E: dpkg was interrupted...."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by quietbear on 2009-02-10
I have an update to install, but whenever I try to install it, I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what do I do now?

---

### Post by taurus on 2009-02-10
Close the update manager window first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Zanahade on 2009-02-12
I am having the same problem. I followed your instructions and got:
zanahade@Boots:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

I did not try to proceed. Any thoughts?

---

### Post by Zanahade on 2009-02-12
Fixed: Turns out I some how fat-figured my libxine1.bin package so I removed and reinstalled gxine. Worked like a charm.

---

### Post by quietbear on 2009-02-12
thanks, all fixed.

---

### Post by Saraslife on 2009-02-12
> **taurus said:**
> Close the update manager window first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

I also got the same error. So I tried the update/upgrade and got...

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.

any suggestions?

---

### Post by bodhi.zazen on 2009-02-12
> **Saraslife said:**
> I also got the same error. So I tried the update/upgrade and got...

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.

any suggestions?

Depends on what and how you are trying to install.

You can try the -f flag , it usually works, but it sometimes causes breakage.

Again, depends on what you are doing or if you are using 3rd party repos or an alpha.

---

### Post by Saraslife on 2009-02-12
I ran -f and I worked. thanks!

---

