---
title: "CUDA runtime problem"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by rupex2101 on 2010-03-08
Hello all,

I am using Ubuntu 9.10 and trying to install CUDA.
I could install it but unable to run the sample problems in SDK/bin/linux/release/
I am getting this error:

CUDA Device Query (Runtime API) version (CUDART static linking)
Segmentation fault

Could you guys help me out please!!

---

### Post by undecim on 2010-03-08
Looks like it's a bug in CUDA.

Not much you can do about it, except make sure you have the latest version of CUDA.

---

### Post by mung on 2010-03-16
I have this problem too. I've read elsewhere that it's the CUDA API but also maybe it's because we're using 9.10 rather than 9.04 which is supported.

---

### Post by mung on 2010-03-16
Have just updated my drivers to 190.53 for my 8600M GT and device Query now works...

---

