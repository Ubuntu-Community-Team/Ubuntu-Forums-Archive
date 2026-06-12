---
title: "Ubuntu 11 NO TASKBARS"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by rarivera11 on 2011-05-02
i just upgraded to ubuntu 11 tried to activate compiz 3d cube and now i have neither of the 2 taskbars and also I dont have the window options like minimize maximize close. How can I fix this???

---

### Post by Peter09 on 2011-05-02
if you can get to a terminal try 

```
unity --reset
```

---

### Post by Adrianzr1 on 2011-05-02
for a new terminal

> ctrl + alt + t

then write what peter says

---

### Post by rarivera11 on 2011-05-02
I cant get to a terminal. I can only open what I have in my desktop and thats it.

---

### Post by rarivera11 on 2011-05-02
Tried ctrl + alt + t and it doesnt work either.

---

### Post by rarivera11 on 2011-05-02
Someone there??

---

### Post by 5149.5 on 2011-05-02
Alt+F2 will get you started.

---

### Post by corncob on 2011-05-02
> **rarivera11 said:**
> Someone there??

Sounds like an issue with the theme maybe.  Try right-clicking on the desktop and select 'change desktop background'.  When the window opens select the Theme Tab and -- ugh -- change the theme.  I'm using the classic desktop and don't know anything about Unity but if this doesn't work you might try changing the desktop to classic on startup.

---

### Post by nerdy_kid on 2011-05-02
afaik enabling the cube disables unity.  To fix this, switch to a virtual terminal by hitting <ctrl> <alt> <F1>.  Log in, and do this:

```

export DISPLAY=:0
unity --reset
sudo reboot

```

and that should get you back up and running again.

---

