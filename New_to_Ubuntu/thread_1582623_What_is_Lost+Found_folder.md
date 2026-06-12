---
title: "What is Lost+Found folder ?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by ericstrom on 2010-09-26
I've notice a folder called Lost + Found. It has an X in the folder. I've seen it in a couple of places.

What is it ? What is it's purpose ?

---

### Post by marshmallow1304 on 2010-09-26
Any corrupted file fragments recovered during a disk check go there.  Every partition has a lost+found.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by Mi11z on 2010-09-26
> **marshmallow1304 said:**
> Any corrupted file fragments recovered during a disk check go there.  Every partition has a lost+found.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

In windows too?

---

### Post by Butthead on 2010-09-26
> **Mi11z said:**
> In windows too?

No.  For that you usually just get the blue screen of death. :mrgreen:

---

### Post by bsalem on 2010-09-27
There is a Recovered_Files dir for NTFS that looks like it does pretty much the same thing as lost_and_found on a
UNIX filesystem, This convention for UNIX goes back alot of years and is supported on many older fs types for UNIX.

---

