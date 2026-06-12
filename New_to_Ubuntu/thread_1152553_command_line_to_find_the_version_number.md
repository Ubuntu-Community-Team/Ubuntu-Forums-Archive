---
title: "command line to find the version number"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by rfbeck on 2009-05-07
Hi,
What command line can I use to find the version number of Ibex.
Thanks,
______
Robert

---

### Post by Didius Falco on 2009-05-07
> **rfbeck said:**
> Hi,
What command line can I use to find the version number of Ibex.
Thanks,
______
Robert

This will show version number/release, code name and kernel

```
lsb_release -a && uname -r
```

Regards,

Didius

---

