---
title: "How to find out if running amd64 or i386?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by jbutzu on 2009-08-26
Hi.  I am trying to install virtual box and I know I my computer has amd64 processor.  The problem is when trying to install v.b. I see a message stating that this is not correct.  I downloaded the version for i386 and it seems to be working.  Why is that?  

:confused:

Thanks - 
John

Oh- I and I am running ubuntu *latest version

---

### Post by tuxxy on 2009-08-26
Open terminal and enter this command;

```
uname -m 
```

If the output is x86_64 then you are running 64-bit, maybe you selected a 32-bit ISO from the Ubuntu website by mistake? for more information on the OS you can run

```
uname -a

```

---

### Post by ibutho on 2009-08-26
One option is to use uname e.g. "uname -sm". If you get something like i686 then you are running the 32 bit version.

---

### Post by R3fr4cti0n on 2009-08-26
open a trminal and past this```
uname -a
```

if it is 64 bit itll say x84_64 or something like that if not, its 32 32 says... i think i383

---

### Post by R3fr4cti0n on 2009-08-26
tuxxxy beat me to it! lol

---

### Post by tuxxy on 2009-08-26
hehe yep you have to be quick round here R3fr4cti0n :lolflag:

---

### Post by fela on 2009-08-26
> **R3fr4cti0n said:**
> tuxxxy beat me to it! lol

You can edit posts you know :)

---

### Post by jbutzu on 2009-08-26
Thank you to all that replied!
:P

---

### Post by fela on 2009-08-26
> **jbutzu said:**
> Thank you to all that replied!
:P

No problem! :D

---

