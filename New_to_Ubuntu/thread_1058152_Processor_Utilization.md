---
title: "Processor Utilization"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by cfree220 on 2009-02-02
I just took a look at the system monitor and noticed that, although both cores are being used, they do not appear to be used simultaneously. One core will be running at 80-100%, while the other sits at ~o%. Then they will switch. The processor is the Intel Core2Duo T8300 (2.4GHz). OS is Ubuntu 8.10 64-bit.

---

### Post by notquitemichael on 2009-02-02
i suspect that's something to do with weather the application itself is coded to use both processors efficiently.
i shouldn't worry as i doubt you're losing any performace.

---

### Post by Titan8990 on 2009-02-02
This is because the vast majority of applications are not programmed to be multi-threaded. You will see less of this as programmers take advantage of multi-core systems.

---

