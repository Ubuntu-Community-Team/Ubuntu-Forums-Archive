---
title: "stymied by Nvidia install complication"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-16
Hi,

Karmic Koala advises me to install nvidia driver to regain my old scrn res prefs. but complications have arisen and i don't know what my next move should be?  What should I do ?

Thanks


nnjond@den-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".


ERROR: Unable to write to directory '/etc/X11'.

nnjond@den-desktop:~$

---

### Post by realzippy on 2009-11-16
You need root privileges ( sudo ):

**sudo nvidia-xconfig**

---

### Post by nnjond on 2009-11-16
Thanks, but, it hasn't moved me on much.

nnjond@den-desktop:~$ sudo nvidia-xconfig
[sudo] password for nnjond: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

nnjond@den-desktop:~$

---

### Post by realzippy on 2009-11-16
Delete current xorg.conf before running sudo nvidia-xconfig:

sudo rm /etc/X11/xorg.conf


edit:
if done,run *gksudo nvidia-settings*

---

