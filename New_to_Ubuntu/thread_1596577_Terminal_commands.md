---
title: "Terminal commands"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by jodonald on 2010-10-14
I just had java go crazy on me and i was trying to kill google chrome.  I couldn't use my moues but I was able to open terminal.  However, i couldn't remember what the command for chrome was so that i could kill it.  Is there an easier way to find the command for programs or is it all a memory game?

---

### Post by renzokuken on 2010-10-14
you could run
```
ps ax
```
to give you a list of running programs and their ID numbers and kill the chrome process using its id....for example

```
kill 12345
```
(obviously replace the number with the one associated with chrome from ps ax

---

### Post by jodonald on 2010-10-14
Perfect.  Thank you sir!

---

