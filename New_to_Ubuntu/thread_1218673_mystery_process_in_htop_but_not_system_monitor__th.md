---
title: "mystery process in htop but not system monitor | theme randomly changes, screenshots"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by earthpigg on 2009-07-20
i dont know if these two problems are related. running 9.04 amd64. perhaps the theme issue should be piped into the mystery process.... anyways

*some* (but not all) parts of my theme seem to randomly and suddenly be disregarded. i pointed out a few of the differences in the screenshot, if you look closely you can see others.


the only way to get it back is to restart X. the screenshot titled 'compare.jpg' demonstrates. when this happens, my system becomes sluggish and less responsive.

running 'metacity --replace' followed by 'compiz --replace' has no effect.

in addition, there is an X and GDM related mystery process that shows up in htop at the top when sorted by %CPU, but does not show up at all in gnome-system monitor. this is the second screenshot, 'X.jpg'.

i can't seem to locate the process using ps, only the expected Xorg:
```

ep@ep-9:~$ ps -A | grep X
 3328 tty7     00:05:06 Xorg
ep@ep-9:~$ 
```

the mystery process, outlined in red in X.jpg, shows up in htop even now when i am not having the issue, but it is not sitting at 35-55% of my %CPU in htop, and my system is not sluggish at the moment.


any ideas? :confused:

---

### Post by CatKiller on 2009-07-21
> **earthpigg said:**
>  *some* (but not all) parts of my theme seem to randomly and suddenly be disregarded. i pointed out a few of the differences in the screenshot, if you look closely you can see others.

Themes are applied by the gnome-settings-daemon. Occasionally (I don't know why) this fails to start, and you end up with the primitive-looking default Gnome theme. You can generally run gnome-settings-daemon from the Alt-F2 Run dialogue to start the daemon and have your theme applied again.

---

### Post by The Cog on 2009-07-21
I've got a process like that. It shows up in
ps -Af | grep X
but not in 
ps -A | grep X

---

### Post by earthpigg on 2009-07-22
thanks cat and cog, ill keep that in mind next time it happens.

does anyone know if there is a way via CLI to verify if a daemon is or is not running?

---

### Post by Durden on 2009-07-22
"ps auxg | grep daemon-name"

---

