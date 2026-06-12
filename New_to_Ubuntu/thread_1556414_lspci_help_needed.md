---
title: "lspci help needed"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-08-19
Need a little help interpreting this:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

```
I'm not sure if I'm using both, or one or the other. There's an ATI proprietary driver that might help with the freezing problem I'm having when switching from X to tty, so I need to know if the second one listed is actually doing something.

Also, if I install the driver and things get fouled up, is there a way to uninstall it in recovery mode?

---

### Post by Chris1274 on 2010-08-19
So according to sysinfo, the ATI Radeon itself is the graphics card.

---

