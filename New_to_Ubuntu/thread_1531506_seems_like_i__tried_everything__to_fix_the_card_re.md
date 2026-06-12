---
title: "seems like i  tried everything  to fix the card reader would update help ?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by ubunguy on 2010-07-15
I changed  preferences .fdi to true

I tried to create a new options.conf

I added  /sbin/modprobe pciehp pciehp_force=1

or

sudo nano /etc/modules and add options pciehp pciehp_force=1

to modprobe

I even tried this

Do the following things.
1. Backup the file /etc/modules
sudo cp /etc/modules /etc/modules.bak
2. Add one line to /etc/modules
gksu gedit /etc/modules
or
sudo vi /etc/modules
3.Tag this on to the end of the file in a new line:
tifm_sd

and lastly I tried this  

Media Card Readers
You need to edit*/etc/default/grub*(as root ofc) and find the
line that starts:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change it to read

GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 elevator=noop quiet
splash"


I may have tried some other methods but they did not have worked.

If I run the update manager will this help my case im  using easy peasy but I  have not ran the update manager yet , I really need  this card reader to work ,going on vacation soon and dont want to  be bothered with carrying around a usb card reader everywhere I go.

So let me know ill work on this tonight. also i am new to linux and easy peasy so i may have done one of these codes wrong ,and im using an acer aspire one 532h:(

thanks

---

