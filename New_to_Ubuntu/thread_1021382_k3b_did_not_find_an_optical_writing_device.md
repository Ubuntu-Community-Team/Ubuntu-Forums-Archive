---
title: "k3b did not find an optical writing device"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by hifly1231 on 2008-12-25
I'm trying to burn audio to cd for the first time in Ubuntu Intrepid Ibex.  I'm getting the pop-up stating "NO CD/DVD writer found - k3b did not find an optical writing device".  What do I do?

Thanks!!!

---

### Post by Dark Aspect on 2008-12-25
> **hifly1231 said:**
> I'm trying to burn audio to cd for the first time in Ubuntu Intrepid Ibex.  I'm getting the pop-up stating "NO CD/DVD writer found - k3b did not find an optical writing device".  What do I do?

Thanks!!!

Merry Christmas,

Go to the Settings tab and click on configure K3B and then devices. Under devices click on add device and specify your CD/DVD drive from the dev folder. If you don't know what your device is, you can use the Disk Usage Analyzer tool under Applications to show both your Hard drive and your CD/DVD drive.

Just for reference mine is

```
/dev/scd0
```

---

### Post by hifly1231 on 2008-12-26
> **Dark Aspect said:**
> Merry Christmas,

Go to the Settings tab and click on configure K3B and then devices. Under devices click on add device and specify your CD/DVD drive from the dev folder. If you don't know what your device is, you can use the Disk Usage Analyzer tool under Applications to show both your Hard drive and your CD/DVD drive.

Just for reference mine is

```
/dev/scd0
```

Thank you!!!

---

