---
title: "Ubuntu-restricted-extras - Ver 8.10"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Alan F on 2008-12-30
When trying to install 'ubuntu-restricted-extras' from within 'Add/Remove Programs' I get the following error message.


"Cannot install 'ubuntu-restricted-extras'

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."



How can I determine which are the offending installed programs?

---

### Post by jorj82 on 2008-12-30
Try installing from a terminal, that should tell you.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Raynman37 on 2008-12-30
Did you try going to *System > Administration > Synaptic Package Manager* and then restricted extras.  Then mark install and it should work.

---

### Post by Alan F on 2008-12-30
I had already tried as suggested by Raynman37 with same result.

Trying to install via terminal as suggested by jorj82 identified that 'libavcodec51' had to be uninstalled but when I accepted that terminal proceed with the installation it crashed during installation.

However by uninstalling 'libavcodec51' and its dependancies 'gstreamer0-10-ffmpeg' and 'libavformat52' in synaptic I was then able to install 'Ubuntu-restricted-extras' via add.remove programs.

My thanks to both of you.

---

