---
title: "Device Manager?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by servicetech on 2009-04-25
Where is the ubuntu equivalent of "Device Manager" in windows?

---

### Post by kwacka on 2009-04-25
Not sure why you are after a Device Manager, but the command ```
sudo lshw
``` list all hardware.
```

sudo lsmod
```lists running kernel modules.


Also gnome-device-manager is in the repositories.

---

### Post by servicetech on 2009-04-25
For installing/updating drivers.

---

### Post by kwacka on 2009-04-25
Right, the applications I mentioned are for reporting what is there, rather than the Windows route.

Drivers for what device do you need to install?

---

### Post by UbuntuNerd on 2009-04-25
you can also install System Info in a terminal type:
```
sudo aptitude install sysinfo
```
to open it go to Applications > System Tools > Sysinfo
it should provide most of the info you need

---

### Post by kansasnoob on 2009-04-25
> **servicetech said:**
> For installing/updating drivers.

Well, in 8.04 you would perhaps go to System > Administration > Hardware drivers ......... maybe?

what would be really helpful is to know what hardware you want to install:confused:

Installing a different graphics card is totally different than installing a different audio card!

Linux is NOT Windows! No similarity beyond what you see in front of you!

Edit: As I think about it the same is true with Windows! Updating the driver for my printer or scanner may be totally different than updating the driver for a new video or audio card!

Must know specifically what you're upgrading!

---

### Post by servicetech on 2009-04-25
I was wanting to install the Haupagge 2250 drivers once they are released.

---

### Post by kwacka on 2009-04-25
Looking at the developers page for this at [http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/) it seems he's managing to get it moving along well.

Its very likely that when it is released instructions will be included in the file.

---

