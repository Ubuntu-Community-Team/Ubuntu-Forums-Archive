---
title: "compiz dosnt run immediately on login"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by mudrain911 on 2009-01-03
after i log in to xubuntu, rather than starting compiz, XFWM is started, then is closed and compiz+ emerald opens. is there a way to make it so that XFWM is not run at all and is replaced by compiz?

---

### Post by anjilslaire on 2009-01-03
yup:
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)

If you have everything installed, slip down to the "Make it default" section. I'm doing this, and it works great :)

---

### Post by mudrain911 on 2009-01-03
oh in the file u have to edit, i had compiz --replace instead of just compiz, ill go test it now.

---

### Post by mudrain911 on 2009-01-03
well xfwm still is loading first, but now it is faster... if it is at all possible i would like for it to load directly into compiz... can anyone else try and help?

---

### Post by cardinals_fan on 2009-01-04
Strange - this should have done it:
```
The more-difficult-but-better way

So… You prefer the scary stuff? Well, it’s not that difficult, actually. You just press Alt+F2 and enter

gksudo "mousepad /etc/xdg/xfce4-session/xfce4-session.rc"

Basically, that opens the file xfce4-session.rc with root rights with the text editor mousepad.

In this file, all you have to do is replace:

Client0_Command=xfwm4

…with:

Client0_Command=compiz

(Thank Ubuntuforums user sisco311 for this one)

Do note that this makes Compiz default for all users, as opposed to the previous method which made it default just for you.
```

---

