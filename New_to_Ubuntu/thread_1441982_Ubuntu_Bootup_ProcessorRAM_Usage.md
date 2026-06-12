---
title: "Ubuntu Bootup Processor/RAM Usage"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by _h_ on 2010-03-29
Not sure if I had asked this before, but I am curious as to what Ubuntu accomodates on bootup as far as processor #'s and RAM goes.

There's a feature in Windows that allows a user to select how many processors to use, and a set amount of RAM to help boot up times. When I had Windows 7 Ultimate 64bit, I had the option set to use both my processors and all my RAM for boot.

Does Ubuntu do something like this by default, or does Ubuntu only use 1 core and a determined amount of RAM for boot?

Would there be anyway to modify this at all if Ubuntu does use such feature?

---

### Post by oldos2er on 2010-03-29
In the file /etc/init.d/rc, you can change concurrency=none to concurrency=shell. This allows the bootup process to use dual (or greater) CPUs.

---

### Post by _h_ on 2010-03-29
> **oldos2er said:**
> In the file /etc/init.d/rc, you can change concurrency=none to concurrency=shell. This allows the bootup process to use dual (or greater) CPUs.

Thanks! :popcorn:

---

### Post by _h_ on 2010-04-12
> **oldos2er said:**
> In the file /etc/init.d/rc, you can change concurrency=none to concurrency=shell. This allows the bootup process to use dual (or greater) CPUs.

Just a little follow up, I just noticed this on a fresh install when I went to alter this file again:

```
# Valid options are 'none', 'startpar' and 'makefile'.
```

Is concurrency=shell an actual valid option?

---

### Post by oldos2er on 2010-04-12
So it does. I'm running Lucid at the moment; let me test 'startpar' and I'll get back to you.

Edit: I just changed "shell" to "startpar". Seems to boot faster with startpar, so you may want to try that. Although using "shell" produced no errors that I noticed.

---

### Post by _h_ on 2010-04-12
> **oldos2er said:**
> So it does. I'm running Lucid at the moment; let me test 'startpar' and I'll get back to you.

Edit: I just changed "shell" to "startpar". Seems to boot faster with startpar, so you may want to try that. Although using "shell" produced no errors that I noticed.

What about makefile? Wanna test that for me? xD

I'll go ahead and use startpar and check my bootcharts.

EDIT: Makefile isn't good, doesn't allow me to shut down forcing me to force a shut down via holding power button which isn't good at all.

---

