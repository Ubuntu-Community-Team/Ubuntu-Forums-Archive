---
title: "how to switch back to gnome from gnome shell"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by smokystone on 2010-10-29
Hi, I just set to start gnome shell by completely changing from normal gnome session by the command:

ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string

It works well, but I don't know how to switch back to the normal gnome session, so does any one have idea how to do that?

Thanks a lot.

---

### Post by cariboo on 2010-10-29
There is a gnome-shell thread in Natty Testing & Discussion, you may want to ask your question in that [thread]("http://ubuntuforums.org/showthread.php?t=1603874")

---

