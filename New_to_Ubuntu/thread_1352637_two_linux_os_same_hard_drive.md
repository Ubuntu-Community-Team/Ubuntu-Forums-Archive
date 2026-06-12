---
title: "two linux os same hard drive"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-11
Can SimplyMepis and Pclinuxos be installed in same hard drive or would i run into
problems with bootloader?Thanks

---

### Post by abeisgreat on 2009-12-11
Sure, why not. I'm not familiar with those distros, but I'm sure they use lilo, or grub, or something similar, which would allow for dual booting :)

---

### Post by ~sHyLoCk~ on 2009-12-11
Make sure your bootloader is installed to MBR. You can always boot into one OS and edit the bootloader config file if it doesn't detect the other OS automatically.

---

