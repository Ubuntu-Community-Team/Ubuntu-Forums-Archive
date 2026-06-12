---
title: "tab auto completel not working"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by natman on 2010-09-14
Hi,
I open up a terminal and type "sudo apt-" now if i tab, i expect to see "get" but nothing happens. similarly when i type "sudo apt-get install mar" and press tab i cannot see a list of packages that start with "mar".
I used to be able to do this on my previous Kubuntu, can anyone help out? By the way auto complete works fine outside of "apt-get".
thanks:

---

### Post by jtarin on 2010-09-14
To enable smart completion, edit your /etc/bash.bashrc file. Uncomment the following lines, by removing the # in the beginning of the lines:

```
#if [ -f /etc/bash_completion ]; then
# . /etc/bash_completion
#fi
```

[For a more extensive tutorial and suggestions.]("http://www.debian-administration.org/articles/316")

---

### Post by sisco311 on 2010-09-14
EDIT:
jtarin beat me to it.

---

### Post by jtarin on 2010-09-14
> **sisco311 said:**
> EDIT:
jtarin beat me to it.And I'm a slow typer.:p

---

