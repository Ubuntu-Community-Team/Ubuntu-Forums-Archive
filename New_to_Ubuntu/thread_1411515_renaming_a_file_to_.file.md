---
title: "renaming a file to .file"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by techfish on 2010-02-20
how can I rename a file to .file

I use this code:
```
mv file .file
```


It just removes the file

---

### Post by Mustard on 2010-02-20
> **techfish said:**
> how can I rename a file to .file

I use this code:
```
mv file .file
```


It just removes the file

Do you have 'show hidden files' on?

---

### Post by HereInOz on 2010-02-20
have a go at:

mv file ".file"

Should do the job.

---

### Post by HereInOz on 2010-02-20
Good thought Mustard, he may not be doing ls -a to show hidden files.  Didn't think of that one.

---

### Post by click4851 on 2010-02-20
aren't all .files actually hidden by default.....Is it possible they are there, but hidden?

---

### Post by 3rdalbum on 2010-02-20
lol lol lol

They aren't being removed, they're being hidden - because files whose names begin with a period are hidden files on Linux, Unix and Mac OS X.

---

