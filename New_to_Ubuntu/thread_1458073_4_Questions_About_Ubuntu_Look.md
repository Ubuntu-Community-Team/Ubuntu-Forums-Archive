---
title: "4 Questions About Ubuntu Look"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by lanetherif on 2010-04-19
Hi, as they are small and probably with easy answers I didn't want to open 4 different threads.

1. In one occasion, I clicked yes/ok for a prompt that was asking me whether is it ok to remove the clock and the calendar from top right. So, I have no clock indicator at the moment. How can I bring it back?

2. In the same fashion, though not with my consent in any way, the sound indicator on top right is missing. Although I get used to living without it, I would be happy to see it again, but how? :)

3. The Compiz cube is inverted ie. when it is rotated, I see desktops in the inner face of cube, not the outside. I tried to google it, but couldn't come up with a sensible search string. :) Any idea?

4. When I change the theme, Amarok just for a moment seems to follow the new colors, but then returns back to the default blue one. Is it something fixable or about Amarok itself?

Thanks...

---

### Post by LowSky on 2010-04-19
> 1. In one occasion, I clicked yes/ok for a prompt that was asking me whether is it ok to remove the clock and the calendar from top right. So, I have no clock indicator at the moment. How can I bring it back?

Right click on the panel, go to add to panel, choose the clock or whatever

> 2. In the same fashion, though not with my consent in any way, the sound indicator on top right is missing. Although I get used to living without it, I would be happy to see it again, but how? 
same as above just for sound obviously

> 3. The Compiz cube is inverted ie. when it is rotated, I see desktops in the inner face of cube, not the outside. I tried to google it, but couldn't come up with a sensible search string. :) Any idea?

You need to go into Compiz manager program and go to cube and choose the different option from there, sorry im on Windows at work, I can barely help on this

> 4. When I change the theme, Amarok just for a moment seems to follow the new colors, but then returns back to the default blue one. Is it something fixable or about Amarok itself?

Amarok is a KDE application, so it doesn't follow the rules of Gnome very well. I don't think there is a fix for this

---

### Post by kaldor on 2010-04-19
> 
Amarok is a KDE application, so it doesn't follow the rules of Gnome very well. I don't think there is a fix for this

As the OP is new to Linux, I'll clear this part up for them.

Ubuntu's default Desktop Environment (DE) is called GNOME. GNOME uses something called GTK to power the UI and its programs. This is not Windows/Mac, so you have a lot of choice in what you can do; KDE is another very popular DE, but it does not use GTK, but uses Qt (pronounced "cute"). So, when you have a "KDE app" in GNOME, it won't integrate very well and will be a bit slower. Same results as running a GNOME app on KDE.

---

### Post by LowSky on 2010-04-19
thanks kaldor, I was thinking my explanation was a bit short.

Oh and GNOME is pronounced Genome... but many people use the mythical creature pronunciation too, at least my friends do. LOL

---

### Post by lanetherif on 2010-04-19
Thanks...
Three of them are gone and one still stands. :)
I won't mind Amarok, I found the tick I was searching in Compiz (I had been looking for it in wrong part of settings) and I brought back the clock. However, there was no option for sound under add to panel. 
Any *more *ideas? ;)

---

### Post by LowSky on 2010-04-19
are you sure the icon looks like a white dial with blue to red escalating coloring, the app should be named sound preferences

again i'm doing this form memory as Im using Windows

if no do this

go into the home folder and show the hidden folders (CTRL+H), find the folder .gconf/apps/panel and delete it then log out and log back in

---

### Post by QIII on 2010-04-19
Don't know if I would say "GeeNome".  But perhaps I quibble.  One of my degrees is in Modern Languages and Literatures (German), with some concentration in linguistics.

GNOME was developed by two Mexican developers, and, in keeping with reduced vowels in the Mexican variation of Spanish, the pronunciation generally given is

 [&#609;&#601;&#712;no&#650;m]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English")

I hope those special characters don't get messed up in the presentation on your browsers.

The inverted "e" is pronounced much like the "a" at the end of "comma".   It is what is known as a "reduced vowel", so it is unstressed.

guhNOME

In fast speech, that usually reduces to g'NOME.

In any case, it is not pronounced like the mythical gnome ("nome")

---

### Post by KOld Iron on 2010-04-19
Regarding your missing Volume Control look here:
[**Volume Control Missing From Panel**]("http://ubuntuforums.org/showthread.php?t=1437484")

---

### Post by lanetherif on 2010-04-19
> **LowSky said:**
> are you sure the icon looks like a white dial with blue to red escalating coloring, the app should be named sound preferences

again i'm doing this form memory as Im using Windows

if no do this

go into the home folder and show the hidden folders (CTRL+H), find the folder .gconf/apps/panel and delete it then log out and log back in

I deleted the folder and it worked sort of. :) I got the power button and the one that directly enables the messenger back.  Moreover, my icons are also gone which is not a big problem, I can rearrange them. 
Still, no sound button.
It can't be about my sound driver, can it?

---

### Post by LowSky on 2010-04-19
KOld Iron's post is the solution
[http://ubuntuforums.org/showthread.php?t=1437484](http://ubuntuforums.org/showthread.php?t=1437484)

---

### Post by lanetherif on 2010-04-19
> **LowSky said:**
> KOld Iron's post is the solution
[http://ubuntuforums.org/showthread.php?t=1437484](http://ubuntuforums.org/showthread.php?t=1437484)


I was reading it and I was back to tell that now the problem solved.

Thank you all. :)

---

