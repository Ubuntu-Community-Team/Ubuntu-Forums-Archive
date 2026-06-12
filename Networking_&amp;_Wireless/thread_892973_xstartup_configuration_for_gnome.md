---
title: "xstartup configuration for gnome"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by berntsonr on 2008-08-17
:confused: How should I change my xstartup so that I get the standard full ubuntu gnome desktop with tightvncserver? Currently xstartup is:

  #!/bin/sh


  xrdb $HOME/.Xresources
  xsetroot -solid grey
  x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
  x-window-manager &

When connecting from my Windows XP machine, I used to get the full ubuntu desktop environment, but now I only get the shell terminal.

thanks
ron

---

