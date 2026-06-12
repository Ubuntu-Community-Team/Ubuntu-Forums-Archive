---
title: "chrome crashes all the time.."
date: 2010-02-17
forum: New to Ubuntu
---

### Post by orky7 on 2010-02-17
i updated to 5.0.307.7 and it crashes all the time it just get disappeared all the time after some time i run it in the terminal and after termination it spit out this information in the terminal

[23147:23161:24490297048:FATAL:/usr/local/google/b/slave/chrome-official-linux-64/build/src/base/nss_util.cc(84)] Check failed: NSS_VersionCheck("3.12.3"). We depend on NSS >= 3.12.3
Trace/breakpoint trap

so how to upgrade this NSS thing
thanks.

---

### Post by achase79 on 2010-02-17
you should just need to install libnss3 from the repositories.

---

### Post by orky7 on 2010-02-17
i upgraded it still giving the same error message

---

### Post by orky7 on 2010-02-17
it get solved install this "libnss3-dev" from synaptic and it work for me no more crashes.

---

### Post by Tikkyca on 2010-02-18
That can happen when you have lot of extensions installed,each extension has it's own process,and if there are lot of processes running in the same time,it is going to crash over and over,and OVER.

---

