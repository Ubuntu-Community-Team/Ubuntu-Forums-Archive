---
title: "help??"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-04-23
i recently reinstalled xubuntu 8.04 using wubi.
problem is when i turn on the computer,
the loading screen is ok but then half way,
it stops and then a black screen appears with this:
starting something              [OK]
starting something              [OK]
starting something              [OK]
starting something              [OK]
starting something              [OK]
starting something              [OK]

something like that. i cant keep up what exactly those were
because it was quick to appear then disappear then it shows me the login screen.

is this normal?

any help to get rid of this scenario when loggin in?
thanks!

---

### Post by Paqman on 2009-04-23
> **iam_newhere said:**
> 
is this normal?


No, but it's not necessarily bad either. Is everything working on the machine otherwise? USB? Bluetooth? Printers? That kind of thing?

---

### Post by iam_newhere on 2009-04-23
> **Paqman said:**
> No, but it's not necessarily bad either. Is everything working on the machine otherwise? USB? Bluetooth? Printers? That kind of thing?

yes. everything is fine.
but i just find it kind of not pleasing though.

did u experience this thing too?

---

### Post by Paqman on 2009-04-23
> **iam_newhere said:**
> yes. everything is fine.
but i just find it kind of not pleasing though.


Agreed, scrolling text ain't pretty

> 
did u experience this thing too?

Nope. Basically what's happening is that something is interrupting the boot process to the point that the system thinks it should show you. If you want to get to the bottom of it, you can start trawling through your boot logs (they live in /var/log) to see if you can spot the error. IIRC you can also hit ctrl-s to stop messages scrolling during boot, so that you cna read them.

---

### Post by iam_newhere on 2009-04-24
> **Paqman said:**
> Agreed, scrolling text ain't pretty



Nope. Basically what's happening is that something is interrupting the boot process to the point that the system thinks it should show you. If you want to get to the bottom of it, you can start trawling through your boot logs (they live in /var/log) to see if you can spot the error. IIRC you can also hit ctrl-s to stop messages scrolling during boot, so that you cna read them.

ok i will try that tomorow. im tired. thanks for suggestions!

---

