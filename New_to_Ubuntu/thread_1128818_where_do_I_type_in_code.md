---
title: "where do I type in code?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by hortstu on 2009-04-18
I just installed ubuntu the other night so forgive my ignorance.

Ive been going through the 'tutorials and tips' section, specifically the one about WINE. I dont know where to type in the codes that are given.  Can someone fill me in?

---

### Post by Bucky Ball on 2009-04-18
Applications-> Accessories-> Terminal

---

### Post by doas777 on 2009-04-18
you will find that most forum help is command based. just copy and paste them. you can copy/paste within the terminal by rightclicking with your mouse, or by using ctrl + shift + c to copy and ctrl + shift + v to paste.

if a command messes up because of a typo, just hit your "up" arrow, and the command will come back up, so you can fix it rather than retype.

if a tutorial says somthing must be run as "root" or administrator,
just put 'sudo' in front of the command
```

sudo <command>

```
it will then prompt you for your password. type it in and hit enter again to execute the command.

if you ever need to cancel a command while it is running, use ctrl + c

thats a crash course on the shell. hope it helps

---

### Post by rhcm123 on 2009-04-18
> **hortstu said:**
> I just installed ubuntu the other night so forgive my ignorance.

Ive been going through the 'tutorials and tips' section, specifically the one about WINE. I dont know where to type in the codes that are given.  Can someone fill me in?

your terminal. (applications -> accesories -> terminal)
If you have source code, write it to a file called code.c on your desktop, then run this command in your terminal:
```
gcc ~/Desktop/code.c
```

---

### Post by hortstu on 2009-04-18
thanks for the help.

---

