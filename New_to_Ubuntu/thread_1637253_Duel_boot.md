---
title: "Duel boot"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by cwejg on 2010-12-04
Hello all
I am just starting with Ubuntu and installed it duel boot with Windows Vista. It is working well and I don't want to mess it up however when I restart the computer the opening menu gives me a choice of Ubuntu (recovery mode) or Windows (recovery mode) I don't understand the recovery mode and haven't tried it for fear of messing up the Ubuntu installation. I am attaching a snapshot of the screen but not sure how it will turn out.

Thanks,
Chuck

---

### Post by Quackers on 2010-12-04
Welcome to UF :-)
That is normal. 
The multiple entries appear when new kernels are installed (via update).
The recovery mode entries are for when a problem exists in your normal booting up. No need to try it if you don't want to :-) But you can if you want :-)

---

### Post by Megaptera on 2010-12-04
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don&#8217;t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

If you&#8217;d like a GUI,Ubuntu-Tweak is a good choice where you can remove them from Applications->Package Cleaner->Clean Kernel

---

