---
title: "You have no write permissions for the directory"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by InSoRi on 2011-06-24
...And the directory is usr/share/(program I'm trying to install). The directory usr/share is the preferred directory, but apparently I don't have write permissions for that directory. Isn't that a bit weird? And how can I get that permission?

I really need this program installed by tomorrow, and I'm a complete newbie to Ubuntu, so I start getting a bit frustrated now... Can anyone help me?

Cheers
InSoRi

---

### Post by Neoncamouflage on 2011-06-24
Go to /usr and try this:
```
chmod 777 share
```

That should give all users read, write, and execute permission for the directory. You may want to change it back after, especially if you're on a shared computer.

---

### Post by InSoRi on 2011-06-24
Hi, thanks for helping - but unfortunately it didn't do anything. All I got was *chmod: changing permissions  of 'share': operation not permitted *

What could this be?

---

### Post by Neoncamouflage on 2011-06-24
Ah, my bad, run it as sudo.

---

### Post by InSoRi on 2011-06-24
Great! Thanks! I got it now, it's installing :-D

---

### Post by Neoncamouflage on 2011-06-24
Happy to help, just remember that it's now open for all users to write regardless of whether they have root access. So if you want to fix that just do chmod again but with 755. Gives root accounts read, write, execute permission but everyone else only read and execute.

---

### Post by InSoRi on 2011-06-24
Thanks, you've been to great help :-) I appreciate it!

---

