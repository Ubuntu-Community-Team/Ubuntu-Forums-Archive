---
title: "what is the advantage of using cross compiler"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by nadeemvit on 2010-12-13
hi,

what is the advantage of cross compiler over nativ compiler?
why do i need to cross compile any c binary even though i include the same header file
in an application.how does the size of cross compiled binary less than the native compiled binary?

regards
nadeem

---

### Post by StephenDavison on 2010-12-13
It's not about the source code.  It's really about creating a binary targeted for a different architecture.  The first thing that came to my mind was speed.  Think about using a fast host computer to cross-compile a kernel for a much slower target machine that has limited resources.

Two seconds typing "cross compile" for a Google search returned this intro:
[http://www.landley.net/writing/docs/cross-compiling.html](http://www.landley.net/writing/docs/cross-compiling.html)

---

