---
title: "ubuntu help : man pages unreadable"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Lioobayoyo on 2010-11-22
Hey all,

i'm new to ubuntu. (10.04 lucid lynx)

i tried to watch the built-in help (buton help on top of screen)

when i go on Advanced topics -> Terminal command references (man pages)

i get this :

[[IMG]http://img517.imageshack.us/img517/5690/screenshothc.png[/IMG]](http://img517.imageshack.us/i/screenshothc.png/)
looks like some character sets haven't been installed...

how can i fix that ?

thanks in advance !

---

### Post by cariboo on 2010-11-22
I would suggest you re-install language-pack-gnome-en-base, it's in the repositories.

---

### Post by Lioobayoyo on 2010-11-29
thx for your help

i've done it (sudo aptitude reinstall language-pack-gnome-en-base), and even rebooted my computer, but it doesn't work

note that the problem is only for the help page i mentionned and for the titles of the sub-pages concerned. once i click on the various lines i can access the list of commands, constants etc. of the man clearly, but i just don't know where i'm browsing.

---

### Post by karthick87 on 2010-11-29
You should enable UTF-8.Type the following in terminal
```
export LANG=en_US.UTF-8
```

---

### Post by demilord on 2011-01-27
its a very old and unresolved issue.. its known by the devvers... but it stays unassigned and priority is on low... Maybe this year it will get fixed.. But I dont count to much on it.

---

