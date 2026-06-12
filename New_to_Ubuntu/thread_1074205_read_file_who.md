---
title: "read file: who ?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-18
Hi there,
Is there any way to know which user read a particular file? Suppose the computer has 3 users. user1 has a read only file in home directory. If user2 or user3 read that file, is there any way to tell which user read it?

---

### Post by brian_p on 2009-02-19
> **cosine352 said:**
> Hi there,
Is there any way to know which user read a particular file? Suppose the computer has 3 users. user1 has a read only file in home directory. If user2 or user3 read that file, is there any way to tell which user read it?

Use the stat command to get the last access time. Match with who was logged in. Fails if more than one user is logged in.

---

