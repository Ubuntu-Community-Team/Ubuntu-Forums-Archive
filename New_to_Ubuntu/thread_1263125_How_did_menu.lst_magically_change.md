---
title: "How did menu.lst magically change"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by eddski on 2009-09-10
I deleted some older kernels through synaptic, as instructed, and then went to reboot and I get this "error 15" after booting grub. My windows instal booted fine, but ubuntu. After reading some posts, and after much frustration, I looked at menu.lst and found some numbers changed on the initrd line. After correcting 2 lines everything is good. How in the world did those lines change, has anybody had that problem, and how can I prevent it from happening again?

---

### Post by mcduck on 2009-09-10
What numbers were changed?

If you make any changes to Ubuntu's boot options in the menu.lst file, make sure that you also do the same changes in the default options section of the same file. Kernel updates (and running update-grub manually) read the options to be used from the default options section, not from your current menu entries.

---

### Post by eddski on 2009-09-10
thanks for the explanation and quick reply. I will note this for future reference.

---

### Post by Paqman on 2009-09-10
Whenever you add or remove kernels, the system will automatically edit the Grub list. It has to, otherwise Grub would be out of step with what was actually bootable on the system. Normally it does this without messing up the file. Was your menu.lst a standard one written by the machine, or have you ever edited it manually?

---

### Post by eddski on 2009-09-11
Yes I did a couple of manual edits, but I never had a problem with it.

---

