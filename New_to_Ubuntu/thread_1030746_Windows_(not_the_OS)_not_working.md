---
title: "Windows (not the OS) not working?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-01-04
OK, I have had 3 post about this, each post had a temporary fix but not a permanent solution. Alright, I have a working gnome and emerald theme, but to have the window buttons(close,maximize) I have to run emerald --replace on a different desktop (compiz-fusion) but it gets annoying to do it every time I reboot. Anyone have a solution?:(

---

### Post by howefield on 2009-01-04
Add the command to your sessions list.

Systems > Preferences > Sessions and press the add button.

Type emerald --replace in the command field and anything you want in the other two, should be ok when you reboot.

If you use compiz, tell the settings manager to use emerald.

Open compiz settings manager and go "effects" then "Window Decoration" and in the command field, overtype /usr/bin/emerald

---

### Post by kansasnoob on 2009-01-04
Sorry, I'm clueless, but I'd suggest linking the previous posts.

You know just copy-n-paste the links to those posts here so we know what's already been done. What worked temporarily, etc.

---

### Post by Martin Marshalek on 2009-01-04
I'm assuming that you have a Nvidia card right? If so, I had a similar problem and found this in another thread, it should fix your problem:

Go to System---->Administration---->Software Sources. Then go to Third-Party Sources (or Software I'm not sure which as I'm using Windows right now) and click add. In the new window type: ```
deb http://fr.archive.ubuntu.com/ubuntu jaunty main universe 
```
And then click close. Make sure the new source is checked. It will reload sources and tell you there are updates. IGNORE them (unless you want Jaunty Jackalope). Then open a terminal and type:
```
sudo apt-get install nvidia-glx-180
```

After that installs go back to Software Sources and uncheck the new source. Now reboot and your problem is fixed.

---

