---
title: "[SOLVED] quickest way to disable compiz &amp;amp; reenable with exact settings as before?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by earthpigg on 2009-01-07
threat title says it all :)

reason: google earth runs like crap with compiz on.

im sure there is some superquick terminal command to do this....

thanks in advance!

---

### Post by drs305 on 2009-01-07
Although I don't know the command to replicate previous customizations, to disable compiz you can run:
```
metacity --replace
```

Note: When using compiz, you can backup your existing settings via the CompizConfiguration Settings Manager (System > Preferences > CompizConfiguration Settings Manager > Preferences > Profile and Backend > Export. I usually export the settings before making major compiz changes in case I don't like the new results and can't remember all the settings I've changed.

---

### Post by overdrank on 2009-01-07
> **earthpigg said:**
> threat title says it all :)

reason: google earth runs like crap with compiz on.

im sure there is some superquick terminal command to do this....

thanks in advance!

You may look at the fusion-icon in the [The Great Desktop Effects FAQ of 2009]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by earthpigg on 2009-01-07
compiz --replace gets it back -- thanks dude :)

---

### Post by SunnyRabbiera on 2009-01-07
well if you right click on the desktop and select "change desktop background"
go to the last tab, turn effects off by clicking the first circle.
If you have advanced setup it should remember your settings :D

---

### Post by bixejo on 2009-01-07
> **earthpigg said:**
> threat title says it all :)

reason: google earth runs like crap with compiz on.

im sure there is some superquick terminal command to do this....

thanks in advance!

I dropped [[COLOR=Navy]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6055842&mode=linear&highlight=compiz#post6513152") a very simple way to switch on/off compiz with just one keystroke. Also, read in the same thread a post by Forlong with a more sophisticated and elegant way to do this.

Hope this helps.

Regards,

---

