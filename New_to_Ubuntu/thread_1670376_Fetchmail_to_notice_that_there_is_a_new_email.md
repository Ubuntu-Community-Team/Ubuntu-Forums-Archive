---
title: "Fetchmail to notice that there is a new email?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by honeybear on 2011-01-18
fetchmail -k says the number of emails.
 
Anyone knows how to say that there is new emails waiting and un-read? 
to do it just WELL, list we should expect ... Not easy actually :(

---

### Post by sandyd on 2011-01-18
> **honeybear said:**
> fetchmail -k says the number of emails.
 
Anyone knows how to say that there is new emails waiting and un-read? 
to do it just WELL, list we should expect ... Not easy actually :(
use zenity

---

### Post by honeybear on 2011-01-18
> **sandyd said:**
> use zenity

?? you know what is zenity? 
[http://library.gnome.org/users/zenity/2.31/figures/zenity-text-screenshot.png.en_GB](http://library.gnome.org/users/zenity/2.31/figures/zenity-text-screenshot.png.en_GB)

---

### Post by sandyd on 2011-01-18
> **honeybear said:**
> ?? you know what is zenity? 
[http://library.gnome.org/users/zenity/2.31/figures/zenity-text-screenshot.png.en_GB](http://library.gnome.org/users/zenity/2.31/figures/zenity-text-screenshot.png.en_GB)
i do.
wrap fetchmail -k with zenity so that mail notifications show up as zenity dialogs.

---

### Post by HermanAB on 2011-01-18
...or you can go all the way and install a complete mail server like Citadel.  It has support for fetchmail built in, so it is happy working slaved to another mail server.  

Basically, Citadel supports *all* mail protocols, so it can literally do anything with your mail, any which way you want and the default configuration installs in only about 20 minutes. SO you are up and running in no time flat.

---

### Post by honeybear on 2011-01-19
> **sandyd said:**
> i do.
wrap fetchmail -k with zenity so that mail notifications show up as zenity dialogs.
but
fetchmail -k says the number of emails.
does not say whether the email is new or not ...

---

