---
title: "All sorts of Samba weirdness"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by rts on 2007-03-14
Running a fully up-to-date edgy and have a Samba share mounted.  This share is used heavily with a lot of reading and writing.

Lately processes that read/write this share have been spewing "Input/output errors" and "Out of memory" errors, with many "error=-12" messages in dmesg (which, I guess, means ENOMEM).

Any ideas what could provoke such things?  The machine has 512 MB, which should be enough (other machines with a similar configuration don't have this problem).

---

