---
title: "Aliases"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by davidstri on 2009-03-13
Hi, I made an alias rm='rm -i' using the terminal. It works with the current terminal but when I close the terminal and open it up again, the alias doesn't work again. Am I doing something wrong or is that just the way it works?

---

### Post by taurus on 2009-03-13
If you set it from a terminal, it only applies to that current terminal so perhaps you think about adding that to your ~/.bashrc.

```
gedit ~/.bashrc
```
Then add whatever alias you want to the end of it.

```
alias rm='rm -i'
```
Save it and then

```
source ~/.bashrc
```

---

### Post by davidstri on 2009-03-13
Thanks, that worked.

---

