---
title: "what do I do about the file change messages when upgrading?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by bobmac on 2010-05-24
Folks,

When upgrading to a new version, at several points in the installation, messages (dialogs), display asking what to do to certain files. For example, one file that I've noticed appears to be named menu.lst. The message with this has several options with the default being 'leave as is'. When it is left 'as is',however, when the installation is done, and the system reboots, the options for selection seem to be the same as the previous version. 

I suspect that I should be selecting something else but there are several options.

Any ideas on what I should choose?

Regards,

Bob

---

### Post by Dayofswords on 2010-05-24
what exactly are you upgrading?

9.04 to 9.10?

---

### Post by Elfy on 2010-05-24
Similar to this I would imagine

[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

---

### Post by gdonwallace on 2010-05-24
Menu.lst displays the available kernels that are installed on your machine by Ubuntu.  If you have not made any changes to menu.lst (i.e. changed what displays when it boots, or added to it another boot option) then go ahead and accept the new one.  This way you will be able to boot with the newest linux kernel.

---

