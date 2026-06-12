---
title: "screen resolution messed up after adding KVM switch"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by SKOREAPV83 on 2009-05-29
My friends who I live with own two desktop computers and decided to hook up a KVM switch to use both of them with a single keyboard, mouse, and monitor. The Dell OptiPlex GX150 runs Windows XP Home and the Compaq 5000 runs Ubuntu 9.04. The screen resolution is fine on the Dell, but on the Compaq, it reverted to 800 x 600 and now everything is way too big on the screen. Prior to adding the KVM switch, it was FINE. The KVM switch is generic; it does not have any brand name on it. We would appreciate any help to get the screen resolution back to normal on the Compaq.

---

### Post by CatKiller on 2009-05-30
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver (or in this case, a KVM) not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

