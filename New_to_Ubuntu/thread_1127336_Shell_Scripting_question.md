---
title: "Shell Scripting question"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by SuperMiguel on 2009-04-16
Why won’t the exit command terminate the script, when placed in a shell script like this: 
( statements; exit ) How would you fix this, so the script exits after running the statements?

---

### Post by JohnFH on 2009-04-16
The brackets start a subshell, so the exit command will just exit the subshell.

If you want to exit but only if the statements work, then forget the brackets and do something like:

statement && exit

---

### Post by unutbu on 2009-04-16
Remove the parentheses?

---

