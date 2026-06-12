---
title: "Changing color depth"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Anuovis on 2011-03-06
Hello,
I want to run one app that needs 16-bit color depth but there is no GUI in Gnome to do that.

Since Gnome has been annoying as hell with its philosophy of "simplicity", I wouldn't mind switching to KDE if it has an easy way to switch between the color depths. Is it possible?

Otherwise, it probably means creating an xorg.conf but I already broke my system once with that and I'm really reluctant to try it again. Could anyone point to a really step-by-step guide that has clear instructions how to roll back in case things go wrong?

I am afraid I might need to reinstall my whole system since I am fairly new to Ubuntu and don't know how to recover if things go bad.

Any help and/or alternatives how to accomplish this would be really appreciated.

---

### Post by stoneage on 2011-03-06
Which application?

Maybe I don't understand you, but surely you are already viewing 24 bit colour?

If you want to reduce it try, System -> Preferences -> Display, or the settings for your graphics drivers, System -> Administration -> NVIDIA X Server Settings (Display Configuration - X Screen tab), or the equivalent.

---

### Post by Anuovis on 2011-03-06
Sorry, should have provided some more info.

It's *Pharaoh*, a rather old game. I tried running in through Wine and on virtual Win XP, it crashes on both soon after launching. A very similar game by another company runs just fine and it uses 32-bit resolutions. I also found another user complaining how window manager can't handle 16-bit color and crashes. Figured I could have the same issue.

My card is ATI x1400, running on default open drivers.

Even if this game doesn't work, there is a good chance I will still need to deal with color depth changes in the future, so it might be taken as a more general question on how to accomplish that.

---

### Post by stoneage on 2011-03-06
I know this is old, but maybe there is something in it for you:-
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=351&iTestingId=58170](http://appdb.winehq.org/objectManager.php?sClass=version&iId=351&iTestingId=58170)

I think it is more likely something other than colour depth is the problem, though it is only a guess. 

:)

---

### Post by Anuovis on 2011-03-07
Thanks.

Yes, I checked that. And I don't know how but I managed to run that game without crashing on virtual machine, after disabling guest addons.

But the problem kind of remains, I still don't know what do do with color depth. Maybe I should go try one of the guides after learning a bit more about system recovery.

---

### Post by vanquishedangel on 2011-06-26
Hi, I did this on an old laptop to improve speed and very limited memory.  I added a file in /usr/share/X11/xorg.conf.d named xorg.conf and this is its contence:

Section "Screen"
        Identifier "default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth 16
EndSection

Hope this works for you I am using Lubuntu natty

Note that the post changed in its display after submitting,  the words Identifier, Device, Monitor, and DefaultDepth are inline with the first " in "Screen" and the words Section and EndSection are at the edge. You may also specify the number value for the color depth of your choice ie: 24, 16, 8, etc.

---

