---
title: "Applying patch to tar.gz file"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by f00k3r on 2009-06-23
Hi,

    I have a tar.gz file and I need to apply a patch to it. How do I go about doing it. As can be seen, I'm really new to Linux. Please help me out.


Thanks,
Bharat.

---

### Post by michy99 on 2009-06-23
What is the name of the tar.gz file and what is it for? Also, what is the name of the patch and where did you get it from?

---

### Post by aeiah on 2009-06-23
chances are you dont want to apply a patch to a tar.gz file. a tar.gz file is actually a compressed package, much like .zip or .rar files. what i assume you want to do is unpack the tar.gz, apply the patch to a contained file or files, and then perhaps repackage it into a tar.gz

more details would be useful though of course.

---

### Post by billgoldberg on 2009-06-23
> **f00k3r said:**
> Hi,

    I have a tar.gz file and I need to apply a patch to it. How do I go about doing it. As can be seen, I'm really new to Linux. Please help me out.


Thanks,
Bharat.

Think of a .tar.gz package as a .zip of .rar package.

It's just an compressed archive.

---

### Post by f00k3r on 2009-06-23
Hi,

   Thanks for the quick reply. The patch is for : 
**nesc-1.1.3.tar.gz** 
and the patch is:
**builtin_offset.patch.nesc**
This is what the patch says:
```
ebebc2013f0403eb69009df94216a50491be1396
diff --git a/src/c-parse.gperf b/src/c-parse.gperf
--- a/src/c-parse.gperf
+++ b/src/c-parse.gperf
@@ -69,7 +69,7 @@ if, IF, NORID
 inline, SCSPEC, RID_INLINE
 int, TYPESPEC, RID_INT
 long, TYPESPEC, RID_LONG
-offsetof, OFFSETOF, NORID
+__builtin_offsetof, OFFSETOF, NORID
 register, SCSPEC, RID_REGISTER
 return, RETURN, NORID
 short, TYPESPEC, RID_SHORT
```

Now I have installed an earlier version of nesc and the patch can be applied to that too. This is how it is to be applied:
```
patch -p1 < builtin_offset.patch.nesc (in nesc)
```
I am unsure as to how and where to apply the patch. If I go into 
nesc-1.1.2b/src and use the above command, it says:File to patch? and I don't know which file it is. 
Thus, I'm thinking of keeping the patch in the tar.gz file and then installing it all over again.

Thanks,
Bharat.

---

### Post by f00k3r on 2009-06-23
So now that I have the tar.gz file and the patch file..how do i untar it, **apply the patch** and then tar it? Any ideas?


Thanks,
Bharat.

---

### Post by f00k3r on 2009-06-23
> **f00k3r said:**
> So now that I have the tar.gz file and the patch file..how do i untar it, **apply the patch** and then tar it? Any ideas?


Thanks,
Bharat.
Ok..in addition to that, is it possible to uninstall after I have 'make install' a tar.gz package?
Thanks,
Bharat.

---

