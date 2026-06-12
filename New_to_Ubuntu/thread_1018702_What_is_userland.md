---
title: "What is userland?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by cpepera on 2008-12-22
I was hoping that someone might be able to explain what userland is to me in noob language?  Specifically, I have been reading about how to run a particular application on a server and the documentation recommends "a 64 bit kernel in combination with a 32 bit userland".  What does this mean?  Thanks!

---

### Post by y6FgBn)~v on 2008-12-22
I believe this is the definition you are looking for;

Userland refers to an application space that is external to the kernel[1] and is protected by privilege separation. More specifically, it can refer to the set of libraries provided by the operating system for performing input/output or otherwise interacting with the kernel and is often used interchangeably with user space in this context. It can also refer to non-kernel system components such as a shell or user utilities for manipulating filesystem objects that are collectively referred to as "the userland".

In the filesystem hierarchical sense, userland means storage space on the system disk that is not part of critical system storage, i.e., storage space used for storage of user files such as personal documents and other non-critical data. On Unix systems this space typically resides in the Home directory.

Source: Wikipedia

---

