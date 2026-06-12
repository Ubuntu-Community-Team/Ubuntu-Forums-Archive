---
title: "What motherboard really works?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by flameproof on 2009-01-14
My error, I bought a GF8100VM-M3 with GeForce 8100 on board and thought it will work. After trying different Nvidia drivers for a few weeks now (173 still the best with strong flicker every few seconds, others unworkable or no screen at all) I am ready to Install Xp on that PC.

I still want one PC with Ubunut - what motherboard I can use that will REALLY work with the existing 173 or 177 drivers? Or any MB with good linux support will do.

I look for the low end, well below $100 with all on board.

---

### Post by cmnorton on 2009-01-14
Nvidia should have a list of motherboards with which they are compatible, but you may not hit your price target. 

After reading a lot of posts in these forums, my suggestion is you purchase a system from someone used to dealing with Linux and even better Ubuntu, and can pretty much guarantee things will work they way you want.

Else, look for used components.

---

### Post by Paqman on 2009-01-14
> **flameproof said:**
> 
I still want one PC with Ubunut - what motherboard I can use that will REALLY work with the existing 173 or 177 drivers?

Have you tried the 180 drivers? [A lot of folks]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180") report excellent results.

You'll need to use the "Proposed" repo to get them.

---

### Post by flameproof on 2009-01-14
> **Paqman said:**
> Have you tried the 180 drivers? [A lot of folks]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180") report excellent results.

With 180.22 I get a crazy flicker screen - and that one a fresh installation right from the CD.

---

### Post by Paqman on 2009-01-14
Might be cheaper just to get a well-supported graphics card rather than a whole new mobo if your only problem is graphical. Certainly a lot easier to fit.

---

### Post by Ben Page on 2009-01-14
If you have extra PCI-e slot, I would go with 9xxx series of GF. I have GF 9400GT 512 RAM bought for 30EUR (but it clocks great and plays the newest titles in 30fps) and most importantly is fully compatible with 177 drivers in Ubuntu - download-activate-and thats it.

---

### Post by flameproof on 2009-01-14
> **Ben Page said:**
> If you have extra PCI-e slot, I would go with 9xxx series of GF. I have GF 9400GT 512 RAM bought for 30EUR (but it clocks great and plays the newest titles in 30fps) and most importantly is fully compatible with 177 drivers in Ubuntu - download-activate-and thats it.

My motherboard was €50, incl. VGA on board. Another 30 seems a little excessive. I rather use the current MB for Xp, which I am sure, will work perfectly on it.

Is there no list of MBs that work with Ubuntu out of the box? Sounds a bit strange that the make an O/S and have no recommended hardware.

I have another old MB here, Asrock with 6100 graphic. It also also has problem and can't run 1280x1024 mode. Seems the Ubuntu graphic development got stuck 1995.

---

### Post by anewguy on 2009-01-14
Is it safe to assume you have looked up your monitors' resolutions/frequencies to be sure you have the correct refresh, etc., for the resolutions you are trying?

EDIT:  Also, have you tried using envyng and just let it set everything up for you?

Dave :)

---

### Post by flameproof on 2009-01-14
> **anewguy said:**
> Is it safe to assume you have looked up your monitors' resolutions/frequencies to be sure you have the correct refresh, etc., for the resolutions you are trying?

It's a 19" and was before used in Xp with the resolution.

EDIT:  Also, have you tried using envyng and just let it set everything up for you?
[/QUOTE]

envyng: no such application .........

was that the right spelling?

---

### Post by anewguy on 2009-01-14
It's possible the Windows driver detected the monitor and set the proper frequencies for the resolution chosen.  If Ubuntu doesn't actually "know" your monitor, it wouldn't be able to set the frequencies correctly and that could cause flicker (might not be the cause of yours, but it is possible).

Envyng is correct for 8.04 and up. Prior to 8.04 it was just envy.  You'll need to install it via synaptic package manager.  Please post back if any problems, questions, or if you have success.

Dave :)

---

### Post by flameproof on 2009-01-14
> **anewguy said:**
> It's possible the Windows driver detected the monitor and set the proper frequencies for the resolution chosen.  If Ubuntu doesn't actually "know" your monitor, it wouldn't be able to set the frequencies correctly and that could cause flicker (might not be the cause of yours, but it is possible).

Envyng is correct for 8.04 and up. Prior to 8.04 it was just envy.  You'll need to install it via synaptic package manager.  Please post back if any problems, questions, or if you have success.

Dave :)

I found it here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It does install in 8.10 AM64 and starts too. But it seems that it does the same as as the "restricted drivers" function. 

Now I am in the office, my trouble PC is at home. However, this office PC (geforce 6100) could only get 1152x.... resolution, 1280x1024 got me always black screen. Now I tried the old "96" driver and - 1280x1024 suddenly works.

I try that at home tonight. But I have doubts it will work with my newer 8100 graphic. I will post results later.....

Note: envyNG does not find any of the 180.** drivers.

---

### Post by Victormd on 2009-01-14
> **flameproof said:**
> envyng: no such application .........

was that the right spelling?

Look for envyng in synaptic and you will come up with 3 packages. However, you need to have the restricted and/or multiverse (don't remember which) package sources enabled:
```
SYSTEM>ADMINISTRATION>SOFTWARE SOURCES
```
Under the "Ubuntu Software" tab.

---

### Post by flameproof on 2009-01-14
> **Victormd said:**
> Look for envyng in synaptic and you will come up with 3 packages. However, you need to have the restricted and/or multiverse (don't remember which) package sources enabled:
```
SYSTEM>ADMINISTRATION>SOFTWARE SOURCES
```
Under the "Ubuntu Software" tab.

For this old office PC with gefore 6100 it was a nice surprise that the "96" driver works best. 

For the new PC at home I will check later, but definitely give it a try.

---

### Post by flameproof on 2009-01-15
Here an update what happen so far to my GeForce 8100 MB today:

1. I installed OpenSuse 11.1 386 - wow, that REALLY sux! Even can't get to the desktop after install.

2. I re-installed Ubuntu 8.10 - this time the 386 version

After that let the 210 updates install. The screen gives me a flicker from time to time. Mainly near the bottum of the screen. It's slightly better when I change from the goat background to a monochrome one.

3. I installed "envyng" for loading different nvidia drivers.

4. I try from the bottom "71"  "96" give me a black screen - Ubuntu will start in low graphics mode.

5. "173" - screen movement, scrolling is noticeable faster. The screen flashes every few seconds. Specially when I move the mouse over the menu. Not really usable.

6. "177" - strong flicker. Unusable.

My monitor came automatically up with the right LG type with 1280x1024. Changing that to something lower is undiscussable. 

"180" drivers didn't show up in the menu. 

I tried everything. Seems GeForce 8100 is unsupported.

What can I do next?


> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
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
    ModelName      "LG L1942"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8100 / nForce 720a"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    8
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       8
    EndSubSection
EndSection


---

### Post by anewguy on 2009-01-15
You will probably need to enter mode lines in the xorg.conf to include the higher res and possibly the freqs needed.  I post back mine but I'm on a Windows box right now and won't be around my Ubuntu box for quite a while.  You might try searching for ubuntu xorg.conf mode line in Yahoo or Google to see if it comes up with something.  Some people claim these methods don't work in 8.10 with the changes to xorg, however I had to manually edit mine and put the same old things back in to get it to work.  After that the settings manager let me do the rest.

Perhaps someone else can post back sample modeline entries for you to try.

dave :)

---

### Post by flameproof on 2009-01-15
That xorg.conf above came from: administration>nvidia x server settings

Strangely, when I do sudo nano /etc/X11/xorg.conf I get:


> Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
EndSection

Something f'ed up with that system, that I just installed a moment ago.

---

### Post by anewguy on 2009-01-15
It's been a while, so bear with me, but I think the nvidia settings just creates a file which you must manually copy (using sudu) to /etc/X11/xorg.conf.  Be sure to save your existing /etc/X11/xorg.conf first, and as you make changes save a copy each time something more works for you, so you can isolate any problem behaviour to the last update.

Dave :)

---

### Post by abyssius on 2009-01-15
I believe i had a similar problem to yours. I fixed it by editing the xorg.conf file slightly. Basically, I added the HorizSync and VertRefresh lines, in the Monitor section, and Added the Subsection "Display" lines within the Screen Section. The code below shows your posted xorg.conf file with the relevant lines added. I hope this helps.

```

Section "Monitor"
Identifier "Configured Monitor"
[B]HorizSync       30.0 - 83.0
VertRefresh     56.0 - 75.0[/B]
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
    [B]SubSection     "Display"
        Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]
EndSection

Section "Module"
Load "glx"
Disable "dri2"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
EndSection

```

---

### Post by flameproof on 2009-01-16
Putting those lines in didn't work.

I put the whole nvidia script into xorg.conf and that didn't bring any change either.

When I set colors to "8" the screen is stable - but 256 colors is not really acceptable. When I set colors to "16" the flicker is better, but not gone. It's down to one flicker any few seconds. 

What can I do next?

---

### Post by handydan918 on 2009-01-16
> **flameproof said:**
> 

I put the whole nvidia script into xorg.conf and that didn't bring any change either.


What can I do next?

Wow. Why did you do that?

---

### Post by flameproof on 2009-01-16
> **handydan918 said:**
> Wow. Why did you do that?

My intention is to get rid of that annoying flicker. 

Now with the whole sript in Xorg.conf it's better. But it does come back when I watch youtube.

I also did:  sudo apt-get install fusion-icon

When I switch to Metacity it also seems to add a bit more stability.

What can I do next?

---

### Post by HunterK on 2009-01-16
> **flameproof said:**
> With 180.22 I get a crazy flicker screen - and that one a fresh installation right from the CD.

180.22 are not good for me.  Compiz is very jerky, even plain 2D with compiz disabled is bad.  It may have to do with me running a 6800GT.  Anyways, 180.18 work GREAT for me!  If 180.22 dont work for you, try 180.18.

---

### Post by flameproof on 2009-01-16
Is there a way to get the different 180.** via envyNG ?

---

### Post by flameproof on 2009-01-18
After plenty of testing with Ubuntu 8.10 32 + 64, OpenSuse 11.0 32+64, 11.1 32 I have a conclusion:

nvidia 8100 is NOT suitable for any form of Linux with a screen. Avoid anything with geforce 8100! If you have a 8100 - give up now!

Finally I got a separate geforce 8400 (~US$30) for my PC and it works out of the box perfectly - even without installing any of the special 173 or 177 drivers!

No flicker, 24b colors, 1280 x 1024, the "goat" Background, full screen effects - all work out of the box.

---

### Post by 73ckn797 on 2009-01-18
[LEFT]I have 2 Biostar Mobo's and the Nvidia graphics work flawlessly with Ubuntu. Just bought one of them from Micro Center with AMD Sempron 3200 processor for $65 USD.
[/LEFT]

---

### Post by diablo75 on 2009-01-19
I bought a XFX nVidia 9600 GSO with 756 MB of ram for about 75 or 80 dollars off tiger direct not long ago.  It was a special "pink friday" item... so the price might be different.  It's worth every penny.

---

### Post by cariboo on 2009-01-19
I think its time to stop and take a deep breath, the 180 drive works great with my on board nvidia 6100 and with my add on 8400GS. Start in recovery mode and use xfix from the menu to get a default /etc/X11/xrog.conf, then choose resume. Once you are at the desktop, remove any nvidia drivers you have installed. Make sure you are totally upgraded, then use System-->Administration-->Hardware Drivers and select the recommended driver. If you are getting a flickering problem, it more then likely is your monitor. abyssius suggested you add the following to /etc/X11/xorg.conf:

```
Section "Monitor"
Identifier "Configured Monitor"
HorizSync       30.0 - 83.0
VertRefresh     56.0 - 75.0
EndSection

``` 

This should get you to the point that if you need to you can make adjustments using System-->Administration-->Nvidia X Server Settings.

Jim

---

### Post by HavocXphere on 2009-01-19
Glad you got it fixed...even if it cost some $$$.

Also had a weird flicker on the monitor every 3sec or so. In my case disabling the "Detecting RANDR (monitor) changes" service" fixed it. The flicker was more of a black/dark 2cm line flashing across the screen every now and again.

---

