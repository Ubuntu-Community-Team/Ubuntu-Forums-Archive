---
title: "[SOLVED] Hardware Drivers and synaptic from minimal install"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Goll on 2009-01-01
Hardy x64

I just installed on an LVM encrypted drive from the minimal install.
First thing I did was install

xorg, xinit, and ubuntu-desktop.

I figured that would take care of everything, and I went ahead and went through- tried to install synaptic etc.
Synaptic's installed, but it's not showing in the menu.

Hardware Drivers is not installed- I don't know how to install that, so if anyone knows please say!
I've already tried going through and installing it through synaptic (by opening synaptic in terminal because it's not in the menu (!)- but that hasn't worked.
It's the proprietary drivers that normally pops up for the nvidia after a regular install.

I think everything else is fine.

---

### Post by Goll on 2009-01-01
This was fixed by searching synaptic for hardware drivers.
There's a package called **discover** (which did not install when the ubuntu-desktop was installed)
Discover will allow you to enable the nvidia drivers by going to Appearance options and enabling the aesthetics appearance crap, this will download the proprietary drivers.

---

### Post by mkvnmtr on 2009-01-01
I have found that the search in Synaptic and then going to the web site of the app will answer most of my questions.

---

