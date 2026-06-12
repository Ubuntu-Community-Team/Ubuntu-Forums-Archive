---
title: "Plymouth: Grunge Screen"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Psumi on 2010-02-14
This is a thread dedicated to the issue that WILL come (as it currently is in Fedora, even on their stable distros.)

Please utilize the following steps to resolve the issue, if you cannot resolve the issue, please post here with your graphics card model.

1. In your computer's BIOS, reset the display settings to default. (if that is an external display on a laptop, then set it to the LCD or internal display instead.)
2. In ubuntu, set the display to what it was originally when the system worked with plymouth (if you don't know, then it's possible your resolution has to be set via tty or another liveCD via xorg.conf.)
3. (Only do last if previous methods did not work) Re-install the system using the [***_[COLOR="Red"]mini.iso[/COLOR]_***]("https://help.ubuntu.com/community/Installation/MinimalCD"), and install gnome, xfce4, lxde or kde metapackages. These metapackages will install the base DEs for use with your system. THIS WILL NOT INSTALL PLYMOUTH.

Special instructions for--possibly older--ThinkPad users: ENABLE HV EXPANSION (This should be on by default.)

Some computers will also display the grunge screen when switching resolutions during a logged in session, please refrain from switching resolutions when logged in.

---

