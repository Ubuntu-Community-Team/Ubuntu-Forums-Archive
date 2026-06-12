---
title: "gnome panels not appearing in 10.04"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by candtalan on 2010-05-11
I did a clean install of 10.04 but after log in, I see a desktop screen with no top or bottom panels. I have use of the mouse and can for example create a new folder on the desktop and rename it (keyboard ok). This is an oldish machine but is still perfectly usable.

At login, I see a session choice and if I choose gnome safe session, it works ok. Maybe I should make the default as safe session, but how would I do that?

This machine is dual boot ubuntu for tests and also runs another Ubuntu 10.04 which was version upgraded from 9.10, and this 10.04 works perfectly. Maybe some settings which were good in 9.10 were carried forward in the online upgrade?

Anyway, what is wrong that my clean install is not working? And what can I investigate or do?

Any ideas please?

---

### Post by adam22 on 2010-05-11
Right click where the panel should be and select "Add Panel." No idea why it's screwed up..maybe some corruption in the media you used or just some strange bug.

---

### Post by karthick87 on 2010-05-11
Execute these commands in terminal

```

[COLOR=Red]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/COLOR]
```


This will restore your panels..

---

### Post by candtalan on 2010-05-11
Thanks for the responses

@ getyourkarthick  - it works, great!
I used 
ctrl alt F1
to obtain a virtual terminal, typed the commands line by line and 
Return each time,
then to revert to the gui I used
ctrl alt F7

Something I just noticed:
When booting and still in the early startup, and on the display immediately before the grub list screen, I see a couple of lines or error messages which fleetingly appear:
error: no suitable mode found.
error: unknown command 'terminal'

---

### Post by candtalan on 2010-05-11
I looked at various logs in  /var/log, an dthe only thing which to my untrained eye seems of interest  might be in /var/log/syslog

May 11 09:17:36 machinename gdm-simple-greeter[901]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May 11 09:19:54 machinename gdm-session-worker[903]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

---

### Post by doublewitt on 2010-07-21
Add this to your collection of software...

download this nice little application that either restores your default panels (top and bottom) or restores saved panels that you personally customized. You might have to re-boot your computer to see the results.

The application is called **PanelRestore**
[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

It's tiny (787 bytes). Simply follow the instructions on the webpage - it's easy to use...
If you get a 404 message from the link, just click on Ubuntu tools and then click on video...

---

