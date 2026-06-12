---
title: "Upgrades keep wiping out my ALSA"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-09-19
I am really getting tired of having to reinstall ALSA every 1-2 weeks :( It seems that everytime I get a major update, I have to reinstall ALSA again to get my sound back.

Is there any way to stop this from happening again and again?

Is it only a problem with Ubuntu 9.04 (The version I have)? Would upgrading to a newer version help solve this problem (I really don't want to, but I will if I have to) If so, which version?

Any help would be greatly appreciated. :)

-Desi

---

### Post by Jazzy_Jeff on 2010-09-19
Is this the ALSA that came with Ubuntu or did you compile it yourself?

---

### Post by Vaphell on 2010-09-19
the problem is that alsa driver is installed into the kernel directory, so every time there is a new version of the kernel your current alsa driver is not used anymore (every kernel version has it's own dir tree). I am not sure but it's possible that the updates to existing versions of the kernel overwrite your custom driver too.

Same thing with gfx drivers for nvidia/ati - it's automagically done when the system handles everything, but when you install the drivers manually, you have to update them every time kernel gets an update.

---

### Post by DesiArnez6 on 2010-09-20
As far as I know, it is the one preinstalled with my system (ALSA) However I did follow this process quite a few times.:[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

So, is upgrading my version of Ubuntu to a newer version the only thing I can do? I hope there is another way.

-Desi

---

### Post by warfacegod on 2010-09-20
You can stop accepting kernel updates but that's something of a security risk.

It's doing this because you are using a custom driver. When you update the kernel that driver is lost. The same thing happens to people that use compiled video drivers.

If you want to know if a newer version of Ubuntu will run your sound then try the Live environments. You'll know pretty quickly if that version will give you sound out of the box.

---

