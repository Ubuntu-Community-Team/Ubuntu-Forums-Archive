---
title: "how do you mount a DVD?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by harryliddic on 2010-03-04
How do you mount a dvd? I got the Bios set to cd-rom which is the closest I seem to able to get.

---

### Post by Locutus_of_Borg on 2010-03-04
uhh mounting a dvd should have nothing to do with the bios unless you are trying to boot off of a dvd

to mount a dvd, generally 'sudo mount -o loop /dev/sr0 /media/cdrom'

the dvd contents then will be accessible under /media/cdrom

---

### Post by harryliddic on 2010-03-04
I have a cdrom only and a dvd/cdrom would that need a different command? and neither shows up in fstab is the normal?

##
harry@harry-desktop:~$ 'sudo mount -o loop /dev/sr0 /media/cdrom'
bash: sudo mount -o loop /dev/sr0 /media/cdrom: No such file or directory
##

---

