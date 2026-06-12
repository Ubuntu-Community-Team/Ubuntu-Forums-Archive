---
title: "no graphics driver available for 9.04"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-04-27
I upgraded to 9.04 and the ati radeon 9550 propreitary driver disappeared from the Hardware Drivers list.

So, I went to get it from ati, and when I went to install it, it told me something along the lines of:

```

matt@matt-desktop:~$ cd /home/matt/Desktop
matt@matt-desktop:~/Desktop$ ./hey.run
Created directory fglrx-install.EJOCjz
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.EJOCjz
matt@matt-desktop:~/Desktop$ 

```

So, I suspect that the kernel isn't supported (I'm not sure though). Is there anything I can do?

---

### Post by Didius Falco on 2009-04-27
From ATI:

> AMD has moved a number of DX9 ATI Radeon™ graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.
 The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):
 ATI Radeon 9500 Series
ATI Radeon 9550 Series
<snip>

This means you'll have to use the open source driver instead of the proprietary one - or buy a newer card that is supported.

Sorry to be the bearer of bad news...

---

### Post by mattbutsko on 2009-04-27
Is there a website with a list of open source drivers? If not I'm sure google searching should work fine.

Thanks.

---

### Post by Didius Falco on 2009-04-27
You can get the 'xserver-xorg-video-radeon" driver through Synaptic. That's the open source driver for your card.

---

