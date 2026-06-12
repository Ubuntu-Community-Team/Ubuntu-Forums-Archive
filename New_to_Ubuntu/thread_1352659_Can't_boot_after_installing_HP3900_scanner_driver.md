---
title: "Can't boot after installing HP3900 scanner driver"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by skinks on 2009-12-11
After installing driver for HP3900 scanner, Ubuntu hangs on "loading hardware drivers", goes to low graphics mode and gives message about not finding Group "scanner" and going to /etc/udev/rules.d/025_hp3900.rules.  I have no idea how to uninstall this driver and get back to where I was.

---

### Post by abeisgreat on 2009-12-11
> **skinks said:**
> After installing driver for HP3900 scanner, Ubuntu hangs on "loading hardware drivers", goes to low graphics mode and gives message about not finding Group "scanner" and going to /etc/udev/rules.d/025_hp3900.rules.  I have no idea how to uninstall this driver and get back to where I was.

I would guess that, based on the error, that you needed a group called "scanner", and people in that group would be able to use the scanner. And the group probably doesn't exist. If you can drop to a shell, you should be able to make the group and add your user. Check the useradd or adduser commands. You can make and add users to groups with one of them, and I can never remember which does which.

---

### Post by skinks on 2009-12-11
Thanks for tip.  I added the group and added myself as user.  On reboot, it still hangs for about 5 minutes on the "Loading hardware drivers..", but now does NOT go into low-graphics made and does not show message about group or HP scanner.  It still tries to reconfigure the graphics and ends up with blank screen.  It must still be trying to load the driver for HP scanner and hanging up.  How do I skip loading this driver?

---

