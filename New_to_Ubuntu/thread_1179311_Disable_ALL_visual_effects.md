---
title: "Disable ALL visual effects?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-06-05
Hi, 
I've been trying to figure out how to disable all visual effects in Ubuntu. I don't want to watch my window minimizing, I want it to just minimize, etc.

System > Appearance > Visual Effects is set to None.

How can I disabled the remaining visual effects (theres still lots). Please don't suggest using Xubuntu or another distro, I want Ubuntu with the visual effects disabled.

Thanks to anyone that can try to help me out. :)

---

### Post by chrisod on 2009-06-05
Turn off all Compiz effects also.

---

### Post by philinux on 2009-06-05
> **ubuntuforums said:**
> Hi, 
I've been trying to figure out how to disable all visual effects in Ubuntu. I don't want to watch my window minimizing, I want it to just minimize, etc.

System > Appearance > Visual Effects is set to None.

How can I disabled the remaining visual effects (theres still lots). Please don't suggest using Xubuntu or another distro, I want Ubuntu with the visual effects disabled.

Thanks to anyone that can try to help me out. :)

what are your pc specs?

---

### Post by NightwishFan on 2009-06-05
With Compiz disabled you are likely using the Metacity Window Manager, which is the GNOME default. If you can still see a shadow under the Windows, then either compiz is still enabled, or you are using another compositing Window manager.

To disable some eye candy on Metacity, press alt+f2 and type:
```
gconf-editor
```
A registry style editor should come up. (Do not worry it is very easy and convenient to use). Simply search for metacity, or find it under applications. Do not edit the schema, just the normal entries. There should be a checkbox titled 'reduced resources'. Simply uncheck it, and metacity should be very minimal. If you like the wireframe or not is up to you. Also check if compositing is enabled, it should not be.

---

### Post by ubuntuforums on 2009-06-05
@chrisod: Yes, that's already disabled. Ubuntu seems to be missing the options like Windows XP has: Control Panel > Performance and Maintenance > System > Advanced > Settings (under Performance). You can there select or deselect individual visual settings for Windows XP. It seems that disabling visual effects in Ubuntu only disables the majority of them. You cannot disable all of them?

@philinux: PC specifications is irrelevant. I would like to disable the effects on my computer which is more than capable of having all visual effects at maximum. I just don't want visual effects as I find them annoying, I want my computer to do everything right away, I don't want a 1/4 second delay to watch my window minimizing or anything.

So you do know, I want to disable the visuals on two computers I now have running Ubuntu 9.04.

The first is my own computer, which in Windows I can play Crysis at near maximum settings and high fps. I want the visuals disabled simply because I find them annoying, and useless. I use Windows Classic theme in XP with all visuals disabled.

Now the other computer is my parents computer, it could benifit by the effects being disabled. They're running a 2Ghz Pentium 4, with 1GB of ram, Nvidia 5700. But Ubuntu runs fine, they're just the same as me, and they don't want the pointless visuals that only take up memory, and delay things (like why would you want to watch your window minimizing).

edit: @NightwishFan: Thanks, I'll try that.

---

### Post by NightwishFan on 2009-06-05
You can also configure compiz to snappier. It is fun to have effects, and if you have a standard (non-integrated) video card they should perform great. The only thing you have to watch is OpenGL applications, which may be a bit slower with compositing, just disable compiz when you run these applications. I have mine set up to use a keyboard command to disable/enable.

---

### Post by yaroto98 on 2009-06-05
boot to console.

---

### Post by philinux on 2009-06-05
I agree the wait to see concentric rectangles is damned annoying. That why I prefer compiz, I think it's quicker but could be an illusion.

---

### Post by ubuntuforums on 2009-06-05
@philinux: Yeah, well, gonna do some experimenting with different settings.

@yaroto98: Go away.

---

### Post by philinux on 2009-06-05
I know in your first post that you dont want xubuntu, but how about a different window manager. You can have more than one and choose the option at login.

---

### Post by ubuntuforums on 2009-06-05
I didn't know about different window managers, I'll have to look that up. Thanks.

---

### Post by NightwishFan on 2009-06-06
Metacity is a very mininal window manager, and it integrates with GNOME. It is the default, without Compiz.

If you install compizconfig-settings-manager or simple-ccsm you can edit compiz settings, it seems hard at first but it is not, you can always just reset individual settings if you misconfigure something.

You can use ICEWM or another WM with GNOME by adding example: icewm --replace to GNOME autostarted applications.

Good luck and have fun!

---

### Post by philinux on 2009-06-06
At last metacity without the minimise animation.

[http://linux.derkeiler.com/Mailing-Lists/Debian/2005-01/1113.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-01/1113.html)

Also this:-
Reduced resources for Metacity also hides window contents when moving. But turning on accessibility fixes that:
'desktop/gnome/interface/accessibility'

---

