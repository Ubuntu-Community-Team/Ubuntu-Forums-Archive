---
title: "Installing drivers for nvidia fx5200 - install fails"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by DaveInPhx on 2010-02-11
After a long story of tries and fails, here I am again, cap in hand, looking for help!

I had problems with thei PC running the onboard via card, so i finally decided to install an nvidia card out of another PC.  This card is the nvidia geforce fx5200 with 128mb of video ram, and is in an AGP socket.   I tried booting up with it, then got the hardware drivers warning about drivers available, so i went and had a look. I want to enable the desktop effects, and this card should handle it, so I click "enable" and wait.   After about 30 minutes or so i gave up and started having all sorts of problems from partially installled drivers!

I blew them all away and started again, found that hardware drivers was missing from the menu (ok, so I overdid the blow away), and got that back in again following tips from [mikewhatever]("http://ubuntuforums.org/member.php?u=160645") which got me back to square one.

Then I tried the online manual again and installing the drivers from hardware driver hangs at about 25%.   I did some more digging and found a quoted post with a full set of root terminal instructions:
```
*** Download the Nvidia drivers to /home (done)
*** in a root terminal:
sudo telinit 3
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-173.14.22-pkg1.run
*** followed the prompts through the setup and then ....
xserver
```back to square one again! I get the three little guys holding hands (ubuntu logo) and then the screen goes black and the monitor goes to sleep, no video input.

Reboot, drop to a root terminal, delete xorg.conf and reboot again, it comes up into 1024x768, nvidia drivers are disabled, but at least the system is useable!

Any suggestions would be welcomed!

---

### Post by Stunt Double on 2010-02-11
Go to Synaptic Package manager and install envyng-gtk. It will also install envyng-core. Then try Hardware Drivers again.

---

### Post by patchwork on 2010-02-11
If the screen goes blank after the usplash again, try hitting CTRL-ALT-F1 to enter console mode.  Log into the command line, and please review your /var/log/Xorg.0.log  .  It could be that your driver is working fine, but your monitor is not being properly detected.  This could cause the X server to set the resolution to a mode unusable for your monitor (the blank screen).


EDIT:  Also, if there is a problem with the driver you should see that in the log as well.

---

### Post by DaveInPhx on 2010-02-11
I tried envyng-gtk, still getting the same results. I also tried running it from the applications menu (it created a link there), nothing happens.

I went to the Synaptic manager and downloaded the 173 version, ran it and it installed successfully.  On reboot, it went back to a black screen again, so i followed the advice and examined the log. Sure enough, the monitor was causing the problem!

I made a copy of xorg.conf and then sent the original to /dev/null and rebooted. It came up in vesa mode at 1024x768. From here I edited the copy of xorg.conf and copied it back into place, adding the monitor specifications to it.  On reboot, I got a black screen yet again, and now I'm not sure what to try next.

The xorg.config is currently :- ```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Nvidia"
        Monitor         "W2053"
        DefaultDepth    24
        SubSection "Display"
                Modes        "1600x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Nvidia"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    BusID   "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "W2053"
        VendorName      "LG"
        ModelName       "W2053"
        Option          "DPMS"
        ModeLine        "1600x900" 108.000 1600 1640 1720 1800 900 901 904 1000 +hsync +vsync
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection


```

The Xorg.0.log file for that run is posted at [http://pastebin.org/90462](http://pastebin.org/90462)

Any suggestions?

---

### Post by patchwork on 2010-02-12
You've got at least two different errors going on.  The first one to look at is the agpgart issue (the edid/resolution stuff can wait until this is sorted out).  I haven't had personal experience with the AGP Gart issue, so I need to do some research.  Might be a little while before I can post anything on this....haven't forgotten about you.

---

### Post by patchwork on 2010-02-12
Ok, from [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-f.html")
try adding these lines to the "Device" Section of your xorg.conf (ModeDeug is not from that link, but will create a more verbose log)

```
Option "NvAGP" "3"
Option "ModeDebug" "True"
```

The NvAGP 3 option will attempt to load the NVAGP GART if the default AGP GART load fails

---

