---
title: "Touchpad: Three-finger swipe?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Parace on 2009-11-11
I've been using Ubuntu Karmic for about a week now and have mostly been happy with it, but I've been trying to get my touchpad working the way it did in Windows and haven't had much luck. I'm using an EeePC 1000HE and in Windows I was able to use three-finger gestures for back/forward. I can't find any way to get this working in Ubuntu. Is it possible, and if so how?

---

### Post by bradleypariah on 2009-11-11
This is probably a dumb question, but have you gone to the menu:

System > Preferences > Mouse > Touchpad tab?

The upgrade screwed up mine too, but that's how I fixed it good as new.

---

### Post by Parace on 2009-11-11
I used that to get two-finger scrolling, but I don't see anything for the back/forward three-finger swipe. This is a fresh install, first time I've ever used Ubuntu.

---

### Post by bradleypariah on 2009-11-11
Oh, I see.  I haven't actually used that function, I am sorry.  Perhaps there are motherboard/chipset drivers for that specific trackpad?  When you do a fresh install, those drivers are lost.  Although the driver CD that came with your laptop is probably Microsoft only, perhaps the manufacturer has Linux versions available on the internet?

---

### Post by durand on 2009-11-11
There is a specific touchpad configuration program that may well have that. Search synaptic (System > Administration > Synaptic Package Manager) for it.

---

### Post by henriquemaia on 2009-12-14
> **durand said:**
> There is a specific touchpad configuration program that may well have that. Search synaptic (System Administration > Synaptic Package Manager) for it.

Simple as it seems, I forgot to look that thing first. I was trying to find some way to compile the proper driver, blah blah blah... - and this simple thing had it done. Thanks!

---

### Post by henriquemaia on 2009-12-17
I suggest that anyone trying to configure their touchpads properly to look into **synclient** command and its wide array of options. Very handy.

---

### Post by Troll_the_Great on 2009-12-17
> **henriquemaia said:**
> I suggest that anyone trying to configure their touchpads properly to look into **synclient** command and its wide array of options. Very handy.

This program doesn't have a GUI? I don't know how to set it using the CLI only...:(

---

### Post by Troll_the_Great on 2009-12-18
Or maybe a tutorial on how to set it using the CLI...

---

### Post by Troll_the_Great on 2009-12-20
Anybody?

---

### Post by Troll_the_Great on 2009-12-23
Bump!

---

### Post by snapy on 2010-07-05
Does anybody know how to configure a threeFinger-action or something like MacBook does it? thank you very much!

---

### Post by tom.swartz07 on 2010-07-05
Looking into synclient, (at least for my touchpad) there doesnt seem to be any options for three finger scrolling.

I would suggest, in your case snapy, that you look and see what options you could change and configure.

Open a terminal from applications, accessories, terminal and type
```
synclient -l
```

It will list a ton of options.
Copy and paste em back here; we could sort through them together.

---

### Post by snapy on 2010-07-05
thank you for your nice and immediate answer.

this is the output:
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
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
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
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
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
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

```and **hwinfo --mouse --short** outputs
```
mouse:                                                          
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
  /dev/input/mice      PS/2 Generic Mouse
```two-finger scrolling works proper (I think, that's the reason for the "Macintosh mouse button emulation"), which I configured in System > Preferences > Mouse > Touchpad.

---

### Post by snapy on 2010-07-06
so, how can I enable threeFinger-actions (e.g. when three finger go up, use UP key, when three finger go down, use DOWN key)?

---

### Post by thelionphoenix on 2010-07-06
Can someone help? I have two finger scrolling disabled and i can't enable it...

---

### Post by snapy on 2010-07-07
> **thelionphoenix said:**
> Can someone help? I have two finger scrolling disabled and i can't enable it...

try to enable it here System > Preferences > Mouse > Touchpad. if you can't enable it here, I assume your notepad doesn't support it.

@[tom.swartz07]("http://ubuntuforums.org/member.php?u=831692") so whats about my question?

---

### Post by snapy on 2010-07-08
does anybody know how to enable three-finger-actions? (e.g. three finger up minimize, three finger down show up again)

---

### Post by tom.swartz07 on 2010-07-08
Sorry for the unexplained absence. My mistake, I didnt see the new posts.

Unfortunately, it doesnt look like Ubuntu has the driver support for the 3 finger action. Looking at the list of variables that the previous command put out, there is no mention of 3 finger swipe, nor would there be unless the drivers supported it/software could use it.

There is an application that allows you to use specific gestures to issue commands, this *MIGHT* enable support for 3 finger gestures. Give me about 1 hour and Ill find the name of the application for you.

---

### Post by tom.swartz07 on 2010-07-08
Didn't even need that long!

The program is called easystroke.
Its in the software center. I don't use it anymore, so I cant vouch for its usefulness in this case, but I do know it has a TON of features that might be relevant.

---

### Post by snapy on 2010-07-13
thank you very much! (even if three-finger gestures doesn't work with easygestures)

---

### Post by Melclic on 2013-04-18
Because of my frustration in not having the three finger swipe gesture to work and all the tools like touchegg to be a dead end for me i created a script that can be easily configured. Please see this post:

[http://ubuntuforums.org/showthread.php?t=2117981](http://ubuntuforums.org/showthread.php?t=2117981)

---

### Post by oldos2er on 2013-04-18
Old thread closed.

---

