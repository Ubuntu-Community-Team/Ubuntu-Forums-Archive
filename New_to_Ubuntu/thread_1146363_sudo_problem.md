---
title: "sudo problem"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by y_garti on 2009-05-02
hi everyone i have a problem with sudo
i log on as root and do visudo and enter the fowling  line (just for test)

test ALL=NOPASSWD: ALL

and still every time i use sudo with user test it ask me for a password( i even restart my pc and it still doesn't work)

thanks for your help

---

### Post by Hospadar on 2009-05-02
Try putting parenthesis around the first ALL

[http://sial.org/howto/sudo/](http://sial.org/howto/sudo/)

---

### Post by y_garti on 2009-05-02
i figure out what was my problem but thanks anyway

---

### Post by unutbu on 2009-05-02
Please share -- What was the problem?

---

### Post by y_garti on 2009-05-02
this is the sudoers file (well the relvent part)

```
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
tets ALL=(ALL) NOPASSWD: ALL
```
what i did in the begin is to create a new line after the root line but my test user is a part of the admin group so the last line rest my line so to fix it i just move the line to the end of the file and it fix the problem

---

### Post by unutbu on 2009-05-02
Ah. So the last rule wins. Thanks very much.

---

