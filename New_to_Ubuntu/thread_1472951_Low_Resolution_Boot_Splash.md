---
title: "Low Resolution Boot Splash"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by pizza-is-good on 2010-05-04
Hello,

First Lucid problem... (Not major one thankfully)

OK, here it goes:
My boot splash is appearing in a very low resolution, and it just looks really unprofessional.
I figure that there should be an easy fix for this, but I can't seem to find it.
I have tried to change the grub resolution with start-up manager, and that works fine for grub, but not for the boot splash.
The log-in screen is fine, no problems there.
My display's max resolution is 1280x800. (My guess is that boot splash is 800x600)

I am using 10.04 64-bit. Maybe that? I installed 32-bit on a friend's laptop, and no problems there with the boot splash resolution.
That is mainly why I care, because I saw how neat his looked, and was ashamed mine looked like an ugly purple blob.

All my laptop's specs are in my signature. I will provide any other info needed. Help will be appreciated.

~pizza

---

### Post by TheNerdAL on 2010-05-04
Maybe this thread might help: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by pizza-is-good on 2010-05-05
> **TheNerdAL said:**
> Maybe this thread might help: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

Thanks. I followed this:

> **philinux said:**
> 
**[COLOR=DarkRed]Bootup/Plymouth.[/COLOR] **
Users should experience a much faster boot however some users may  experience problems with Plymouth after the nVidia graphics driver has  been enabled. Users may experience plymouth using lower graphics  resolution. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013)

Graphical solution : [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
```
gksu gedit /etc/default/grub
``` and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via  VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXPAYLOAD_LINUX=1680x1050** Save the file and run ```
sudo  update-grub
```The resolution chosen should be your monitors native  resolution.

Other graphics card users may get a black screen with flashing cursor  and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this  option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```Plymouth now has a hard dependency on mountall thus trying to  remove Plymouth would remove half the OS. The advice is, if you don't  want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the  floppy in the bios. This has been reported as a fix to this. [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)

If the problem is plymouth not displaying, and a black screen from grub  to gdm, this could be due to graphics drivers needing to be loaded  quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787)

Plymouth is installed with 2 themes by default you can install more via  synaptic.
To change themes this code is used.
```
sudo update-alternatives --config default.plymouth

```

Not everything worked in the above workaround. I had to do the 'Graphical Solution'. That fixed the resolution(It had more things to configure than the above workaround). Then I did the above fix for the dark screen flashing cursor. That worked good.

Thanks again. Much appreciated.

~pizza

---

### Post by MusicMan374 on 2010-05-31
I had the same exact issue with mine, the graphical fix done by softpedia did the trick, the fix in the post didn't though. Been looking for this fix for awhile, works like a charm. Although for some reason when I edit my /etc/default/grub in the line to set the gfx mode or whatever it is exactly, when I updated grub, it would still have a 1280x1024 bootloader resolution in grub.cfg, and I assume that had something to do with startup-manager being installed. I have since uninstalled it and edited grub.cfg directly to fit my monitor and now everything works.

---

