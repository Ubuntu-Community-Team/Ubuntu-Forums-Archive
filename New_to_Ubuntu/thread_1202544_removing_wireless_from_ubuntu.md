---
title: "removing wireless from ubuntu"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by muted1987 on 2009-07-02
I am in the process of eliminating modules from my kernel and was wondering as this is a wired Desktop  to a router how do i eliminate things like wireless and mobile broadband

---

### Post by carml on 2009-07-02
Why do you want to do that?

---

### Post by muted1987 on 2009-07-02
because i have no need for them and dont want them there they are loaded and not needed but i cant find where they are.

---

### Post by ukripper on 2009-07-02
> **muted1987 said:**
> I am in the process of eliminating modules from my kernel and was wondering as this is a wired Desktop  to a router how do i eliminate things like wireless and mobile broadband

Find modules you want to remove using:
```
lsmod
```

then 
```
rmmod name_of_module_here
```

---

### Post by muted1987 on 2009-07-02
ty but that will only disable for now im looking to completely remove them from startup everytime besides i have seen that they not modules so i will have to hunt through synaptic thx anyway

---

### Post by ukripper on 2009-07-03
why don't you just blacklist them in modprobe.d/blacklist ? Thereafter they won't load up during startup

---

