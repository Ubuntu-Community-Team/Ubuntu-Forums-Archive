---
title: "OpenGL issues"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by DMzda on 2011-06-12
After installing Natty, compiz started messing up. Other programs that use OpenGL also do the same thing (See atttachment). Compiz ran fine in Maverick. 

My graphics card is an ATI Radeon x300.

Are there any alternative drivers that I can install?

---

### Post by VOT Productions on 2011-06-12
Try the fglrx drivers. You can either do **sudo apt-get install fglrx** or look in **Synaptic**.

---

### Post by DMzda on 2011-06-12
After installing those drivers, compiz still doesn't work properly (No window borders, and docky complains about lack of compositing). glxgears doesn't run, giving a Segmentation fault.

---

### Post by VOT Productions on 2011-06-12
If you have **CCSM** installed, enable **Compositioning**.
Also, try **sudo glxgears**.

---

### Post by DMzda on 2011-06-12
Same errors. Also, the ATI Catalyst Control Center says that the graphics card is not supported, or similar.

---

### Post by VOT Productions on 2011-06-12
Odd... follow this link. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[B]sudo apt-get remove fglrx
  sudo apt-get install xserver-xorg-video-ati[/B]

---

### Post by DMzda on 2011-06-12
I have done that, and still the problem persists.

---

### Post by silex89 on 2011-06-12
What about the proprietary drivers for your card?, did you installed them from jockey?

---

### Post by VOT Productions on 2011-06-12
[Removed due to double post]

---

### Post by VOT Productions on 2011-06-12
Try ALT+F2 then compiz --replace

---

### Post by DMzda on 2011-06-12
> **silex89 said:**
> What about the proprietary drivers for your card?, did you installed them from jockey?
Jockey says that there are no proprietary drivers available for my system.

> **VOT Productions said:**
> Try ALT+F2 then compiz --replace
Doing this still doesn't make a difference.

---

### Post by dFlyer on 2011-06-12
I read some where on the forum that ati cards have a problem with unity. How true that is I don't know.

---

### Post by beew on 2011-06-12
Since you have the open driver you can try adding the xorg-edgers ppa to your sources list and update.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

I have had problem with OpenGL in one ati machine I run Natty on. OpenGL version was 1.7 using the open source driver. Upgrading with this ppa boosted it up to OpenGl 2.1 and things that didn't work before suddenly started working.

Read carefully first. If anything goes wrong purge the ppa using ppa-purge, so install that first.

---

### Post by DMzda on 2011-06-12
> **dFlyer said:**
> I read some where on the forum that ati cards have a problem with unity. How true that is I don't know.
I don't use unity, just the classic desktop.

> **beew said:**
> Since you have the open driver you can try adding the xorg-edgers ppa to your sources list and update.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

I have had problem with OpenGL in one ati machine I run Natty on. OpenGL version was 1.7 using the open source driver. Upgrading with this ppa boosted it up to OpenGl 2.1 and things that didn't work before suddenly started working.

Read carefully first. If anything goes wrong purge the ppa using ppa-purge, so install that first.
That installs and works fine, but the issues still persist.

---

