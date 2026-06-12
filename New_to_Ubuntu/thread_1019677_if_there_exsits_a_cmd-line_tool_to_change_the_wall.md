---
title: "if there exsits a cmd-line tool to change the wallpaper in GNOME envirment."
date: 2008-12-23
forum: New to Ubuntu
---

### Post by haha.ysj on 2008-12-23
Hi, everyone.

I want to write a shell script to change wallpaper according to some strategy. (For example, according to time of day, festive, special days and so on)

I wonder if there exsits a cmd-line tool for me to change the wallpaper in GNOME envirment.(Gnome 2.24.1)

btw, I found a file (~/.gconf/desktop/gnome/backgroud/%gconf.xml) which saves the current wallpaper setting.

It would be gratefull if anyone gives me a clue.  :D

---

### Post by decoherence on 2008-12-23
i do believe the command you want is called gsetroot

---

### Post by Dedoimedo on 2008-12-23
Does this work for you:

```

gconftool-2 --type string --set /desktop/gnome/background/picture_filename /path/to/image.jpg

```

See more details:
[http://linux.die.net/man/1/gconftool-2](http://linux.die.net/man/1/gconftool-2)

Cheers,
Dedoimedo

---

### Post by haha.ysj on 2008-12-23
> **Dedoimedo said:**
> Does this work for you:

```

gconftool-2 --type string --set /desktop/gnome/background/picture_filename /path/to/image.jpg

```



Thanks a lot~ ^^
That is what I try to find!

---

