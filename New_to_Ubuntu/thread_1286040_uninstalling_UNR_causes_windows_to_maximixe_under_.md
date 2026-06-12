---
title: "uninstalling UNR causes windows to maximixe under taskbars"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-10-08
Greetings,

I originally installed UNR on my Mini 9. From there, as an experiment, I installed xubuntu-desktop and kubuntu-desktop at the same time.

My first strange bug was that when I started up a XFCE session, I saw the UNR program running with the standard XFCE taskbars at the top and bottom.  Perplexed, I went into Synaptic and uninstalled all the UNR programs. I restarted the computer, and now when any maximized program opens, the topmost and bottommost of the window is covered up by the taskbars. This is also true in GNOME (I haven't played with KDE yet so I don't know if this is an issue).

Any advice to restore the proper maximize size?

Thanks,
Red

---

### Post by nothingspecial on 2009-10-08
```
sudo apt-get remove maximus
```

or just disable it in system > preferences > startup applications

---

### Post by Redmage913 on 2009-10-08
BEAUTIFUL!

Thank you very much.

--Red

---

### Post by nothingspecial on 2009-10-08
No problem  \\:D/

---

