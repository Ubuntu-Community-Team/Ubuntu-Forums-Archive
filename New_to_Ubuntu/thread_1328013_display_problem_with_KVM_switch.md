---
title: "display problem with KVM switch"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by jakesanderson on 2009-11-16
I recently installed Ubuntu 9.10 on my old Dell Dimension 4550 PC, with this ATI video card:
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

When I run with the monitor directly connected to the video card, it gets autodetected just fine, and I can set a resolution of 1600x1200.  

When I go through my KVM switch, however, it doesn't auto-detect correctly, and the best res I can get to is 800x600.  

I've perused the threads here, and tried a number of suggestions.  I created an xorg.conf file that seems to work (I can confirm that it is being used, rather than autodetect).  However, when I put the KVM switch back in the mix, I get a reduced set of display resolution options again with xrandr.  It seems like autodetect is still happening, and overriding the xorg.conf settings?  Is there a way to disable the auto-detect completely?  Or maybe there is a problem with my xorg.conf.  Do I need a specific ATI driver?

Here's the xorg.conf I used:

Section "Monitor"
Identifier "Generic Monitor"
Modelname "Custom 1"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
Modeline "1600x1200@60"  115.20  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device ""
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1600x1200@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

Thanks in advance for any suggestions,

Jake

---

### Post by garvinrick4 on 2009-11-16
jakesanderson  I would very much like to discuss KVM switches with you when you
get you problem figured out.
Short on room and would indeed like to use KVM switch and have some questions.
One cpu would have to be Windows for my Pops he is 80 and Linux makes him nervous.
He deserves what ever he wants.
I would like to have seperate Linux box, Windows/Ubuntu box I have now. I believe to
ask who is using, better than a google.  Thanks Hope you get someone to come along and
right your ship.

---

### Post by ukripper on 2009-11-16
As it is 9.10 there is no need to have xorg.conf, Can you move your xorg.conf to xorg.conf_backup and reboot with KVM intact. Xserver will detect resolution settings and other settings from dbus.

---

### Post by laidback on 2009-11-16
Ukripper, just in case this is of interest. I've used a KVM for some years now. Switching between a Windows box and my Ubuntu pc. I use 1280x1024 on both systems and my Belkin KVM allows me to switch between the 2 at will. If I switch the Ubuntu pc on after the Windows box has been shut down I'll probably have to press the selection button on top of the KVM as it doesn't correctly detect the new source, however this isn't a major problem for me so I haven't worried about it. There is keystroke switching too, but I've forgotten the keystrokes so don't both with it.

Kindest Regards

---

### Post by ukripper on 2009-11-16
> **laidback said:**
> Ukripper, just in case this is of interest. I've used a KVM for some years now. Switching between a Windows box and my Ubuntu pc. I use 1280x1024 on both systems and my Belkin KVM allows me to switch between the 2 at will. If I switch the Ubuntu pc on after the Windows box has been shut down I'll probably have to press the selection button on top of the KVM as it doesn't correctly detect the new source, however this isn't a major problem for me so I haven't worried about it. There is keystroke switching too, but I've forgotten the keystrokes so don't both with it.

Kindest Regards

Even I use belkin kvm 2 ports and other unbranded 4 ports and both work flawlessly under jaunty desktops and hardy server.

Below is the toggle keystrokes you might need for belkin kvm to toggle between different switch:
> scroll lock twice then up arrow
scroll lock twice then down arrow 

---

### Post by laidback on 2009-11-16
Ukripper,

Thanks for the info.

---

### Post by ukripper on 2009-11-16
> **laidback said:**
> Ukripper,

Thanks for the info.

No worries mate. 

Not sure if OP's problem has sorted out.

---

### Post by jakesanderson on 2009-11-18
Thanks for the replies.  Unfortunately, none of them really address the problem, unless you're telling me I should be using a different desktop or server, or perhaps upgrade my KVM?   It sounds like most of the respondents have KVM switches that auto-detect just fine.  In my case, my monitor auto-detects fine when directly connected, to 1600x1200 res, but with the KVM switch in the path, 800x600 is the max res with autodetect.  I tried adding an xorg.conf, which according to the man page would take precedence over the auto-detect.  Unfortunately, it seems that the auto-detect is still overriding my xorg.conf settings.  

The question is, how to avoid this?  I know my monitor will function at this res through the KVM switch, because it works with Windows.  Can I disable the auto-detect mechanism?  I don't need it, honestly...

---

### Post by the.phantom on 2009-11-18
just a hunch, it worked for me on my "no name" auto/manual kvm


switch a and b around
mine calls default A and it dif fix my trouble
and i have resolution set the same on both systems on mt monitor

can't hurt to try it

---

### Post by jakesanderson on 2009-11-18
I tried the swap A and B suggestion.  Sadly, no luck.  I will keep trying.

---

### Post by QIII on 2009-11-18
If you can bang your head under the desk a few times while connecting each machine to the monitor in turn without the KVM switch in the mix, then you have probably reduced the likely causes to one of two things: the hardware itself or the way that each OS is communicating with it.

I didn't spot the make and model of the KVM switch, but it might be worth your while to google it and see if others are having similar issues with that particular model on other OSs.

Launchpad might also be enlightening.

I have a KVM switch that goes fine back and forth between two machines when I have Ubuntu running on each or Windows running on each, but is shifted slightly off center on one or the other when I have Windows running on one and Ubuntu on another.  A minor irritation, but easily addressed by pressing the auto adjust feature on my monitor.

---

