---
title: "2 ubuntu versions in grub?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by soryu on 2009-12-07
why 2? how or can i remove the old one?
i like 1.

---

### Post by NoaHall on 2009-12-07
Do you mean different kernel versions? They are different core systems(one is newer). It's a good idea to have at least 2, because one might have problems for you.

---

### Post by LunaticHiatus on 2009-12-07
one does look cleaner but having older kernels available is good in case the latest and greatest kernel also makes your drivers act screwy. There are applications for adjusting how grub looks, I'm not sure what the one for grub 2.0 is though.

---

### Post by soryu on 2009-12-07
thank's guys.

---

### Post by Bradj47 on 2009-12-07
> **LunaticHiatus said:**
> one does look cleaner but having older kernels available is good in case the latest and greatest kernel also makes your drivers act screwy. There are applications for adjusting how grub looks, I'm not sure what the one for grub 2.0 is though.

There are applications to do so, but editing the /boot/grub/menu.lst file is easy enough. Just add **#** marks to the lines that you don't want to show in GRUB. Don't delete them though, because you might want them in the future. If you have trouble figuring things out, copy/paste the contents of **/boot/grub/menu.lst** here and I'll tell you where to add **#** marks.

---

### Post by D3M0L1$H3® on 2009-12-07
If you only use Ubuntu, and it bothers you, just don't look at the menu til it's done =p

---

### Post by 73ckn797 on 2009-12-07
If you are using Ubuntu Karmic Koala 9.10 here is no "menu.lst" that can be edited. You can get "startupmanager" from Synaptic and it will let you do some changes to the boot menu.

You can also uninstall the earlier kernel through Synaptic and the boot menu will reflect that change.

---

### Post by Locke_99GS on 2009-12-07
If using Grub 2 (fresh install of 9.10, for instance) there is no menu.lst, and there are no gui utilities to work with it yet.

Edit files at /etc/default/grub and in /etc/grub.d in order to modify Grub2. Run *update-grub* to rebuild grub menu.

---

