---
title: "Edit grub_timeout in grub2"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by kyeh on 2009-11-17
I've been reading some guides on how to edit grub2 but i still don't get why my grub_timeout doesn't work!

It seems that whenever i ran sudo update-grub, nothing happens to the timeout. I managed to change the resolution without problems though.

At the moment grub boots to the menu and does nothing after that.

My grub.cfg file:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

...snipped...

```

My desired result would be on boot grub should display the menu for 3 seconds and if nothing happens, boot to the first thing on the list.

---

### Post by Darce on 2009-11-17
You should remove the quotation marks from around the 3 at GRUB_TIMEOUT so that it reads like this :

GRUB_TIMEOUT=3

Cheers,

Tim

---

### Post by ranch hand on 2009-11-17
Here is some of my grub file;
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="100"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
Yes  I like a long time out.

I would check the link in my sig.  I would recommend the second link in it to you as a possible place for the cure of your problem.

---

