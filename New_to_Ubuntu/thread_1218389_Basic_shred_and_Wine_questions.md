---
title: "Basic shred and Wine questions"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Cuddles McKitten on 2009-07-20
1. Does the shred command have any ability to shred free (unused) disk space?

2. I think I already know the answer in this one, but I need someone to destroy all hope for me.  If I want to run a Windows program through Wine, do I absolutely need to have some sort of a Windows partition on my hard drive?

-Thanks

---

### Post by Mornedhel on 2009-07-20
> **Cuddles McKitten said:**
> 1. Does the shred command have any ability to shred free (unused) disk space?

shred shreds files.

> **Cuddles McKitten said:**
> 2. I think I already know the answer in this one, but I need someone to destroy all hope for me.  If I want to run a Windows program through Wine, do I absolutely need to have some sort of a Windows partition on my hard drive?

No, you don't. You can install Windows programs through Wine ; they'll be in "~/.wine/drive_c". It is also possible to run programs from an existing partition (handy in case you are dual booting), but not mandatory.

---

### Post by Cesaar on 2009-07-20
2. No, you don't need to have any Windows partitions to run a Windows program through Wine.

---

### Post by Mornedhel on 2009-07-20
Re. the shred question, I've just taken a look to the repositories, a package called secure-delete claims to include an utility to do what you need.

---

### Post by Cuddles McKitten on 2009-07-20
> **Mornedhel said:**
> Re. the shred question, I've just taken a look to the repositories, a package called secure-delete claims to include an utility to do what you need.

No, you don't. You can install Windows programs through Wine ; they'll be in "~/.wine/drive_c". It is also possible to run programs from an existing partition (handy in case you are dual booting), but not mandatory.

Hooray!  Both problems came out better than I expected.  Thanks.

---

