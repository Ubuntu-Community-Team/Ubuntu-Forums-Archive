---
title: "How do I fork a process from bash?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-24
Self entitled.

---

### Post by undecim on 2010-02-24
I might not understand exactly what you mean, but If I am running a GUI program from the terminal (for example, to see the debugging output) and then decide I want to close the terminal to clean up my screen, I press Ctrl + Z in the terminal and type "%1 & disown", which makes the completely process seperate from bash. 

If you want to do that as you start the process, you can use "command & disown"

---

### Post by warp99 on 2010-02-24
Forget the previous answer I understand what you want. When you run the command just put an & at the end and the process will "fork" from the current bash shell. Example:

```
nautilus &
```

Now nautilus will "fork" from the bash shell as a separate process. Sometimes you have to press enter again in the terminal if there's a non fatal error.

---

