---
title: "Services settings has no Unlock"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by MadsRH on 2009-06-09
By accident I unchecked the *Graphical login manager* (GDM) in the **System -> Administration -> Services Settings** and now my computer boots up without starting X!

I can login and write *startx* which will show my desktop, but now the unlock button in the *Graphical login manager* has been disabled :-(

How do I get my good old desktop back?

---

### Post by PmDematagoda on 2009-06-09
Instead of starting X using the startx command, try starting it by invoking the gdm init script manually using:-
```
/etc/init.d/gdm start
```
you may need to do that as root. Starting the session this way should ensure that the necessary services are started when X is started.

---

### Post by ptn107 on 2009-06-09
From your desktop press ALT+F2 and type:
```
gksu services-admin
```
Re-check 'Graphical login manager (gdm)' and click close.  Restart your computer.

---

### Post by MadsRH on 2009-06-09
> **ptn107 said:**
> From your desktop press ALT+F2 and type:
```
gksu services-admin
```
Re-check 'Graphical login manager (gdm)' and click close.  Restart your computer.

The unlock button is still not selectable :-(

---

### Post by MadsRH on 2009-06-09
[SIZE="5"]**[COLOR="SeaGreen"]SOLVED![/COLOR]**[/SIZE]

> **PmDematagoda said:**
> Instead of starting X using the startx command, try starting it by invoking the gdm init script manually using:-
```
/etc/init.d/gdm start
```
you may need to do that as root. Starting the session this way should ensure that the necessary services are started when X is started.

I couldn't make it work, but then I remembered that I forgot to add the *sudo *command and everything started fine. Then I was able to click unlock and re-click GDM :-)

_Thanks you so much_ for helping me PmDematagoda and also ptn107 ;)



BTW, what's up with the **thanks **buttons? Will they ever return?

---

