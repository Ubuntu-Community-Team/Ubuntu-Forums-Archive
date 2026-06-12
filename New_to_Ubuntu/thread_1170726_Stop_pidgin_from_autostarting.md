---
title: "Stop pidgin from autostarting"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by starkat2k on 2009-05-26
I've searched the forums (and asked the Google) but can't find a definite answer.  I'm hoping you guys can help.

I've got xubuntu installed on my eee 901.  Pidgin is installed, and autostarts upon login.  I do NOT want it to autostart, I just want it to run when I open it.  There's no settings inside Pidgin (that I can find) that specify the autostart behavior.  Additionally, it's not in the Austostarted apps settings.

I have tried manually quitting pidgin from the icon in the system tray, but it stll comes back up after a reboot.  Additionally, I have it set to not save my session info.

Anyone have any idea where I can find the setting that controls this?

---

### Post by spcwingo on 2009-05-26
Look in /home/your_username/.config/autostart/  I'm almost certain that's where you'll find the .desktop file that is auto-starting it.

---

### Post by starkat2k on 2009-05-26
Thanks for the reply.

There's nothing in that directory.  None of the other standard autostart locations have anything in them which I can't identify.  (nm-applet.desktop, gnome-power-manager.desktop, etc, but I know what all of those do).

Any other ideas?

---

### Post by spcwingo on 2009-05-26
The only other place I can think of is /etc/xdg/autostart.

---

