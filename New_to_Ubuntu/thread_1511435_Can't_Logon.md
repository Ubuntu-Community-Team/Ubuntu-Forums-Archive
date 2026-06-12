---
title: "Can't Logon"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by xTwitchyx23 on 2010-06-16
Hello...

... I am dual-booting Vista and Ubuntu... I've Been Using Ubuntu for a couple of months now, but just today, I booted, loaded ubuntu, It loaded up but All I see is the mouse cursor and a black screen... A Little Help, Please???

---

### Post by stderr on 2010-06-17
Hi

Could you try hitting Ctrl + Alt + F1 at that stage, and if you then see a login prompt, login as usual, and enter the command:

```
startx
```

This tries to start the X Server (GUI). Any interesting error messages that you get would be useful.

---

