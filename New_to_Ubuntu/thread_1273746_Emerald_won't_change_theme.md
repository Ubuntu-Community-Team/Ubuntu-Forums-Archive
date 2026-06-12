---
title: "Emerald won't change theme"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by oohbuntoo on 2009-09-23
Not sure if I posted this question already.  When I try to change themes in Emerald it won't work.  I type "emerald --replace" in terminal, which changes it, but, when I try to close terminal it says it's still running.  I don't know how to get the selected theme to stick for good.

---

### Post by overdrank on 2009-09-23
> **oohbuntoo said:**
> Not sure if I posted this question already.  When I try to change themes in Emerald it won't work.  I type "emerald --replace" in terminal, which changes it, but, when I try to close terminal it says it's still running.  I don't know how to get the selected theme to stick for good.

Hi and use the alt, F2 keys and enter the command :)

---

### Post by credobyte on 2009-09-23
```
emerald --replace &

```

Don't forget to add as a startup application ( so you shouldn't do this again each time you reboot ).

---

### Post by oohbuntoo on 2009-09-23
> **overdrank said:**
> Hi and use the alt, F2 keys and enter the command :)
Thanks for the tip overdrank!

---

### Post by oohbuntoo on 2009-09-23
> **credobyte said:**
> ```
emerald --replace &

```

Don't forget to add as a startup application ( so you shouldn't do this again each time you reboot ).
Hey, what do I type in the command field when I try to add Emerald to the start up program list??

---

### Post by oldos2er on 2009-09-23
> **oohbuntoo said:**
> Hey, what do I type in the command field when I try to add Emerald to the start up program list??

/usr/bin/emerald

---

### Post by oohbuntoo on 2009-09-23
> **oldos2er said:**
> /usr/bin/emerald
Thanks a mill, I'll get right on it!

---

### Post by mcduck on 2009-09-24
> **oohbuntoo said:**
> Hey, what do I type in the command field when I try to add Emerald to the start up program list??

The best way is to set Compiz itself to use Emerald by default, by changing the command in the CompizConfig Settings Manager, under the Window Decoration-plugin's settings.

If you just add "emerald --replace" to Gnome's startup, you'll be first starting Compiz with GWD, and then immediately replacing it with Emerald. Better just load Emerald in the first place.. ;)

---

### Post by oohbuntoo on 2009-09-24
> **mcduck said:**
> The best way is to set Compiz itself to use Emerald by default, by changing the command in the CompizConfig Settings Manager, under the Window Decoration-plugin's settings.

If you just add "emerald --replace" to Gnome's startup, you'll be first starting Compiz with GWD, and then immediately replacing it with Emerald. Better just load Emerald in the first place.. ;)
Good lookin' out mcduck.  I learn something everyday on this site.  Thanks a hunid yo!

---

