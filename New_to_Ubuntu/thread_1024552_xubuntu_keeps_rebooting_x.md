---
title: "xubuntu keeps rebooting x"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by absalom on 2008-12-29
Hi, i have a problem with eeeXubuntu 7.10.

my problem is that i've tried to configure auto log-in but somehow in the process i got an error which restarts X very often just after the computer blanks out the screen by fading (as if a screensaver was coming on), however i have set the computer not to use any screensaver.

so all is fine as long as i don't leave the computer on for a long while

/var/log/messages contains

Dec 29 11:20:52 geisha gnome-power-manager: (whisky) Power Manager is already running in this session.
Dec 29 11:22:05 geisha gnome-power-manager: (whisky) Power Manager is already running in this session.
Dec 29 11:23:23 geisha gnome-power-manager: (whisky) Power Manager is already running in this session.
... and so on ad infinitum

please don't ask me to update because certain proprietary drivers for a external device did not work on newer versions.

---

### Post by Dedoimedo on 2008-12-29
Do you mind reconfiguring xorg.conf to defaults?
Do you know how to do this, btw - if not, ask.
Dedoimedo

---

