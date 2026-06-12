---
title: "KVM Switch?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by aer0usa on 2009-01-11
Hi. Sorry this isn't really Ubuntu-related, it's hardware. I'd bet someone here knows at least where to look for the answer to this question, though.

I got a KVM (Keyboard, Video, Mouse) switch so I can share a monitor, keyboard, and mouse between my new Ubuntu box and my Windoze work computer. The monitor is an LCD monitor that likes to work at 2048x1024. Both the work computer and the Ubuntu computer will work with the monitor at that resolution.

However, when I run the Ubuntu computer through the KVM switch, the highest resolution available in Monitor Resolution Settings is 1024x768. The minimal documentation that came with the KVM says that it supports 1920x1440 @ 220MHz.

Is there some way to specify a resolution in Ubuntu? Or to 'trick' the KVM somehow? Or should I be searching for another solution? I'm trying to figure out how to get hold of the KVM manufacturer too. Thought I'd see if anyone here had any insight.

Thanks!
Eric

---

### Post by iaculallad on 2009-01-11
KVM documentation say's that it supports 1920x1440 @ 220MHz (Refresh rate), But the actual value that you can use will always depend on the type of monitor (and video adapter) you are currently using.

---

### Post by aer0usa on 2009-01-12
Hi iaculallad. 
If I leave the KVM out, I can use the monitor at 1280x1024. So I'm pretty sure it's not the monitor or video adaptor.
Thanks anyhow,
Eric

---

### Post by shazbut on 2009-01-12
I have the same issue when connecting through my KVM, and have to manually force the max resolution in xorg.conf.

If you're using 8.04 or earlier you can use displayconfig-gtk to manually set the monitor type and have it added to xorg.conf:
```
sudo apt-get install displayconfig-gtk
displayconfig-gtk
```

If you're on 8.10 displayconfig-gtk is gone, so you need to use a combination of cvt, xrandr, and editing xorg.conf.  I used the instructions here:
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Basically you need to generate a modeline with cvt in this format:
cvt <XRes> <YRes> <Refresh>
So for 1280x1024 @ 60Hz:
cvt 1280 1024 60

Then you can test it using xrandr by copying and pasting (highlight, then middle-cick for terminal copy/paste) the modeline into xrandr --newmode, as per the link I posted (sorry I can't be more specific, I've only used xrandr a couple times).

To make the change persistent the modeline needs to be added to your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
Paste the entire modeline inside the Section "Monitor", you may also need to add the SubSection "Display" as per the example in the link I posted.

These instructions might be a bit vague, but I know what you're trying to do can be done and hopefully they point you in the right direction.

---

### Post by aer0usa on 2009-01-14
Thanks, Shazbut!
I have 8.04, so that was easy!
Cheers,
Eric

---

### Post by Kellemora on 2009-01-14
Hi aer0

I took a look at this because I run a KVM switch myself.

I've never ever had a problem with monitor resolutions, they show up exactly how I set them WHILE in the monitor.

But I have to go to a Windows machine in order to change setting of the KVM using the keyboard.  I can use the keyboard instead of the buttons on the KVM switch, but apparently not if I'm looking at an Ubuntu screen.

Took me the longest time to figure out what the problem was too!
I replaced the keyboard twice, thinking it had a short or something, since all the leds would begin flashing, tried different styles of keyboards, etc.
Then I noticed when switching from a Windows box to Ubuntu, no problem, I just had to manually press a button on the KVM to get OUT of Ubuntu or to another Ubuntu machines.
So, IF I need to change the USB ports to a different machine, I just go to a Windows Machine FIRST make my changes then can use the keyboard to get back to Ubuntu again.

Glad to hear you have your video problem solved!

TTUL
Gary

---

### Post by aer0usa on 2009-01-17
Hi everyone,

There's another wrinkle to this issue now. Once I'm logged in, the desktop appears at 1280x1024, but the login screen seems to appear at a higher resolution. The username and password fields appear offset down and to the right, as though the login screen is too large for the monitor. Any ideas? Thanks!

---

### Post by Kellemora on 2009-01-17
Hi aer0

I've posted a fix many times, it's called Huge Log-In Screen easy fix.  Just run a search for it.

Basically it just tells you to set the screen resolution up using Screens and Graphics tab instead of the System Preferences sub directory tab for screen resolution.  Also how to install Screens and Graphics tab if it's not already installed, for easy change of resolutions.  But the Huge Log-in Screen problem is changed elsewhere, so see my paper on that.

TTUL
Gary

---

### Post by aer0usa on 2009-01-19
Thanks again Gary!

---

### Post by torrenterror on 2009-02-10
> **shazbut said:**
> I have the same issue when connecting through my KVM, and have to manually force the max resolution in xorg.conf.

If you're on 8.10 displayconfig-gtk is gone, so you need to use a combination of cvt, xrandr, and editing xorg.conf.  I used the instructions here:
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Basically you need to generate a modeline with cvt in this format:
cvt <XRes> <YRes> <Refresh>
So for 1280x1024 @ 60Hz:
cvt 1280 1024 60

Hi,

I'm having the same difficulty with a KVM switch, could you please post your xorg.conf so I can see what I'm doing wrong?

Thanks

---

### Post by shazbut on 2009-03-02
I found a better way to fix the problem, instead of messing with cvt and modelines, etc.  Just force the correct horizontal and vertical frequencies for your monitor model in the monitor section of xorg.conf.  So google the specs of your monitor for the 2 ranges needed then add them to the section:
```
Section "Monitor"
    Identifier    "Configured monitor"
    HorizSync     31-101
    VertRefresh    60-160
EndSection
```

DON'T USE the values above, find out the real specs for your own monitor.
Now, there should be many more options available under the screen resolution tool/nvidia-xconfig.  Also, I had to manually set the refresh rate to 60Hz under nvidia-xconfig or else it complained about a bad metamode or somesuch...

---

