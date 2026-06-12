---
title: "ATI Graphics card problem"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by SINZAR on 2008-12-11
I'm using an ATI Radeon 9200 Pro with Hardy Heron and I'm stuck with the limited resolution of 1024 x 768. I've been using google and the search function and come up with some topics that gave me a base to start with but I haven't gotten anywhere. 

Here's my xorg.conf

> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection


and here's my lshw -C Display output

>  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8


The last thing I tried was running sudo dpkg-reconfigure xserver-xorg which didn't help. The only thing it changed was adding "UseFBDev"              "true" to the xorg.conf. Previously under configured video device I had a blank line which is different from other peoples xorg.conf's with similar cards. I've tried changing it in the hidden Screens and Graphics option but 1024 x 768 is still the highest it will go.

I have the machine hooked up to my home theater system/lcd tv so the resolution I have isn't fitting as it stretches the video.

---

### Post by Titan8990 on 2008-12-11
Was there not option to select ATI in dpkg-reconfigure xerver-xorg?


The open source drivers is all you will have to work with as the proprietary ATI drivers don't support cards that old.

---

### Post by SINZAR on 2008-12-11
There wasn't really any video options in the depkg-reconfigure xserver-xorg except for the first question which asked if I wanted the kernel to help out with something and I choose yes.

---

### Post by Titan8990 on 2008-12-11
It should be the next option after that. The default is Vesa.

---

### Post by SINZAR on 2008-12-11
I went through and tried it again, but after the kernel question it moves on to keyboard questions. Nothing else relating to video set up.

---

### Post by SINZAR on 2008-12-12
Any other suggestions?

---

### Post by overdrank on 2008-12-12
> **SINZAR said:**
> Any other suggestions?

Hi have you tried using the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by Mucho on 2008-12-12
go to ATI site.. 
and download newest driver for your card and isntall that

---

### Post by SINZAR on 2008-12-12
> **overdrank said:**
> Hi have you tried using the command ```
gksu displayconfig-gtk
``` and adjust there.

Tried it but with no luck.

After messing around with it some more I really messed things up. I reverted back to my original partially working xorg.conf so I'm back at square one. 

If I can't get a solution here I'm going to have to resort to getting another video card or abandoning ubuntu for this project. I don't want to do either. I know other people have gotten this working so I don't see a reason why I can't either. Any other ideas?

---

### Post by tgalati4 on 2008-12-12
I didn't see a device section:

Section "Device"
  BoardName    "3D Rage Pro AGP 1X/2X"
  Driver       "ati"
  Identifier   "Device[0]"
  Option       "AccelMethod" "XAA"
  Option       "XaaNoPixmapCache" "on"
  Screen       0
  VendorName   "ATI"
EndSection

Of course, replace "ati" with "radeon"

---

### Post by overdrank on 2008-12-12
> **SINZAR said:**
> Tried it but with no luck.

After messing around with it some more I really messed things up. I reverted back to my original partially working xorg.conf so I'm back at square one. 

If I can't get a solution here I'm going to have to resort to getting another video card or abandoning ubuntu for this project. I don't want to do either. I know other people have gotten this working so I don't see a reason why I can't either. Any other ideas?

There is also the xfix option when booting into recovery mode. This can correct graphics issues

---

### Post by SINZAR on 2008-12-13
> **tgalati4 said:**
> I didn't see a device section:

Section "Device"
  BoardName    "3D Rage Pro AGP 1X/2X"
  Driver       "ati"
  Identifier   "Device[0]"
  Option       "AccelMethod" "XAA"
  Option       "XaaNoPixmapCache" "on"
  Screen       0
  VendorName   "ATI"
EndSection

Of course, replace "ati" with "radeon"

I tried adding it in but it didn't seem to have any effect after restart.

---

### Post by b0b138 on 2008-12-13
Assuming everything works correctly booted from the live cd, copy the xorg.conf from the live section to your install.

---

### Post by SINZAR on 2008-12-14
Good thinking I'll have to give that a try

---

