---
title: "[SOLVED] where do mozilla video plugins live?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by gorgon on 2009-01-01
Hi,

I just installed the mozilla-vlc-plugin, but when I want to activate it in firefox preferences it does not show as an option, so I guess I have to point to where the plugin lives. Anyone know this?

cheers!

---

### Post by Tim Sharitt on 2009-01-01
firefox looks for plugins in /usr/lib/mozilla/plugins. I would think that is where it would install to, but if not just put a lin in the plugin folder pointing to the plugin.
```
cd /usr/lib/mozilla/plugins
sudo ln -s /path_to_plugin
```

---

### Post by joukez on 2009-01-01
I believe  you will not find it there but when you look in the addon section it will be there. In the preference section you can choose a player for the kind of file you want to play. Just klik on one of them, on the left it will show a drop down and you can choose.

               gr. Jouke

---

### Post by Yoshi_Matrix on 2009-01-01
> **gorgon said:**
> Hi,

I just installed the mozilla-vlc-plugin, but when I want to activate it in firefox preferences it does not show as an option, so I guess I have to point to where the plugin lives. Anyone know this?

cheers!
**I take it you went to Tools in the browser then clicked the Add-Ons tab then selected the VLC add on then clicked it's options. That might help you. Happy New Year all!! **

---

### Post by gorgon on 2009-01-01
I got the mplayer plugin instead, and it got installed to /usr/lib/mozilla/plugins , so no problem. thanks anyways!

---

