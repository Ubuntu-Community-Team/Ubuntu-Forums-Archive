---
title: "Can't get past the purple screen in 10.04 that says Ubuntu with the four dots"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Irish1 on 2010-11-14
I tried to configure my xinput settings and did something wrong.  Can anyone tell me what I should do to at least be able to pull up a terminal window?

---

### Post by Irish1 on 2010-11-14
I tried to configure my xinput settings and did something wrong.  Can anyone tell me what I should do to at least be able to pull up a terminal window?

---

### Post by Hippytaff on 2010-11-15
Have you tried booting into recovery mode?
 
Or boot from LiveCD and then you can have a look around and try to diagnose the problem
```

dmesg | less

```
Boot logs can be found here
```

cat /var/logs/boot.log

```

---

