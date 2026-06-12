---
title: "Dell latitude Speaker Problems"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Kailien92 on 2009-08-05
I just bought a dell latitude d810 and for some reason there is no sound coming through the external speakers. I know close to nothing about computers too so that isnt helping much either...anyone know what the problem could possibly be?

---

### Post by django0909 on 2009-08-05
Try typing 

```
sudo alsamixer
```

into a terminal. Put your password in when it asks and scroll across the faders to see if any are turned down?

---

### Post by Kailien92 on 2009-08-06
I'm sorry, but what is a terminal? And how do I get to it?

---

### Post by superprash2003 on 2009-08-06
Applications->Accessories->Terminal .. thats where you type commands..

---

### Post by Kailien92 on 2009-08-06
Okay so i got to the terminal and now it wont let me type anything...

---

### Post by LewRockwell on 2009-08-06
> **Kailien92 said:**
> Okay so i got to the terminal and now it wont let me type anything...

help us help you...

first, which operating system are you using on that Dell D810?

is this a new or used system and do you know who installed the operating system(s)?

regarding the terminal, you state that "it won't let you type anything" but we normally hear that when someone is attempting to type their password in for sudo and it doesn't appear to be doing anything...

the password does NOT show up as you type it and depress "enter"

also, the code should be this:```
**gksudo alsamixer**
```

.

---

