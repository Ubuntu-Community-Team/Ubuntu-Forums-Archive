---
title: "New laptop, touchpad works but not detected as one"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by akiratheoni on 2009-11-26
Hey guys I just bought an Asus UL50Ag.

Everything works out of the box which I am very excited about. 

The only issue I guess is me; I'm not used to typing on a laptop so my hands frequently brush against the touchpad and screw up my posts and essays and stuff.

Well okay the other issue is that while my touchpad works (I can scroll by using two fingers and such), Ubuntu doesn't recognize think my touchpad is a touchpad. Apparently on laptops there is a third tab under System -> Preferences -> Mouse, but there isn't for me.

I just want to disable my touchpad while typing. I've followed the directions on [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) but since Ubuntu doesn't recognize my touchpad as a Synaptics Touchpad in the first place, it doesn't work.

Help? I'm running Ubuntu 9.10.

---

### Post by akiratheoni on 2009-11-27
Bump, still need the help. I figured out how to disable my touchpad entirely but for when I don't have access to a mouse this would be helpful.

---

### Post by Bio Leo on 2009-12-19
I've the same problem w/ the same laptop.  It seem to be a kernel driver issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418282]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418282")
hopefully to be fixed in the near future.
What did you do to disable the touchpad?

---

### Post by MKep on 2009-12-28
Same laptop, same problem.  I hope a fix comes soon!:neutral:

---

### Post by proctortc on 2010-01-09
Different, but still new, laptop: Dell Vostro V13.  I'm having the same exact same problem though.  It's a bit annoying that these manufacturers don't make sure these features work when they're shipping these computers.  But I guess we should just be thankful that Linux is getting the mainstream support.

---

### Post by 73ckn797 on 2010-01-09
Check System/Preferences/Mouse/Touchpad and see if that will fix you up. see attached screenshot.

---

### Post by proctortc on 2010-01-09
Any suggestion as to whether I should post a new bug report?

---

### Post by proctortc on 2010-01-09
This is the problem.  There is no detected touchpad, so there is no touchpad tab on the mouse preferences.

For example, this is the relevent output for  xinput list   :
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0

"Macintosh mouse button emulation"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

"PS/2 Generic Mouse"    id=6    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1


Unless the "Virtual core pointer" refers to the touchpad, I don't think that the touchpad was properly detected.

---

### Post by 73ckn797 on 2010-01-09
> **proctortc said:**
> Any suggestion as to whether I should post a new bug report?

If you have exhausted all possible recommendations and solutions found you can report it as a new found bug or add comments to the other posted bug report, mentioned in prior post.

Was your install a fresh one or a WUBI (within Windows)?

I also recommend searching at [http://www.uboontu.com](http://www.uboontu.com).

---

### Post by DoubleJBrady on 2010-02-03
I wanted to add that I am having the same issue. Like proctortc I recently purchased a V13n from Dell.

---

### Post by gotsanity on 2010-02-08
I am having this problem as well (on a HP DM3). It seems that its just picking up the touchpad as a standard mouse instead of a touchpad. This kinda sucks because I normaly can use my touchpad with multitouch and gestures.

Anyone have any idea how to fix this?

---

### Post by MichaelRX8 on 2010-02-09
I too just bought a HP DM3. Gotta say I love this thing so far. I also have the touch pad issue, would make this thing that much more awesome if it worked. Anybody heard of anything yet?

---

### Post by DeeMenace on 2010-02-18
I'm having the same problem on a gateway nv5927u . multi touch trackpad is showing up as ps2 mouse. I can only scroll down with the trackpad and when i try to scroll up it jumps to the end of the page. it's very annoying. I hope there is a fix for this soon.

---

### Post by mathletics on 2010-02-20
Same problem.

I'm on an Asus UL30vt. The touchpad/mac emulation works great (1, 2, and 3-finger clicks all work, scrolling works) but the tap-to-click is SO SENSITIVE. I do not have the touchpad/trackpad panel under System>Preferences>Mouse. Trackpad isn't recognized.

---

### Post by Zanven on 2010-03-18
I kinda have the same issue. My laptop is a few years old and an HP Pavilion dv2000 running windows the whole time until my HDD went completely corrupt and put a new one in and loaded Linux. Its Xubuntu gnome or rodent or something but I'm completely new to Linux period. There doesn't seem to be a system > preferences > touchpad but in applications/settings/mouse it only has ps/2 and mac button emulation but nothing on touchpad.

Mainly I want to be able to disable the touchpad clicking and use the buttons instead but not disable it all together.

---

### Post by Zanven on 2010-03-29
I was looking at the ubuntu wiki for answers and I found these pages: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) and [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL")

The "xinput list" command shows the trackpad:
...
"AlpsPS/2 ALPS GlidePoint"    id=8    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 767
        Resolution is 1
...
 and "xinput list-props 8" brings up this:
    Device Enabled (117):    1
    Synaptics Edges (262):    153, 870, 115, 652
    Synaptics Finger (263):    12, 14, 127
    Synaptics Tap Time (264):    180
    Synaptics Tap Move (265):    56
    Synaptics Tap Durations (266):    180, 180, 100
    Synaptics Tap FastTap (267):    0
    Synaptics Middle Button Timeout (268):    75
    Synaptics Two-Finger Pressure (269):    139
    Synaptics Two-Finger Width (270):    7
    Synaptics Scrolling Distance (271):    25, 25
    Synaptics Edge Scrolling (272):    1, 0, 0
    Synaptics Two-Finger Scrolling (273):    0, 0
    Synaptics Move Speed (274):    0.400000, 0.700000, 0.039124, 40.000000
    Synaptics Edge Motion Pressure (275):    14, 79
    Synaptics Edge Motion Speed (276):    1, 102
    Synaptics Edge Motion Always (277):    0
    Synaptics Button Scrolling (278):    1, 1
    Synaptics Button Scrolling Repeat (279):    1, 1
    Synaptics Button Scrolling Time (280):    100
    Synaptics Off (281):    0
    Synaptics Guestmouse Off (282):    0
    Synaptics Locked Drags (283):    0
    Synaptics Locked Drags Timeout (284):    5000
    Synaptics Tap Action (285):    0, 3, 0, 0, 1, 2, 3
    Synaptics Click Action (286):    1, 1, 1
    Synaptics Circular Scrolling (287):    0
    Synaptics Circular Scrolling Distance (288):    0.100000
    Synaptics Circular Scrolling Trigger (289):    0
    Synaptics Circular Pad (290):    0
    Synaptics Palm Detection (291):    0
    Synaptics Palm Dimensions (292):    10, 99
    Synaptics Coasting Speed (293):    0.000000
    Synaptics Pressure Motion (294):    14, 79
    Synaptics Pressure Motion Factor (295):    1.000000, 1.000000
    Synaptics Grab Event Device (296):    1
    Synaptics Area (297):    0, 0, 0, 0
    Synaptics Capabilities (298):    1, 1, 1, 0, 0
    Synaptics Jumpy Cursor Threshold (299):    0
But I don't know how exactly to edit the parameters or what the numbers mean. All I want to do is disable tap clicking

edit = 8) translates to 8 then ) apparently

---

### Post by DoubleJBrady on 2010-03-30
> **Zanven said:**
> I was looking at the ubuntu wiki for answers and I found these pages: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) and [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL")

As I understand it, the issue that most of us are having is that the touchpad is not being detected as a touchpad, it is being detected as a generic PS/2 mouse.

If you enter,
xinput list
into the terminal and see synaptics or alps, then you can probably fix your problem. On the other hand if it says generic PS/2 mouse, then as far as I know there is no solution yet.

---

### Post by Zanven on 2010-03-30
> **DoubleJBrady said:**
> As I understand it, the issue that most of us are having is that the touchpad is not being detected as a touchpad, it is being detected as a generic PS/2 mouse.

If you enter,
xinput list
into the terminal and see synaptics or alps, then you can probably fix your problem. On the other hand if it says generic PS/2 mouse, then as far as I know there is no solution yet.

It is detecting it as Alps but there still is no touchpad tab in mouse settings. How do I fix that then?

---

### Post by DoubleJBrady on 2010-03-31
> **Zanven said:**
> It is detecting it as Alps but there still is no touchpad tab in mouse settings. How do I fix that then?

I am having the PS/2 problem, so I am not an expert on how to fix the issue with the Alps driver. Though from what I remember reading, certain files can be edited to alter the settings. But as I'm sure you have seen, this is not easy nor fun. I have spent hours reading how to fix my problem and I saw a number of threads that talk about editing files for both the synaptics and alps drivers. Sorry that I cannot be of more help.

---

### Post by Zanven on 2010-03-31
I did solve my problem. I ran the command [xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Tap Action" 8 0, 0, 0, 0, 0, 0, 0] changing the value to 0,0,0,0,0,0,0 from 0,3,0,0,1,2,3. Though I don't know what the value means it fixed my problem so I stuck it into .profile so it runs when I log in.

---

### Post by bytescribe on 2010-03-31
Hmmm...reading this thread almost makes me want to just save up for one of those regular-sized laptops with Linux pre-installed (the ones advertised on the back of the Ubuntu magazine my boyfriend sometimes gets) so I don't have to worry about configuring much of ANYthing except maybe wireless internet. :P Yeah, they're helluva lot more expensive than an Eee PC by Asus, but I kinda want the larger screen. :P

---

