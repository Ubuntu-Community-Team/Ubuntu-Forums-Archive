---
title: "GNOME apps fail to load"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by tom.gobel on 2009-11-03
I've run into a bit of a pickle, and I'm not sure how to proceed.

During my recent session, I began to notice that various GUI apps would fail to initialize and load.  The first failure I noticed was Firestarter GUI, then the file browser (~explorer on Windows), then I tried Evolution and one or two more apps.  All have the same result.

Down in the bottom taskbar, I see what looks like a new window opening, which says 'Starting ___' and then it just closes itself down.

Like an idiot, I closed the term session I had open, and the GUI logout/restart/shutdown menu seems to be doing nothing when I try it as well.

I haven't gotten around to setting up remote telnet/ssh access yet, so that option appears to be off the table for any sort of remote shutdown attempt.

I'm really hoping to avoid a hard shutdown if possible... any thoughts on a way out of this jam?

---

### Post by ajgreeny on 2009-11-03
If it is just gnome applications that crash, try starting an app from xterm.  Use Alt+F2 to get the run dialog and then type **xterm** in the command box.  If you can get that to run, try starting a gnome app that normally crashes by typing its name in there, eg **nautilus** and report back errors that appear in the terminal.

If you need to shutdown and can still use the keyboard, it's Ctrl+Alt+F1 to get a command line and then login with name and password, and use command ```
sudo shutdown -h now
```to switch off or ```
sudo shutdown -r now
``` to reboot. ```
sudo reboot
``` also works.

---

### Post by tom.gobel on 2009-11-03
Fantastic, I was able to reboot but unfortunately not get the cmd prompt to try and run any GNOME apps.  Thank you very much.

---

