---
title: "bash: How to printf a text in color and blinking constantly?"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-08-08
Hello,

bash: How to printf a text in color and blinking constantly?

---

### Post by DaithiF on 2010-08-08
Hi,
for example, this gives blinking green on black:
```
printf '\e[5;32;40m Blink Text\e[m\n'
```
google for ansi control characters for the full set of codes

also, note that blinking doesn't currently work in gnome-terminal.  (but it does in xterm).
Bug: [https://bugs.launchpad.net/bugs/590735](https://bugs.launchpad.net/bugs/590735)

---

### Post by frenchn00b on 2010-08-08
> **DaithiF said:**
> Hi,
for example, this gives blinking green on black:
```
printf '\e[5;32;40m Blink Text\e[m\n'
```
google for ansi control characters for the full set of codes

also, note that blinking doesn't currently work in gnome-terminal.  (but it does in xterm).
Bug: [https://bugs.launchpad.net/bugs/590735](https://bugs.launchpad.net/bugs/590735)

wow so cool !! thanks !!

---

