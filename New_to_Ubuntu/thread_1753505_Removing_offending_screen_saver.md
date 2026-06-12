---
title: "Removing offending screen saver"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-05-09
Dear All,
I like to set my screen saver to random. All of them work fine, but only one, namely GLText, is causing my computer to freeze. Is there any way I can either remove this single screen saver or set it not to be activated?

I know that I can set my screen saver to a particular one, but I like the random option.

Thanks.

P.S. I tried gconf-editor but perhaps that is not the correct way of doing it.

---

### Post by user1397 on 2011-05-09
> **mmasroorali said:**
> Dear All,
I like to set my screen saver to random. All of them work fine, but only one, namely GLText, is causing my computer to freeze. Is there any way I can either remove this single screen saver or set it not to be activated?

I know that I can set my screen saver to a particular one, but I like the random option.

Thanks.

P.S. I tried gconf-editor but perhaps that is not the correct way of doing it.
screensavers are in /usr/share/applications/screensavers/   

type alt+f2, the run 'gksudo nautilus' which will give you a root file browser.

then go to the aforementioned folder, find that screensaver that is causing you problems, and delete it (or if you want to keep it for whatever reason, move it out of that directory or rename it something like screensaver.backup

---

### Post by sisco311 on 2011-05-09
> **mmasroorali said:**
> 
P.S. I tried gconf-editor but perhaps that is not the correct way of doing it.

It is.

In gnome-screensaver-preferences select the random option, then open gconf-editor, edit the /apps/gnome-screensaver/themes key and remove the screensavers-gltext entry.

---

### Post by mmasroorali on 2011-05-09
> **sisco311 said:**
> It is.

In gnome-screensaver-preferences select the random option, then open gconf-editor, edit the /apps/gnome-screensaver/themes key and remove the screensavers-gltext entry.

I did earlier as you said above. But the GLText entry was still listed in the list of Screensaver Preferences list, and it this one eventually froze my machine when it got randomly selected from my random selection.

---

