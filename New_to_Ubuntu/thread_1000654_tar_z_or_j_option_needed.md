---
title: "tar z or j option needed?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by bcd87 on 2008-12-03
A lot of people say that when you're extracting you need to put the z or j option for respectively gzip or bzip2, but is this really needed?
From my experience I can untar the archives no problem without specifying either option. Both gzip and bzip2 are untarred with nothing but:
```
tar xf foo.tar.(gz/bz2)
```

So why use the z or j option for extracting?

---

### Post by loomsen on 2008-12-03
You're right, doesn't matter actually...

**tar -xf foobar.tar.gz**
and
**tar -xf foobar.tar.bz2 **

should create the same output, extracting your archive.

If you want to create an archive, use:

**tar -cjf foobar.tar.bz2 foo bar**
respectively
**tar -czf foobar.tar.gz foo bar**

to create archives from files **foo** and **bar**

---

### Post by louieb on 2008-12-03
Habit?  Older versions of tar may need it.

---

### Post by bcd87 on 2008-12-03
So basically it's a thing of the past and can be safely ignored nowadays? (Unless you're actually creating a package obviously)

---

### Post by scorp123 on 2008-12-03
> **louieb said:**
> Older versions of tar may need it. Exactly.

---

