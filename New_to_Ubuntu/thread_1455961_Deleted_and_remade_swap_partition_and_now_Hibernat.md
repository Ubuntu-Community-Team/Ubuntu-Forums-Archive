---
title: "Deleted and remade swap partition and now Hibernate option is gone from Restart Optio"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by edcompsci on 2010-04-16
I deleted and remade my swap partition and now the ibernate option is gone from restart options. Is there a way to fix this?

---

### Post by quadproc on 2010-04-16
> **edcompsci said:**
> I deleted and remade my swap partition and now the ibernate option is gone from restart options. Is there a way to fix this?
The hibernate function uses the swap space to remember everything that was in memory when the system was shut down.  Therefore, if the hibernate function cannot find a swap space, or the swap space is too small, then hibernate won't work.

I am not sure if the swap function has to be working for hibernate to work; you could try ```
swapon
```.

Also, you could try swapon -s to see what the system thinks is happening with the swap area.

quadproc

---

