---
title: "Stuck in Shell"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by pslinger on 2009-02-15
I need help getting out of Shell mode and back to the desktop. I used Wubi to install and everything was fine. I downloaded 252 updates and rebooted. I am using a dual boot, and after logging in, it goes right to a shell environment, I downloaded the beginners guide and it says that using "ctrl+alt+F-7" will take me back to the desktop. This does not work, it just seems to hang at the command line screen. Please help...

Thanks,

Pat

---

### Post by Kareeser on 2009-02-15
startx

---

### Post by pslinger on 2009-02-15
Is that what I type in the command line to get back to the desktop?

---

### Post by cerealtx on 2009-02-15
> **pslinger said:**
> Is that what I type in the command line to get back to the desktop?

that is used to start your xorg server assuming its not starting, if that does not work, type ```
gdm &
```

---

