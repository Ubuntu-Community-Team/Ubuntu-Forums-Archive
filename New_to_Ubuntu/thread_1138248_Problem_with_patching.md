---
title: "Problem with patching"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Free4Eternity on 2009-04-26
I know this is kinda stupid, but I am trying to patch the open source tools of vmware for it to work on intrepid. I downloaded the patches from <http://sourceforge.net/tracker/?func=detail&atid=989708&aid=2048423&group_id=204462> , but I simply do not know what to do with them.

I tried 
```
 $patch -i intrepid.patch
patch -p0 -i intrepid.patch

```

but both of them began to prompt me the file to patch. I am very confused right now...

---

### Post by ddrichardson on 2009-04-26
You have the vmware source, don't you?

---

### Post by Free4Eternity on 2009-04-26
yep I got it from the official site, as the prebuilts didn't work for me.

---

### Post by albinootje on 2009-04-26
> **Free4Eternity said:**
> yep I got it from the official site, as the prebuilts didn't work for me.

```

diff --git a/open-vm-tools/guestd/foundryToolsDaemon.c b/open-vm-tools/guestd/foundryToolsDaemon.c
index 944ffff..a2a2e3e 100644
--- a/open-vm-tools/guestd/foundryToolsDaemon.c
+++ b/open-vm-tools/guestd/foundryToolsDaemon.c

```
Looking at the content of the intrepid.patch it looks like it needs "git" installed (Installed "git-core" might be enough), and it expects a directory called "open-vm-tools".

Normally you apply a patch like this, after "cd-ing" into the source code directory, or just one level above it (Right now I don't remember which one it was) :
```

patch -p0 < intrepid.diff

```

---

### Post by ddrichardson on 2009-04-26
Its normally in the source root folder depending on what generated the patch - this one is.

---

### Post by Free4Eternity on 2009-04-26
thanks for the speedy reply, but it is still not working...
it returned with this error.

```

patch -p0 < intrepid2.patch
can't find file to patch at input line 12
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|commit 45f57c57137fb28dfa55c0d48f6d7259b6082f90
|Author: Adar Dembo <adar@vmware.com>
|Date:   Fri Aug 15 16:01:09 2008 -0700
|
|    In commit 46f4578680af93fb824942546a6cc3e31121f90d, I made some mistakes when
|    add checks for return values of two functions. This should fix said mistakes.
|
|diff --git a/open-vm-tools/guestd/main.c b/open-vm-tools/guestd/main.c
|index b74d101..fba65fb 100644
|--- a/open-vm-tools/guestd/main.c
|+++ b/open-vm-tools/guestd/main.c
--------------------------
File to patch: ^C

```

---

### Post by Free4Eternity on 2009-04-27
bump

---

