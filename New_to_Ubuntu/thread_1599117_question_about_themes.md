---
title: "question about themes?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-10-17
hello everyone,
let.s see if we can "do this" :)

we have a 'family laptop' as my mom calls it, that we all have different user accounts on.

my account is the only administrator, and it needs to stay that way, because i.m the only true geek of the house. my mom, dad, brother, not so much.

the problem is that the other day, when i was on my account, i made the gnome panel completely transparent, instead of the "some-of-the-things-are-transparent-and-some-of-them-are-not-kind-of-thing"; i 'fixed' the transparency problem, per sé.

the way i went about doing this, is that i navigated to /usr/share/themes/Ambiance/gtk-2.0/gtkrc with root priveleges, and edited the following line with gedit:

```
include "apps/gnome-panel.rc"
```

i changed it to :

```
include "apps/gnome-panel.rc.bak"
```

saved, logged out, back in, bars were transparent, yay!
____________________________

so the problem being, since I edited it as root, it changed all of the other accounts too, and they all look weird, and i want them to stay like they did (the default ambience theme), but i want to keep mine transparent. how do i go about doing this?
____________________________

basically, the question is: how do i keep mine transparent, but keep the rest of my family's default, without it looking weird?
____________________________

any help is greatly appreciated,
-cheers :popcorn:

---

### Post by Verbeck on 2010-10-17
the contents of /usr/share/* is shared by every one on the computer. so if you want to change a theme for you only, save the modified theme in /home/<user name>/.themes 

hope that helps

---

### Post by owners4life5 on 2010-10-17
> **Verbeck said:**
> the contents of /usr/share/* is shared by every one on the computer. so if you want to change a theme for you only, save the modified theme in /home/<user name>/.themes 

hope that helps

followed instructions, works like a charm now :)

thank you very much, sir

marking as solved :D

---

