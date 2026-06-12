---
title: "Graphics driver messed up after updates yesterday"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by xItachi on 2009-07-14
Hi, I'm using Ubuntu 9.04 and it's been running well, but yesterday I installed some updates through the Update Manager, and it asked me to restart, so I did.  When I was back in Ubuntu, it gave me some problem about graphics, I had a few choices (troubleshoot, boot up ubuntu using safe graphics mode only for this session, reconfigure).  I tried reconfigure and that didn't seem to help, so now I'm just in safe graphics mode.  Any idea of how I can restore my original graphics driver?

I tried
```
$ sudo dpkg --configure xserver-xorg
```
but it gave me:
package is already installed and configured

then
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```
and restarted but that didn't help either

Thanks!

Edit:
Okay I've got a hold of the error message:

```
Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0): Failed to set tiling on front buffer: rejected by kernel

What would you like to do?
- Run Ubuntu in low-graphics mode for just one session
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login
```

---

### Post by nhasian on 2009-07-15
yeah those commands stopped working in intrepid i think.  what version of ubuntu are you using now?  please post the output of these terminal commands:
```

uname -a
```

```
lsb_release -a
```

```
lshw -C display
```

---

### Post by xItachi on 2009-07-15
First of all nhasian thanks for helping me out.

```
$ uname -a
Linux stephen-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
```

```
$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty
```

```
$ lshw -C display
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
```

I remember when I upgraded to Jaunty, there was a problem with the intel video driver and it was too slow, so I followed some guide online to configure it or something so that it works faster.  I tried searching for the same guide but I couldn't find it.  

I tried two other guides just now:

[_HOWTO: Jaunty Intel Graphics Performance Guide_]("http://ubuntuforums.org/showthread.php?t=1130582")

[_Reverting the Jaunty Xorg intel driver to 2.4 - Ubuntu Wiki_]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

After these two, when I restarted my computer, I actually made it to the login screen without the error and the graphics looked very nice and clean, like how it originally did before I installed the updates.  I thought the problem was fixed, but when I attempted to login, the screen turns black for a while and then it goes back to the login screen.  So something is not quite right yet.

I also saw a message saying something about how a display manager is already running on :0, and that I should try to run it on a different server (F7 or higher). I chose yes, but no effect.

---

### Post by 3rdalbum on 2009-07-15
> **xItachi said:**
> I remember when I upgraded to Jaunty, there was a problem with the intel video driver and it was too slow, so I followed some guide online to configure it or something so that it works faster.

Ah-ha! That's what we needed to know.

If you've installed a new graphics card driver that Ubuntu itself doesn't offer to you, then you will need to reinstall or recompile the driver whenever you update your kernel.

If you installed the driver from a 3rd party repository, then that driver has been built for the old kernel that you are no longer running, and won't work as-is for the new kernel (it would need to be recompiled).

I can't really offer any suggestions unfortunately - I tried messing with my Intel driver and just made things worse, so any suggestions I give would be "the blind leading the blind". If you'd found the actual HOWTO again then you could try following it again.

The only thing I can suggest would be to remove any repositories that you might have added to get a new Intel driver, and then reinstall all packages relating to Xorg and Intel graphics. This would leave you with the stock Ubuntu Intel driver, at least in theory. (I tried this course of action and somehow completely broke graphics entirely, your milage may vary).

---

### Post by xItachi on 2009-07-15
Thanks, I will try to find the other how-to, but I have a question.  Does the Update Manager ever install new kernels?  If I didn't install a new kernel, I wouldn't have to update my intel driver would I?  I thought kernels are only updated when you install a newer version of Ubuntu or manually install it.

---

