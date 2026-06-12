---
title: "Software sources trouble?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by AliSajidImami on 2009-10-12
Hi all,

I have this problem, that whenever I try to close the "software sources" application, it says "The information about available software is out-of-date", when i click the "reload" button, it reloads but after that,  the application goes gray, and doesn't exit. After i close it myself and run it again, it happens again. Can anyone tell me whats wrong?
Thanks in anticipation.

---

### Post by |Mitch| on 2009-10-12
nm...

---

### Post by nothingspecial on 2009-10-12
Do it from the terminal to see if any error messages are returned.

```
sudo apt-get update
```

---

### Post by AliSajidImami on 2009-10-12
It worked. Thanks a lot.
But why wasn't it working with the GUI?

---

### Post by MelDJ on 2009-10-12
i think it would have come back if you had waited a while as it was loading a lot of things. that made it grey out

---

### Post by AliSajidImami on 2009-10-12
I waited for about two hours and it didn't. But thanks.

---

### Post by lidex on 2009-10-12
You may have an errant setting in there. Try running ```
sudo apt-get update
``` in terminal again and check the terminal output for clues.
When something like this happens it's easy enough to re-install. You can do that quite simply in this case with "Add/Remove Applications" they try again.

---

