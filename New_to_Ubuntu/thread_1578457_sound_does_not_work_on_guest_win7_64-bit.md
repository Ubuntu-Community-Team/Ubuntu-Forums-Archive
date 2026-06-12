---
title: "sound does not work on guest win7 64-bit"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by sefa on 2010-09-20
Hi,
 
I have a win7 64-bit guest on a Ubuntu 10.04 64-bit desktop. Everything works well except the sound. 
 
I run the img something similar to this (I don't have access to the machine now)
 
kvm -m 3036 win7-clone.img -cdrom /dev/cdrom -std-vga -soundhw all -full-screen
 
I tried adding the ac97, es1370, sb16 but no luck... Sounds work fine with ubuntu and winxp guests...
 
Has anyone else run into the same problem?
 
 
Thanks,
Sefa

---

