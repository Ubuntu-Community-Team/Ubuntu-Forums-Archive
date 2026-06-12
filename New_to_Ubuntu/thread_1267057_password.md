---
title: "password"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by gnilaeh on 2009-09-15
can the password prompts be turned off?   it creates a problem in the terminal where my keyboard stops working.

---

### Post by adalal on 2009-09-15
> **gnilaeh said:**
> can the password prompts be turned off?   it creates a problem in the terminal where my keyboard stops working.

The password prompts there are to prevent any accidental / malicious activities from taking place. However, if you plan on doing work that would require you to use the root access every line, you can just drop to the root account using:

```
sudo su
```

After that, all you have to do is insert your password once, and then thereafter, you are logged in as root, which would not require any more system passwords for that terminal (and neither do you have to use sudo or gksudo to do administrative work).

---

### Post by MelDJ on 2009-09-15
do you mean no text or asteriks come? thats completely normal. just type you password and press enter

---

### Post by adalal on 2009-09-15
oh sorry, thought you meant you did not want to type in the password, in that case, yeah, like MelDJ said, keep typing it in, it will not show up as anything.

---

### Post by gnilaeh on 2009-09-15
Ok. Thank you for replying.

---

