---
title: "file:dev/null"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-13
Some of my files are stuck in file:dev/null and will not print...how can I get them out of that folder and into the print queue. Thanks.

---

### Post by louieb on 2009-05-13
/dev/null is the black hole aka "bit bucket" of Linux. Normally used to send output you never want to see again. 

Any output you sent there is gone.

---

### Post by whoop on 2009-05-13
> **dunbrokin said:**
> Some of my files are stuck in file:dev/null and will not print...how can I get them out of that folder and into the print queue. Thanks.
/dev/null is a bit like a black hole (i'm not kidding). It's a null device, it will never return something and everything you put in it will be gone.

So in your situation it could mean something like. The system can't print for some reason so the "printing-stream" (I just invented a word :p) is being put to /dev/null.

---

### Post by Iowan on 2009-05-13
I suppose you could think of /dev/null as a "write-only" directory.

---

### Post by whoop on 2009-05-13
> **Iowan said:**
> I suppose you could think of /dev/null as a "write-only" directory.
Ahh, that explains why my hd is so full ;)

---

### Post by lisati on 2009-05-13
I like the "black hole" idea presented by other posters.

My understanding of /dev/null is that it is, loosely speaking, the Linux equivalent of the MS-DOS/Windows device "null:" (spelling?) It's a bit like a file name you can use when you don't need a real file - when used as an input file, it returns an "end of file" condition, and when used for output, the output just disappears with no hope of recovery.

---

### Post by dunbrokin on 2009-05-13
Thanks all....back to trying to reconstruct my print queue items then...

---

