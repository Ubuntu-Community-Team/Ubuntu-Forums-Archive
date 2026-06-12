---
title: "Mouse Cursor Not Working Outside of Web"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Isoroth321 on 2011-01-29
[SIZE=2]Hey Guys,

I was looking Gnome-look.org and found some cool mouse cursors.  But apparently they only work when I hover my mouse over a web page.  Is this normal or does this need to be fixed somehow?

Thanks
[/SIZE]

---

### Post by kr0n1x on 2011-01-29
> **Isoroth321 said:**
> [SIZE=2]Hey Guys,

I was looking Gnome-look.org and found some cool mouse cursors.  But apparently they only work when I hover my mouse over a web page.  Is this normal or does this need to be fixed somehow?

Thanks
[/SIZE]

Hi, when you say "over a web page", do you mean a link to a page? (by default is it a hand with a finger touching the link :P ?)

Maybe the file you've downloaded doesn't include all the cursors forms...

---

### Post by Isoroth321 on 2011-01-30
> Hi, when you say "over a web page", do you mean a link to a page?[SIZE=2]
No.  The cursor that I have chosen to be my supposed default only works when I basically place it over my browser.  And it goes to the white cursor outside of it. [/SIZE]:-k

---

### Post by Verbeck on 2011-01-30
its a small bug with compiz
the work around is to change the default cursor in /usr/share/icons/default/index.theme
*```
gksu gedit /usr/share/icons/default/index.theme
```*and within that file
```
[icon theme] 
Inherits=**CursorThemeName**

```
then, re-login

---

### Post by Isoroth321 on 2011-01-30
[SIZE=2]Woot! It worked!  Thanks <3[/SIZE]

---

