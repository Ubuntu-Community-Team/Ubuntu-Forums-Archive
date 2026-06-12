---
title: "HDMI doesn't work all of a sudden"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by jackie hayes on 2009-09-15
I know, that sounds silly.  But I did the updates this afternoon, the computer asked to be restarted, I politely allowed it to do so, then chose to shut it down when the login screen came up (using the options tab at the bottom).  No biggie.  (Btw, I don't know what the updates were -- I barely glanced before clicking the okay.)  But  when I turned it on later, the monitor wouldn't flicker to life as it usually does.

Now I can't get HDMI to work no matter what I do.  I've tried restarting, unplugging, and screaming in myriad orders -- no luck.  D-Sub connection works, except the settings still seem to be for HDMI.  I only see a fraction of the screen and can't access the menus at the top.

So, first, if anyone has any ideas on how to fix it, or what went wrong, those would be aces.  But I know I haven't provided that much info, so a first step might be helping me get the resolution right (using the D-Sub connection).  I can't access most of the programs via the menu (the top bar doesn't seem to work), so if there's some way I can right-click to get to a settings menu, that would be extremely helpful.  Thanks for any help you can give!

Edit:  Got the settings okay for the D-Sub connector.  But if anyone has any ideas on the HDMI, that looked MUCH better.  I'm running 9.04, basic Ubuntu desktop, Asus M3A78 Pro mobo.

---

### Post by oldfred on 2009-09-16
Restarting means you probably installed an update to your kernel. Did you have custom video drivers installed? They often recompile the kernel to work with the video correctly. If so you may need to go back and reinstall the video drivers to get them to work with the new kernel.

Standard drivers should not be an issue as they are configured for your kernel.

---

### Post by tgalati4 on 2009-09-16
Rerun the proprietary driver application.  It should detect your card and recompile the shim required to work with your new kernel.

Note to self:  updates to the kernel or xorg can cause breakage.  Perform those updates only when you have time to deal with the breakage.

---

