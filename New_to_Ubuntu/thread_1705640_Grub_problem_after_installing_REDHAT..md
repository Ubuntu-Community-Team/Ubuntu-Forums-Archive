---
title: "Grub problem after installing REDHAT."
date: 2011-03-12
forum: New to Ubuntu
---

### Post by ebycs on 2011-03-12
Help.....!!!

               Till today, i am running UBUNTU along with WINDOWS. Today i removed the WINDOWS os and installed REDHAT 5 in that partition. But the problem is that, i cant boot the 'UBUNTU'. I think there is some error in the grub. When i select the 'other' option in the grub, it shows 'rootnoverify (hd0,4) chainloader +1'. Nothing is happened after this screen. How can i solve this problem and thus to have access to my UBUNTU???

---

### Post by andrewthomas on 2011-03-12
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Just reinstall from a LiveCD following the above instructions using 
**SIMPLEST - Copy GRUB 2 Files from the LiveCD**


What you did was to let Redhat install to the MBR instead of its / partition.

---

