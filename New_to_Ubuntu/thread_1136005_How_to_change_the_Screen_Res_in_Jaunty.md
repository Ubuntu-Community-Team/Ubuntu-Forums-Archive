---
title: "How to change the Screen Res in Jaunty"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by kc5hwb on 2009-04-24
I have searched this forum and google.. and can't find anything that works for changing the screen res in Jaunty.  Mine is set to 800x600 and I can't figure out how to get it higher.  I was previously running Hardy Heron and I had my res set really high, but I don't remember how I did that.  My vid card is a Nvidia GeForce 6200

---

### Post by Sub101 on 2009-04-24
Should be: System==>Preferences==>Display

If you use a nvidia card it will then prompt, do you want to use the software for your card. I do not know the next screen if you do not have a Nvidia. 

I believe one of the areas which was to be improved in jaunty was to do with display management.

EDIT: Ive just reread and see your using an Nvidia. Once in the Nvidia control panel select, "X Server Display Configuration" and at the bottom right is "Resolution"

---

### Post by Didius Falco on 2009-04-24
System/Preferences/Display.

---

### Post by kc5hwb on 2009-04-24
System/Preferences/Display = only have a res up to 800x600...I need something higher than this, which is the reason for my post.

Sub101, where is this control panel?  I got no prompt.

---

### Post by Sub101 on 2009-04-24
System ==> Admin ==> X Server Settings.

Im assuming it is a generic control panel for all nvidia drivers. I may be wrong.

---

### Post by kc5hwb on 2009-04-24
> **Sub101 said:**
> System ==> Admin ==> X Server Settings.

Im assuming it is a generic control panel for all nvidia drivers. I may be wrong.

I do not have this option

---

### Post by presence1960 on 2009-04-24
> **kc5hwb said:**
> I have searched this forum and google.. and can't find anything that works for changing the screen res in Jaunty.  Mine is set to 800x600 and I can't figure out how to get it higher.  I was previously running Hardy Heron and I had my res set really high, but I don't remember how I did that.  My vid card is a Nvidia GeForce 6200

I had to use nvidia-settings to get all available res's for my acer 19" WS. If it isn't installed use Synaptic to install nvidia-settings or ```
sudo apt-get install nvidia-settings
``` in terminal. It will be under System>Administration> Nvidia X Server Settings.

This is of course assuming you have the proprietary driver installed.

---

### Post by kc5hwb on 2009-04-24
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

That is what I get after installing Nvidia...

---

### Post by kc5hwb on 2009-04-25
anyone?

---

### Post by kc5hwb on 2009-04-25
I found an old thread of mine where I asked this question before, several versions back, and the answer was to stop GDM and run this command:

```
sudo dpkg-reconfigure xserver-xorg
```

However, this doesn't work anymore.  I seem to recall that it didn't on the last couple of versions either, but I cannot remember what I used to change the resolution before.

---

### Post by kimharding on 2009-04-25
I have wasted over a day in trying to resolve this issue, my laptop uses a Trident Video Accelerator CyberBlade XP Ai1  (Trident CyberALADDIN-T (M1644) chipset), this is not exactly cutting edge hardware and yet Ubuntu fails to support it. No wonder people want to use XP instead. I want to use Ubuntu, because when it works, it works well, but that is when it works. Can we please have a resolution to this problem soon!

---

### Post by kc5hwb on 2009-04-25
Wow....What a simple fix. Here I was looking to edit some text file somewhere, like I have on previous versions, and all I had to do was go to System->Admin->Hardware Drivers and install the latest version for my Nvidia card, then reboot. Works perfectly now, thanks!

---

### Post by kimharding on 2009-10-30
> **kc5hwb said:**
> Wow....What a simple fix. Here I was looking to edit some text file somewhere, like I have on previous versions, and all I had to do was go to System->Admin->Hardware Drivers and install the latest version for my Nvidia card, then reboot. Works perfectly now, thanks!

Sadly when I tried that all I got was a driver of a software modem, which isn't much use...

I have just started to experiment with Karmic and I am coming up against the same problem all over again, not happy. :(

---

### Post by OscarFoxtrot on 2009-10-30
> **kc5hwb said:**
> Wow....What a simple fix. Here I was looking to edit some text file somewhere, like I have on previous versions, and all I had to do was go to System->Admin->Hardware Drivers and install the latest version for my Nvidia card, then reboot. Works perfectly now, thanks!

Well it might have worked for you but it broke my system!

---

### Post by oldrocker99 on 2009-10-30
I have the nVidia 185 drivers installed and activated for my 8600. I run nvidia-settings and, when I try to change the resolution and save the settings, I get "Failed to parse existing X config file '/etc/X11/xorg.conf'!" returned. This happens whether I run with sudo or not.

My xorg.conf file:

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Not much there, I know. Should I just try digging through the archives to find the best way to set this up? I'm currently limited to 1024x768 (MUCH better than 800x600, I know). Under Intrepid, I had 1600x1200.

Bitch, moan. Aside from that, I like Karmic just fine.

:guitar:

---

