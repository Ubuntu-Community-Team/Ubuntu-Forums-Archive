---
title: "failed to execute su-to-root no such file or directory =["
date: 2009-01-31
forum: New to Ubuntu
---

### Post by godfromdfo on 2009-01-31
ok, long story short, I downloaded wifi rader from windows, transfered and installed it ubuntu because network manager doesnt like wep... but now.. wifi rader doesnt launch it just comes up with the titles message... please help =[

---

### Post by cmnorton on 2009-01-31
You've got a bunch of problems listed here.

I don't understand the part about downloading something from Windows.

It sounds like if you got your Network Manager problems fixed, you would be all set. What problems did you have with Network Manager?

---

### Post by fsando on 2010-02-04
> **godfromdfo said:**
> ok, long story short, I downloaded wifi rader from windows, transfered and installed it ubuntu because network manager doesnt like wep... but now.. wifi rader doesnt launch it just comes up with the titles message... please help =[

Hi
Had similar problem with another program when trying to run it as root from the menu.

The problem is confusing - here's how I found the solution (for future reference).

I looked into the menu's actual command and saw "su-to-root". I tried to run that from the command line and got:
```
~$ su-to-root
The program 'su-to-root' is currently not installed.  You can install it by typing:
sudo apt-get install menu
...

```
Which is the solution.

---

