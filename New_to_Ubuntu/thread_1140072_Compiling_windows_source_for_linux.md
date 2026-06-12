---
title: "Compiling windows source for linux"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by t0p on 2009-04-27
If you have the source code for a windows app, is it possible to compile it to run on linux? Would it be difficult? Are there any languages a windows app might be written in that couldnt be compiled for linux?

---

### Post by blueridgedog on 2009-04-27
> **t0p said:**
> If you have the source code for a windows app, is it possible to compile it to run on linux? Would it be difficult? Are there any languages a windows app might be written in that couldnt be compiled for linux?

It could not work in visual basic or .net as they have library dependencies that do not exit in the Linux world, but if you have C code or Java code and did not mind porting the library calls, then yes, with some work, you get compile it.

---

### Post by Hospadar on 2009-04-27
This is a very broad topic, and there's a lot too it.

If you're Writing a new application, write it in something like java or python that is easy to port (most things will just work)

if it's already written (or needs to be in C) then you're going to be doing a lot more work

---

