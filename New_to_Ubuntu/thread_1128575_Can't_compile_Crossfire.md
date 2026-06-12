---
title: "Can't compile Crossfire"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by eilios on 2009-04-17
I wanted to try Crossfire, so I downloaded the source and went into terminal and typed "./configure"(Like I was told to by every guide I read), and it ran fine for the first 4-5 seconds, but then I got this error.

```

configure: error: curl/curl.h header not found, but metaserver2 support is enable.  Install header file or use --disable-metaserver2

```

The disable metaserver does not work, and I have no idea what the header is or how to get it. Help?

---

### Post by llamabr on 2009-04-17
Why not just install from the repositories?

crossfire-common - Common files for Crossfire

---

### Post by eilios on 2009-04-17
> **llamabr said:**
> Why not just install from the repositories?

crossfire-common - Common files for Crossfire
Well, that's a temporary fix but sooner or later it would be good to learn how to compile things from source.

---

### Post by llamabr on 2009-04-17
> **eilios said:**
> Well, that's a temporary fix but sooner or later it would be good to learn how to compile things from source.

I'm not entirely certain that's true.  i havn't compiled an application from source in years.

The best way in ubuntu to add or remove programs is to use the package manager.  it makes sure that everything stays consistent, and that you don't have to update libraries, etc.

---

