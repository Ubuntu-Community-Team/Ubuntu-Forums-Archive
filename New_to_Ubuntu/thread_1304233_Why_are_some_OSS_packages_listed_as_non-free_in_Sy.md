---
title: "Why are some OSS packages listed as non-free in Synaptic?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by drchupacabra on 2009-10-29
When I install [Xara Extreme]("http://www.xaraxtreme.org"), it is listed under local/non-free, while their website states it is OSS (using 9.04)?? Is there a list somewhere of the authors/managers of a repository with the consideration for each package? And how could you contact them to ask what the problem is with a certain package?

---

### Post by iMisspell on 2009-10-29
```
sudo dpkg-query --status PROGRAM-NAME-IN-QUESTION
```
Will list off info...

---

### Post by drchupacabra on 2009-10-29
Thanks!

---

### Post by mcduck on 2009-10-29
> **iMisspell said:**
> ```
sudo dpkg-query --status PROGRAM-NAME-IN-QUESTION
```
Will list off info...

No need for "sudo" in that command.. Listing package info doesn't require administrative permissions. :)

---

