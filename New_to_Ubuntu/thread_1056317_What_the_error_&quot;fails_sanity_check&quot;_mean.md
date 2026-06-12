---
title: "What the error &quot;fails sanity check&quot; means?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Hadso on 2009-01-31
I was uncompressing fluxbox 1.1.1 and I had this message or error:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check


1) What it's means?
2) What happened whit the uncompressed files?

Thanks,

---

### Post by cwsnyder on 2009-01-31
The error message: "Fails sanity check" means the uncompressor doesn't have any idea how to uncompress the files, because the files fail the internal file check.

---

### Post by Hadso on 2009-01-31
So, what sould I do?
Waht happened with the uncompressed files?

Thanks!

---

### Post by cwsnyder on 2009-01-31
There ARE no uncompressed files, just the archive.  You will have to get a new copy of the archive, it is corrupted.  That is what it means when it 'fails sanity check.'  The computer can't make sense of the file to uncompress anything from it.

---

### Post by Hadso on 2009-01-31
It's done. Thanks!

---

