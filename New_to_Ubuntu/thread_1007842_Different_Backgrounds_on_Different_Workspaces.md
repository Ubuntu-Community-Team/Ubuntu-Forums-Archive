---
title: "Different Backgrounds on Different Workspaces"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by bbright20 on 2008-12-10
First off I am loving Ubuntu and everything that you can do with it! I currently have 4 workspaces set up and I am trying to use a different background for each space. I have searched and read several threads and have had no luck. 
I also tried this [http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/#1]("http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/#1")
Which I had no luck. I was wondering if anybody could point me in the right direction. Thanks in advance!

---

### Post by jimmy the saint on 2008-12-10
Just did a little research for you. 
I searched for "multiple wallpapers compiz"  It turns out that compiz supports this feature.  I then tried it. It failed.

I looked at a few more search results.  It turns out that compiz applies multiple wallpapers (if told) but nautilus (which controls the desktop) puts it's wallpaper on top.  There is currently no (easy) way to fix this (that I found). 

One solution that would probably work, if you are willing to the do the work, would be to pick your wallpapers and join them in the gimp so that they are one big wallpaper.  place the resulting image as your wallpaper and center it.

---

### Post by bbright20 on 2008-12-10
Thanks for all the help!

---

### Post by fubbleskag on 2008-12-10
you can tell nautilus to stop drawing it's own desktop - the downside is you'll no longer see any desktop icons. if you can live with that, go into gconf-editor and browse to apps/nautilus/preferences and uncheck "show_desktop" (should not require a restart of X)

---

### Post by bbright20 on 2008-12-10
> **fubbleskag said:**
> you can tell nautilus to stop drawing it's own desktop - the downside is you'll no longer see any desktop icons. if you can live with that, go into gconf-editor and browse to apps/nautilus/preferences and uncheck "show_desktop" (should not require a restart of X)

I have tried that before, but I have a cube set up as a sphere and when I uncheck "show_desktop" it changes my cube back to a square. And does not allow me to change the deformations. Any suggestions on why that happens? Thanks.

---

### Post by fubbleskag on 2008-12-10
> **bbright20 said:**
> I have tried that before, but I have a cube set up as a sphere and when I uncheck "show_desktop" it changes my cube back to a square. And does not allow me to change the deformations. Any suggestions on why that happens? Thanks.hmm, strange. I just enabled sphere and it works fine for me with unique wallpapers. maybe try changing the order you make the changes (shouldn't make a difference, but what can it hurt to try)?

---

### Post by bbright20 on 2008-12-11
> **fubbleskag said:**
> hmm, strange. I just enabled sphere and it works fine for me with unique wallpapers. maybe try changing the order you make the changes (shouldn't make a difference, but what can it hurt to try)?

I have tried it multiply ways and have had no luck.(I think my computer is possessed sometimes). I will just have to stick with this for now. :( Oh well, Ubuntu is still awesome. Thanks for all the help!

---

### Post by bapoumba on 2008-12-11
[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

And if you want to follow or input in the bug report:
[http://bugzilla.gnome.org/show_bug.cgi?id=444320](http://bugzilla.gnome.org/show_bug.cgi?id=444320)

---

### Post by feisty john on 2008-12-11
KDE allows you to set different wallpapers for different workspaces. At least, KDE 3.5 does; I didn't try it when I was using KDE 4.

---

### Post by binbash on 2008-12-11
> **feisty john said:**
> KDE allows you to set different wallpapers for different workspaces. At least, KDE 3.5 does; I didn't try it when I was using KDE 4.

Also Kde4

---

