---
title: "cant download new software"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-08-04
everytime i try and download something from the ubuntu software center and click install i get this message  Requires installation of untrusted packages  The action would require the installation of packages from not authenticated sources.  and it wont download has anyone seen this lately?

---

### Post by gordintoronto on 2010-08-04
What version of Ubuntu?  Have you tried Synaptic? If you select Administration/Software Sources, does anything look odd?

---

### Post by ornothaloapq on 2010-08-04
ubuntu 10.04   running the update manager now   that might help

---

### Post by sandyd on 2010-08-04
> **ornothaloapq said:**
> ubuntu 10.04   running the update manager now   that might help
post the output of
```

sudo apt-get update
```

---

### Post by beew on 2010-08-04
Go to System > Administration> software source (or in Synaptic choose settings and then repositories, it is the same thing) . Go to the "Ubuntu Software" panel and change the entry in "Download from" from the drop down menu and see if that helps. I have had that problem before, I changed server then all was fine. There might have been a glitch in the server where you download from.

---

### Post by DJDannyB on 2010-12-27
I have the same problem.... I'm running ubuntu 10.10 and there is no administration>software sources for me to alter!!

Never mind i found it in the software center properties B)

---

