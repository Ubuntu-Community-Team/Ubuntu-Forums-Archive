---
title: "Partial distribution upgrade on fresh install?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Falc7 on 2009-07-04
I have just clean installed 9.04, and update manager is giving me strange messages about having to do a partial distribution upgrade, however every time i click start upgrade, nothing happens, the update manager window dissapears without doing anything. Please help

---

### Post by earthpigg on 2009-07-04
what happens if you do this:

```
sudo apt-get update && sudo apt-get upgrade
```

that will theoretically do the exact same thing as the point-and-click method, but the text output may give us a hint as to what the problem is.

---

### Post by Falc7 on 2009-07-04
okay, did that, everything seemed to go smoothly, FF updated, and i restarted the computer, however update manager is still advising me about a partial distribution upgrade, and now when i put that code into terminal i get:

josh@josh-laptop:~$ sudo apt-get update & sudo apt-get upgrade
[1] 3806
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
josh@josh-laptop:~$

---

### Post by Falc7 on 2009-07-04
I think i am gonig to do a fresh install, this is mucked up, now when i put that into terminal it tries to update packages that have already been updated last time.

---

### Post by earthpigg on 2009-07-04
what does this do?

```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by Falc7 on 2009-07-05
> **earthpigg said:**
> what does this do?

```
sudo aptitude update && sudo aptitude dist-upgrade
```

I've reinstalled, and no longer have this problem, thanks :)

---

