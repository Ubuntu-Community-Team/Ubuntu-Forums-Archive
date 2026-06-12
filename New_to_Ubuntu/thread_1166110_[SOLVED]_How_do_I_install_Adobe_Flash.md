---
title: "[SOLVED] How do I install Adobe Flash?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by plucesiar on 2009-05-21
Hello, I went to the Adobe Flash site and downloaded the tar.gz file. I extracted it but I'm not sure how to install it.
There are 2 files in the folder:
flashplayer-installer and libflashplayer.so

What do I run in the terminal?

I tried running "sudo apt-get make install"
but it returned "E: Invalid operation make"

---

### Post by JoshRobertson92 on 2009-05-21
**sudo apt-get install adobe-flashplugin**

Or download .deb from **[http://www.adobe.com/shockwave/download/alternates/](http://www.adobe.com/shockwave/download/alternates/)**

and then[B] sudo dpkg -i install_flash_player_10_linux.deb
:D
[/B]

---

### Post by kpkeerthi on 2009-05-21
[https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")

---

### Post by aysiu on 2009-05-21
.tar.gz files should generally be a last resort method of software installation.

More details here:
[http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash)

---

### Post by tomcheng76 on 2009-05-21
try **sudo apt-get install flashplugin-nonfree** ?

---

### Post by TpyKv on 2009-05-21
sudo apt-get update 

(first of all)

and then

sudo apt-get install ubuntu-restricted-extras

(will get all the non free plug ins, java, flash, MS fonts, DVD and music decoders, the lot)

Good luck :)

---

### Post by LunaticHiatus on 2009-05-21
what TpyKv said

---

### Post by plucesiar on 2009-05-21
holy smokes those replies were quick!
Thanks a bunch everyone!

---

