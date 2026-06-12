---
title: "No video"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by saintj0n on 2010-03-18
I can't get X to start up.  It says device not detected.  I have a Radeon 4350HD integrated card.  This Xorg.conf: works on mepis but how can I pass these parameters to Ubuntu?

Section "ServerLayout"
  Identifier "XFree86 Configured"
  Screen 0 "Screen0" 0 0
 #Screen 0 "ATIScreen" 0 0
 #Screen 1 "Screen1" RightOf "Screen0"
 #Option "Xinerama" "true"
 #Option "Clone" "true"
  InputDevice "Keyboard0" "CoreKeyboard"
 #InputDevice "PS/2 Mouse" "CorePointer"
  InputDevice "USB Mouse" "CorePointer"
 #InputDevice "Touchpad" "SendCoreEvents"
 #InputDevice "ALPS Touchpad" "SendCoreEvents"
 #InputDevice "Appletouch" "SendCoreEvents"
 #InputDevice "Stylus" "SendCoreEvents"
 #InputDevice "Eraser" "SendCoreEvents"
 #InputDevice "Cursor" "SendCoreEvents"
 #InputDevice "Serial Mouse" "CorePointer"
EndSection

Section "ServerFlags"
  Option "AllowMouseOpenFail" "true"
EndSection

Section "Files"
# Xorg 7.0 font paths
    FontPath 	"/usr/share/fonts/X11/100dpi:unscaled"
    FontPath 	"/usr/share/fonts/X11/misc:unscaled"

# Other font paths
    FontPath 	"/usr/share/fonts/truetype/arphic"
    FontPath 	"/usr/share/fonts/truetype/freefont"
    FontPath 	"/usr/share/fonts/truetype/kochi"
    FontPath 	"/usr/share/fonts/truetype/ttf-bitstream-vera"

# path to defoma fonts
    FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection

Section "Module"
  Load "dbe"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "type1"
  Load "v4l"
  Load "vbe"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "keyboard"
  Option "CoreKeyboard"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "us"
  Option "XKbOptions" ""
EndSection

Section "InputDevice"
  Identifier "Serial Mouse"
  Driver "mouse"
  Option  "Protocol" "Microsoft"
  Option  "Device" "/dev/ttyS0"
  Option  "Emulate3Buttons" "false"
  Option  "Emulate3Timeout" "70"
EndSection

Section "InputDevice"
  Identifier "Touchpad"
  Driver "synaptics"
  Option "Device" "/dev/psaux"
  Option "Protocol" "auto-dev"
  Option "LeftEdge" "1700"
  Option "RightEdge" "5300"
  Option "TopEdge" "1700"
  Option "BottomEdge" "4200"
  Option "FingerLow" "25"
  Option "FingerHigh" "30"
  Option "MaxTapTime" "180"
  Option "MaxTapMove" "220"
  Option "VertScrollDelta" "100"
  Option "HorizScrollDelta" "0"
  Option "MinSpeed" "0.09"
  Option "MaxSpeed" "0.18"
  Option "AccelFactor" "0.0015"
  Option "SHMConfig" "on"
EndSection

Section "InputDevice"
  Driver "synaptics"
  Identifier "ALPS Touchpad"
  Option "Device" "/dev/input/mouse0"
  Option "Protocol" "event"
  Option "LeftEdge" "130"
  Option "RightEdge" "840"
  Option "TopEdge" "130"
  Option "BottomEdge" "640"
  Option "FingerLow" "7"
  Option "FingerHigh" "8"
  Option "MaxTapTime" "180"
  Option "MaxTapMove" "110"
  Option "EmulateMidButtonTime" "75"
  Option "VertScrollDelta" "20"
  Option "HorizScrollDelta" "0"
  Option "MinSpeed" "0.25"
  Option "MaxSpeed" "0.50"
  Option "AccelFactor" "0.030"
  Option "EdgeMotionMinSpeed" "200"
  Option "EdgeMotionMaxSpeed" "200"
  Option "UpDownScrolling" "1"
  Option "CircularScrolling" "1"
  Option "CircScrollDelta" "0.1"
  Option "CircScrollTrigger" "2"
  Option "SHMConfig" "on"
EndSection

Section "InputDevice"
  Identifier "Appletouch"
  Driver "synaptics"
  Option "Device" "/dev/psaux"
  Option "Protocol" "auto-dev"
  Option "LeftEdge" "100"
  Option "RightEdge" "1120"
  Option "TopEdge" "50"
  Option "BottomEdge" "310"
  Option "FingerLow" "25"
  Option "FingerHigh" "30"
  Option "MaxTapMove" "220"
  Option "TapButton1" "1"
  Option "TapButton2" "3"
  Option "TapButton3" "2"
  Option "MinSpeed" "0.79"
  Option "MaxSpeed" "0.88"
  Option "AccelFactor" "0.0015"
  Option "SHMConfig" "on"
EndSection

Section "InputDevice"
  Identifier "PS/2 Mouse"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/psaux"
  Option "Emulate3Buttons" "false"
  Option "Emulate3Timeout" "70"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "InputDevice"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "ExplorerPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "InputDevice"
  Identifier "Stylus"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "stylus"
  Option "Device" "/dev/input/wacom"
Endsection

# Settings for wacom eraser
Section "InputDevice"
  Identifier "Eraser"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "eraser"
  Option "Device" "/dev/input/wacom"
Endsection

# Settings for wacom cursor (mouse)
Section "InputDevice"
  Identifier "Cursor"
  Driver "wacom"
  Option "Mode" "Relative"
  Option "Type" "cursor"
  Option "Device" "/dev/input/wacom"
Endsection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
  Option "DPMS" "true"
  HorizSync    30-75
  VertRefresh  55-70

EndSection

Section "Monitor"
  Identifier "Monitor1"
  VendorName "unknown"
  ModelName "unknown"
  Option "DPMS" "true"
  HorizSync    30-75
  VertRefresh  55-70
EndSection

Section "Monitor"
  Identifier  "ATIMonitor"
  VendorName "unknown"
  ModelName "unknown"
  Option "DPMS" "true"
  HorizSync    30-75
  VertRefresh  55-70
EndSection

Section "Device"
  Identifier  "Card0"
  Driver "intel"
  BoardName "unknown"

  Screen 0
 #Option "UseDisplayDevice" "dfp"
 #Option "MonitorLayout" "crt,crt"
 #BusID  "PCI:1:0:0"
 #Option "sw_cursor" # needed for some ati cards
 #Option "hw_cursor"
 #Option "NoAccel"
 #Option "ShowCache"
 #Option "ShadowFB"
 #Option "UseFBDev"
 #Option "Rotate"
  Option "UseInternalAGPGART" "no"

  Option "XAANoOffscreenPixmaps" "true"

# savage special options, use with care
 #Option "NoUseBios"
 #Option "BusType" "PCI"
  Option "DmaMode" "None"

# nvidia special options, use with care
  Option "CursorShadow" "1"
  Option "CursorShadowAlpha" "63"
  Option "CursorShadowYOffset" "2"
  Option "CursorShadowXOffset" "4"
  Option "FlatPanelProperties" "Scaling = native"
  Option "NoLogo" "true"
  Option "UseEDID" "true"
  Option "AddARGBGLXVisuals" "true"
  Option "RenderAccel" "true"
 #Option "AllowGLXWithComposite" "true"
EndSection

Section "Device"
  Identifier  "Card1"
  Driver "intel"
  BoardName "unknown"

  Screen 1
 #Option "MonitorLayout" "crt,crt"
 #BusID  "PCI:1:0:0"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 16
  
  SubSection "Display"
  Depth 8
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  
  # Only the official NVIDIA driver supports twinview
  # these setting are an example
  Option "TwinView" "false"
  Option "SecondMonitorVendorName" "unknown"
  Option "SecondMonitorModelName" "unknown"
  Option "SecondMonitorHorizSync" "30-75"
  Option "SecondMonitorVertRefresh" "55-70"
 #Option "MetaModes" "1024x768, 1024x768"
  Option "TwinViewOrientation" "RightOf"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection

Section "Screen"
  Identifier "Screen1"
  Device "Card1"
  Monitor "Monitor1"
  DefaultColorDepth 16
  
  SubSection "Display"
  Depth 8
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 15
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 16
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 24
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
  SubSection "Display"
  Depth 32
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
EndSection

Section "Screen"
  Identifier "ATIScreen"
  Device "Card0"
  Monitor "ATIMonitor"
  DefaultColorDepth 16
  
  SubSection "Display"
  Depth 24
  Modes "1280x1024" "1024x768" "800x600"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection

---

