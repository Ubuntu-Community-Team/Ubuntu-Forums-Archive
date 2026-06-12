---
title: "Synaptics Touchpad, gpointing-device-settings is not working"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by JMW4th on 2010-02-06
ok so, I am in Xubuntu.  

I downloaded and installed gpointing-device-settings and I've got two issues here.

First, just know that the tap-to-click is the absolute most annoying thing I can think of in regards to this computer, i absolutely hate it. it makes me want to punch my computer. i always end up clicking on pages I don't want to when I am just moving the mouse around.

anyhow, when i ran gpointing-device-settings it worked the first time, and it shut down both tap-to-click AND vertical scrolling. my touchpad has a seperate pad for vertical scrolling. I want to keep that Pad fuunctional, i just don't want the main pad to tap-click. there is no option to do this, it is either all or nothing.

now, my real problem is that while this package worked the first time, when I re-booted my computer, the settings do not appear to be working.  I checked to make sure they were still set, and they are. but apparently, gpointing-device-settings is not overriding the default Mouse settings like it is supposed to.

any clue how to fix this, so I can use my touchpad without cursing every 2 minutes?

---

### Post by JMW4th on 2010-02-06
I figured it out.

I uninstalled gpointing-device-settings and I installed the older "gsynaptics" package.

and that is doing everything I want it to.

---

### Post by Culip on 2010-10-19
I'm afraid but I don't understand what you meant . . . "gsynaptics" depends on "gpointing-device-settings", and so I can't remove "gpointng-..." and install "gsynaptics" only.

I actually have a problem too; the "circular scrolling" doesn't work on Lubuntu Maverick (but yet it works on Xubuntu Maverick.) Does anybody have an idea?

gsynaptics: v1.5.1-2
gpointing-device-settings v1.5.1-2

---

### Post by runrun395 on 2011-08-13
I FIGURED IT OUT!!! Do NOT run gpointing-device-settings as sudo!

---

