---
title: "How to change default background loaded on boot"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by nalgarryn on 2010-10-10
[FONT="Palatino Linotype"]Hi again!

When i boot into ubuntu the default background that was installed with the OS shows until someone logs in and then their custom background is installed.

Could someone please explain how I got about changing the background that shows before anyone logs in (the default one loaded by the system) and also how to change the login screen appearance? I did look at the themes thing, but all the login pages downloads are just images and I am not sure how to take a picture from the web and implement it as the login page.


Thanks in advance.


~~~
Acer Aspire 5315-2681 notebook
Ubuntu Lucid installed (latest as of Oct 6, 2010)
[/FONT]

---

### Post by jtarin on 2010-10-10
You will need ubntu-tweak to do this. You can find it in the Software Manager or Synaptic.

---

### Post by wojox on 2010-10-10
Or this way

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using Crtl+ALT-F7 or Crtl+ALT-F8
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

---

### Post by nalgarryn on 2010-10-10
Thanks guys. I'm going to call this solved and experiment! :)

---

