---
title: "Evolution wont start"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by mvalviar on 2009-12-21
```
mvalviar@mumee:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...
** (evolution:13179): DEBUG: mailto URL command: evolution --component=mail %s
** (evolution:13179): DEBUG: mailto URL program: evolution

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:13179): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:13179): DEBUG: New Indicator: Inbox pop:
** (evolution:13179): DEBUG: New Inbox inidicator
** (evolution:13179): DEBUG: New Indicator: mvalviar@mumee mbox:///var/mail/mvalviar
** (evolution:13179): DEBUG: New account: mvalviar@mumee (mbox:///var/mail/mvalviar)
** (evolution:13179): DEBUG: Number of email accounts: 3
** (evolution:13179): DEBUG: EI: SHELL STARTUP


```
Evolution just won't start. Please help me. I just shows as a darkened box window.

---

### Post by Chesamo on 2009-12-21
Have you tried purging and reinstalling Evolution?

---

### Post by milosz.galazka on 2009-12-21
Look at [http://ubuntuforums.org/showthread.php?t=87033](http://ubuntuforums.org/showthread.php?t=87033) for evolution --force-shutdown. Just don't delete ~/.evolution directory. If you need rename it so you could import messages.

---

### Post by mvalviar on 2009-12-21
Solved. Sorry I usually search for an answer myself. But in this case I need my mail fast for my work and I simply don't have the time.

Thank you for helping me.

---

