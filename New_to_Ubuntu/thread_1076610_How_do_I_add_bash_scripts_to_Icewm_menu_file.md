---
title: "How do I add bash scripts to Icewm menu file?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-02-21
I just wanted to know how I can add terminal apps to the Icewm Menu.

I can't find documentation or this anywhere.

Any ideas? Thanks in advance.

---

### Post by kerry_s on 2009-02-21
read the man page for the terminal your using to see what the exec switch is, for example xterm would be:

xterm -e your-command

example htop:
xterm -e htop

now if it's a command that runs and quits you can put a hold:
xterm -hold -e your-command

---

### Post by pluckypigeon on 2009-02-21
> **kerry_s said:**
> read the man page for the terminal your using to see what the exec switch is, for example xterm would be:

xterm -e your-command

example htop:
xterm -e htop

now if it's a command that runs and quits you can put a hold:
xterm -hold -e your-command

Cheers. Thanks for that.

---

