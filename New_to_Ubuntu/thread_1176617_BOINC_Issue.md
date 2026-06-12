---
title: "BOINC Issue"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by CosmicFlux on 2009-06-02
Hey,

I'm trying to run BOINC on my Ubuntu 8.10 system. Only, I get the following error message:

(*boincmgr:17825): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",*


Any ideas?


Cosmic

---

### Post by khelben1979 on 2009-06-02
I don't know. I suggest that you download the latest version directly from the Boinc homepage. [Check this]("http://boinc.berkeley.edu/download.php"). I think this will fix your issues.

Have you tried opening the Boinc Manager GUI within [Gnome]("http://en.wikipedia.org/wiki/GNOME") and [KDE]("http://en.wikipedia.org/wiki/Kde")?

---

### Post by CosmicFlux on 2009-06-02
No, I don't have the GUI. I downloaded it from SETI@home's web page because I couldn't find it in Synaptic.

---

### Post by khelben1979 on 2009-06-02
Did you try a new install from the link I suggested?

You can also try:
```
sudo apt-get install boinc-manager
```

---

### Post by CosmicFlux on 2009-06-03
Yeah I did. Didn't work though. I think it may have something to with with an issue I'm having with Gutsy. I'm going to do a clean install of 9.04 and see if that helps.

Thanx


Cosmic

---

