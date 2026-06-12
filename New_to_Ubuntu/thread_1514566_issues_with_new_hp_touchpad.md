---
title: "issues with new hp touchpad"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by lazurrpewpew on 2010-06-21
I just got an HP Pavilion dm4 laptop and have installed 10.04 on it. These laptops (and I think along with all the newer HP laptop models) have mac-esque touchpads. Like it's all one big touchpad. The right and left click buttons are underneath the touchpad and there are "drawn on" lines on the touchpad that let you know where these buttons are. I don't know if this description makes sense...if people don't know what I'm talking about here, I can post a picture or you can google image it. 

The issue is that ubuntu doesn't distinguish the left and right click regions of the touchpad from the rest of the touchpad (well I guess this makes sense since it's all one damn touchpad). Basically, in order to actually right or left click, I have to click the very very bottom on the touchpad and it's pretty annoying to do. The way I position my hand, it's pretty much impossible to, for example, select and highlight anything with one hand because the cursor goes all craaazy.  Anything that requires clicking and simultaneous mouse moving is really annoying to do. 

Does anyone know of possible solutions? Thanks in advance!

---

### Post by yeleek on 2010-06-21
This what your after?
[http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

---

### Post by lazurrpewpew on 2010-06-26
Yes, that's it! I had forgotten that they were called multitouch trackpads duur. 

Anyway, it seems like there is unfortunately no solution yet for Synaptics trackpads :(.

---

### Post by blackicepro on 2010-07-24
yeah I have the same problem with my hp dv6t select edition. Did you find a solution to this issue yet?

---

### Post by sandyd on 2010-07-24
> **blackicepro said:**
> yeah I have the same problem with my hp dv6t select edition. Did you find a solution to this issue yet?

I use 2finger tap for thr right click and one finger tap for left click. works perfectly, as its multitouch

---

### Post by blackicepro on 2010-07-24
> **carlee said:**
> I use 2finger tap for thr right click and one finger tap for left click. works perfectly, as its multitouch

It seems like my touchpad doesn't have the 2 finger tap for right click feature. I installed kcm-touchpad which fixed the mouse jumping issue when I put more than 1 finger on the keyboard but I still can't right click. Can you post the results of synclient -l?

Thanks.

---

### Post by mandazi on 2010-07-24
> **blackicepro said:**
> It seems like my touchpad doesn't have the 2 finger tap for right click feature. I installed kcm-touchpad which fixed the mouse jumping issue when I put more than 1 finger on the keyboard but I still can't right click. Can you post the results of synclient -l?

Thanks.

i have this issue with when i put more than 1 finger on the mousepad.  where can i get the kcm-touchpad?  im a newb to ubuntu

---

### Post by blackicepro on 2010-07-24
> **mandazi said:**
> i have this issue with when i put more than 1 finger on the mousepad.  where can i get the kcm-touchpad?  im a newb to ubuntu

first backup your synclient settings by using

> synclient -l > synclient_default_settings  in your terminal.

You can install kcm-touchpad by going to system -> administration -> Synaptic package manager.

Then search for touchpad and mark it for installation. I can't recall if I had to reboot or not but do it just to be sure. Note that I still can't right click which is still a huge issue for me.

---

### Post by sandyd on 2010-07-24
> **blackicepro said:**
> It seems like my touchpad doesn't have the 2 finger tap for right click feature. I installed kcm-touchpad which fixed the mouse jumping issue when I put more than 1 finger on the keyboard but I still can't right click. Can you post the results of synclient -l?

Thanks.
I have a totally different config, and I don't run ubuntu (I use Gentoo), so you can't mirior my setup.

However,
can you post the output of
```

ls /etc/X11/xorg.conf.d/
```
If there is no synaptics file in there, run
```

sudo nano /etc/X11/xorg.conf.d/10-synaptics.conf
```

copy this into the file
```

Section "InputClass"
   Identifier "touchpad catchall"
   MatchIsTouchpad "on"
   MatchDevicePath "/dev/input/event*"
   Driver "synaptics"
   Option "TapButton1" "1"
   Option "VertEdgeScroll" "1"
   Option "HorizEdgeScroll" "1"
   Option "CircularScrolling" "1"
EndSection

```
If there is, run
```

sudo mkdir /etc/X11/xorg.conf.d.bak
sudo mv /etc/X11/xorg.conf.d/name_of_file /etc/X11/xorg.conf.d.bak/name_of_file
```
and replace name_of_file with the name of the synaptics file (again, I can't tell you exactly what the name of it is), and then run the above commands (starting from the first command that starts with "nano"

Hope that helps.

---

### Post by blackicepro on 2010-07-25
> **carlee said:**
> I have a totally different config, and I don't run ubuntu (I use Gentoo), so you can't mirior my setup.

However,
can you post the output of
```

ls /etc/X11/xorg.conf.d/
```
If there is no synaptics file in there, run
```

sudo nano /etc/X11/xorg.conf.d/10-synaptics.conf
```

copy this into the file
```

Section "InputClass"
   Identifier "touchpad catchall"
   MatchIsTouchpad "on"
   MatchDevicePath "/dev/input/event*"
   Driver "synaptics"
   Option "TapButton1" "1"
   Option "VertEdgeScroll" "1"
   Option "HorizEdgeScroll" "1"
   Option "CircularScrolling" "1"
EndSection

```
If there is, run
```

sudo mkdir /etc/X11/xorg.conf.d.bak
sudo mv /etc/X11/xorg.conf.d/name_of_file /etc/X11/xorg.conf.d.bak/name_of_file
```
and replace name_of_file with the name of the synaptics file (again, I can't tell you exactly what the name of it is), and then run the above commands (starting from the first command that starts with "nano"

Hope that helps.

Thanks for the help, but it didn't seem to work for me. I think the settings you have in your synaptics.conf is what I have in my synclient but I still don't have the right click option with double finger tap :(

---

### Post by mandazi on 2010-07-26
> **blackicepro said:**
> first backup your synclient settings by using

 in your terminal.

You can install kcm-touchpad by going to system -> administration -> Synaptic package manager.

Then search for touchpad and mark it for installation. I can't recall if I had to reboot or not but do it just to be sure. Note that I still can't right click which is still a huge issue for me.

I installed the packages and it's still jumps when I put 2 fingers on the trackpad.

---

### Post by blackicepro on 2010-07-27
> **mandazi said:**
> I installed the packages and it's still jumps when I put 2 fingers on the trackpad.

can you post synclient -l output?

---

### Post by sandyd on 2010-07-27
> **blackicepro said:**
> Thanks for the help, but it didn't seem to work for me. I think the settings you have in your synaptics.conf is what I have in my synclient but I still don't have the right click option with double finger tap :(
this screenshot may make it a bit more clear.
set the "bottom left" and "bottom right" as the touchpad controls

---

### Post by mandazi on 2010-07-27
> **blackicepro said:**
> can you post synclient -l output?

Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

---

### Post by sandyd on 2010-07-27
> **mandazi said:**
> Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    [B]EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7[/B]
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0 **<- Might wanna adjust this.**
.

---

### Post by mandazi on 2010-07-27
> **carlee said:**
> .
How would I do that.  I'm a newb with ubuntu

**Edit**: Nevermind figured it out

I played with my settings, but can't seem to get it working.  It still jumps when I put 2 fingers on my touchpad.

---

### Post by 12barz on 2010-08-13
Can't get mine to work either.  HP dm4 1060US running lucid 64 bi. Tried adding psmouse file to /etc/modprobe.d   That resulted in a touchpad that allowed clicking and allowed me to highlight text, but I lost scrolling.  Also the trackpad tab on Preferences - Mouse disappeared.  Can't think of anything to do but use a usb mouse until somebody comes up with a fix. Bummer.

---

### Post by blackicepro on 2010-08-18
I just booted Ubuntu today to see if anything has been patched and indeed an update was released. You can now right click by using the button on the trackpad. Here's my current synclient config.

```

Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
    LockedDrags             = 1
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

```

This is without kcm-touchpad so you can remove that package. Scrolling is done normally on the edge of the touchpad so two finger scrolling isn't available at this time.

---

### Post by peteleco on 2010-08-26
Hi,

let's keep this forum on =P, anyone can enable/disable the touchpad tappin the led area??

---

### Post by metaltroubador on 2010-09-10
Have you tried enabling two finger scolling by going to System-->Preference-->Mouse then going to the trackpad tab and enabling two finger scrolling?

---

### Post by sokotana on 2010-09-19
Hello,
I've the same problems with my new HP dm4. I installed ubuntu and I have the same issue, two fingers on the touchpad makes the pointer jump. Does anyone find a solution ???
Thanks.

---

### Post by Chris1274 on 2010-09-19
> **sokotana said:**
> Hello,
I've the same problems with my new HP dm4. I installed ubuntu and I have the same issue, two fingers on the touchpad makes the pointer jump. Does anyone find a solution ???
Thanks.

You might try this:
```
echo 'options psmouse proto=exps' >> /etc/modprobe.conf
```

After you reboot you shouldn't have any more erratic touchpad behavior. However, you'll lose scrolling and other two-finger features, you'll just have barebones touchpad capabilities.

---

### Post by alexljz on 2010-12-04
Am I right in saying that the issues with the HP dm4 touchpad have not been fully resolved yet? I just installed Ubuntu 10.10 and I can't right-click or do any form of multi-touch without the cursor jumping.

Thanks!
alex

---

