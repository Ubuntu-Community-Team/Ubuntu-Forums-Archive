---
title: "KDE in Edubuntu 10.04"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by ninos on 2010-06-14
I'm using Edubuntu 10.04 .

Before I type my password,
I have the choice of various desktops.
GNOME works fine,
but whenever I choose KDE 
the blue screen appears, then its welcoming audio signal,
but later on, I only get a black screen!

Do I need to download a package for KDE to work properly?

---

### Post by 67GTA on 2010-06-14
Silly question, but have you installed KDE? Edubuntu uses gnome by default. You have to install kubuntu-desktop. Warning, this will pull in the full KDE4 environment and clutter your menu with all installed apps. You will also have to choose to either keep the default gdm login manager or use kdm.

---

### Post by 67GTA on 2010-06-14
Just checked the packages, and it looks like ```
kde-full
``` doesn't pull in all of the kubuntu files, and should give you a cleaner kde environment.

---

