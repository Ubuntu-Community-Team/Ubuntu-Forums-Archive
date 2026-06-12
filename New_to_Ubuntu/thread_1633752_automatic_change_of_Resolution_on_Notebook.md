---
title: "automatic change of Resolution on Notebook"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Schwarzie on 2010-11-29
Hello everbody.

I have no idea where to place this question, but since im a complete Linux Beginner i write it down here :D


Recently i installed Linux Mint (based on Ubuntu 10.10) on my Lenovo R61i (1.66 Core2Duo, 2GB Ram (soon 4GB) Nvidia NV140M).
This is paralell to my Windows 7.

I have 3 states of use for my Notebook. Mobile. In Dockingstation using my 24" Screen and in Dockingstation using the Notebook Screen while using the 24" for my other Computer (via KVM Switch)

In mobile use everything is fine.

For the Dockingstation use windows 7 automatically switches the Resolutions to the active Display and deactivates the Notebook Screen when the display is closed.

Linux always uses the correct Display resolutions, but uses a Virtual Screen to emulate a 1920x1200 Screen even on my Desktop. And Linux doesnt recognize when i close my Notebook and its not possible to clone the Screens and just use the highest available resolution. (If i have the Notebook Screen AND the 24" in use at the same time Windows gives me a cloned view with a lower Resolution on my Notebook, and switched the 24" to its native resolution once i close the Notebooks screen.)

What do i have to do to get to the desired result?

And when someone already reads through this Wall of text: Is there a possibility to Sync the Windows and the Linux Version of Firefox?

---

### Post by Schwarzie on 2010-11-30
Nobody has an Idea how to solve this? Or was my explanation garbadge?

---

### Post by theluddite on 2010-11-30
> **Schwarzie said:**
> Nobody has an Idea how to solve this? Or was my explanation garbadge?

Did you try installing the proprietary driver?  I believe it's under System>Restricted Drivers.  I'm not sure which video card you have, but I've found this to be the simplest, and most n00b friendly fix, depending on your card.

If that doesn't work, you may need to experiment with /etc/X11/xorg.conf, which is definitely not n00b-proof.  I'd recommend trying the easy fixes first before you mess about with xorg.conf.

For your second question, I don't believe there is.  I have my firefoxes synched amongst different computer running linux by using Dropbox, but since the profiles are stored in different paths under Windows and Linux, I expect you can't have one common profile for use by different platforms.

---

### Post by Schwarzie on 2010-12-02
> **theluddite said:**
> Did you try installing the proprietary driver?  I believe it's under System>Restricted Drivers.  I'm not sure which video card you have, but I've found this to be the simplest, and most n00b friendly fix, depending on your card.

If that doesn't work, you may need to experiment with /etc/X11/xorg.conf, which is definitely not n00b-proof.  I'd recommend trying the easy fixes first before you mess about with xorg.conf.
Yes, im using the proprietary Driver. This distribution asked my directly after the first start if i want to Download and install it.
Im using a Nvidia NVS140M

And the problem is more Linux not detecting that the big Screen is no longer active/connected OR that my Notebook is closed.

EDITH:
#######XORG.CONF################
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
###################################

---

