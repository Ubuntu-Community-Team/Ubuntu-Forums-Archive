---
title: "ATI Display Woes"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by rtsheffy on 2010-03-23
[LEFT]Ok here"s a Texas size pain in the neck for you. I have an IBM a22p Thinkpad laptop. The ATI video card is giving me, and my Pennsylvania copilot, the blues. I have the triple screen issue and after reading all the fixes I can't find one that works. When I plug in an external 30inch monitor to it, the resolution goes up to 1600x1200 and it works fine on the laptop screen. But turn it back down one notch and it starts doing the crazy.  Right now to view the screen I have to boot with the external and when it loads the password screen the external shuts off by itself the on board screen turns on again. After that I can unplug the external and run with the high resolution.  I've tried rewriting the display properties with no luck. If I let it boot without the external then it doesn't give the option to increase the resolution past 800x600 and that doesn't work. Who has the fix?
[/LEFT]

---

### Post by sandyd on 2010-03-23
> **rtsheffy said:**
> [LEFT]Ok here"s a Texas size pain in the neck for you. I have an IBM a22p Thinkpad laptop. The ATI video card is giving me, and my Pennsylvania copilot, the blues. I have the triple screen issue and after reading all the fixes I can't find one that works. When I plug in an external 30inch monitor to it, the resolution goes up to 1600x1200 and it works fine on the laptop screen. But turn it back down one notch and it starts doing the crazy.  Right now to view the screen I have to boot with the external and when it loads the password screen the external shuts off by itself the on board screen turns on again. After that I can unplug the external and run with the high resolution.  I've tried rewriting the display properties with no luck. If I let it boot without the external then it doesn't give the option to increase the resolution past 800x600 and that doesn't work. Who has the fix?
[/LEFT]install ahrdware drivers from System -> Administration -> hardware drivers.

---

### Post by NightwishFan on 2010-03-23
When you get the chance, on the machine in question. Open a terminal and run this command. Post the output here using CODE tags.

```
sudo lshw -C display
```

---

### Post by rtsheffy on 2010-03-23
It says "no proprietary drivers are in use on this system". This is a new in stall so???

---

### Post by rtsheffy on 2010-03-23
*-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage Mobility M3 AGP 2x
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:f8000000-fbffffff(prefetchable) ioport:2000(size=256) memory:f0200000-f0203fff memory:f0220000-f023ffff(prefetchable)


This what you are looking for?

---

### Post by sandyd on 2010-03-23
```

sudo apt-get remove --purge xorg-driver-fglrx
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
gksudo gedit /etc/X11/xorg.conf
```
copy and paste (replaceing everything if the file already has something in it)
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver "ati"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
#Ive added the below stuff to assist you in setting your screen resolution if necessaary
#"depth" deals with the monitor depth. "modes" deals w/ the resolution.
#Remove the hashtags from the front of everything below this line to activate.
   
        #SubSection "Display"
        #        Depth           24
        #        Modes           "1440x900"
        #EndSubSection
EndSection


```

---

### Post by rtsheffy on 2010-03-24
Still the same triple screen

---

### Post by rtsheffy on 2010-03-24
Iused the subs and it loaded with display low graphics errors but I loaded it anyway and its working but I need to set itas default. How?

---

### Post by clhsharky on 2010-03-24
HI

This is very old technology. I don't believe 8MB memory will span 30" display at that res.

Last MS driver Release Date:	2000-08-31

[http://www.thinkwiki.org/wiki/ATI_Rage_Mobility_M3](http://www.thinkwiki.org/wiki/ATI_Rage_Mobility_M3)

> ATI Rage Mobility M3 or 128
This is a ATI video adapter
M3 has 8MB, 128 has 16MB
Features
Chipset: ATI Rage 128
PCI ID: 1002:4c46
AGP 2X
8 or 16MB SGRAM video memory
Linux X.Org driver
This adapter is supported by recent versions of the 'r128' driver as found in X.Org.
ThinkPad LCD
Display on the internal LCD works as long as you set the monitor settings correctly. DPMS may or may not detect the proper settings.
External VGA port
Works fine. Dualhead is supported in Xorg 6.9 and higher.
SVideo port
The SVideo port should be supported by the current Xorg radeon driver.
Please read How to get TV-Out working on ATI graphic cards on how to set it up.
DVI port
??
Proprietary ATI driver
This chip is not supported by the proprietary ATI driver
Linux kernel Framebuffer driver
This chip is supported by the generic drivers vesafb and uvesafb. It is also listed as supported by aty128fb but reports suggest otherwise [1].

Sharky

---

### Post by rtsheffy on 2010-03-24
This is where I received my info from that helped me.
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by clhsharky on 2010-03-24
Hi

I'm glad that you got some help. Don't expect to much from your card, it is older than anything on that page. Be happy it works.


Sharky

---

### Post by rtsheffy on 2010-03-24
The difference is the color depth.
my laptop is only 16 color for some reason so that solved it for me. Hooray for Forum Help!!!!!!!!!!!

Section "Device"
        Identifier      "Generic Video Device"
        Driver         "ati"
      
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
    HorizSync    28-72
    VertRefresh    43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
    Device          "Generic Video Device"
    Monitor         "Generic Monitor"
        
    DefaultDepth    16
   
        SubSection "Display"
                Depth           16
                Modes          "1600x1200" "1440x900" "1024x768"
        EndSubSection
EndSection



Thanks Guys

---

### Post by rtsheffy on 2010-03-24
Don't need much. but it work decent enough with windows, I hope it works here. Any way to change the card?

---

### Post by Mark Phelps on 2010-03-24
> **rtsheffy said:**
> Don't need much. but it work decent enough with windows, I hope it works here. 
MS Windows uses totally different video drivers from Linux; thus, "working in windows" has absolutely nothing to do with whether or not it will work in any Linux distro.

---

