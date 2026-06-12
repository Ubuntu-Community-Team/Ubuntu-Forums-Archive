---
title: "Firefox; Gnash and Flash"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by il pepe on 2009-08-03
**[FONT=Arial][SIZE=2]i [/SIZE][/FONT][FONT=Arial][SIZE=2]have [/SIZE][/FONT][FONT=Arial][SIZE=2]a problem with firefox or better flash. Some web applications don't work.[/SIZE][/FONT]**


I did the about:plugins thing and i posted the output at the end of this post. I tried to install the shockwave and gnash thing, as the about:plugins thing is a bit confusing, and both were installed firefox said, whilst i only could chose gnash as the flash player. Any help?

[B]
[/B]

**Shockwave Flash**

 Bestandsnaam:  libgnashplugin.so Shockwave Flash 9.0 r999. Gnash 0.8.5, the GNU SWF Player.   Copyright © 2006, 2007, 2008 [Free Software   Foundation]("http://www.fsf.org/"), Inc. 
Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   Compatible Shockwave Flash 9.0 r999.   MIME-type Beschrijving Achtervoegsels Actief    application/x-shockwave-flash Shockwave Flash swf Ja

---

### Post by coldReactive on 2009-08-03
```
sudo apt-get remove gnash
```

Gnash and flash are conflicting each other.

Oh and...

Shockwave Flash (SWF) =/= Shockwave

---

