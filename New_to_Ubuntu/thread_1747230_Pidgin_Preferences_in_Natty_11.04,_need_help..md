---
title: "Pidgin Preferences in Natty 11.04, need help."
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Christopher on 2011-05-02
How do i access the preference/settings menu for Pidgin in Ubuntu 11.04? Thanks in advance Chris.

---

### Post by Christopher on 2011-05-02
Anyone?

---

### Post by Christopher on 2011-05-02
Im trying to access preferences in Pidgin, does anyone know how i can do this? Thanks. Chris.

---

### Post by sauma on 2011-05-02
When you have the main Pidgin window active, move the mouse to the top of the screen. You should see words appear. Tools>Preferences. Or Ctrl+P.

---

### Post by Christopher on 2011-05-02
> **sauma said:**
> When you have the main Pidgin window active, move the mouse to the top of the screen. You should see words appear. Tools>Preferences. Or Ctrl+P.

Awesome thank you, i had to use control p, using the mouse to hove didn't do anything, thought that was odd.

---

### Post by Christopher on 2011-07-30
How can you add people to your ignore list? I had someone message me and i have no idea who they are. Thanks. Chris.




Also how do i tell what version of Pidgin im running?

---

### Post by akoskm on 2011-07-30
> **Christopher said:**
> How can you add people to your ignore list?
I suppose the **Block** option from the context menu should do this job for you!
> **Christopher said:**
> 
I had someone message me and i have no idea who they are. Thanks. Chris.




Also how do i tell what version of Pidgin im running?

Help > About or type in the terminal:
```

apt-cache show pidgin | grep Version:

```.

---

### Post by doulos564 on 2011-09-08
I have this same issue:
Version: 1:2.7.11-1ubuntu2

In Ubuntu 11.04 64-bit.

---

### Post by Christopher on 2011-09-09
> **akoskm said:**
> I suppose the **Block** option from the context menu should do this job for you!

Help > About or type in the terminal:
```

apt-cache show pidgin | grep Version:

```.



[B]Thank you!

Version: 1:2.7.11-1ubuntu2
Version: 1:2.9.0-1ubuntu0+pidgin2.11.04[/B]

---

