---
title: "Changed time settings, now what"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by brubakes on 2010-11-19
I have a Ubuntu server that I have set to check with internet ntp servers vs the local clock.  How do I make this go into effect.  As of now the workstation still shows an incorrect time.  Can I do this without having to restart?

---

### Post by spikoley on 2010-11-19
I have never used it, but I think the command *ntpdate* is what you are looking for.  For more information check out the man page.

```
man ntpdate
```

---

