---
title: "Questions about Shell??"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by karthick87 on 2010-02-12
When i press the key **CTRL+ALT+F1** it takes me to the shell prompt showing "**Ubuntu 9.04 Learners-desktop tty1**" Similarly when i press **CTRL+ALT+F2** it takes me to the another shell prompt showing "**Ubuntu 9.04 Learners-desktop tty2**" and so on..What is the difference between all these shells???

---

### Post by tom56 on 2010-02-12
No difference, it's just so you can do more than one thing at once. It's also possible to have different users logged in to each one.

---

### Post by nothingspecial on 2010-02-12
Try installing byobu (a fancy name for gnu-screen).

It gives you the same functionality but you can run it in the gui.

F2 to create a new session F4 moves forward F3 moves back.

You can use it in the tty consoles aswell.

You can imagine how confusing it can get if you run byobu in all 6 consoles.

---

### Post by Bachstelze on 2010-02-12
> **getyourkarthick said:**
> When i press the key **CTRL+ALT+F1** it takes me to the shell prompt showing "**Ubuntu 9.04 Learners-desktop tty1**" Similarly when i press **CTRL+ALT+F2** it takes me to the another shell prompt showing "**Ubuntu 9.04 Learners-desktop tty2**" and so on..What is the difference between all these shells???

You're confusing "shell" and "terminal". The shell is the programs that runs in a terminal and lets you enter commands. The terminal is the device the shell runs of. In your case, the terminal is a virtual console, and there are several of them.

To answer your question, you can just say they are the same, for now. The reason there's several of them is to give the ability to run several programs simultaneously. Typically, when you run a program in a terminal, you can't run another one in the ame terminal until the first one has terminated. Swiching to another terminal lets you run another program while the first one is still running on the first terminal.

---

### Post by falconindy on 2010-02-12
The difference is the tty device they utilize for input/output.

```
ls /dev/tty[0-9]*
```

---

### Post by karthick87 on 2010-02-12
Thank you..

---

