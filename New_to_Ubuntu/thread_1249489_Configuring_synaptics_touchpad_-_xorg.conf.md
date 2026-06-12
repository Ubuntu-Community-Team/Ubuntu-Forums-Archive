---
title: "Configuring synaptics touchpad - xorg.conf?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-25
My synaptics touchpad has not functioned right from the moment I installed Ubuntu Jaunty.  It will only rarely allow me to double tap then hold and drag. So moving windows around is a pain as well as scrolling in many situations... and drag and drop in general.

Came across info to use synclient... and changing settings in this way 
(Info here [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad))

This produced some good results using some of the parameters suggested here ([http://ubuntuforums.org/showthread.php?t=365683](http://ubuntuforums.org/showthread.php?t=365683))

But I have not been able to put the config changes into xorg.conf without rendering my pc nearly unbootable... and when I use synclient, the changes don't stick when I reboot.

Here's what I put in xorg.conf...
```
Section "InputDevice"
    Identifier        "Synaptics Touchpad"
    Driver            "synaptics"
    MaxTapMove        "110"
    MaxDoubleTapTime     "1"
    SingleTapTimeout    "3"
    VertTwoFingerScroll    "0"
    LockedDrags        "1"
    LockedDragTimeout    "1200"
EndSection
```

What this did was somehow wreck the video config so I had to boot to low res mode (which still took several tries... my Grub menu was not showing up either, which is another issue) and repair the file.

**So... what would be the *right* way to **change some of my touchpad parameters and make 'em stay that way?

(btw, no, the options in system>preferences>mouse do not include the ones that need fixing)

---

### Post by aharown07 on 2009-09-01
I'll answer my own question now for the benefit of anyone else looking for this info.
The xorg.conf method is obsolete in Jaunty. Don't try that.
gsynaptics is only of use if you want to alter a couple of the most basic touchpad settings. And in Jaunty--if you're using an ALPS touchpad at least--what you set in gsynaptics will intermittently fail to stay set.
(This may only be the case if you have synclient enabled, but I'm not sure about that)


The method to use involves editing hal .fdi files.
Best info I've found on how to do that effectively in Jaunty is here:  
[http://bhagwad.com/blog/2009/04](http://bhagwad.com/blog/2009/04)

Nice step by step and it works. What I can't help with yet is getting the right parameters to make double tap drag work properly. It's a trial and error process and will take me a while to figure it out. 

I'm off next to study a thread that may help alot with that: [http://ubuntuforums.org/showthread.php?t=365683](http://ubuntuforums.org/showthread.php?t=365683)[]("http://ubuntuforums.org/showthread.php?t=1213717")

---

### Post by aharown07 on 2009-09-01
OK, below is what works best for me so far. This is my entire .fdi file (which you can name anything you like, by the way)

There is one problem: to get a double tap & hold on a scroll bar arrow to *act* like a click-and-hold, I had to set MaxTapTime=300. You'll see this at the bottom of the .fdi file below. But **the MaxTapTime value does not stick.** On my system it reverts to 180 on every reboot.
Solution: create an entry in startup applications that has the synclient command. (Synclient settings work for the duration of a session).  The command is just ```
synclient MaxTapTime=300
```. That takes care of it for me.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLES:
        Switch on shared memory, enables the driver to be configured at runtime
    <merge key="input.x11_options.SHMConfig" type="string">true</merge>

    Maximum movement of the finger for detecting a tap
    <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>

    Enable vertical scrolling when dragging along the right edge
    <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>

    Enable vertical scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>

    Enable horizontal scrolling when dragging with two fingers anywhere on the touchpad
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>

    If on, circular scrolling is used
    <merge key="input.x11_options.CircularScrolling" type="string">true</merge>

    For other possible options, check CONFIGURATION DETAILS in synaptics man page
        -->

    <merge key="input.x11_options.FingerHigh" type="string">20</merge>
    <merge key="input.x11_options.MaxTapMove" type="string">1000</merge>
    <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
    <!--<merge key="input.x11_options.LeftEdge" type="string">200</merge>-->
    <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
    <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
    <merge key="input.x11_options.MaxSpeed" type="string">0.8</merge>
    <merge key="input.x11_options.MinSpeed" type="string">0.6</merge>
    <merge key="input.x11_options.FastTaps" type="string">1</merge>
    <merge key="input.x11_options.AccelFactor" type="string">0.4</merge>
    <merge key="input.x11_options.TrackStickSpeed" type="string">0</merge>
    <merge key="input.x11_options.RightEdge" type="string">850</merge>
    <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
    <merge key="input.x11_options.LockedDrags" type="string">1</merge>
    <merge key="input.x11_options.LockedDragTimeout" type="string">850</merge>
    <merge key="input.x11_options.PalmDetect" type="string">1</merge>
    <merge key="input.x11_options.EdgeMotionUseAlways" type="string">1</merge>
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">300</merge>
    </match>

     <match key="info.product" contains="AlpsPS/2 ALPS GlidePoint">
    <merge key="input.x11_driver" type="string">synaptics</merge>
    </match>
  </device>
</deviceinfo>
```

Note: a breakthrough for me in getting double-tap-drag to work was setting the MaxTapMove value a good bit higher.... that and discovering that the double tap will not "grab" the title bar of a window like a mouse click-and-hold does. Rather, you double tap and start dragging. The drag motion enables the grab. There's probably a better way to get that result, but I have not found it.

---

### Post by aharown07 on 2009-09-02
Further experimenting revealed that lower MaxTapMove value and several other tweaks improved matters. MaxTapMove value as high as before resulted in unexpected behavior at times.
Along w/several other settings, the result was "too sensitive." Those below work better.
Note: palm detect does not appear to work on this particular Laptop.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        
    <merge key="input.x11_options.FingerHigh" type="string">35</merge>
    <merge key="input.x11_options.MaxTapMove" type="string">200</merge>
    <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
    <!--<merge key="input.x11_options.LeftEdge" type="string">200</merge>-->
    <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
    <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
    <merge key="input.x11_options.MaxSpeed" type="string">0.8</merge>
    <merge key="input.x11_options.MinSpeed" type="string">0.6</merge>
    <merge key="input.x11_options.FastTaps" type="string">1</merge>
    <merge key="input.x11_options.AccelFactor" type="string">0.4</merge>
    <merge key="input.x11_options.TrackStickSpeed" type="string">0</merge>
    <merge key="input.x11_options.RightEdge" type="string">885</merge>
    <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
    <merge key="input.x11_options.LockedDrags" type="string">1</merge>
    <merge key="input.x11_options.LockedDragTimeout" type="string">850</merge>
    <merge key="input.x11_options.PalmDetect" type="string">1</merge>
    <merge key="input.x11_options.EdgeMotionUseAlways" type="string">0</merge>
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">300</merge>
    <merge key="input.x11_options.PressureMotionMinFactor" type="string">.5</merge>
    </match>

     <match key="info.product" contains="AlpsPS/2 ALPS GlidePoint">
    <merge key="input.x11_driver" type="string">synaptics</merge>
    </match>
  </device>
</deviceinfo>
```

---

