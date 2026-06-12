---
title: "openbox transparency"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by dzon65 on 2010-03-05
Does anyone know how to have transparent openbox-menus ?Xcomp and transset are installed.
Like this:

---

### Post by m_duck on 2010-03-05
I believe that screenshot is actually XFCE (though I don't *know*) due to there being menu icons. You can enable a transparent menu in Openbox but it requires xcompmgr-dana and not standard xcompmgr ([Ref]("http://crunchbanglinux.org/forums/topic/3360/transparency-in-menu/")).

As far as I know, xcompmgr-dana is not in the Ubuntu repos (though I think Crunchbang has it) so you will probably need to compile it yourself.

[Here]("http://oliwer.net/xcompmgr-dana/") is the source that is used in the Arch Linux PKGBUILD for the unofficial xcompmgr-dana package and [thread=1412644]here[/thread] is a thread on here which suggests possible required dependencies for it when compiling on Ubuntu.

From the Crunchbang thread I posted at the top, you can then run xcompmgr with the following options to get a transparent menu:```
xcompmgr -I1 -O1 -Ff -m.86
```Note that the ***-m*** switch determines the opacity so 1 is opaque and I guess 0 would be completely transparent (and useless!).

HTH

EDIT: This, being the first time I have tried this myself, have just noticed that this makes *all* menus transparent, so the File, Edit etc menus, in addition to the Openbox root menu.

---

### Post by dzon65 on 2010-03-05
Ah,the dana.That's why it didn't work.I put in that command but nothing happened.Thanks for this reply.
Kind regards,J.

---

### Post by dzon65 on 2010-03-05
Works pretty well.One more thing.How do I keep those settings?When I close the terminal,the settings are lost.

---

### Post by m_duck on 2010-03-05
Are you using Openbox within Gnome? If so I would suggest making a small script and then automatically running it upon login.

```
#!/bin/bash
xcompmgr -I1 -O1 -Ff -m.86 &
```

Put that in (say) ***/home/yourusername/.scripts/startxcompmgr*** and make it executable (right click and allow executable permissions) or in terminal:```
chmod +x /home/yourusername/.scripts/startxcompmgr
```Next, in the Gnome Session and Startup menu (or whatever it's called) add an entry, and in the command field add the path to that script you just made.

If you didn't want it to always start when you log in, ensure when running the xcompmgr command from the terminal, that you append an ampersand to it which will make it run in the background and (mostly) will not be affected when the terminal window is closed.

---

### Post by dzon65 on 2010-03-06
Yeaeah!!Thanks for this tip.
Kind regards,J.

---

