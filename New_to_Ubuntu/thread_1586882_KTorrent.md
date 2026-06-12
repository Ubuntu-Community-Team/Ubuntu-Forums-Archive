---
title: "KTorrent"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by fuse_Man91 on 2010-10-02
Weird problem here. I installed KTorrent, and the only way I can run it is through the alt+F2 command. Where is KTorrent actually installed??? I want to create a launcher on the desktop but in order to do that I need to know the path to the program. Does anyone know how to find this out (for future reference if this happens again)?

---

### Post by Hippytaff on 2010-10-02
Could try 
```

locate ktorrent

```

in the terminal
[

---

### Post by SeijiSensei on 2010-10-02
On a Kubuntu machine, it's in Applications > Internet from the main menu.  KTorrent is a file transfer program, so it's classified as an Internet application.

In KDE, you can add it to your Favorites menu after right-clicking its icon in the Internet submenu.

If you installed it into GNOME Ubuntu, rather than using Kubuntu and KDE, I'm afraid I can't help you. I'd suggest that you try the GNOME Applications menu and see if there's an Internet group there as well.

As for program paths, nearly every program you install will be in /usr/bin, as in /usr/bin/ktorrent.  When you log in, a path to that directory is added to your environment, so you can just type "ktorrent" from Alt-F2 or a terminal.

---

### Post by fuse_Man91 on 2010-10-02
Thanks!!! That seemed to work. :)

---

