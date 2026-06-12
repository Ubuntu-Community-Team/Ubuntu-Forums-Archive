---
title: "Jaunty hangs following startup"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by SDL on 2009-06-26
Hi.

I've just upgraded from Intrepid to Jaunty but now my computer hangs about a minute after loading the desktop. The display continues to work but the mouse and keyboard are completely unresponsive meaning that I can only power down using the button on the case.

I've had similar problems on upgrading previous versions but these have always been corrected by using ACPI=off and installing the proprietary NVidia and Broadcomm drivers. I've done all of this in Jaunty but without success (it was a real task to do that before the PC crashed!)

The computer works fine in recovery mode and I've run the command ```
apt-get update
``` so I think that should mean that the system is fully up-to-date.

Furthermore, I get the same problems booting from the LiveCD. I've burned multiple CD's, the MD5 sums have been OK and they haven't had any problems when I've checked them for errors.

I'm currently using Ext4 but I had the same issue with Ext3.

Does anybody have any suggestions to fix this please?

Stephen.

P.S. The problem is so bad that even if I start shutting down the PC before it has hung, it can sometimes hang just before completing the shutdown process! :(

---

### Post by bhadotia on 2009-06-26
> **SDL said:**
> ```
apt-get update
```

Its:
```
sudo apt-get update && sudo apt-get upgrade
```
to update the system.

Which graphics card and mother board are you using?

---

### Post by SDL on 2009-06-26
Yeah, sorry I did use apt-get upgrade as well.

My graphics card is Nvidia GeForce FX5700 and the motherboard is Foxconn 755A01/K8S755A Series. Both worked fine on all of the previous versions of Ubuntu since Feisty.

---

### Post by SDL on 2009-07-25
I've got a week off now so it'd be nice to try and get this fixed whilst I'm not busy if anybody has any ideas what the problem could be please?

Thanks for reading.

Stephen.

---

### Post by SDL on 2009-08-09
Sorry to triple post but I'm still stuck on this and editing my last 'bump' didn't move this back to the top of the forum! Many thanks for any help.

Stephen.

---

### Post by LewRockwell on 2009-08-09
which LiveCD are you trying?

.

---

### Post by SDL on 2009-08-09
The 32bit desktop version of 9.04. Thanks for the reply.

---

