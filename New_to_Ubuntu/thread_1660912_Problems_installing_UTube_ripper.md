---
title: "Problems installing UTube ripper"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by kozhi on 2011-01-06
I am using Ubuntu for about a year & half now, currently using the latest 10.10 version. I can do most of the basic things, such as updating, installing using Synaptic (or .deb packages).

I am trying to install uTube Ripper. 

An earlier version available on sourceforge meant for Ubuntu is utube_1.7-1_i386.gtk.deb. I have downloaded it and installed by double clicking the file. While it installed, and shows up under "Applications", it doesn't run. Not sure if this is version incompatibility.

The latest version available on sourceforge is Utube Ripper-2.0-Linux-x86-Install. On downloading, when I double click to install (like I do for .deb packages), nothing happens and an error message comes (asking me to specify how to open this file).

Any advice is welcome. Thanks.

---

### Post by lisati on 2011-01-06
Youtube made some changes some time back. Please see the link in my sig.

---

### Post by kozhi on 2011-01-06
> **lisati said:**
> Youtube made some changes some time back. Please see the link in my sig.

Sorry if this sounds dumb, but by "sig" you mean the links at the bottom of your post? If so, then I did check the link related to youtube ("Before you download from Youtube"), where you are discussing youtube terms of service and piracy. That's fine.

But then what about the problem with utube installation, particularly, about installing files that have "install" at the end, not .deb extensions. If you could point to this I shall be grateful.

More generally, how might one rip the audio off video formats?

Thanks.

---

### Post by lisati on 2011-01-07
> **kozhi said:**
> 
More generally, how might one rip the audio off video formats?

Thanks.
No idea. I've only used Windows software for that job - on my own videos, of course! Perhaps someone else can help with suggestions for audio extraction.

"UTube", when spoken, does sound a bit like "YouTube", and we don't want to run into any potential legal complications of what we're  doing :D

---

### Post by scorsagr on 2011-07-29
Sorry! I don't speak English.

Installing Utube Ripper-2.0-Linux-x86-Install.
**1)** Dependencies: install **Gambas** and **QT4**.

**2)** Download Utube Ripper-2.0-Linux-x86-Instal:
```
cd && wget -q http://sourceforge.net/projects/utube/files/AutoInstallers/Utube%20Ripper-2.0-Linux-x86-Install
```

**3)** Installation Utube Ripper (Default: /usr/local/Utube):
```
cd && sudo ./Utube\ Ripper-2.0-Linux-x86-Install
```

**4)** Shortcut Menu **Utube Ripper**.
Change:
> /usr/local/Utube/utube.gambas
by
> /usr/local/Utube/utubeqt/utube.gambas

Shortcut Menu **Uninstalling Utube Ripper** is correct.

Link [Utube Ripper]("http://sourceforge.net/projects/utube/")

---

