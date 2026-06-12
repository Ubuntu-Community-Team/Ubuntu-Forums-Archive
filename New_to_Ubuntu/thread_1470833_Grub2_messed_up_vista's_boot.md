---
title: "Grub2 messed up vista's boot"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by jacklsw2008 on 2010-05-03
Ever since i installed 10.04 on my laptop, the Grub 2 bootloader kinda messes up my Vista boot. It would hang before vista gets to boot and I have to force my laptop to restart a few times to start up vista.

Did anybody else encounter this problem with grub 2? is there any way i can use the legacy grub as the bootloader?

---

### Post by cap10Ibraim on 2010-05-03
Did you install the updates , they fix this issue

---

### Post by Paul T. on 2010-05-03
You might find some help here:

[http://ubuntuforums.org/showthread.php?t=1469314&highlight=boot](http://ubuntuforums.org/showthread.php?t=1469314&highlight=boot)

---

### Post by jacklsw2008 on 2010-05-04
thanks guys. i'll try it out :)

---

### Post by jacklsw2008 on 2010-05-08
hmm. i found a solution for my case. i just edit the grub file:
1. sudo gedit /etc/default/grub
2. in the file, uncomment this part 
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

---

### Post by wilee-nilee on 2010-05-08
> **jacklsw2008 said:**
> hmm. i found a solution for my case. i just edit the grub file:
1. sudo gedit /etc/default/grub
2. in the file, uncomment this part 
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

Not a good idea unless you backup the original and know what your doing. Post this boot script in code tags. Just past it to the thread highlight  the text in the reply and hit #.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

