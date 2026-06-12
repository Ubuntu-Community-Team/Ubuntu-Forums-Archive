---
title: "Building a new kernel - permission denied?."
date: 2009-09-01
forum: New to Ubuntu
---

### Post by sunrex on 2009-09-01
I'm following this guide here:

[http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization](http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization)

but when I get to the point for zcat, I get this:

> tyler@DDC-ONE:/usr/src/linux-2.6.26.8$ zcat ../patch-2.6.26.8-rt16.gz | patch -p1
patching file arch/arm/kernel/process.c
patch: **** Can't rename file /tmp/poeyGLrd to arch/arm/kernel/process.c : Permission denied
tyler@DDC-ONE:/usr/src/linux-2.6.26.8$

Any ideas on how to bypass/resolve this?. Thank you.

---

### Post by PGScooter on 2009-09-01
I thin you need to use sudo. But I have never built a kernel and am a noobie, so don't trust me:)

Usually though, "Permission denied" either means use sudo or chmod it.

---

### Post by sunrex on 2009-09-01
> **PGScooter said:**
> I thin you need to use sudo. But I have never built a kernel and am a noobie, so don't trust me:)

Usually though, "Permission denied" either means use sudo or chmod it.

I tried sudo.

---

### Post by PGScooter on 2009-09-01
what about chmoding the file before you try to patch it?

---

### Post by sunrex on 2009-09-01
bump

---

### Post by NoaHall on 2009-09-01
It seems like the file is being used - try booting using a old kernel, and then trying.

I also assume you're doing this from ctrl + alt + F1?

---

### Post by tobias_r33per on 2009-09-01
It either being used or , your permissions on the patch files are all outta-whack

Most patches have the permissions set from the machine they were built (at least that's what I've found anyways) chmod the files so that they are all writable and readable directly at least 0777 just for safety

---

