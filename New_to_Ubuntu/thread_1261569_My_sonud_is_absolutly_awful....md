---
title: "My sonud is absolutly awful..."
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Coh3n on 2009-09-08
I just installed 9.04 on my laptop, and everything is working accordingly except my sound is brutal.  I'm guess I have to install some sort of driver, but I have no idea which one to get.  Any help would be greatly appreciated.

Thanks,

Coh3n

---

### Post by nandemonai on 2009-09-08
> **Coh3n said:**
> I just installed 9.04 on my laptop, and everything is working accordingly except my sound is brutal.  I'm guess I have to install some sort of driver, but I have no idea which one to get.  Any help would be greatly appreciated.

Thanks,

Coh3n

First, check your mixer levels. Secondly, post the output from:

```
lspci
```

---

### Post by 3rdalbum on 2009-09-09
> **Coh3n said:**
> I just installed 9.04 on my laptop, and everything is working accordingly except my sound is brutal.

If it's distorting, try turning down the PCM channel a little bit in the volume control.

---

### Post by Coh3n on 2009-09-09
> **3rdalbum said:**
> If it's distorting, try turning down the PCM channel a little bit in the volume control.

Haha that worked great, thanks very much! :D

---

### Post by credobyte on 2009-09-09
To get the default config, set PCM to 80%. If it's higher/lower, you'll definitely have problems with your sound quality.

---

### Post by ashwinhgtx on 2009-09-09
You could also try muting the default microphone if it's connected. You can turn it back on whenever you need it.

---

