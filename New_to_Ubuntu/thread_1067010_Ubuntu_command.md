---
title: "Ubuntu command"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Drenriza on 2009-02-11
Is their a command that tells you about you're system hardware, such as.

what gfx you got hdd, mb, cpu and so on?

Thanks on advanse

---

### Post by halitech on 2009-02-11
you may need to install it but lshw will do it in the terminal. you can also output it to a file

```
lshw > ~/Desktop/config
```

---

### Post by The Cog on 2009-02-11
Or:
> sudo lshw -html > Desktop/config.html


---

