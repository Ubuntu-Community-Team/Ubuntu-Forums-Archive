---
title: "How do I make ktorrent and amule start everytime my computer boots?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by guest_user on 2009-12-05
Is there any other way than putting it in rc.local?
Anyway, for rc.local what is the format like, do I have to put a semicolon after each line?

Thanks in advance

---

### Post by guest_user on 2009-12-06
bump

---

### Post by cartisdm on 2009-12-06
Have you tried System > Preferences > Sessions.  Once inside that window there is a setting for Startup Programs.  You should be able to put any program in here and it will start automatically when you boot into your desktop


EDIT: I just saw that you're on kubuntu.  I am looking right now for where the startup sessions are located for kubuntu

EDIT 2: Ok, from what I found there should be a folder called

```
~/.kde/Autostart
```

Navigate to that folder and create a shortcut to your desired programs.  Upon restart your programs should auto start after login

---

### Post by guest_user on 2009-12-07
Great but how do I get them to start minimised?

---

### Post by cartisdm on 2009-12-07
> **guest_user said:**
> Great but how do I get them to start minimised?

Now you're just being picky! ;) No, of course I'm just messing with you.  I will keep looking into getting them minimize, but glad to see we are getting somewhere.

---

### Post by cartisdm on 2009-12-07
> **guest_user said:**
> Great but how do I get them to start minimised?

This might be a a long shot but try opening up the shortcut you created and modify the command it launches to look like this (where "program_name" is the particular program you want to launch):

```
program_name -iconic
```

I wish I could give more specific directions but I don't have a KDE environment in front of me in which to test it myself

---

