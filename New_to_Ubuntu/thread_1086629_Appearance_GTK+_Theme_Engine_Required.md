---
title: "Appearance GTK+ Theme Engine Required?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
Just installed a theme, and it says it won't display properly until I get GTK+ Theme Engine?

How, where?

I looked on Synaptic Package Manager, tried to install a few I thought it might be, still same message on the appearance menu...

Plz help!

---

### Post by jaminux on 2009-03-04
Just install them all. They are quite small. Search (by names) in the synaptic for gtk-engines... 

There are gtk2-engines as well, but there is one of those you shouldn't install, will get info for you in a sec.

---

### Post by mcduck on 2009-03-04
If the error tells you which GTK engine it's missing, install that engine. if it doesn't, ignore the error and your theme will work just like it should.

The error is just an ugly result from a commonly used trick when creating GTK themes, current version of the theme manager gets a bit confused because of it and as a result produces that error.

In other words:
- If the error syas it's missing *GTK+ engine "*, the error message is faulty and can be just ignored.
- When it says it's missing *GTK+ engine "Aurora"*, install the specified GTK engine.
(Notice the single quote in the faulty error compared to name of the missing engine in quotes in the real error.)

edit: no use installing unnecessary GTK engines for this, it *is* actually referring to GTK2 engines, definitely not GTK1 which is rather old and rarely used for anything any more. But even if you installed all the GTK1 and GTK2 engines available that wouldn't still remove the faulty error.

If you really want to get rid of the error message edit all your theme files and change every instance of *engine ""* to *engine "pixbuf"*. Lots of work and the themes will work just like before, so I wouldn't bother.

---

### Post by jaminux on 2009-03-04
All the gtk2-engines-ubuntulooks. If you install that one it wants to remove ubuntu desktop...

---

### Post by jaminux on 2009-03-04
> **mcduck said:**
> If the error tells you which GTK engine it's missing, install that engine. if it doesn't, ignore the error and your theme will work just like it should.

The error is just an ugly result from a commonly used trick when creating GTK themes, current version of the theme manager gets a bit confused because of it and as a result produces that error.

Apparently my stuff is unnecessary then. It can't hurt though if you like themes. The packages are only small and modern hard drives are big :p

---

### Post by mcduck on 2009-03-04
> **jaminux said:**
> Apparently my stuff is unnecessary then. It can't hurt though if you like themes. The packages are only small and modern hard drives are big :p

No, it doesn't hurt. Although most of the extra theme engines are rather ugly, and even then you'd definitely want the GTK2 engines, as most likely you don't even have any apps that use GTK1.

Better get nice themes from gnome-look.org instead. :)

---

### Post by Gp. on 2009-03-04
I've installed all of the packages when I searched for GTK+ Theme engine. Still gives me the message? :S

---

