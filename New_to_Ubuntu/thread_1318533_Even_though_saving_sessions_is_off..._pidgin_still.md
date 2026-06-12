---
title: "Even though saving sessions is off... pidgin still starts when I login!"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-07
How do I stop pidgin from starting when I login when I don't save the session in the first place?

---

### Post by coldReactive on 2009-11-08
Bump

---

### Post by desperado665 on 2009-11-08
Might be as easy as making sure you've logged out of pidgin before shutting your PC down. I have noticed that behavior in Mint KDE. If pidgin is actively running when I shut down, it auto starts then next time I log in, even though save session is off. Must be something in pidgin making it act that way. If I log out of pidgin before shutting down, then it doesn't load.

---

### Post by Sir Jasper on 2009-11-08
Is the program box unticked; or is Save Session unticked on quit/reboot, or both?

---

### Post by coldReactive on 2009-11-08
> **desperado665 said:**
> Might be as easy as making sure you've logged out of pidgin before shutting your PC down. I have noticed that behavior in Mint KDE. If pidgin is actively running when I shut down, it auto starts then next time I log in, even though save session is off. Must be something in pidgin making it act that way. If I log out of pidgin before shutting down, then it doesn't load.

I right-click the tray icon and choose quit. How is that NOT logging off?

(Note: I have pidgin to always show the tray icon, because that envelope icon sucks.)

> **Sir Jasper said:**
> Is the program box unticked; or is Save Session unticked on quit/reboot, or both?

Program box? Yes, Save Session is unticked when I log out.

---

### Post by Sir Jasper on 2009-11-08
In Xubuntu go to:
Settings > Xfce 4 Settings Manager > Session and Startup > Applications Assistant and see which boxes are ticked.

If that doesn´t help then I don´t know.

---

### Post by coldReactive on 2009-11-08
> **Sir Jasper said:**
> In Xubuntu go to:
Settings > Xfce 4 Settings Manager > Session and Startup > Applications Assistant and see which boxes are ticked.

If that doesn´t help then I don´t know.

If you mean Application Autostart, I've already set Pidgin to "never" and it no longer appears in the list, so I can't uncheck it.

There is no Applications Assistant.

---

### Post by Sir Jasper on 2009-11-08
As an aside, Applications Assistant appears in Xububtu 9.04. Has this problem only happened with your 9.10 ? If so did you do a Fresh Install or did you Upgrade?

---

### Post by coldReactive on 2009-11-08
> **Sir Jasper said:**
> As an aside, Applications Assistant appears in Xububtu 9.04. Has this problem only happened with your 9.10 ? If so did you do a Fresh Install or did you Upgrade?

I fresh installed. But due to this bug ( [http://bugzilla.xfce.org/show_bug.cgi?id=5954](http://bugzilla.xfce.org/show_bug.cgi?id=5954) ) I had to install xdm rather than gdm after while.

---

### Post by sisco311 on 2009-11-08
clear the ~/.cache/sessions/ directory.

---

### Post by coldReactive on 2009-11-08
> **sisco311 said:**
> clear the ~/.cache/sessions/ directory.

Wow, thanks, that worked.

---

