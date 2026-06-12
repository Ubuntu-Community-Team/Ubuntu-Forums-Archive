---
title: "Wubi Install fail"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by master2bz on 2009-03-10
All I get is a bunch of text abd something called a shell?

---

### Post by linuxuser21 on 2009-03-10
Is it getting messed up on the Ubuntu installation or before that?

---

### Post by orethrius on 2009-03-10
Here I was going to ask which ISO was used, as this sounds remarkably like a baseline Server install.

---

### Post by linuxuser21 on 2009-03-11
> **orethrius said:**
> Here I was going to ask which ISO was used, as this sounds remarkably like a baseline Server install.

Yeah it does.  Is it a server install?

---

### Post by Crafty Kisses on 2009-03-11
Hey there master2bz, welcome to the Linux community! Now it may be very possible you installed the server edition via Wubi, but if you're sure you didn't then we can try a couple of things my friend. We might need some more information so we can point you in the right direction here. So for example what are your system specs? Is it just a blinking cursor or are you getting "BusyBox"? What version of Ubuntu are you trying to install? I'd also like to know are you trying to install 32-bit or 64-bit Ubuntu? You also might want to try running the following on Windows:
```
chkdsk /r

```
Make sure you run it on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

---

