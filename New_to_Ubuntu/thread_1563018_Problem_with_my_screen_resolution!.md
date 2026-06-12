---
title: "Problem with my screen resolution!"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-08-28
When i try to set the resolution of my monitor so it fits my screen, i don't get the best one, here's what i have:
[IMG]http://dl.dropbox.com/u/5392244/Screenshot-Monitor%20Preferences.png[/IMG]

[B][COLOR=SeaGreen]lspci output:
[/COLOR][/B][COLOR=SeaGreen][COLOR=Black][PHP]mbg@mbg-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
mbg@mbg-desktop:~$ 

[/PHP][/COLOR]
[/COLOR][B][COLOR=SeaGreen]
[/COLOR][/B] [SIZE=3][COLOR=DarkGreen]X11 folder outputs: [/COLOR][/SIZE]

[PHP]
mbg@mbg-desktop:/etc/X11$ ls
app-defaults             xinit                          Xresources
cursors                  xkb                            Xsession
default-display-manager  xorg.conf-backup-100826000511  Xsession.d
fonts                    xorg.conf.failsafe             Xsession.options
rgb.txt                  Xreset                         Xwrapper.config
X                        Xreset.d


mbg@mbg-desktop:/etc/X11$ more xorg.conf.failsafe 
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


mbg@mbg-desktop:/etc/X11$ more xorg.conf-backup-100826000511 
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
mbg@mbg-desktop:/etc/X11$ [/PHP]

---

### Post by Zzl1xndd on 2010-08-28
If you have an ATI or Nvidia card, go to System > Administration > Hardware Drivers and see if anything is listed here. If so Install these drivers.

---

### Post by Smudgey on 2010-08-29
I have identical problem. Nvidia drivers installed but best resolution I can get is 1024x768 on a 4:3 monitor - I know the card and monitor support 1280x1024, which is my preferred resolution but 1024 the best it will do under linux, causing text especially to be less than sharp. 

I have in the past managed to get the better resolution, but I have no idea what I did to get it. Any help would be much appreciated. I've lost count of the number of times I've tried fixes as suggested in many threads, but so far none of them have worked.

Regards

---

### Post by realzippy on 2010-08-29
> **Smudgey said:**
> I have identical problem. Nvidia drivers installed but best resolution I can get is 1024x768 on a 4:3 monitor - I know the card and monitor support 1280x1024, which is my preferred resolution but 1024 the best it will do under linux, causing text especially to be less than sharp. 

I have in the past managed to get the better resolution, but I have no idea what I did to get it. Any help would be much appreciated. I've lost count of the number of times I've tried fixes as suggested in many threads, but so far none of them have worked.

Regards

...your problem is **not** identical at all;OP has an Intel video card.
So please open your own thread;threadnapping confuses all.
Gonna help you with your nvidia/resolution problem then...

---

### Post by cchaos on 2010-08-29
> **Smudgey said:**
> I have identical problem. Nvidia drivers installed but best resolution I can get is 1024x768 on a 4:3 monitor - I know the card and monitor support 1280x1024, which is my preferred resolution but 1024 the best it will do under linux, causing text especially to be less than sharp. 

I have in the past managed to get the better resolution, but I have no idea what I did to get it. Any help would be much appreciated. I've lost count of the number of times I've tried fixes as suggested in many threads, but so far none of them have worked.

Regards
More or less a little "niggle" I currently have with my monitor, except I dont fully know if my Nvidia card will take 1280x1024 but my monitor certainly does.

My monitor is mentioned here: [http://ubuntuforums.org/showthread.php?t=1113062](http://ubuntuforums.org/showthread.php?t=1113062) and needless to say I have now upgraded my whole pc since making that thread, and my current graphics card is a PNY GeForce 240 1024Mb (though ubuntu 9.10 is detectiong it as a 230)

EDIT: Whoops, didnt even notice the different type of graphics card

---

### Post by realzippy on 2010-08-29
> **tweakedenigma said:**
> If you have an ATI or Nvidia card, go to System > Administration > Hardware Drivers and see if anything is listed here. If so Install these drivers.

OP has an Intel video chip/card:

[I]00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
[/I]

@ MBG1987

your xorg.conf shows that you use the "fbdev" video driver.
Did you edit this manually?

---

### Post by realzippy on 2010-08-29
> **cchaos said:**
> More or less a little "niggle" I currently have with my monitor, except I dont fully know if my Nvidia card will take 1280x1024 but my monitor certainly does.

My monitor is mentioned here: [http://ubuntuforums.org/showthread.php?t=1113062](http://ubuntuforums.org/showthread.php?t=1113062) and needless to say I have now upgraded my whole pc since making that thread, and my current graphics card is a PNY GeForce 240 1024Mb (though ubuntu 9.10 is detectiong it as a 230)

EDIT: Whoops, didnt even notice the different type of graphics card

Open your own thread,then we can work out your resolution problem  ;-)

---

### Post by MBG1987 on 2010-08-29
> **realzippy said:**
> @ MBG1987

your xorg.conf shows that you use the "fbdev" video driver.
Did you edit this manually?

I don't remember, but in case i edited it, what should i do now?

best regards

---

### Post by realzippy on 2010-08-29
...rename the *xorg.conf* (so it does not "exist");and boot without.AFAIK
the inteldriver should load automatically...
If this does not help,you can create a xorg.conf that fits your hardware by typing:

```
sudo Xorg -configure
```

Then reboot...

---

### Post by Smudgey on 2010-08-29
My apologies - I was only looking at the image posted and is what I see when I try to improve my resolution ie I can't. I was under the impression this place was for absolute beginners, hence my mistake. I'll try not to bother you again.

---

### Post by realzippy on 2010-08-29
Nah,no need to apologize.Seems as I should;I did really want to say: If you open your own thread,you get more help.Sorry..

---

