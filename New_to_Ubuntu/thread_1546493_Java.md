---
title: "Java?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by tim_ex on 2010-08-05
I don't think that my Java is working, i cant get youtube to work. i am currently running

9.10 (karmic)
kernel linux 2.6.31-14-generic
GNOME 2.28.1

thanks

---

### Post by mikewhatever on 2010-08-05
Java? I don't think youtube makes use of Java at all. Install flashplayer and try again.

---

### Post by _h_ on 2010-08-05
```
sudo apt-get install flashplugin-installer
```

Or if you want a ton of goodies such as flash, java and other restricted goodies:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tim_ex on 2010-08-05
i ran both of the codes _h_ suggested 
sudo apt-get install ubuntu-restricted-extras
and
sudo apt-get install flashplugin-installer the flash player still is not working is there anything else i can try?
thank you

---

### Post by QIII on 2010-08-05
Do you have gnash or swfdec installed?  They conflict with Flash.

Could you type

```
about:plugins
```

in the navigation bar in FF and tell us what the Flash plugin version is?


(Calling lovinglinux!  Where are you?)

---

### Post by sydbat on 2010-08-05
> **QIII said:**
> Do you have gnash or swfdec installed?  They conflict with Flash.

Could you type

```
about:plugins
```

in the navigation bar in FF and tell us what the Flash plugin version is?


(Calling lovinglinux!  Where are you?)If lovinglinux doesn't mind...install the [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") add-on for Firefox. It _will_ fix your flash issues.

---

### Post by QIII on 2010-08-05
May I take a moment to send out a syrupy and maybe silly thanks to lovinglinux for Flash-Aid ...

---

### Post by mikewhatever on 2010-08-05
> **tim_ex said:**
> i ran both of the codes _h_ suggested 
sudo apt-get install ubuntu-restricted-extras
and
sudo apt-get install flashplugin-installer the flash player still is not working is there anything else i can try?
thank you

Have you restarted Firefox?

---

### Post by tim_ex on 2010-08-06
so here is the version of flash that i have

File name:  libgnashplugin.so Shockwave Flash 10.1 r999. Gnash 0.8.6, the GNU SWF Player.   Copyright (C) 2006, 2007, 2008, 2009 [Free   Software Foundation]("http://www.fsf.org/"), Inc. 
Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   Compatible Shockwave Flash 10.1 r999. it does not look like i have swfdec. I followed these instructions and still it does not work 
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

does anyone have anyother ideas. oh and i have restarted FF
thanks

---

### Post by QIII on 2010-08-09
Remove gnash through the Synaptic Package Manager.

Use lovinglinux' Flash-Aid as suggested above.

---

### Post by sandyd on 2010-08-09
> **QIII said:**
> Remove gnash through the Synaptic Package Manager.

Use lovinglinux' Flash-Aid as suggested above.
see signature for adobe flash tools.

click " remove" then click [install (x86)]

---

