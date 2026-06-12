---
title: "Help with graphic display"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by kabuli on 2009-04-03
Hi all,

Just installed ubuntu 8.10 desktop on my asus laptop, but display is just flickering and the graphic is awful, it would seem that need a graphics driver or the like. How do I tell what graphics card i have and then get a driver for it(if thats the problem)

Note: graphics card worked fine under winxp
I can attach a screen shot if necessary

---

### Post by Tobi-fp on 2009-04-03
please, can you find out what card you use?

---

### Post by Tobi-fp on 2009-04-03
a screen shot wont be neccesary, but if you use a nvidia card, you might need to install the dedicated nvidia driver

---

### Post by kabuli on 2009-04-03
How do I check/confirm what G/Card I have?
I believe its a sis m760gx(details from winxp days)

---

### Post by odinb on 2009-04-03
Please do an lspci at a command prompt and look for the line starting with "VGA compatible controller:" after the numbers.

This will tell you what GPU you have.

If in doubt, post the result here, and I am sure someone will be able to help further!

---

### Post by Kareeser on 2009-04-03
Please try the following:

System -> Administration -> Hardware Drivers

... and enable the graphics card driver.

---

### Post by kabuli on 2009-04-03
Thanks,

This is the output,

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


I don't see any thing beside a wireless driver under sys->admin->HW Driver..Does this mean this card is not supported or do I need to dl the driver manually (if manually,can someone plz point out how as I looked everywhere and couldn't find it)

cheers

---

### Post by ivanvajar on 2009-04-03
You can try [here]("http://www.sis.com/download/agreement.php?url=/download/"), but it looks like there are no drivers for your chipset.

---

### Post by halitech on 2009-04-03
> **kabuli said:**
> Hi all,

Just installed ubuntu 8.10 desktop on my asus laptop, but display is just flickering and the graphic is awful, it would seem that need a graphics driver or the like. How do I tell what graphics card i have and then get a driver for it(if thats the problem)

Note: graphics card worked fine under winxp
I can attach a screen shot if necessary

graphics card probably worked under windows because SiS makes a driver for windows and it was probably installed.

> **kabuli said:**
> Thanks,

This is the output,

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


I don't see any thing beside a wireless driver under sys->admin->HW Driver..Does this mean this card is not supported or do I need to dl the driver manually (if manually,can someone plz point out how as I looked everywhere and couldn't find it)

cheers

SiS sucks when it comes to supporting linux so chances are what you see is what you have and probably not going to get much better. sorry.

---

### Post by kabuli on 2009-04-03
Thats a bumer :( hoping not to go back to  windowz..

THough I found this other thread so hoping 8.4 is the go.. 
 [https://bugs.launchpad.net/ubuntu/+bug/287475](https://bugs.launchpad.net/ubuntu/+bug/287475)

Thanks all

---

### Post by DavidTangye on 2009-04-12
FYI: I have just upgraded from Hardy to Intrepid on an ASUS laptop, and the screen graphics are bad now, whereas before it was fine. The title bars and backgrounds are 'sparkly' and colours are wrong. I have the same results of lspci:
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
 The graphics are fine under Puppy linux 2.17, and puppy uses a SIS driver. I copied the xorg.conf file from the Puppy setup to ubuntu, but the ubuntu session was still bad, so I know that the issue is not related to any xorg.conf parameters. The problem is with the SIS driver. If I change to driver to VESA in ubuntu's xorg.conf I get low-res graphics (800x600 or similar), not the 1280x768 that I want.

---

### Post by DavidTangye on 2009-04-14
> **DavidTangye said:**
> If I change to driver to VESA in ubuntu's xorg.conf I get low-res graphics (800x600 or similar), not the 1280x768 that I want.I have now got the display running at 1280x768 resolution, in both Ubuntu Intrepid and Puppy 4.12.

[LIST]
[*]Ubuntu: the refresh rate shows as 0Hz!, and I need to use the vesa driver, as the sis driver still gives a snowy, sparkly screen
[*]Puppy:  the refresh rate shows as 75Hz and its uses the sis driver.
[/LIST]

---

### Post by la5lia on 2009-04-21
How did you do it ? I have the same computer with same problem.
What do i need to write in the xorg file ??

---

### Post by la5lia on 2009-05-02
I gave up on this problem in ubuntu.:(
pclinux however works great om this laptop :)

---

### Post by DavidTangye on 2009-05-16
> **la5lia said:**
> How did you do it ? I have the same computer with same problem.
What do i need to write in the xorg file ??
Sorry I did not see your post. Here is the xorg.conf file I hacked, after getting Puppy to set it up to work first.  I have pasted it here as the file attachment facility does not let it upload. It shows the sis driver and all its possible options. Perhaps one of them would fix the problem. However, as also shown, I switched out the sis driver and switched in the vesa driver.

#Special base config file used in Puppy Linux.

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"
    Load "synaptics"

# This loads the DBE extension module.

    Load        "dbe"      # Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load       "glx"

# This loads xtrap extension, used by xrandr
    Load       "xtrap"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

##    RgbPath    "/usr/X11R7/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)

    FontPath   "/usr/X11R7/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R7/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R7/lib/X11/fonts/TTF/"

EndSection

Section "ServerLayout"
    Identifier     "theServer"
    Screen      0  "theScreen" 0 0
# commented out by update-manager, HAL is now used
#    InputDevice    "Keyboard xPuppy" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Mouse xPuppy" "CorePointer"
# commented out by update-manager, HAL is now used
#    InputDevice    "Synaptics Touchpad xPuppy" "AlwaysCore"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier  "Keyboard xPuppy"
#    Driver      "kbd"
#    Option      "XkbRules" "xorg"
#    Option      "XkbModel" "pc102"
#    Option      "XkbLayout" "us" #xkeymap0
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier  "Mouse xPuppy"
#    Driver      "mouse"
#    Option        "Protocol" "IMPS/2" #mouse0protocol
#    Option        "Device" "/dev/mouse"
#    #Option      "Emulate3Buttons"
#    #Option      "Emulate3Timeout" "50"
#    Option      "ZAxisMapping" "4 5" #scrollwheel
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier "Synaptics Touchpad xPuppy"
#    Driver "synaptics"
#    Option "Device" "/dev/psaux"
#    Option "Protocol" "auto-dev"
#    Option "LeftEdge" "1700"
#    Option "RightEdge" "5300"
#    Option "TopEdge" "1700"
#    Option "BottomEdge" "4200"
#    Option "FingerLow" "25"
#    Option "FingerHigh" "30"
#    Option "MaxTapTime" "0"
#    Option "MaxTapMove" "220"
#    Option "VertScrollDelta" "100"
#    Option "MinSpeed" "0.10"
#    Option "MaxSpeed" "0.30"
#    Option "AccelFactor" "0.0030"
#    Option "SHMConfig" "on"
#    #Option "Repeater" "/dev/ps2mouse"
#EndSection

Section "Device"
    ### Available Driver options are:-
    ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
    ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
    ### [arg]: arg optional
    #Option     "Accel"                  # [<bool>]
    #Option     "AccelMethod"            # <str>
    #Option     "TurboQueue"             # [<bool>]
    #Option     "FastVram"               # [<bool>]
    #Option     "HostBus"                # [<bool>]
    #Option     "RenderAcceleration"     # [<bool>]
    #Option     "ForceCRT1Type"          # <str>
    #Option     "ForceCRT2Type"          # <str>
    #Option     "ShadowFB"               # [<bool>]
    #Option     "DRI"                    # [<bool>]
    #Option     "AGPSize"                # <i>
    #Option     "GARTSize"               # <i>
    #Option     "Vesa"                   # [<bool>]
    #Option     "MaxXFBMem"              # <i>
    #Option     "EnableSiSCtrl"          # [<bool>]
    #Option     "SWCursor"               # [<bool>]
    #Option     "HWCursor"               # [<bool>]
    #Option     "UseColorHWCursor"       # [<bool>]
    #Option     "Rotate"                 # <str>
    #Option     "Reflect"                # <str>
    #Option     "Xvideo"                 # [<bool>]
    #Option     "InternalModes"          # [<bool>]
    #Option     "OverruleFrequencyRanges"     # [<bool>]
    #Option     "RestoreBySetMode"       # [<bool>]
    #Option     "ForceCRT1"              # [<bool>]
    #Option     "XvOnCRT2"               # [<bool>]
    #Option     "PanelDelayCompensation"     # <i>
    #Option     "PDC"                    # <i>
    #Option     "PanelDelayCompensation2"     # <i>
    #Option     "PDC2"                   # <i>
    #Option     "PanelDelayCompensation1"     # <i>
    #Option     "PDC1"                   # <i>
    #Option     "EMI"                    # <i>
    #Option     "LVDSHL"                 # <i>
    #Option     "ForcePanelRGB"          # <i>
    #Option     "SpecialTiming"          # <str>
    #Option     "TVStandard"             # <str>
    #Option     "UseROMData"             # [<bool>]
    #Option     "UseOEMData"             # [<bool>]
    #Option     "YV12"                   # [<bool>]
    #Option     "CHTVType"               # [<bool>]
    #Option     "CHTVOverscan"           # [<bool>]
    #Option     "CHTVSuperOverscan"      # [<bool>]
    #Option     "CHTVLumaBandwidthCVBS"     # <i>
    #Option     "CHTVLumaBandwidthSVIDEO"     # <i>
    #Option     "CHTVLumaFlickerFilter"     # <i>
    #Option     "CHTVChromaBandwidth"     # <i>
    #Option     "CHTVChromaFlickerFilter"     # <i>
    #Option     "CHTVCVBSColor"          # [<bool>]
    #Option     "CHTVTextEnhance"        # <i>
    #Option     "CHTVContrast"           # <i>
    #Option     "SISTVEdgeEnhance"       # <i>
    #Option     "SISTVAntiFlicker"       # <str>
    #Option     "SISTVSaturation"        # <i>
    #Option     "SISTVCFilter"           # [<bool>]
    #Option     "SISTVYFilter"           # <i>
    #Option     "SISTVColorCalibFine"     # <i>
    #Option     "SISTVColorCalibCoarse"     # <i>
    #Option     "SISTVXScale"            # <i>
    #Option     "SISTVYScale"            # <i>
    #Option     "TVXPosOffset"           # <i>
    #Option     "TVYPosOffset"           # <i>
    #Option     "SIS6326TVAntiFlicker"     # <str>
    #Option     "SIS6326TVEnableYFilter"     # [<bool>]
    #Option     "SIS6326TVYFilterStrong"     # [<bool>]
    #Option     "SIS6326TVForcePlug"     # <str>
    #Option     "SIS6326FSCAdjust"       # <i>
    #Option     "YPbPrAspectRatio"       # <str>
    #Option     "TVBlueWorkAround"       # [<bool>]
    #Option     "ColorHWCursorBlending"     # [<bool>]
    #Option     "ColorHWCursorBlendThreshold"     # <i>
    #Option     "CRT2Detection"          # [<bool>]
    #Option     "ForceCRT2ReDetection"     # [<bool>]
    #Option     "SenseYPbPr"             # [<bool>]
    #Option     "CRT1Gamma"              # [<bool>]
    #Option     "CRT2Gamma"              # [<str>]
    #Option     "GammaBrightness"        # <str>
    #Option     "GammaBrightnessCRT2"     # <str>
    #Option     "CRT2GammaBrightness"     # <str>
    #Option     "Brightness"             # <str>
    #Option     "NewGammaBrightness"     # <str>
    #Option     "CRT2Brightness"         # <str>
    #Option     "CRT2NewGammaBrightness"     # <str>
    #Option     "Contrast"               # <str>
    #Option     "NewGammaContrast"       # <str>
    #Option     "CRT2Contrast"           # <str>
    #Option     "CRT2NewGammaContrast"     # <str>
    #Option     "CRT1Saturation"         # <i>
    #Option     "XvGamma"                # [<str>]
    #Option     "XvDefaultContrast"      # <i>
    #Option     "XvDefaultBrightness"     # <i>
    #Option     "XvDefaultHue"           # <i>
    #Option     "XvDefaultSaturation"     # <i>
    #Option     "XvDefaultDisableGfx"     # [<bool>]
    #Option     "XvDefaultDisableGfxLR"     # [<bool>]
    #Option     "XvChromaMin"            # <i>
    #Option     "XvChromaMax"            # <i>
    #Option     "XvUseChromaKey"         # [<bool>]
    #Option     "XvInsideChromaKey"      # [<bool>]
    #Option     "XvYUVChromaKey"         # [<bool>]
    #Option     "XvDisableColorKey"      # [<bool>]
    #Option     "XvUseMemcpy"            # [<bool>]
    #Option     "BenchmarkMemcpy"        # [<bool>]
    #Option     "XvDefaultAdaptor"       # <str>
    #Option     "ScaleLCD"               # [<bool>]
    #Option     "CenterLCD"              # [<bool>]
    #Option     "EnableHotkey"           # [<bool>]
    #Option     "ForceCRT1VGAAspect"     # <str>
    #Option     "ForceCRT2VGAAspect"     # <str>
    #Option     "MergedFB"               # [<str>]
    #Option     "TwinView"               # [<str>]
    #Option     "MergedFBAuto"           # [<bool>]
    #Option     "CRT2HSync"              # <str>
    #Option     "SecondMonitorHorizSync"     # <str>
    #Option     "CRT2VRefresh"           # <str>
    #Option     "SecondMonitorVertRefresh"     # <str>
    #Option     "CRT2Position"           # <str>
    #Option     "TwinViewOrientation"     # <str>
    #Option     "MetaModes"              # <str>
    #Option     "MergedDPI"              # <str>
    #Option     "MergedXinerama"         # [<bool>]
    #Option     "TwinviewXineramaInfo"     # [<bool>]
    #Option     "MergedXineramaCRT2IsScreen0"     # [<bool>]
    #Option     "MergedNonRectangular"     # [<bool>]
    #Option     "MergedMouseRestriction"     # [<bool>]
    Identifier  "sis Video Device"
    Driver      "sis" #card0driver
    VendorName  "Silicon Integrated Systems [SiS]"
    BoardName   "661/741/760/761 PCI/AGP VGA Display Adapter"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier    "vesa Video Device"
    Driver    "vesa"
EndSection

Section "Monitor"
    Identifier   "theMonitor"
    VendorName   ""
    ModelName    ""
    HorizSync    31.5-90
#    HorizSync    30-90 min-max
    VertRefresh  54-76
#    VertRefresh  54-70 min-max
    #UseModes     "Modes0" #monitor0usemodes
    EndSection
    
Section "Modes"
    Identifier "Modes0"
    #modes0modeline0
EndSection

Section "Screen"
    Identifier "theScreen"
    Device     "vesa Video Device"
#    Device     "sis Video Device"
    Monitor    "theMonitor"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x800" "1280x768" "1024x768" "800x600"
    EndSubsection
EndSection

###############################################################################

---

