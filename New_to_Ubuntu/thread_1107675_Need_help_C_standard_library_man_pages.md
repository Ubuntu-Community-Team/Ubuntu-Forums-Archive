---
title: "Need help C standard library man pages"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by mvalviar on 2009-03-27
Is there a way to complete the man pages of the C standard library? Because there is a man page for printf but there isn't any for most of the other standard functions.

---

### Post by lloyd_b on 2009-03-27
> **mvalviar said:**
> Is there a way to complete the man pages of the C standard library? Because there is a man page for printf but there isn't any for most of the other standard functions.Try installing the package "manpages-dev" ("sudo apt-get install manpages-dev" in a terminal window, or use the package manager of your choice).

This contains most of the man(2) (system calls) and man(3) (standard library functions) man pages.

I've never understood why they don't just add this to "build-essential" - yeah, it's not truly *essential*, but it's very nice to have these if you're going to be working in C...

Lloyd B.

---

### Post by mvalviar on 2009-03-27
Thanks!

---

