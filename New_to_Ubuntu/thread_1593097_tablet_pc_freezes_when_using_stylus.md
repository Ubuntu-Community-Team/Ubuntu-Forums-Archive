---
title: "tablet pc freezes when using stylus"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by herja on 2010-10-11
Hello everybody!
It's my first post!
I installed ubuntu 10.10 on my dell latitude xt tablet pc.
If i use xournal with my stylus, after a few seconds tablet freezes (hard reset is necessary). It also happened with different program for taking notes, gournal).
I tried both ubuntu and kubuntu, but the same problem occured.
Any suggestions?

---

### Post by Favux on 2010-10-11
Hi herja,

Welcome to Ubuntu forums!

We need to figure out which driver has the stylus.  It should be the wacom driver.  In a terminal enter:
```
xinput --list
```
and post the output.

It's also possible that you just need to turn touch off when in Xournal.  We can do that easily.

---

### Post by herja on 2010-10-11
Hi Favux!
The output of 'xinput --list' command:

> &#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse           id=9    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                         id=10   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                         id=11   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                        id=12   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                         id=13   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                         id=14   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                        id=15   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                        id=17   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=16   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=18   [slave  keyboard (3)]

---

### Post by Favux on 2010-10-11
Alright, notice the devices are duplicated.  One set should be spurious.  But it's possible they are interfering.  I'm going to guess that means you have the Vista N-trig firmware.  In other words you've never installed Win 7 or updated the firmware.

To find out what driver has which device we would use in a terminal:
```
xinput list-props "N-Trig Pen stylus"
```
and
```
xinput list-props "N-Trig Touchscreen"
```
And then look at the output.  But since you have the devices paired use the ID #'s like so:
```
xinput list-props 11
```
etc.  That will allow us to tell which is which.

Now with a XT you actually do kind of have an eraser.  It is suppose to be one of the stylus side switches, rather than a nub on the end of the stylus like with a Wacom stylus.  But let's not worry about it for now.

---

### Post by herja on 2010-10-11
> I'm going to guess that means you have the Vista N-trig firmware. In other words you've never installed Win 7 or updated the firmware.

I had vista, now I have win7.

The output of 'xinput list-props "N-Trig Pen stylus"':
```
Warning: There are multiple devices matching 'N-Trig Pen stylus'.
To ensure the correct one is selected, please use the device ID, or prefix the                                                                 
device name with 'pointer:' or 'keyboard:' as appropriate.                                                                                     
                                                                                                                                               
unable to find device N-Trig Pen stylus 
```


The output of 'xinput list-props "N-Trig Touchscreen"':
```
Warning: There are multiple devices matching 'N-Trig Touchscreen'.                                                                                                                                                                                                             
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                               
unable to find device N-Trig Touchscreen      
```    

-----------------------------
xinput list-props 11:
```
Device 'N-Trig Pen stylus':                                                                                                                                                                                                                                                    
        Device Enabled (132):   1                                                                                                                                                                                                                                              
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000                                                                                                                                       
        Device Accel Profile (258):     0                                                                                                                                                                                                                                      
        Device Accel Constant Deceleration (259):       1.000000                                                                                                                                                                                                               
        Device Accel Adaptive Deceleration (260):       1.000000                                                                                                                                                                                                               
        Device Accel Velocity Scaling (261):    10.000000                                                                                                                                                                                                                      
        Wacom Tablet Area (281):        0, 0, 9600, 7200                                                                                                                                                                                                                       
        Wacom Rotation (282):   0                                                                                                                                                                                                                                              
        Wacom Pressurecurve (283):      0, 0, 100, 100                                                                                                                                                                                                                         
        Wacom Serial IDs (284): 1, 0, 2, 0                                                                                                                                                                                                                                     
        Wacom TwinView Resolution (285):        0, 0, 0, 0                                                                                                                                                                                                                     
        Wacom Display Options (286):    -1, 0, 1                                                                                                                                                                                                                               
        Wacom Screen Area (287):        0, 0, 1024, 768                                                                                                                                                                                                                        
        Wacom Proximity Threshold (288):        42                                                                                                                                                                                                                             
        Wacom Capacity (289):   -1                                                                                                                                                                                                                                             
        Wacom Pressure Threshold (290): 27                                                                                                                                                                                                                                     
        Wacom Sample and Suppress (291):        2, 4                                                                                                                                                                                                                           
        Wacom Enable Touch (292):       0                                                                                                                                                                                                                                      
        Wacom Hover Click (293):        1                                                                                                                                                                                                                                      
        Wacom Enable Touch Gesture (294):       0                                                                                                                                                                                                                              
        Wacom Touch Gesture Parameters (295):   50, 20, 250                                                                                                                                                                                                                    
        Wacom Tool Type (296):  "STYLUS" (298)                                                                                                                                                                                                                                 
        Wacom Button Actions (297):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

---

### Post by Favux on 2010-10-11
OK, so the Win7 firmware.

The stylus (11) output shows it is on the wacom driver.  I'm a little worried about touch showing up in the output too.  Now check the other "stylus" 14 and see if a driver is on it.

Also check the two touches 12 & 15.  What we should see is the evdev driver on 12.

---

### Post by herja on 2010-10-11
I got three outputs:

xinput list-props 14:
```
Device 'N-Trig Pen stylus':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (258):     0
        Device Accel Constant Deceleration (259):       1.000000
        Device Accel Adaptive Deceleration (260):       1.000000
        Device Accel Velocity Scaling (261):    10.000000
        Wacom Tablet Area (281):        0, 0, 9600, 7200
        Wacom Rotation (282):   0
        Wacom Pressurecurve (283):      0, 0, 100, 100
        Wacom Serial IDs (284): 1, 0, 2, 0
        Wacom TwinView Resolution (285):        0, 0, 0, 0
        Wacom Display Options (286):    -1, 0, 1
        Wacom Screen Area (287):        0, 0, 1024, 768
        Wacom Proximity Threshold (288):        42
        Wacom Capacity (289):   -1
        Wacom Pressure Threshold (290): 27
        Wacom Sample and Suppress (291):        2, 4
        Wacom Enable Touch (292):       0
        Wacom Hover Click (293):        1
        Wacom Enable Touch Gesture (294):       0
        Wacom Touch Gesture Parameters (295):   50, 20, 250
        Wacom Tool Type (296):  "STYLUS" (298)
        Wacom Button Actions (297):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
```
xinput list-props 12
```
Device 'N-Trig Touchscreen':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (258):     0
        Device Accel Constant Deceleration (259):       1.000000
        Device Accel Adaptive Deceleration (260):       1.000000
        Device Accel Velocity Scaling (261):    10.000000
        Evdev Reopen Attempts (251):    10
        Evdev Axis Inversion (262):     0, 0
        Evdev Axis Calibration (263):   <no items>
        Evdev Axes Swap (264):  0
        Axis Labels (265):      "Abs X" (276), "Abs Y" (277), "None" (0), "None" (0)
        Button Labels (266):    "Button 0" (300), "Button Unknown" (252), "Button Unknown" (252), "Button Wheel Up" (138), "Button Wheel Down" (139)
        Evdev Middle Button Emulation (267):    2
        Evdev Middle Button Timeout (268):      50
        Evdev Wheel Emulation (269):    0
        Evdev Wheel Emulation Axes (270):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (271):    10
        Evdev Wheel Emulation Timeout (272):    200
        Evdev Wheel Emulation Button (273):     4
        Evdev Drag Lock Buttons (274):  0
```
xinput list-props 15
```
Device 'N-Trig Touchscreen':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (258):     0
        Device Accel Constant Deceleration (259):       1.000000
        Device Accel Adaptive Deceleration (260):       1.000000
        Device Accel Velocity Scaling (261):    10.000000
        Evdev Reopen Attempts (251):    10
        Evdev Axis Inversion (262):     0, 0
        Evdev Axis Calibration (263):   <no items>
        Evdev Axes Swap (264):  0
        Axis Labels (265):      "Abs X" (276), "Abs Y" (277), "None" (0), "None" (0)
        Button Labels (266):    "Button 0" (300), "Button Unknown" (252), "Button Unknown" (252), "Button Wheel Up" (138), "Button Wheel Down" (139)
        Evdev Middle Button Emulation (267):    2
        Evdev Middle Button Timeout (268):      50
        Evdev Wheel Emulation (269):    0
        Evdev Wheel Emulation Axes (270):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (271):    10
        Evdev Wheel Emulation Timeout (272):    200
        Evdev Wheel Emulation Button (273):     4
        Evdev Drag Lock Buttons (274):  0
```

---

### Post by Favux on 2010-10-11
OK, touch is on evdev like we want.

Unfortunately it looks like the spurious set of N-trig devices are picking up drivers too.  Hmmm.

Let's check your 50-wacom.conf in xorg.conf.d:
```
gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
Please post the contents.

We could check your Xorg.0.log in /var/log to get more information on the "spurious" set.  We could try to work up a way to exclude them in the 50-wacom.conf.  But I'm thinking we're going to want you to update the N-trig firmware and see if that fixes things.  But a few more things to try before doing that.

---

### Post by herja on 2010-10-11
Favux, you wrote:
> I'm going to guess that means you have the Vista N-trig firmware. In other words you've never installed Win 7 or updated the firmware.

Is that possible to update N-trig firmware? How can I do that? (Is it enough to install N-trig driver under win7?)
Is that mean that ubuntu uses drivers installed under windows?
Sorry for this kind of questions, but i don't know much about firmware.

---

### Post by herja on 2010-10-11
Contents of 50-wacom.conf in xorg.conf.d:
```
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection

```

---

### Post by Favux on 2010-10-11
Well the N-trig snippet looks correct.  Before updating your firmware let's try turning touch off.

Right now the stylus and touch work, correct?  So to turn touch off try:
```
xinput set-prop 'N-Trig Touchscreen' 'Device Enabled' 0
```
if it complains about that because there are two touch devices let's try and figure out if only one is really active.  That's actually what we are trying to learn.  So in a terminal:
```
xinput set-prop 12 'Device Enabled' 0
```
and
```
xinput set-prop 15 'Device Enabled' 0
```
And change 0 to 1 to turn back on.

By the way we're basically working out of the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  Don't let it overwhelm you.  It's actually broken down into little chunks.  The information on updating the N-trig firmware is near the top.  One of the sections started by the blue text.

---

### Post by herja on 2010-10-11
My Xorg.0.log file

---

### Post by Favux on 2010-10-11
Wow herja that really helped!  I think a see an easy way to exclude the spurious devices.  Hang on a few minutes.

---

### Post by herja on 2010-10-11
> Right now the stylus and touch work, correct?

Stylus does, but touch don't work.

Commands:
xinput set-prop 12 'Device Enabled' 0,
xinput set-prop 15 'Device Enabled' 0,
xinput set-prop 12 'Device Enabled' 1,
xinput set-prop 15 'Device Enabled' 1,
don't change anything (i tried touch and stylus after each of them).
More... my laptop freezed and i had to reboot.

---

### Post by Favux on 2010-10-11
OK, we're going to add a new snippet below the N-trig snippet like so:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection

Section "InputClass"
    Identifier "N-trig ignore mouse dev"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
To edit 50-wacom.conf use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
Save, close and reboot.  I think this will fix things.  Then repeat 'xinput --list'.

But first back up your working 50-wacom.conf and be prepared to restore it from the command line in case we break X.  If you don't know how just ask.

---

### Post by herja on 2010-10-11
I did, and tablet still freezes when I use stylus (black screen, also keys 'caps lock' and 'Scroll Lk (F5)' started flickering).
Output of 'xinput --list':

```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse           id=9    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                         id=10   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                         id=11   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                        id=12   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                        id=14   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                         id=16   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                         id=17   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                        id=18   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=15   [slave  keyboard (3)]

```

---

### Post by Favux on 2010-10-11
Shoot.  Why can't it be easy?

I may have gotten something wrong with the exclude or another driver is setting up on the mouse dev nodes.  Oh well.  We'd have to look at Xorg.0.log again to figure it out.

I think you should just go on to updating the firmware.  Like described in the HOW TO you go to the Dell site and and try to find the 2.239 software bundle, containing the 4.6.5.8.5 firmware.  You have to be in Windows to update the firmware.  Good luck!

Then we want to look at 'xinput --list' again.

---

### Post by herja on 2010-10-11
After update of N-trig:
-stylus stoped working
-touch still doesn't work
Output of 'xinput --list':
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse           id=9    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                         id=10   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                         id=11   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                         id=12   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                        id=13   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                        id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=16   [slave  keyboard (3)]

```

---

### Post by Favux on 2010-10-11
But it's looking good.  No duplicate devices!  And multitouch has appeared!  So nice job.

Notice the name for the stylus has changed.  So try changing the N-trig snippet to:
```
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen stylus"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection

```
and let's see what happens.

---

### Post by herja on 2010-10-12
Favux, good news!
No it works, I use stylus, touch. And both can be turn on and off with ease.

1) How does it happened?
So after update of N-trig under win7 (N-Trig_Multi-Touch-Digitizer_A02_R253240.exe file) i restart tablet and use kubuntu session.
Changed N-trig snippet as in the post above. Rebooted.
Then, while using stylus, laptop freezed.
I had to reboot, and then chose windows7 (during running some communicates concerning N-trig).
Then I reboot comming back to kubuntu. Now stylus and touch works properly. Tablet don't freeze any more.

Thank you, thank you, thank you for your help indeed!!!:guitar:


2) Stylus buttons, and tablet buttons (rotation of the screen) doesn't work. Can you help we with this?
I also would like to find out how to configure tablet pc with external monitor.
Where can I find description of this topic?
Do you think man pages are enough for that?
If not, where documentation for tablet pc configuration can bo found?
For example I would like to have Touchscreen and Multitouch disabled permanently (command 'xinput set-prop 10 'Device Enabled' 0' has to be repeated after reboot).

---

### Post by Favux on 2010-10-12
Great news!!!  :)

Only one of the three tablet buttons work as far as I know.  So instead you can use [Magick Rotation 0.5]("http://ubuntuforums.org/showpost.php?p=9888796&postcount=528") for automatic rotation.  It's on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") thread.
> I would like to have Touchscreen and Multitouch disabled permanently (command 'xinput set-prop 10 'Device Enabled' 0' has to be repeated after reboot). 
You can put it in a start up script.  But why not use a touch toggle script like the one I posted in "b) evdev" in "5) Turning touch on and off" at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  Either way to apply a script at start up see "V. Touch toggle script with notification" at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Also as I understand it "touchscreen" doesn't work when you see "multitouch" so use multitouch in the commands.
> where documentation for tablet pc configuration can bo found?
On the N-trig HOW TO.

I don't know much about an external monitor but it shouldn't be too hard.  Have you installed the ATI proprietary driver?

---

### Post by herja on 2010-10-12
> Have you installed the ATI proprietary driver?

I haven't. In order to do that... is it enough to install fglrx in ubuntu's packages manager? Am I right or something should be uninstalled before?

---

### Post by Favux on 2010-10-12
Hi herja,

I wasn't telling you to install the proprietary drivers.  I just wanted to know what drivers you were using in case you ran into problems with rotation or something.

If your happy with the open source Xorg ATI drivers and they work, fine.

If you want to install the proprietary drivers then System > Administration > Additional Drivers (Jockey) will install them automatically if you tell it to activate the proprietary driver it should offer you.  I don't know if you still have to issue a configuration command to get rotation with the newer ATI proprietary drivers or not.  If so I can give you the command.

---

### Post by herja on 2010-10-12
Hi Favux,

In a few hours I will try to make rotation work, then I let you know.
> If your happy with the open source Xorg ATI drivers and they work, fine.
Not quite. After I enable external monitor there are two problems:
-mouse pointer is in different place than stylus, when I keep it near tablet screen (evdev?)
-if I enable external monitor (not clone) it changes to clone after a second.
That is why I'm intrested in proprietary driver.

---

### Post by Favux on 2010-10-12
OK, that makes sense.  The ATI proprietary driver has the Catalyst Control Center which may help you configure an external monitor.

---

### Post by herja on 2010-10-13
Favux, sorry for posting so late!
First of all I can't see ATI driver in
> System > Administration > Additional Drivers
There are available only two drivers having something to do with wireless connections.
I will try to find solution in the web, how to install proprietary ATI driver (do you know how to solve the issue?).
Then I let you know.

---

### Post by Favux on 2010-10-13
Hi herja,

Check in your Software Sources.  System > Administration > Software Sources > Ubuntu Software  the box in front of "Proprietary drivers for devices (restircted) should be checked.  Or it's also in System > Administration > Update Manager > Settings.

---

### Post by herja on 2010-10-13
Hi!
> the box in front of "Proprietary drivers for devices (restircted) should be checked. 
It was checked.

---

### Post by Favux on 2010-10-13
I don't know what's going on then.  There is a new ATI driver out for Maverick.  I seem to be having problems with Update Manager in Maverick and noticed some threads on that.  It could be the Ubuntu update servers are just down now.  So maybe just waiting a day or so will do it.

---

### Post by herja on 2010-10-13
My graphics card ATI Radeon X1250 is no longer supported. So installation of the newest version of ATI 10.9 fails. I guess this is the reason.

I also installed fglrx, but catalyst control center doesn't run (some error appeared).
So I turned back to default ubuntu open source ati driver.

---

### Post by Favux on 2010-10-13
Ahhh!  So that applies to all of the Dell XT's in Maverick.  I have it the other way.  My motherboard has fairly new ATI chipset and the older releases like Hardy and Karmic don't have an ATI proprietary driver to support it.

So either the open source ATI driver or see if someone has hacked an ATI proprietary driver that supports your video chipset in Maverick.

---

### Post by Explorer98 on 2010-10-30
Hi Favux,
I have exactly the same problem as herja, my HP TX2 locks up with a flashing caps lock led once I start using my stylus. I also have the latest Vista firmware for the ntrig, but unfortunately cannot upgrade to Win7. I have followed the thread and have tried your suggestions, but unfortunately without luck, I still see the duplicate devices and the machine still locks up. Any idea what else I could try? Is there any way to update the ntrig firmware without installing Win7 or anything else I could do on the Linux side to prevent the kernel panic?
Thanks a lot!

---

### Post by Favux on 2010-10-30
Hi Explorer98,

Welcome to Ubuntu forums!

Are you using the default hid-ntrig.ko that comes with Maverick?

---

### Post by Explorer98 on 2010-10-31
Thanks for the fast response - yes, I use the default hid-ntrig that comes with Maverick...

---

### Post by Favux on 2010-10-31
OK.  With the Vista firmware I think you only have single finger touch available.  Ayuthia discovered it turns out the Ubuntu dev.s accidentally left out single finger touch code in the default Maverick hid-ntrig.ko.  So first you need a new hid-ntrig.ko and then we can see where you are.

Ayuthia came up with a dkms version of the hid-ntrig.ko, see:  [http://ubuntuforums.org/showpost.php?p=10007171&postcount=1255](http://ubuntuforums.org/showpost.php?p=10007171&postcount=1255)  He thought Rafi's 5-4-10 hid-ntrig.ko would supply the needed single finger touch code, but it didn't.  So you need to use the little patch he submitted to the launchpad bug report.  So modify the instructions with the ones in this post:  [http://ubuntuforums.org/showpost.php?p=10011624&postcount=1263](http://ubuntuforums.org/showpost.php?p=10011624&postcount=1263)

Good luck!

---

### Post by lotharmat on 2010-10-31
> **herja said:**
> Hello everybody!
It's my first post!
I installed ubuntu 10.10 on my dell latitude xt tablet pc.
If i use xournal with my stylus, after a few seconds tablet freezes (hard reset is necessary). It also happened with different program for taking notes, gournal).
I tried both ubuntu and kubuntu, but the same problem occured.
Any suggestions?

Thank you thank you thank you thank you!!! I've been looking for a program like this for ages!!! - it works flawlessly on my Fujitsu Siemens lifebook!

---

### Post by Explorer98 on 2010-10-31
> **Favux said:**
> OK.  With the Vista firmware I think you only have single finger touch available.  Ayuthia discovered it turns out the Ubuntu dev.s accidentally left out single finger touch code in the default Maverick hid-ntrig.ko.  So first you need a new hid-ntrig.ko and then we can see where you are.

Ayuthia came up with a dkms version of the hid-ntrig.ko, see:  [http://ubuntuforums.org/showpost.php?p=10007171&postcount=1255](http://ubuntuforums.org/showpost.php?p=10007171&postcount=1255)  He thought Rafi's 5-4-10 hid-ntrig.ko would supply the needed single finger touch code, but it didn't.  So you need to use the little patch he submitted to the launchpad bug report.  So modify the instructions with the ones in this post:  [http://ubuntuforums.org/showpost.php?p=10011624&postcount=1263](http://ubuntuforums.org/showpost.php?p=10011624&postcount=1263)

Good luck!

Fantastic, thank you very much, this solved the problem for me!!!

---

### Post by Favux on 2010-10-31
Hi Explorer98,

Outstanding!!!  Nice work.  :)

I'm updating the N-trig HOW TO and now I'll be able to add it fixes the stylus freeze.

---

