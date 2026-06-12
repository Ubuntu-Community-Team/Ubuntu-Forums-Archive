---
title: "resolution issues"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Mortdread on 2011-03-07
I've tried what others have said with using the terminal, but whatever i try i can NOT get my resolution and 1280x1024 where its supposed to be at, its just 800x600 and 640x480, which is giant and beyond giant, theres also a pink box at the top left displaying "Unknown" and you cant click through it, my monitor is a F1703 (old VGA)

(I ran Ubuntu on my old, and very bad computer before, same monitor, no issues)

---

### Post by asuastrophysics on 2011-03-07
Hello and welcome to Ubuntu Forums! Please post the output of 
```
lspci | grep vga
```
from your terminal.

Also, which version of Ubuntu are you currently using?

---

### Post by Mortdread on 2011-03-07
> **asuastrophysics said:**
> Hello and welcome to Ubuntu Forums! Please post the output of 
```
lspci | grep vga
```from your terminal.

Also, which version of Ubuntu are you currently using?

that did nothing, just like everything else, but im using 10.10

---

### Post by matt_symes on 2011-03-07
Hi

```
lspci | grep -i vga
```

or

```
lspci | grep VGA
```

Kind regards

---

### Post by Mortdread on 2011-03-07
> **matt_symes said:**
> Hi

```
lspci | grep -i vga
```or

```
lspci | grep VGA
```Kind regards


got this message, nothing else
 "01:00.0 VGA compatible controller: nVidia Corporation Device 0de1 (rev a1)"

---

### Post by matt_symes on 2011-03-07
Hi

You might want to post the output of your xorg file as well (if you have one). 

```
cat /etc/X11/xorg.conf
```

What drivers do you have installed for your card ?

Kind regards

---

### Post by asuastrophysics on 2011-03-07
OP: After you post the output of xorg.conf, can you go to System -> Administration -> Hardware Drivers

Click on "Hardware Drivers" and could you post a screenshot of that window please?

---

### Post by jda8818 on 2011-03-07
Mortdread:

10.10 installations try to detect your monitor type at first install, but if that process fails everything defaults to 800x600 @ 60 Hz.

In order to provide this missing monitor information you need to create an xorg.conf (a configuration file) and place it in the /etc/X11/ directory where it will be read and acted upon at boot.  Recent Ubuntu releases just don't include this file at all by default.

Here's my 10.10 xorg.conf file:

```
Section "Device"
    Identifier    "ATI Rage PRO 128"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "ViewsonicP815"
    HorizSync       30-115
    VertRefresh     50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "ViewsonicP815"
    Device        "ATI Rage PRO 128"
EndSection
```Don't copy my file verbatim!  

The identifiers (names) of the monitor and video card (Device) are not important.  They just must match the identifiers in the "Screen" Section.  The "vesa" driver is a good place to start.

There are only two lines in this file that really matter, those are the "HorizSync" line and the "VertRefresh" line.  The HorizSync parameter will be in units of kHz (kiloHertz) and the VertRefresh parameter will be in units of Hz (Hertz)  You would need to find out what those parameters are for your monitor and put them in the file. Just like above, with a dash between the upper and lower bounds.  Again, don't just copy my values, because my monitor is capable of very high refresh rates and it is not a good idea to drive your monitor at rate above which it is capable.

The system hopefully will absorb your new values and give you resolutions greater than 800x600.  In my case I max out at 1280x1024 and 85 Hz, but I'll probably try to tweak this file for greater resolutions when I have the energy.  There are all sorts of parameters to try, you can just google "xorg.conf" and one of the results will be the man page for the subject which will either keep you busy for a long time or put you to sleep.

If there is an error in the file somewhere, your machine will hang on reboot.  Hold down the shift key at the next boot, drop to a root terminal, navigate to the /etc/X11/ directory and remove (rm) the xorg.conf file, reboot, try again.

good luck!

JA

---

### Post by asuastrophysics on 2011-03-17
> **Mortdread said:**
> that did nothing, just like everything else, but im using 10.10

Terminal is very very picky, and I'm a bit rusty on the CLI. I do apologize for giving you the wrong command.

---

