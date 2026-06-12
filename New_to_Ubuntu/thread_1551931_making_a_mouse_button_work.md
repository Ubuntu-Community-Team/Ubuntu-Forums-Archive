---
title: "making a mouse button work?"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-12
I have a logitech MX5500.   For some reason when I try to assign a keyboard shortcut, it does not assign to the button.  It reacts as though I pressed a key, but it just says "disabled" in the box.  the mx5000-tool did not work to assign the keys.

---

### Post by outleradam on 2010-08-14
I just don't understand how the UI can see a button, but not assign it to something.

---

### Post by outleradam on 2010-08-17
Anyone?

---

### Post by clhsharky on 2010-08-17
outleradam

Is the mx5000-tool a Linux app, if a windows app no.

Sharky

---

### Post by outleradam on 2010-08-17
that app does nothing for the mouse buttons or the side + - and 3d button.

---

### Post by outleradam on 2010-09-01
Bump, anyone get this to work successfully?

---

### Post by jtarin on 2010-09-01
[Problematc hardware, but some success.]("http://ubuntuforums.org/showthread.php?t=1469533")

---

### Post by outleradam on 2010-09-01
That's a different issue all together.  I just got rid of my DiNovo.  That is a bluetooth issue.  My diNovo was always cured by removing the dongle and replacing it. Never had an issue.


My issue is the extra, non-standard keyboard/mouse buttons are not registered.  They can only steel focus and are not capable of being assigned actions.  How Do I get buttons on a mouse and keyboard to register as actions?

---

### Post by jtarin on 2010-09-02
[Your welcome to write your own rules]("https://wiki.ubuntu.com/X/Config/Input#Input Configuration with udev (Ubuntu 10.04)"), such is the power of open source.

---

### Post by jtarin on 2010-09-02
Try the command xev to insure your non-standard keys are recognized.

---

### Post by outleradam on 2010-09-02
Sweet.  That's exactly what I was looking for!!! 

:KS

---

### Post by jtarin on 2010-09-02
A picture is worth a thousand words.

---

### Post by outleradam on 2010-09-02
I guess I spoke too soon.  I've been playing around with it all night and I still don't know what I'm looking at.  

```
MotionNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556605, (153,170), root:(2927,337),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556605, (153,170), root:(2927,337),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556605, (153,170), root:(2927,337),
    state 0x1000, button 5, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556616, (154,170), root:(2928,337),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556988, (154,170), root:(2928,337),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556988, (154,170), root:(2928,337),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14556988, (154,170), root:(2928,337),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14557708, (154,170), root:(2928,337),
    state 0x0, button 2, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14557933, (154,170), root:(2928,337),
    state 0x200, button 2, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14558529, (153,170), root:(2927,337),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14558844, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14559125, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14559407, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14559620, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14560138, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14560408, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14561061, (153,170), root:(2927,337),
    state 0x0, button 15, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14561308, (153,170), root:(2927,337),
    state 0x0, button 15, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14561792, (153,170), root:(2927,337),
    state 0x0, button 13, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14562163, (153,170), root:(2927,337),
    state 0x0, button 13, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14563176, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x5400001,
    root 0x15d, subw 0x0, time 14563400, (153,170), root:(2927,337),
    state 0x0, button 16, same_screen YES


```

I cannot set these buttons up on keyboard shortcuts.  What am I missing?  How can I say, make "button 16"="Zoom In" in keyboard shortcuts?

---

### Post by jtarin on 2010-09-03
Maybe what you want to do is investigate " man xmodmap".

[Then there is this]("http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working"). You r gonna need to set up a few things to get it to work but its possible with an xorg configuration. The xf86-input-evdev package is installed by default in 10.04.

---

### Post by outleradam on 2010-09-03
^^ Thank you very much.  So since I have had much bad luck in the past, I'm going to document what I'm doing here while following the guide in the link above.

I do not have pacman.  and apt-get does not have a xf86-input-evdev package, but the modprobe evdev worked without an error message.

```
adam@adam-desktop:~$ egrep "Name|Handlers" /proc/bus/input/devices
N: Name="Power Button"
H: Handlers=kbd event0 
N: Name="Power Button"
H: Handlers=kbd event1 
N: Name="Macintosh mouse button emulation"
H: Handlers=mouse0 event2 
N: Name="Logitech Logitech BT Mini-Receiver"
H: Handlers=kbd event3 
N: Name="Logitech Logitech BT Mini-Receiver"
H: Handlers=kbd mouse1 event4 
N: Name="Logitech MX Revolution Mouse"
H: Handlers=kbd mouse2 event5 
N: Name="Logitech MX5500 Keyboard"
H: Handlers=kbd event6 

```I have no idea what Macintosh mouse button emulation could be.
so, I'm looking at "kbd mouse2 event5" and "mouse0 event2"
I edited /etc/X11/xorg.conf and added the following:
```
Section "InputDevice"
  Identifier      "Evdev Mouse"
  Driver          "evdev"
  Option          "Name" "Logitech MX Revolution Mouse"
  Option          "evBits"  "+1-2"
  Option          "keyBits" "~272-287"
  Option          "relBits" "~0-2 ~6 ~8"
  Option          "Pass"    "3"
  Option          "CorePointer"
EndSection
```I modified the following section to add "Evdev Mouse" instead of mouse0
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Evdev Mouse" "CorePointer"
    Option         "Xinerama" "0"
EndSection

```Added ```
    Option          "Device" "/dev/input/by-id/usb-Logitech_Logitech_BT_Mini-Receiver_000761F9EF21-event-mouse"
``` to the input device section

I'm rebooting now, and I will be back.

So Ubuntu does not have udevinfo, it has "udevadm info"  Building the rules for the separation of mouse/keyboard goes like this:
```
udevadm info -a -p `udevadm info -q path -n /dev/input/event6` | grep modalias
    ATTRS{modalias}=="input:b0005v046DpB30Be0100-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D5,D9,DB,DF,E2,E7,E8,E9,EA,EB,F0,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,28,29,2A,m4,l0,1,2,3,4,sfw"
    ATTRS{modalias}=="usb:v046DpC709d0100dcE0dsc01dp01icE0isc01ip01"
    ATTRS{modalias}=="pci:v00008086d00003B34sv00001043sd00008383bc0Csc03i20"
```so we take that usb modalias and put it into this statement 
```

echo 'KERNEL=="event[0-9]*", BUS=="usb", SYSFS{modalias}=="usb:v046DpC709d0100dcE0dsc01dp01icE0isc01ip01, SYMLINK+="input/usbmouse"' | sudo tee /etc/udev/rules.d/z10_usb_mouse.rules
```
and run that in the terminal to create a rule  to separate mouse from keyboard

Then go back in and edit /etc/X11/xorg.conf to add the following under the input device
```
  Option          "Device" "/dev/input/usbmouse"
```

---

### Post by jtarin on 2010-09-03
> **outleradam said:**
> apt-get does not have a xf86-input-evdev package, but the modprobe evdev worked without an error message.
Your signature says your using Lucid 10.04. xf86-input-evdev is in the repos. Open up Synaptic and plug "xf86-input-evdev" in the search box. Mine is default installed.

---

### Post by outleradam on 2010-09-03
^^ It's already installed!  yay!

so upon reboot,  I ran the following command in a terminal
```
xmodmap -e "pointer = 1 2 3 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 4 5" &
```all buttons had functionality, but none were the desired functionality.  scroll wheel copies and pastes, the side 3d scroller does forward and back... So to make the changes perminant, I added the following to my /etc/X11/xorg.conf under inputdevice
```
   Option         "ZAxisMapping" "4 5"
   Option         "ButtonMapping" "1 2 3 6 7 8 9 10 11 12 13 14 15 16"

```So after reboot, it did nothing.

so again I ran 
```
 xmodmap -e "pointer = 1 2 3 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 4 5" &
```and again all my buttons were fuxored up.

---

### Post by outleradam on 2010-09-03
since all my buttons were working in the first place, maybe all that was needed is to assign xmodmaps?  I'm looking at that now.

---

### Post by outleradam on 2010-09-03
so the 2 most important files are:

~/.Xmodmap
```
pointer = 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
```
and ~/.xbindkeysrc
```
"/usr/bin/xvkbd -xsendevent -text "\[Left]""
m:0x0 + b:13
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
m:0x0 + b:15

```

These enabled my buttons and allowed my 3d mouse wheel to funcion as a left/right

I will be adding more to xbindkeysrc.


I still can't figure out how to add keyboard shortcuts to the mouse.

---

### Post by jdahm on 2011-04-20
I'm also trying to configure a MX5500 mouse at the moment.  I'd very much like clicking the side scroll wheel to act as mouse button 2 (middle click).  How would I change the line above to achieve that?

---

### Post by outleradam on 2011-04-25
I revised my methods a bit...
here is my /etc/X11/xorg.conf```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.36  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Tue Jan 18 17:15:22 PST 2011

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.12  (buildmeister@builder101)  Fri Oct  8 11:46:43 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "MX Rev"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

     #VX Rev users can type "VX Rev"
    Identifier     "MX Rev"
    Driver         "evdev"
    Option         "Device" "/dev/input/event3"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "HWheelRelativeAxisButtons" "7 6"
    Option         "Buttons" "19"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC 2330V"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Screen"

# Removed Option "TwinViewXineramaInfoOrder" "DFP-1"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


You need compizconfig to be able to modify the button mappings for compiz.

``````
sudo apt-get install compizconfig-settings-manager
```Then set up the commands you would like and assign the buttons manually...   check this out..

Use the command "xev" to determine the button assignments.  After that manually edit your compizconfig files...  For example, this makes the side scroll wheel(buttons 13 and 15) zoom in and out.
/home/adam/.gconf/apps/compiz/plugins/ezoom/allscreens/options/%gconf.xml (enhanced desktop zoom)
```
<?xml version="1.0"?>
<gconf>
    <entry name="zoom_out_button" mtime="1296407807" type="string">
        <stringvalue>Button15</stringvalue>
    </entry>
    <entry name="zoom_box_button" mtime="1296407807" type="string">
        <stringvalue>Disabled</stringvalue>
    </entry>
    <entry name="zoom_in_button" mtime="1296407807" type="string">
        <stringvalue>Button13</stringvalue>
    </entry>
</gconf>
```This makes the side wheel click (button 16) work to show expo mode

/home/adam/.gconf/apps/compiz/plugins/expo/allscreens/options/%gconf.xml
```
<?xml version="1.0"?>
<gconf>
    <entry name="ground_size" mtime="1296407807" type="float" value="0.54000002145767212"/>
    <entry name="vp_saturation" mtime="1296407807" type="float" value="99"/>
    <entry name="ground_color1" mtime="1296407807" type="string">
        <stringvalue>#7979793b</stringvalue>
    </entry>
    <entry name="ground_color2" mtime="1296407807" type="string">
        <stringvalue>#0005ff85</stringvalue>
    </entry>
    <entry name="zoom_time" mtime="1296407807" type="float" value="1.0252000093460083"/>
    <entry name="expo_button" mtime="1296407807" type="string">
        <stringvalue>Button16</stringvalue>
    </entry>
    <entry name="vp_brightness" mtime="1296407807" type="float" value="100"/>
    <entry name="vp_distance" mtime="1296407807" type="float" value="0.091099999845027924"/>
    <entry name="deform" mtime="1296407807" type="int" value="2"/>
    <entry name="curve" mtime="1296407807" type="float" value="0.59210002422332764"/>
    <entry name="expo_animation" mtime="1296407807" type="int" value="1"/>
    <entry name="expo_key" mtime="1296407807" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Super&gt;z</stringvalue>
    </entry>
    <entry name="double_click_time" mtime="1296407807" type="int" value="883"/>
</gconf>
```You have to manually edit the files because Compiz Config only handles a few buttons, we have more then expected.  it works, just manually without the GUI.


I'm not using an xbindkeys file or xmodmap.  they don't work.

---

