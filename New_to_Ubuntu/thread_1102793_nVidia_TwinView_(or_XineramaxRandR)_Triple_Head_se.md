---
title: "nVidia TwinView (or Xinerama/xRandR) Triple Head setup - Help?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Sootah on 2009-03-22
Alrighty, I have X up and running; as evidenced by the fact that I am posting this from my secondary monitor in FireFox while booted to Ubuntu. For a short description of my trials getting X to work with the nVidia drivers and my dual video card setup, you can visit [here](http://ubuntuforums.org/showthread.php?t=1101980).

So, what I need to do now is get my third display up and running either in TwinView or something similar. I do **not** want to use my third monitor as a seperate X display as this screws with the way the other two monitors behaves, and the whole reason I have three screens is so that I can drag applications to all of them.

I have two Samsung 216BWs attached to my nVidia 8800 GTS, and my Samsung 46" LCD TV attached to my older nVidia 7800 GTX. As stated in my previous thread, I am able to get the third monitor working as a seperate X display, but this is unacceptable as I need to all to be in TwinView or something similar.

Any ideas on how to get this running? I shall attach my xorg.conf file and a picture of my display setup shortly.

---

### Post by Sootah on 2009-03-22
Attached.

---

### Post by James_Lochhead on 2009-03-22
Good luck with that, I can barely get 2 working with separate X servers. 

Every time I try TwinView the screen goes bananas and paints random black and white lines up and down my screen then refuses to generate a new xorg.conf till I try for the billionth time.

---

### Post by Sootah on 2009-03-22
Looks like Windows utterly wins on this one. For all the talk about how "superior" Linux is, it only took me 5 minutes to get that config up and running in Vista.

I've spent the past six hours trying to get a simple display setup running with more xorg.conf variants than I care to think about. The ONLY way I can get the third display to even SHOW anything is to set them all as seperate X screens, and even then only the primary display will actually run an application.

Dual displays was *somewhat* simple to setup, once I knew what I was doing; but even that took a bit.

So, seriously, how does this beat Windows? All the "just works" talk seems like a fair amount of BS at the moment - and I've not even bothered to look for drivers for my sound card yet..

---

### Post by James_Lochhead on 2009-03-22
A lot of stuff does just work. Few people have two screen like us so not many people run into this problem... so it is not very significant to users as a whole.

That leaves the notorious problem of sound. It does just work for a lot of people, however if there are sound problems I have found you can generally fix them by reading the forums and asking.

To get mine working I just had to add one line to the end of a file.

I think a lot of the sound problems are caused by manufacturers not adhering to standards. 

As for NVidia... Linux is only a small portion of the market and I doubt fixing drivers for us Linux users is high up their priority list (although they should still be thanked for releasing reasonable drivers - unlike ATI). I think a lot problems would be resolved if we had a functional open source nvidia driver that allowed 3D effects.

---

### Post by James_Lochhead on 2009-03-22
Oh and I have to mention that for me doing a clean install of Ubuntu and getting everything working takes me about 3rd of the time it takes to do the same for Vista.

Most of the time spent wading through badly made manufacturer websites looking for drivers tucked away in a corner... and my laptop is only 6 months old.

---

### Post by Sootah on 2009-03-22
True - Most of it does just work right off the bat, my post last night was out of frustration. My main issue at the moment does stem around exactly what you said though; the things I'm trying to do just aren't mainstream enough to be supported. I enjoy the fact that I can manually edit config files and all that to get what I want most of the time, but at the same time it's insanely frustrating to have to experiment for hours on end to do that.

I'd like to run it as my OS as I need to become more familiar with how it all works as we're going to switch our servers over to Linux here in a while. At the same time, unless I can get X, Gnome, Ubuntu, etc to do what I want it to then I'm not going to use it.

---

### Post by xpod on 2009-03-22
I dont have 3 screens but all i have to do to get TwinView working for my 19 & 22" screens is stick the hightlighted text into the screen section of my xorg.conf.
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
       **Option          "twinview"**
	DefaultDepth	24
EndSection
``` 

I can usually do it through the Nvidia settings utility too but occasionally it has hissy fits.

---

### Post by Sootah on 2009-03-22
I can get my two main monitors working fine, it's the third that I'm having issues with.

---

### Post by browneej on 2010-01-14
I know this was an old post, but here goes for others working on this.  I was able to get a three-head / triple head setup working (nvidia, Xinerama), with two heads in portrait mode for easy reading.  Used Ubuntu 9.04 and 9.10.  See attached xorg.conf.

CONS:
1) Xinerama--required Xinerama on all three screens, only one screen had decent glxgears performance, the other two were horrible. Got tearing in scrolling firefox on any but the first screen.  Third screen being bad would make sense, since I was using the motherboard nvidia 750 output, but the second was the second output of an nvidia 8800 (although in 1050x1650 portrait mode).  Don't remember too well anymore, but I don't think I had success using twinview for the first two displays (one in landscape, one in portrait).
 
2) Compiz--totally unsupported, had to use basic graphics, no fancy wabbling windows, nice Cairo-dock, seamless VirtualBox, etc.  

3) RandR/XRandR (?)--always told me the driver was missing when I opened a window from terminal, though normal window operations seemed to work.  Never did dynamic configurations, though.

4) Unstable (?)--don't know if this was the fault of the X server or something else, but occasionally the whole system would lock up.  

PROS:
1) Able to drag a window to any screen.

2) Windows would automatically maximize to one screen only.

3) Gnome panel stayed on one screen.

4) Most recent Cairo-dock could be pegged to the bottom of any screen (had to use the PPA version)

Hope this helps.

---

### Post by audiomick on 2010-01-14
Thanks for that browneej.

I would like to rotate one of my two monitors. Your xorg.conf might contain the clue I need:D

---

### Post by jstapels on 2010-07-08
I wanted to add that I went through the exact same problems and ended up with the exact same solution (Xinerama on all three monitors). The performance is horrible so I tried using Twinview + Xinerama because I heard that it makes things a little better. However, when I do that it appears that the nVidia driver doesn't advertise the individual sizes of the Twinview'd screens and I'm stuck with a gnome-panel stretching across and windows maximizing across both.

xRandR 1.3 never ended up delivering support for multiple GPUs and it doesn't look like 1.4 will have that support either.

My only hope at this point is that nVidia will find a way to offer a TripleView for linux as part of their 3D Vision driver support, although it's probably unlikely this would be supported back to 8800GT series.

If anyone has come across a solid way to use three monitors in linux (w/ two gpus), please share.

---

### Post by phrac on 2011-02-12
Here's my xorg.conf file generated by nvidia-settings.  This is a triple head setup with two different nvidia cards, 2 22" monitors and 1 24" monitor.
Screen0 is my 24" monitor and to the left and right are the 22" monitors.  I don't run gnome or KDE but it works great in awesome wm.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1680 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC 2436"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
nvidia-auto-select +0+0"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

