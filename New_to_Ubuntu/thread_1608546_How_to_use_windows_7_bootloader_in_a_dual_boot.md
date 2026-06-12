---
title: "How to use windows 7 bootloader in a dual boot?"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by helios_05 on 2010-10-29
Hi,
I want to ask if there is a way to use the windows 7 bootloader as my default loader in a dual boot?
I want to install ubuntu 10.10 64 bit with windows 7 64-bit in a separate partition.
Tried wubi before but now I cannot boot in ubuntu.Thanks in advance.

---

### Post by Omnomnom on 2010-10-29
So basically you want windows 7 as your default OS?

---

### Post by helios_05 on 2010-10-29
Yes,I  find windows bootloader more clean than grub.Tried wubi install but cannot boot after an update.

---

### Post by helios_05 on 2010-10-29
I finally solved it.I install the ubuntu 10.10 in a separate partition with grub in that partition not overwriting the MBR.Then using the EasyBCD([[COLOR=#444444]http://neosmart.net[/COLOR]]("http://neosmart.net")) you can easily edit the windows bootloader to add ubuntu.Thanks.

---

### Post by D3SI on 2010-10-29
i tried that but Windows Loader doesn't show Ubuntu in Loading Options

can you help m8?

---

### Post by Omnomnom on 2010-10-29
Glad you got it solved man.

---

### Post by helios_05 on 2010-10-30
Did you use the EasyBCD bootloader editor?after installing ubuntu( with grub in the ubuntu partition) reboot to windows 7.Then use the EasyBCD to add ubuntu. There is an option there to add a new entry,choose linux in the tabs, then choose grub2 in a drop down list. EasyBCD will automatically configure everything after.Hope this helps.

---

