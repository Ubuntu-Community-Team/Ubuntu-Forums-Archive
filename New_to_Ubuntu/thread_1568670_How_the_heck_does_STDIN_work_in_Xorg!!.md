---
title: "How the heck does STDIN work in Xorg?!?!?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by outleradam on 2010-09-05
I'm trying to figure out the steps along the way that make my mouse and keyboard work with Xorg.  I would like to know the full steps from click to "xev".    

I do not want a guide, I want to know how it works.  I have several keyboard keys which do not show up when I run the xev command.  I have several mouse buttons which do not show up in Xorg, but show up in xev.   I have one mouse button which does not operate in Xorg.   

Here's what I'm dealing with:
1. mouse button which does not have a "button" assigned to it, but displays output in xev
2. 1 mouse button assigned to an XF86 command
3. 8 out of 16 mouse buttons assigned to Xorg "buttons" but the rest cannot be set up in programs like compiz config.0
4. Somehow when assigning buttons, the computer thinks I have 24 buttons on my mouse instead of 16
5. 10 keyboard buttons fully inoperative

I would like to figure it out and write something which will allow my Logitech Revolution mouse and Logitech MX5500 keyboard to work properly.   There are several guides which allow you to use the Logitech MX5500 LCD, but none tell you how to configure it properly under Lucid Lynx.   Lucid also does not come with the proper selections under Logitech for my keyboard, nor does it allow for a mouse to be selected.

So, I need information.  When I hit the button on my keyboard, it goes somewhere, then it goes into X,  Same with my mouse.  I want to know what the configuration files are.

---

### Post by AlphaLexman on 2010-09-05
I would think that installing or checking for the correct drivers, updating them, for your input devices would solve the problem.

---

### Post by outleradam on 2010-09-05
Nope.  The best driver is evdev.  I need to know what is the software route or where is a good place to find it?

1. bluetooth
2. ?
3. evdev
4. ?
5. xbindkeys
6. xorg
7. eventserver

When I press a button, what happens?   I have to trace this problem back a bit.  Some of my buttons are not generating events.  Some of my buttons are generating events and not generating button presses and one of my buttons is generating an XF86 event.  I need to know how to properly handle these events.  I would absolutely love it if I could generate all XF86 events for all buttons on my mouse.

---

### Post by outleradam on 2010-09-06
I mapped out the keys which I want to assign by using the showkey command in the virtual terminal.

[IMG]http://i236.photobucket.com/albums/ff111/DrivingTibNaked/logitechmx5500-lg.png[/IMG]

Now, supposing I want to assign side mousewheel button "280" to "button 7" in Ubuntu, how do I do that?    

Or, how can I assign button 280 to a key combination?  And how can I map the unmapped keys?

---

### Post by AlphaLexman on 2010-09-06
You might get more help at [http://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/bd-p/general](http://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/bd-p/general)

---

### Post by outleradam on 2010-09-06
> **AlphaLexman said:**
> You might get more help at [http://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/bd-p/general](http://forums.logitech.com/t5/Keyboards-and-Keyboard-Mice/bd-p/general)
no. They don't support Linux.  People there are happy that it works on bluetooth.  They also refer people to "linux documentation" as seen here: [http://forums.logitech.com/t5/Keyboards-Bluetooth/MX5500-protocol-documentation-Linux/m-p/223010](http://forums.logitech.com/t5/Keyboards-Bluetooth/MX5500-protocol-documentation-Linux/m-p/223010) Then on top of that people cloud the actual issue with "how can I get my LCD working" or "Use this windows program to do it".   I'm looking to do this natively and your comment is counterproductive by referring a linux issue to a non-linux supporting source.  This issue will stay here in this topic and not get redirected or skewed into the countless threads which lead nowhere.  This issue will be resolved, not covered.

Also, this is a generic question.  I'm not asking for specifics here.  I am looking at "how do I map keys in Ubuntu".  The keycodes are present, the keys are not active.  I want to map keycodes to actions in Ubuntu.  The problem is that there is no actions mapped to the keys.   This is very much an Ubuntu issue.

I tried placing this file in my home dir:
~/.Xmodmap
```

adam@adam-desktop:~$ cat ./.Xmodmap
keycode 280 = XF86ZoomIn 
keycode 282 = XF86ZoomOut 
keycode 283 = XF86SplitScreen 
```and it did not work properly.  It removed my "e" and "r" keys, then mapped them to zoom in and zoom out.   

How can I map these keys in a desirable way?

---

### Post by outleradam on 2010-09-06
Ok, I managed to get all of the mouse buttons working with the following command:
```
adam@adam-desktop:/$ xmodmap -e "pointer = 1 2 3 4 5 6 7 8 10 9 15 11 12 16 13 14 17 18 "
```Now for some reason, whatever buttons are assigned to 7 and 9 will not work.  I don't understand this and I need help

Here is my keymap
```
adam@adam-desktop:/$ xmodmap -pp
There are 24 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1 Left Click
        2              2 Push button on top mouse wheel
        3              3 Right click
        4              4 Scroll Up on top mouse wheel
        5              5 Scroll Down on top mouse wheel
        6              6 Scroll right  on top mouse wheel
        7              7 Scroll Left on top mouse wheel
        8              8 Browser back button
        9             10 Browser Forward button 
       10              9
       11             15
       12             11
       13             12 Side thumb wheel Forward
       14             16
       15             13 Side thumb wheel Backwards
       16             14 Side thumb wheel Click
       17             17
       18             18
       19             19
       20             20
       21             21
       22             22
       23             23
       24             24


```I'm working on it, but for some reason slot  9 is always messing things up.  I don't know why, but they are just very touchy.  If slot 9 is in certain positions, then the mouse will simply not assign a function will not work with the button.

I'm reading these functions from xev
```
adam@adam-desktop:/$ xev |grep button
    state 0x10, button 1, same_screen YES
    state 0x110, button 1, same_screen YES
    state 0x10, button 2, same_screen YES
    state 0x210, button 2, same_screen YES
    state 0x10, button 3, same_screen YES
    state 0x410, button 3, same_screen YES
    state 0x10, button 6, same_screen YES
    state 0x10, button 6, same_screen YES
    state 0x10, button 7, same_screen YES
    state 0x10, button 7, same_screen YES
    state 0x10, button 5, same_screen YES
    state 0x1010, button 5, same_screen YES
    state 0x10, button 4, same_screen YES
    state 0x810, button 4, same_screen YES
    state 0x10, button 8, same_screen YES
    state 0x10, button 8, same_screen YES
    state 0x10, button 10, same_screen YES
    state 0x10, button 10, same_screen YES
    state 0x10, button 12, same_screen YES
    state 0x10, button 12, same_screen YES
    state 0x10, button 13, same_screen YES
    state 0x10, button 13, same_screen YES
    state 0x10, button 14, same_screen YES
    state 0x10, button 14, same_screen YES

```
Any help would be appreciated

---

### Post by outleradam on 2010-09-07
I think I will need to look at this page tomorrow after I've had some sleep:

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

Most of the information is out of date on all other pages.   10.04 removed HAL and replaced it with udev.  I think it was a bit premature, but hey, this may be the answer to my problems.

---

### Post by outleradam on 2010-09-07
I ran lshal | less and these are the devices in question:

```
udi = '/org/freedesktop/Hal/devices/bluetooth_acl_761fb1e4d_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/bluetooth_acl_761fb1e4d'  (string)
  info.product = 'Logitech MX Revolution Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/bluetooth_acl_761fb1e4d_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/bluetooth_acl_761fb1e4d'  (string)
  input.product = 'Logitech MX Revolution Mouse'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.1/2-1.4.1:1.0/bluetooth/hci0/hci0:11/input3/event3'  (string)


udi = '/org/freedesktop/Hal/devices/bluetooth_acl_761fec10a_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/bluetooth_acl_761fec10a'  (string)
  info.product = 'Logitech MX5500 Keyboard'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/bluetooth_acl_761fec10a_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/bluetooth_acl_761fec10a'  (string)
  input.product = 'Logitech MX5500 Keyboard'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.1/2-1.4.1:1.0/bluetooth/hci0/hci0:12/input4/event4'  (string)
```What bugs me is that supposedly HAL was removed from 10.04

---

### Post by outleradam on 2010-09-08
Alright!  I got it figured out!!!!





Run:
```
sudo apt-get install xserver-xorg-input-evdev
```

Now we have to figure out the event which your mouse fires on.
```
cat /dev/input/event1
``` to find out which one makes garbage when you move your mouse.  Repeat with /dev/input/event2, 3 and 4.  Replace my /dev/input/event4 with your event.

Add the following information in the Xorg.conf..  Do not copy and paste.  ServerLayout already has a section. 
then run gedit /etc/X11/xorg.conf
```

Section "ServerLayout"
    InputDevice "MX Rev"
EndSection   


Section "InputDevice"
    Identifier        "MX Rev"     #VX Rev users can type "VX Rev"
    Driver            "evdev"
    Option            "Device" "/dev/input/event4"  #REPLACE THIS WITH THE PROPER EVENT AND REMOVE THIS WORDING
    Option            "Protocol" "auto"
    Option            "CorePointer"
EndSection
```



Compiz only supports 11 buttons in it's GUI, but it can support many more!   It just has to be configured manually.
make scrollwheel forward/back zoom in and zoom out:
~/.gconf/apps/compiz/plugins/ezoom/allscreens/options/%gconf.xml

```
<?xml version="1.0"?>
<gconf>
    <entry name="zoom_out_button" mtime="1283990472" type="string">
        <stringvalue>Button15</stringvalue>
    </entry>
    <entry name="zoom_in_button" mtime="1283990466" type="string">
        <stringvalue>Button13</stringvalue>
    </entry>
</gconf>
```Make the thumb wheel button activate expo mode
~/.gconf/apps/compiz/plugins/expo/allscreens/options/%gconf.xml
```
<?xml version="1.0"?>
<gconf>
    <entry name="expo_button" mtime="1283991057" type="string">
        <stringvalue>Button16</stringvalue>
    </entry>
    <entry name="vp_brightness" mtime="1283987902" type="float" value="99.748100280761719"/>
    <entry name="vp_distance" mtime="1283987902" type="float" value="0.091099999845027924"/>
    <entry name="curve" mtime="1283987902" type="float" value="0.45800000429153442"/>
    <entry name="expo_animation" mtime="1283987902" type="int" value="2"/>
    <entry name="deform" mtime="1283987902" type="int" value="2"/>
    <entry name="double_click_time" mtime="1283987902" type="int" value="883"/>
    <entry name="expo_key" mtime="1283987902" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Super&gt;z</stringvalue>
    </entry>
</gconf>
```

And poof.  All buttons work!   This mouse has too many buttons on it to be used in Ubuntu without some modifications.  Hope this helps!

---

