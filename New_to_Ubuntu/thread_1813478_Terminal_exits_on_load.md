---
title: "Terminal exits on load"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by logic@math on 2011-07-27
hello, I am totally new to Ubuntu, I installed it yesterday and today I was playing around with terminal when I saw that you could add profiles or something. 

**I took a look and I entered a command to run everytime I open terminal BUT I also selected to close terminal after the command was executed. The command was something like:**

```
echo "hello bla bla bla"
```so now when I try to open terminal, it exit immediately so I can't change it back to not executing any command. If anyone could help with this?

---

### Post by Krytarik on 2011-07-27
It seems like the settings you've changed are not capable to achieve the intended target. So, just revert them, run these commands through the Alt+F2 dialog:
```

gconftool-2 --set --type bool /apps/gnome-terminal/profiles/Default/use_custom_command false
gconftool-2 --unset /apps/gnome-terminal/profiles/Default/custom_command
```Greetings.

---

### Post by logic@math on 2011-07-27
> **Krytarik said:**
> It seems like the settings you've changed are not capable to achieve the intended target. So, just revert them, run these commands through the Alt+F2 dialog:
```

gconftool-2 --set --type bool /apps/gnome-terminal/profiles/Default/use_custom_command false
gconftool-2 --unset /apps/gnome-terminal/profiles/Default/custom_command
```Greetings.

Thank you krytarik. Worked without a flaw :)

---

### Post by jtarin on 2011-07-27
redundant

---

