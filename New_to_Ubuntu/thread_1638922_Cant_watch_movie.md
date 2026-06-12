---
title: "Cant watch movie"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by shrivatsa on 2010-12-06
Every media player i used freezes cant even watch a video clip fully ,any solution

---

### Post by wojox on 2010-12-06
Have you installed the codecs?

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

---

### Post by shrivatsa on 2010-12-06
> **wojox said:**
> Have you installed the codecs?

```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```
yup have done it problem is after i start playing video it freezes then again it plays and cycle continues

---

### Post by MooPi on 2010-12-06
Can you give us the specs of your computer. Processor, video, memory capacity age etc.....

---

### Post by philinux on 2010-12-06
> **shrivatsa said:**
> Every media player i used freezes cant even watch a video clip fully ,any solution

Assuming this is ubuntu 10.10 have you enabled a video card driver?

System>admin>additional drivers.

If it offers one go with "Recommended".

---

### Post by shrivatsa on 2010-12-06
> **philinux said:**
> Assuming this is ubuntu 10.10 have you enabled a video card driver?

System>admin>additional drivers.

If it offers one go with "Recommended".

thanks problem solved

---

