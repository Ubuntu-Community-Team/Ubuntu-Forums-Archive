---
title: "Removal vs. complete removal"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2010-05-06
Would someone please tell me what "complete removal" does that " removal" doesn't ? The reason I ask is that I am getting quite a list of old kernels on startup and would like to remove a few using package manager, but am not sure which command to use.
On earlier distros you could set startup manager to restrict the number, but this seems to be missing now.

---

### Post by peculiar penguin on 2010-05-06
> **ex-wirecutter said:**
> Would someone please tell me what "complete removal" does that " removal" doesn't ?
Configuration files created by whatever lives in the package, AFAIK.

---

### Post by Paddy Landau on 2010-05-06
To remove old kernels, it's perfectly fine to use "Complete removal".

We normally recommend that you keep the latest two kernels, just in case something goes wrong with the latest one.

---

### Post by ex-wirecutter on 2010-05-06
So to remove old kernels which do you suggest ?

---

### Post by ex-wirecutter on 2010-05-06
Thanks for that Paddy .

---

### Post by Paddy Landau on 2010-05-06
> **ex-wirecutter said:**
> So to remove old kernels which do you suggest ?
Complete removal, because you won't need their configuration files any more.

---

### Post by ex-wirecutter on 2010-05-06
Thanks everyone [ SOLVED ]

---

