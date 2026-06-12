---
title: "a command to stop the root session in my terminal?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-30
when im having a root session in the terminal by opening an application ,i notice after that the root session remains..

---

### Post by philinux on 2009-06-30
It will time out unless you used sudo -i. I think the default is 10 mins ctrl d will end it.

---

### Post by MrWES on 2009-06-30
> **heyyy said:**
> when im having a root session in the terminal by opening an application ,i notice after that the root session remains..

run the app with & -- puts the job in the background

for example:

evolution & (hit return)

---

### Post by mcduck on 2009-06-30
> **heyyy said:**
> when im having a root session in the terminal by opening an application ,i notice after that the root session remains..

If you mean the time after running a command with "sudo" when you don't need to retype your password, that's 15 minutes and will timeout automatically.

If you open a root session in terminal with "sudo -i" (or some similar command) just run "exit" to return to normal user.

..but if you start a program as root, it will run as root until you close that program.

---

### Post by heyyy on 2009-06-30
i just want a command to stop it before it timed out by itshelf

---

