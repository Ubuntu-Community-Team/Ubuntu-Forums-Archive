---
title: "Used display settings tool and now Compiz doesn't work!"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by emarkd on 2008-12-29
Hello all.  I've just recently installed 8.10 on my laptop and the video setup is very different from before.  Everything worked great on installation, but yesterday I tried to use the display settings tool to enable the svideo output.  The svideo sorta worked but it looked terrible, but my real problem is that I no longer have Compiz working since switching back to single monitor mode.  I tried using the Appearance widget to re-enable the visual effects, but I get a "desktop effects could not be enabled" error, which isn't very helpful.

I know it's possible because everything worked beautifully before I tried the svideo thing, and since almost nothing is handled by the xorg.conf file anymore, I'm pretty lost.  With 8.04, I could simply swap my xorg.conf file for one with svideo out enabled and compositing disabled and both displays worked fine.  For now, I'd just be happy with Compiz working again before I tackle the svideo problems.  Any advice?

The system in question is a Dell Inspiron 6000 with an Intel graphics chipset.  In the past, I've used the i810 driver and it's worked great, but now I don't even know how to see which driver I'm using.

---

### Post by emarkd on 2008-12-29
bump..

---

### Post by emarkd on 2008-12-29
Ok, I got Compiz working again by running xfix from the recovery console, which seems to be a dpkg-reconfigure operation.  I still don't really understand how this new Xorg stores all it's settings...

---

