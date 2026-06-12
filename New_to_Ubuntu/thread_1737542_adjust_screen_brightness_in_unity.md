---
title: "adjust screen brightness in unity"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Someone uk on 2011-04-23
hi i am using ubuntu netbook remix on a samsung NP-N110
i have tried the brightness keys on the keybaord but they don't seem to work, any ideas?

---

### Post by Someone uk on 2011-04-23
anyone?

---

### Post by Matt__ on 2011-04-23
Try the following (from French Ubuntu forum) it was used to resolve the same issue on a friends samsung N145:

sudo add-apt-repository ppa:voria/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install samsung-tools samsung-backlight
sudo reboot

It appears on some systems the function keys begin working but the brightness does not change. In this case, try appending &#8220;acpi_backlight=vendor&#8221; to the GRUB_CMDLINE_LINUX line in Suspend / Resume below.

GRUB_CMDLINE_LINUX=&#8221;acpi_sleep=nonvs acpi_backlight=vendor&#8221;

_____________________________________________________________________________________________________

---

