---
title: "No sound in Jaunty"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by slubkin on 2009-09-09
I am running Ubuntu 9.04, on an Acer machine.  It ran Vista before I installed Ubuntu; sound worked perfectly with Vista.  But, since installing Ubuntu, sound has disappeared.  lspi tells me that the sound card in the Acer is nVidia Corporation MCP61 High Definition Audio (rev a2).

Perhaps I need some driver for this card that works with Ubunto 9.04 (Jaunty)?

Or something else?

Help VERY much appreciated.

Thanks in advance,

  -- Saul

---

### Post by eagle416 on 2009-09-09
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by swoody on 2009-09-09
Hi slubkin, and welcome to the forums ):P

Open a terminal (Applications>Accessories>Terminal) and run:
```
gksu gedit /etc/modprobe.d/alsa-base
```
A gedit window will open with this file. On it's own line, add:
```
options snd-hda-intel model=3stack
```
Then save the file, and reboot your computer.

Please let us know if that takes care of the issue or not :)

---

