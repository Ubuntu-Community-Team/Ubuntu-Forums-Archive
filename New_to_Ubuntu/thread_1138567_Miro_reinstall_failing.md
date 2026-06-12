---
title: "Miro reinstall failing"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by ssdurn on 2009-04-26
Hello

Having removed it a few weeks ago I am trying to reinstall Miro and I'm getting the following error:

E: /var/cache/apt/archives/miro_2.0.3-1ubuntu2_i386.deb: trying to overwrite `/usr/share/applications/miro.desktop', which is also in package miro-data

I am assuming the removal was incomplete, and now the installer is failing - any suggestions?

Thanks

---

### Post by Sealbhach on 2009-04-26
in the terminal, go 

cd /usr/share/applications

then 

sudo rm miro.desktop

Then try again.

.

---

### Post by ssdurn on 2009-04-26
Nope - still getting the same error message ... although I can no longer see the offending entry in the folder when I browse to it.

---

### Post by gandaran on 2009-04-26
> **ssdurn said:**
> Hello

Having removed it a few weeks ago I am trying to reinstall Miro and I'm getting the following error:

E: /var/cache/apt/archives/miro_2.0.3-1ubuntu2_i386.deb: trying to overwrite `/usr/share/applications/miro.desktop', which is also in package miro-data

I am assuming the removal was incomplete, and now the installer is failing - any suggestions?

Thanks
are you installing the same repo version or a newer version?
if it's a newer version check with synaptic if miro-data is completely removed.

---

