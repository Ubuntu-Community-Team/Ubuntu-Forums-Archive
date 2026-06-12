---
title: "Trouble installing ATI x600 Series Driver"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by nolongerBBS on 2010-04-04
I have been trying to install this driver from ATI's site for a while and it wont install the way ATI says it will and it doesn't install with envyNG either so this is as far as i can get in the terminal.

bill_murray@billmurray-desktop:~/Downloads$ sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/karmic
Created directory fglrx-install.PcV46W
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/karmic
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Removing temporary directory: fglrx-install.PcV46W

---

### Post by tom.swartz07 on 2010-04-04
> **nolongerBBS said:**
> I have been trying to install this driver from ATI's site for a while and it wont install the way ATI says it will and it doesn't install with envyNG either so this is as far as i can get in the terminal.

bill_murray@billmurray-desktop:~/Downloads$ sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/karmic
Created directory fglrx-install.PcV46W
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/karmic
[B][U][COLOR="Red"]Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions[/COLOR][/U][/B]
Removing temporary directory: fglrx-install.PcV46W

Hi and welcome to the forums!

Unfortunately, the ATI driver is no longer supported for the current versions of Ubuntu. The last version that the driver was supported for was Ubuntu 8.04. Since then the version of X and xorg was updated and is not compatible with the driver. The Installer even points it out; highlighted above. 


I am in the same situation also; I have an ATI Radeon X1270 card, and it is also on legacy support. 


FORTUNATELY, The current versions of Ubuntu have 'built in' support for the graphics card, although rudimentary. Unless you are planning on playing hardcore games, you should be fine just ignoring the card drivers and using the built in, and default activated, ones that were installed with the OS.

---

### Post by George7a on 2010-04-24
I think I have the same problem! I have just bought ATI HD 4770 and I am getting the same error.

Now, you are telling me that it is not supported and that I will not be able to use the cube and other stuff?
Will it ever be supported again?

---

### Post by Mark Phelps on 2010-04-25
> **George7a said:**
> I think I have the same problem! I have just bought ATI HD 4770 and I am getting the same error.

Your card is nothing like the X600 card; your card IS supported in current ATI Linux drivers. 

So, it is nothing like the same problem -- please start your own thread instead of hijacking this one.

---

### Post by quadproc on 2010-04-25
> **nolongerBBS said:**
> I have been trying to install this driver from ATI's site for a while and it wont install the way ATI says it will and it doesn't install with envyNG either so this is as far as i can get in the terminal.

bill_murray@billmurray-desktop:~/Downloads$ sh ati-driver-installer-[COLOR=Red]9-3[/COLOR]-x86.x86_64.run --buildpkg Ubuntu/karmic

The problem is incompatible versions.  For an older ATI card you need an older ATI driver (such as the one highlighted above) but that old driver is incompatible with your Ubuntu version.  Fortunately, ATI's script checked this for you and prevented you from installing something that won't work.

You could downgrade your Ubuntu version and use the older driver, or you could use the open source "ati" driver provided inside Ubuntu and use a recent Ubuntu version.  The open source driver is not as capable as fglrx (yet) but it is improving rapidly.

It turns out that the real issue here is that X windows did a major and incompatible change between Ubuntu 8.10 and 9.04.  Never the twain shall meet.

Incidentally, if your install had proceeded further then it would have failed because you weren't super user when you ran the script; a _sudo_ at the start of the command would fix that.

quadproc

---

