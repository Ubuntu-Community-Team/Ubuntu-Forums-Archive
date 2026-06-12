---
title: "My words are upside down and backwards Please Help!"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by ElectronicTonic on 2010-11-04
[IMG]http://yfrog.com/0yscreenshotntqp[/IMG] This is my desktop after what I think was a bad/dumb video card driver update. I have Ubuntu 10.10 32bit on my Dell Inspiron 1525 laptop this the first time using Ubuntu. I have taking a Unix class like a year ago but I would appreciate it if you talked to me like I don't know what I'm doing cause I don't. I was able to get anything important off the hard drive in-case I need to reinstall Ubuntu. The problem first started when I could not access my GUI Gnome desktop at all, only the terminal. I searched the web for solutions sudo 'ed this and x-config 'ed that a few times but now my screen is all mess up. please help I could just reformat the drive and reinstall but what fun is it if I don't learn something while right? And if that is your suggestion to start new How? any guides or apts to download would be cool info too

---

### Post by HermanAB on 2010-11-04
Oh, just turn the screen around!

Search on [http://www.google.com/linux](http://www.google.com/linux) for 'xrandr'.  You can configure the screen with that.

---

### Post by anewguy on 2010-11-04
When you've fallen inside your screen and landed upside down to boot, the only thing to do is stand rightside up and type this:

!lanimret siht edisni evitpac dleh gnieb m'I !!!pleH



Dave ;)

---

### Post by wojox on 2010-11-04
Nice GIMP trick. :)

---

### Post by ElectronicTonic on 2010-11-04
> **wojox said:**
> Nice GIMP trick. :)
I wish it were a just a graphic but that's my real screen..

---

### Post by ElectronicTonic on 2010-11-04
> **anewguy said:**
> When you've fallen inside your screen and landed upside down to boot, the only thing to do is stand rightside up and type this:

!lanimret siht edisni evitpac dleh gnieb m'I !!!pleH



Dave ;)
lol i'm not too sure what that means but my penguin is very confused and trapped in a world that is flipped around and upside down.

---

### Post by ElectronicTonic on 2010-11-04
> **HermanAB said:**
> Oh, just turn the screen around!

Search on [http://www.google.com/linux](http://www.google.com/linux) for 'xrandr'.  You can configure the screen with that.
thank you for the advice now I can see everything normal my mouse doesn't know where it's going.. lol

---

### Post by julio_cortez on 2010-11-04
Maybe you can try inverting axes.
I didn't find a proper guide but on Ubuntu Wiki there's a page on how to configure devices:
[https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29](https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29)
(contains a sample taken from [http://daniel.hahler.de/](http://daniel.hahler.de/) so you may well have a look at the original site)

On UF I found this but it's too old probably to be helpful:
[http://ubuntuforums.org/archive/index.php/t-483723.html](http://ubuntuforums.org/archive/index.php/t-483723.html)

---

### Post by Verbeck on 2010-11-04
is this real?:confused:

---

### Post by julio_cortez on 2010-11-04
> **Verbeck said:**
> is this real?:confused:I don't know, but if it is.. Even reversing the axes he'd still have the pointer (the arrow) upside down I guess, provided that it's true :D

BTW: I have made my own mind about it (which involves swapping the top bar with the bottom one and, well, I can't say anything further).. But let's see what happens. This thread had me curious to see how it will evolve.
[COLOR=White]
And I think that what happened is this:
- Swapped the top bar with the bottom one (so the bar with the "places/applications/system" menus would be at the bottom and the one with the trash can would be on top)
- Took a screenshot
- Flipped the screenshot vertically (even the desktop background is upside down IMO, take a look at it and compare it with the default one that you find on wikipedia!!)
- Selected a square around the mouse pointer and re-flipped it vertically back in its original position (so the pointer would result "correct")[/COLOR]

---

### Post by ElectronicTonic on 2010-11-04
> **julio_cortez said:**
> I don't know, but if it is.. Even reversing the axes he'd still have the pointer (the arrow) upside down I guess, provided that it's true :D

BTW: I have made my own mind about it (which involves swapping the top bar with the bottom one and, well, I can't say anything further).. But let's see what happens. This thread had me curious to see how it will evolve.
[COLOR=White]
And I think that what happened is this:
- Swapped the top bar with the bottom one (so the bar with the "places/applications/system" menus would be at the bottom and the one with the trash can would be on top)
- Took a screenshot
- Flipped the screenshot vertically (even the desktop background is upside down IMO, take a look at it and compare it with the default one that you find on wikipedia!!)
- Selected a square around the mouse pointer and re-flipped it vertically back in its original position (so the pointer would result "correct")[/COLOR]
I'm not trolling anyone this is real. Not too sure how I got into the situation which I know does not help. If you would like further proof I'd be happy to show. And as you said if I reversed the screen with xrandr -o 0, xrandr -x and xrandr -y. They still invert (or something) my pointer but I can read stuff now just can't go no where.  I'm a noob when it comes to unix I think I might just reformat and start new.. unless someone has anyone more suggestions. Thank you all for your input.

---

### Post by ElectronicTonic on 2010-11-04
yep..

---

### Post by sandyd on 2010-11-04
> **ElectronicTonic said:**
> yep..

post output of 
```

cat /etc/X11/xorg.conf
```

---

### Post by cgroza on 2010-11-04
Your xorg.conf is messed up. Since you reported that you had video problems it is possible.

---

### Post by kansasnoob on 2010-11-04
I accidentally turned mine 90 degrees once fiddling with gconf. I couldn't quite figure out what I did wrong so I just renamed .gconf and .gconfd  with the "_OLD" suffix at the end, and after restarting X things went back to normal.

---

### Post by anewguy on 2010-11-04
My suggestion was from the standpoint you are trapped inside the screen - you'd have to type backwards for it to be readable on the screen - so.....

Help!!! I'm being held captive inside this terminal!


;)  Dave

---

### Post by ElectronicTonic on 2010-11-05
~$ cat /etc/X11/xorg.conf
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "record"
    Load  "dbe"
    Load  "dri2"
    Load  "dri"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by ElectronicTonic on 2010-11-05
Reformatted my SSD and reinstalled unbuntu 10.10 Anyone that would still like to give me pointers on ubuntu I would really appreciate it.  Thank you all for the support. I truely had a learning experience.

---

### Post by julio_cortez on 2010-11-05
> **ElectronicTonic said:**
> I'm not trolling anyone this is real. Not too sure how I got into the situation which I know does not help.
Well, I did a joke like that once to an intern (*the famous one I talked about in the "Corrupt a wish" game.. I took a screenshot of her desktop, flipped it and set it as background killing Explorer.exe in order not to have the "double taskbar"*), so I just thought you were doing the same. :P
Anyway, if formatting had solved the issue, I'm glad. :)

---

### Post by ElectronicTonic on 2010-11-05
lol that's a good one! I have heard of stuff like that, the cracked lcd image rings a bell haha. and I got my laptop up and running again reformatting and reinstalling ubuntu took max maybe 10 minutes so dope thank you

---

### Post by mbusha on 2011-01-12
Hi all -- another Ubuntu newbie here who has run into the same problem as ElectronicTonic with all the writing appearing backwards and upside down (see attached image of my Desktop -- I'm definitely not this good with photo shop!).  Anyone have any thoughts on options other than re-installation?  Here's some additional information that may help:

I'm running Ubuntu 10.10 on a Lenovo T510.  I can avoid this problem if I boot into recovery mode and then select low graphics mode. 

This problem started after I was messing around with the nVidia drivers.  I eventually realized that my laptop has a 3100M Optimus card, which nVidia seems not to support.  I removed all nvidia* packages I had installed using Synaptic.  After doing this, I was unable to get some of the Compiz features to work (e.g., Window picker).  I decided (for better or worse) to reinstall the xserver-xorg-video-nouveau and xserver-xorg-video-nv packages (also using synaptic), and that's when this started. 

Also, I don't have an /etc/X11/xorg.conf file.  None was initially created, although I created one when playing with the nVidia drivers using the nvidia-xconfig command (which noted that an xorg.conf file did not already exist).  However, that configuration wasn't working, so I got rid of the xorg.conf file when removing the nVidia drivers in an attempt to return the computer to its original state. 

Thanks in advance for any suggestions.

---

### Post by aktiwers on 2011-01-12
Thats some freaky stuff..  never seen nothing like it :)

What if you go to system => Prefernces => Monitor
And under "Rotation" pick "upside down". ?

---

### Post by mbusha on 2011-01-12
Do you know if there's a way to change the monitor orientation from the command line?  It's actually close to impossible to select the right menu using the mouse (get ready for more strangeness): 

The actual location of the places to click remains correct (hopefully this description makes sense, since it's really weird).  That is, if I move my mouse pointer over the (backwards) "System Tools" menu under Applications, it's actually the Games menu that pops open (i.e., the menu that should be at that location if the screen had the correct orientation).  Similarly, to open the two files you see on my Desktop, I can't click on the icon locations in the bottom left of the screen, but need to click on the blank space in the the _top_ left, where they would be if the display looked correct.  

I should probably also mention that the mouse control remains normal -- the controls aren't inverted or anything like that.

---

### Post by mbusha on 2011-01-14
So I seem to be making some progress here.  I generated a xorg.configu file using by shutting down X and using the `Xorg -configure' command.  That seems to detect a lot of my devices and produces a file that looks like this:  

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dri"
    Load  "record"
    Load  "dri2"
    Load  "dbe"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Trying to boot with this typically results in the same problem.  However, if I change the driver on Card1 (what I think is my integrated graphics card) from "intel" to "fbdev", things boot normally.  However, I'm still unable to get the compiz features to work, which makes me suspect that this isn't the optimal driver to be using.  

So, I'm guessing that means there's a problem with the intel driver.  I've tried reinstalling libdrm-intel1 and xserver-xorg-video-intel from synaptic to no luck.  Any other thoughts what I could be doing?

---

