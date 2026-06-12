---
title: "Recovering from crashed full screen program?"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Anessen on 2011-02-04
Hello

I'm using freerdp to connect to a remote server. The problem is that occasionally the connection might drop out for a short while and this causes freerdp to lock up.

Is there an easier way to get out of the program other than going to a console and killing it from there?

Thanks,
Joe

---

### Post by Frogs Hair on 2011-02-04
Right click the gnome panel > add to panel > add force quit applet. If your at full screen use f11 so you can see the top panel.

---

### Post by Anessen on 2011-02-08
Unfortunately, the program grabs the F11 key

---

### Post by kellemes on 2011-02-08
Not using Gnome myself anymore but I remember **Ctrl-Alt-Esc** shows the mousecursor of death. Just click the window and dead it will be..

Edit: You can create the shortcut if needed.. [http://www.thetechrepo.com/main-articles/505-easily-qforce-quitq-or-qend-taskq-on-a-program-in-linux-with-a-keyboard-shortcut]("http://www.thetechrepo.com/main-articles/505-easily-qforce-quitq-or-qend-taskq-on-a-program-in-linux-with-a-keyboard-shortcut")
Using Arch-Xfce it works for me.. just had to install "xorg-xkill" first.. don't know if that's needed on Ubuntu.

---

### Post by Anessen on 2011-02-08
This is very useful, however freerdp seems to grab those keys as well even after I set up the shortcut (and tested it on Firefox)

---

### Post by aeiah on 2011-02-08
try another rdp client? i use tsclient

---

