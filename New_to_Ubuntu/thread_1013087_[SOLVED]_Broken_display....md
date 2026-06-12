---
title: "[SOLVED] Broken display..."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by AndrewS on 2008-12-16
Hello

I've lost my display while "playing around" with Compiz-Fusion - all I get is a black background with the occasional set of coloured dashes.  I assume I'll have to fix this from the command line, but I haven' a clue how to do this.  Can I reset all the display options to default, or uninstall Compiz etc?

Thanks in advance

Andrew

---

### Post by travis31 on 2008-12-16
Try reconfiguring X server 
[http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/]("http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/")

---

### Post by mapes12 on 2008-12-16
In Terminal ```
sudo apt-get --reinstall install ubuntu-desktop
``` should bring back your previous settings.

---

### Post by AndrewS on 2008-12-16
Thanks for the replies.  I have 8.04 on the PC as well, so I used that to do some Google searches.  I used CTRL+ALT+F1 to get to a test-based interface, then used:

gconftool-2 --recursive-unset /apps/compiz

Which put me right.

Andrew

---

