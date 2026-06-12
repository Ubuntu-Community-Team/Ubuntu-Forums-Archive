---
title: "Microsoft Mouse's wheel scrolls extremely fast - how to slow it down?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by egervari on 2010-10-11
I just installed ubuntu, and I can't find a way to set the scroll 
 speed of the mouse. Just moving it by a little causes drastic 
 scrolling. 

 This mouse doesn't really "click" when you move the wheel. It is a 
 very fine-grained wheel. It's moves super-smoothly as if you were 
 turned an actual wheel. 

 
I have a feeling the architecture causes the OS to register multiple 
 presses/clicks in extremely rapid succession. Even on windows, this is 
 the case, but at least their drivers give you a way to dial it down. I 
 have found no such way to do this on ubuntu. 


 
Anyone else have this problem with a Microsoft optic mouse and figured 
 out how to fix it? I've googled the problem and people have the same 
 problem as me, but I never found a fix. I've found lots of 
 suggestions, but none of them panned out for us. 

 
Thanks!

---

### Post by jtarin on 2010-10-11
Main menu>System>Preferences>Mouse
There is also an adjustment in Firefox....if that is your specific problem.

---

### Post by egervari on 2010-10-11
See, that's the thing... I already have went into that Mouse settings dialog that you referred me to and it has no such option for controlling the mouse wheel scroll speed. There are options for everything else, but not that.

As for firefox, I am aware that I can hold ALT to slow it down, but that's too fast. I don't think you understand how fast it is? ;) Not to mention, I have habitualized not holding down alt.

Nonetheless, this problem is beyond the scope of firefox. For example, when viewing a PDF document, it moves an entire page or so with just a slight movement. When playing a video in the movie player, you can skip many minutes by just scrolling by accident. Heck, just touching the wheel moves it by 20 or 30 seconds.

This is a really big problem. I don't blame ubuntu - I blame this mouse. Nonetheless, I really need a way to slow it down :(

---

### Post by jtarin on 2010-10-11
OK....we can do it but its going to be a few hours before I can get back to you. I'm at work now so impossible to go through the process, but there is a solution.

---

### Post by egervari on 2010-10-11
Cool, thanks! I'm glad to hear that there's a solution to this! ;)

---

### Post by jtarin on 2010-10-11
First of all...is this a usb, ps2 or ? connected mouse.What version of Ubuntu. Do you have an /etc/X11/xorg.conf file?

---

### Post by jtarin on 2010-10-11
You might try the "GPointingDeviceSettings" it's a GUI tool from software sources.

---

### Post by egervari on 2010-10-11
> **jtarin said:**
> First of all...is this a usb, ps2 or ? connected mouse.What version of Ubuntu. Do you have an /etc/X11/xorg.conf file?

Hello again jtarin. It's a usb mouse, only a year old. I'm not sure if this is the exact model, but it is very close:

[http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=018](http://www.microsoft.com/hardware/mouseandkeyboard/ProductDetails.aspx?pid=018)

My version of ubuntu is 10.04? It's the latest one. I just downloaded it like 2 days ago and I used the Windows installer.

As for xorg.conf file - I have no idea what that is ;)

---

### Post by egervari on 2010-10-11
> **jtarin said:**
> You might try the "GPointingDeviceSettings" it's a GUI tool from software sources.

Okay, I installed this software, and then went into System->Preferences->Pointing Devices.

It takes awhile to load... I can see it on the task bar with the circle moving, but then it just crashes or something. It's removed all of the task bar with no error message.

EDIT: I went through the kern logs and this is what I found at the bottom:

Oct 11 21:28:10 ubuntu kernel: [  515.643051] gpointing-devic[1993]: segfault at 0 ip 00007f6da07285da sp 00007fffec3bfa18 error 4 in libc-2.11.1.so[7f6da05fb000+17a000]
Oct 11 21:30:22 ubuntu kernel: [  648.026470] gpointing-devic[2019]: segfault at 0 ip 00007fce936585da sp 00007fff936c9388 error 4 in libc-2.11.1.so[7fce9352b000+17a000]

This makes sense because I tried to run it 2 times.

---

### Post by egervari on 2010-10-11
As for my xorg.conf file, This is what it says:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```There is another file in the .d director called 10-vmmouse.conf. This is what that looks like:

```

Section "InputClass"
    Identifier "vmmouse catchall"
    MatchTag "vmmouse"
    MatchDevicePath "/dev/input/event*"
    Driver "vmmouse"
EndSection

```I looked at the Xorg.conf log file and I found this near the bottom:

(II) Microsoft Microsoft® Digital Media Pro Keyboard: initialized for absolute axes.
(II) config/udev: Adding input device Microsoft Microsoft® Digital Media Pro Keyboard (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft Microsoft® Comfort Mouse 4500 (/dev/input/event5)
(**) Microsoft Microsoft® Comfort Mouse 4500: Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft® Comfort Mouse 4500: Applying InputClass "evdev keyboard catchall"
(**) Microsoft Microsoft® Comfort Mouse 4500: always reports core events
(**) Microsoft Microsoft® Comfort Mouse 4500: Device: "/dev/input/event5"
(II) Microsoft Microsoft® Comfort Mouse 4500: Found 9 mouse buttons
(II) Microsoft Microsoft® Comfort Mouse 4500: Found scroll wheel(s)
(II) Microsoft Microsoft® Comfort Mouse 4500: Found relative axes
(II) Microsoft Microsoft® Comfort Mouse 4500: Found x and y relative axes
(II) Microsoft Microsoft® Comfort Mouse 4500: Found absolute axes
(II) Microsoft Microsoft® Comfort Mouse 4500: Found keys
(II) Microsoft Microsoft® Comfort Mouse 4500: Configuring as mouse
(II) Microsoft Microsoft® Comfort Mouse 4500: Configuring as keyboard
(**) Microsoft Microsoft® Comfort Mouse 4500: YAxisMapping: buttons 4 and 5
**(**) Microsoft Microsoft® Comfort Mouse 4500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200**
(II) XINPUT: Adding extended input device "Microsoft Microsoft® Comfort Mouse 4500" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Microsoft Microsoft® Comfort Mouse 4500: initialized for relative axes.
(WW) Microsoft Microsoft® Comfort Mouse 4500: ignoring absolute axes.
(II) config/udev: Adding input device Microsoft Microsoft® Comfort Mouse 4500 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
**(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200**
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

---

### Post by jtarin on 2010-10-11
> **egervari said:**
> Okay, I installed this software, and then went into System->Preferences->Pointing Devices.

It takes awhile to load... I can see it on the task bar with the circle moving, but then it just crashes or something. It's removed all of the task bar with no error message.
Uninstall it then if its giving you problems we will go another direction.

---

### Post by egervari on 2010-10-12
> **jtarin said:**
> Uninstall it then if its giving you problems we will go another direction.

Okay, it's uninstalled ;)

I think the solution has to do with just telling X/Ubuntu to raise/lower the inertia, no? Or the other value? I tried to do this myself, but when I rebooted, Ubuntu erased my changes in the xorg.conf and went with the defaults anyway.

---

### Post by jtarin on 2010-10-12
Have you tried the least obvious and just unplugged your mouse and replug? Might try several ways....unplug...reboot....plugin. Any other combination for the event to be detected properly.

---

### Post by egervari on 2010-10-12
You mean unplug it and replug it, and reinstall that software?

I think trying to set the wheel inertia or some value to control the speed manually might be more correct no? I saw the values... setting them manually might be the right action. I just don't know how to do it exactly as ubuntu seems to erase my changes.

---

### Post by jtarin on 2010-10-12
No do not reinstall any sogtware at this time. Simply unplug your mouse.....wait for sometime, then plug back in. See if evdev has picked it up and issued the correct configuration. Not working correctly? Reboot and as it is going down unplug the mouse when it gets back to the desktop fully...plug back in and see if evdev has picked it up and issued the correct configuration. Post the results.

---

### Post by jtarin on 2010-10-12
> **egervari said:**
> You mean unplug it and replug it, and reinstall that software?

I think trying to set the wheel inertia or some value to control the speed manually might be more correct no? I saw the values... setting them manually might be the right action. I just don't know how to do it exactly as ubuntu seems to erase my changes.AFAIK a new evdev rule needs to be written or one modified to do this.....let's see if a simple unplgging will do it.If not will will have to investigate using the xorg file and maintain changes persistent with each boot.

---

### Post by egervari on 2010-10-12
Dude you are a freaking genius. That actually worked. LOL. I can't freaking believe something like that worked. It didn't seem obvious to me because I would have thought the mouse detection code would be the same whether on boot-up or unplugging it.

Yeah, it works. Like, wow. Thank you.

---

### Post by jtarin on 2010-10-12
> **egervari said:**
> Dude you are a freaking genius. That actually worked. LOL. I can't freaking believe something like that worked. It didn't seem obvious to me because I would have thought the mouse detection code would be the same whether on boot-up or unplugging it.

Yeah, it works. Like, wow. Thank you.LMFAOF:popcorn:

Great!!!! Now this fix should stick througout rebbots, but just in cas it pops up again and doesn't seem to "fix" itself....if you dual-boot windows go into windows and unplug the mouse and replug it in and then boot to Linux.....I know, I know sounds strange but this a strange world we live in...he,he. Sometimes these things don't get detected properly. Mark the thread as solved so someone else can be helped by it.

---

### Post by teege1@live.com on 2011-08-21
> **jtarin said:**
> LMFAOF:popcorn:

Great!!!! Now this fix should stick througout rebbots, but just in cas it pops up again and doesn't seem to "fix" itself....if you dual-boot windows go into windows and unplug the mouse and replug it in and then boot to Linux.....I know, I know sounds strange but this a strange world we live in...he,he. Sometimes these things don't get detected properly. Mark the thread as solved so someone else can be helped by it.
I use a Microsoft Wireless 5000 mouse.  I immediately unplugged the usb transmitter, went to the kitchen for a drink of water, came back, plugged it in, and volia!  Thanks again to all you diligent forum people!

---

### Post by stimuli on 2011-09-09
Ditto. You rule jtarin!

PS my setup has had numerous issues out of the box. This is one solved.

---

### Post by jglazner on 2012-05-10
> **jtarin said:**
> Have you tried the least obvious and just unplugged your mouse and replug? Might try several ways....unplug...reboot....plugin. Any other combination for the event to be detected properly.

WOW.  I'm speechless... I have been googling for over an hour on how to slow down the  scrolling on my M$ Wireless Mouse 5000.  I converted to Archlinux a couple of years ago (I highly recommend that anyone with much linux experience try it!) so I could always have access to the latest and greatest stuff.  Anyway today after updating my system, and rebooting my mouse was scrolling WAAAY to fast. 

It never occured to me to  just 'UNPLUG' it and 'PLUG IT BACK IN'.  I *assumed* that there was some  sort of core change to X or something and was looking for a setting to  change it.  Needless to say, unplugging it and plugging it back in solved it.  I havn't tried rebooting with the mouse still plugged in, but even if that doesn't work, it's not a huge deal to just reset it each time I reboot.

Well I know what *ASSume* spells out, and I definatly feel like that applies right now.

THANKS A MILLION.

---

### Post by wildbill46 on 2012-11-03
> **teege1@live.com said:**
> I use a Microsoft Wireless 5000 mouse.  I immediately unplugged the usb transmitter, went to the kitchen for a drink of water, came back, plugged it in, and volia!  Thanks again to all you diligent forum people!


I know this is marked solved but I thought I'd throw this in.  I have the same microsoft mouse.  I used a dual boot ( XP/Ubuntu ) system for a while and whenever I had been on windows and rebooted into Ubuntu, the scroll wheel would go crazy.  Unplug the USB xmitter for a second and the problem was fixed.  After that, as long as I didn't go back to windows it would work fine.

---

