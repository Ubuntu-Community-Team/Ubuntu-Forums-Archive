---
title: "Cairo Dock black box problem"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by lulio on 2010-07-25
I know there are multiple threads with this problem, as I have looked through them. But my previous attempts at fixing this have been unsuccessful. 
I wasn't having any problems with it until metacity crashed. When I reset it Cairo Dock had the infamous black box. Resetting my visual effects to "extra" would solve the problem for a while, until metacity crashed again. But now resetting the visual effects has no effect on the dock. I've also tried deactivating Compiz and activated metacity compositing, but that didn't seem to do anything either. 
I'm running 10.04, any help is appreciated.

---

### Post by tsantata on 2010-12-14
This is what fixed it for me:

[http://www.pendrivelinux.com/cairo-dock-black-background-fix/](http://www.pendrivelinux.com/cairo-dock-black-background-fix/)

Hope it helps!
TS

---

### Post by rburkartjo on 2010-12-14
tsa tks for posting . have run into that problem myself

---

### Post by OttoMann on 2010-12-20
Hi!

I encountered the same problem with CairoDock, then followed tsantata's advice (Thanks for help!), but this solved the problem only half way. 

What it does it fakes transparency by replacing the ugly black box with your desktop background so the black box is not seen on the background, unfortunately now the background shows over the open windows if you have CairoDock configured to hide and to show it self when you move over with your mouse pointer. 

Most likely you don't have any screen effects enabled on your system. Go to System > Preferences > Appearance and click on Visual Effects tab and mark the Normal field. You might get an window popping up informing you  that the system searches for drivers, after the search is done the Normal screen effects should be on and with them real transparency and you can uncheck the transparency emulation in the System settings in CairoDock (if CairoDock didn't do it by it self).
If the system doesn't find any drivers to enable the normal screen effects than your hardware might not be up to it and you are stuck with the emulation.

---

### Post by Brandel Valico on 2010-12-20
You need to turn on compositing. For instance, you can run Compiz or xcompmgr.
If you're using XFCE or KDE, you can just enable compositing in the window manager options.
If you're using Gnome, you can enable it in Metacity in this way :
Open gconf-editor, edit the key '/apps/metacity/general/compositing_manager' and set it to 'true'.

---

