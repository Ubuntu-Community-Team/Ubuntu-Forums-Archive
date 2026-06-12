---
title: "Trash:/// does not display contents of ~/.local/share/Trash"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Cuddles McKitten on 2009-07-31
I opened my new Pangolin Performance from System76 and noticed that they ship with the GNOME desktop completely empty.  I decided to add a trash can to it through the configuration editor, but my new trash can isn't very functional.  All of my files, when deleted in Nautlius, go directly to /home/username/.local/share/Trash as expected.  However, my trash can and Trash:/// folder always remains empty no matter what's in *my* trash.

To empty my trash, should I just write an rm script or is there a fix/workaround for my trash can not seeming to want to look into my trash folder?

---

### Post by llamabr on 2009-07-31
The .trash/ folder is there for your protection, so you can get files after you've mistakenly deleted them.  A script that deletes them would undermine this safety net.

I just sort of periodically look in it and delete it when I notice that i'm running low on room.  I also should note that I occasionally find things in there I wish I hadn't deleted.

But yes, a simple cron job would rm it periodically, if you prefer.

---

