---
title: "GeForce 5600 FX problems"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by cchaos on 2009-04-01
I have a problem with my graphics card (a Nvidia GeForce 5600 FX). The problem is silly resolutions (see screenshot). Im running a 32 bit computer and dual booting with windows XP and ubuntu 8.10

[IMG]http://i429.photobucket.com/albums/qq14/cchaos81/PC%20screenshots/screenshot-1.jpg[/IMG]

Originally, I thought that it could be down to the driver, so after some tips (mainly links, then an idea that I had) I finally managed to install the updated Nvidia driver for linux from the Nvidia website. However, after a reboot of my computer, I still have the same problem.

Looking around the package manager, Im coming to the conclusion that this graphics card is not supported by ubuntu 8.10 as its not listed in the driver deb packages. Is this the case? I find this hard to believe as I am under the impression that ubuntu/linux works with everything.

I will be grateful for any help recieved.

---

### Post by BDNiner on 2009-04-01
Can you install the NVidia settings package to see if it detects your card correctly? 
```

sudo apt-get install nvidia-settings

```

---

### Post by cchaos on 2009-04-01
> **BDNiner said:**
> Can you install the NVidia settings package to see if it detects your card correctly? 
```

sudo apt-get install nvidia-settings

```
Hi there. Ive just tried the above command for terminal. It says its already installed:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Info what its detecting the graphics card as:
[IMG]http://i429.photobucket.com/albums/qq14/cchaos81/PC%20screenshots/about.jpg[/IMG]

Then I found this:
[IMG]http://i429.photobucket.com/albums/qq14/cchaos81/PC%20screenshots/panning.jpg[/IMG]

Is it just a case of edit the panning to what windows XP sets the resolution as? (1024x768, though I would of thought that ubuntu would allow me to select that resolution anyway)

---

### Post by abyssius on 2009-04-01
I've also had the low resolution problem which I originally blamed on the NVIDIA driver. It turned out that the problem wasn't caused by the driver, it was because the X server didn't properly detect my monitor. All I had to do was to insert the correct horizontal sync and vertical refresh values and my desired resolution in my xorg.conf file to correct this problem. I think this might be the simplest way to fix your problem.

```

Section “Monitor”
Identifier    “Configured Monitor”
HorizSync       30-81
VertRefresh     60
EndSection

Section “Screen”
Identifier    “Default Screen”
Monitor        “Configured Monitor”
Device        “Configured Video Device”
DefaultDepth    24
SubSection      “Display”
Depth           24
Modes           “1024×768_60&#8243;
EndSubSection
EndSection

```
If necessary, the HorizSync, VertRefresh and Modes values can be changed to match your monitor's specs.

---

### Post by cchaos on 2009-04-01
> **abyssius said:**
> I've also had the low resolution problem which I originally blamed on the NVIDIA driver. It turned out that the problem wasn't caused by the driver, it was because the X server didn't properly detect my monitor. All I had to do was to insert the correct horizontal sync and vertical refresh values and my desired resolution in my xorg.conf file to correct this problem. I think this might be the simplest way to fix your problem.

```

Section &#8220;Monitor&#8221;
Identifier    &#8220;Configured Monitor&#8221;
HorizSync       30-81
VertRefresh     60
EndSection

Section &#8220;Screen&#8221;
Identifier    &#8220;Default Screen&#8221;
Monitor        &#8220;Configured Monitor&#8221;
Device        &#8220;Configured Video Device&#8221;
DefaultDepth    24
SubSection      &#8220;Display&#8221;
Depth           24
Modes           &#8220;1024×768_60&#8243;
EndSubSection
EndSection

```
If necessary, the HorizSync, VertRefresh and Modes values can be changed to match your monitor's specs.
Thanks for your info :)

So would it be a case of finding out the monitor settings? Well, I believe that can be done by using a graphics card I know that works under ubuntu: Nvidia GeForce 2MX (which displays sensible resolutions under ubuntu: the only reason why I have swapped the cards is cos the 5600 FX has more memory (128mb compared to 64MB on the 2MX) or should I just try that xorg.conf?

The only other thing I can think of is that its trying to find a monitor on the DVI connector of the card, instead of the (S)VGA connector (which I will test whilst I wait a reply): EDIT: Just tried it: didnt affect it in the slightest

---

### Post by cchaos on 2009-04-05
Update:

Ive tried the panning: that just keeps the same resolution and scales the whole screen to 1024×768, so not really a fix.

Ive edited my xorg.conf to the above xorg.conf: initially (upon log on) it appeared to "fix" the issue.

However, when I logged in, my monitor showed me a message saying that screen resolution was out of range. I think it was because of the refresh rate. Im guessing I need to change the refresh rate or the resolution but I dont know what Hz to try

Ive managed to get back into ubuntu from the recovery selection/failsafe GNOME (which brings back the resolution of 800x600) but doesnt give me the choice to change the resolution.

Any ideas for screen resolutions and refresh rates that are similar? I dont really want to change the graphics card to the old one just to check what ones it uses

---

### Post by cchaos on 2009-04-07
Update number two:

Ive chatted to some people on IRC about this (in the ubuntu and the ubuntu-uk rooms) about the geforce 5600 FX: one "fix" now has given me an option of either 60hz or 56hz in 800x600, but still couldnt give me an option to change the resolution, even under the nvidia xserver program (still).

Ive tried the old graphics card (the geforce 2mx) and that now has the same problem: not showing any decent resolutions.

Conclusion:

I am very tempted to take this to the nvidia forums as I do not think it is a problem with ubuntu.

I think Nvidia have updated their drivers for ubuntu (I had done a reinstall of ubuntu when changing the driver. Since theres no fix for it Ive uninstalled it and put back the geforce 5600 fx (the card I want working), updated the driver: and its the same driver I was trying to get installed in the begining of this post)

---

### Post by manikoske on 2009-05-13
Well, I have exactly the same problem as you have described. I don't think it is Nvidia problem. What type of monitor do you have?

---

### Post by cchaos on 2009-05-13
> **manikoske said:**
> Well, I have exactly the same problem as you have described. I don't think it is Nvidia problem. What type of monitor do you have?
Hi there

I have now solved my problem (with thanks to some people at the IRC chat rooms mentioned, and a little play by myself)

The monitor Im using is an Iiyama ProLite E430T (TFT)

Basically, I had to change the xorg.conf to show the different refresh rates: then the nvidia xserver would show the different resolutions (which I set to what I wanted), but still wouldnt display the correct resolution under the "normal" id: the fix for that was to log in as root, and edit the monitors.xml to the resolution and refresh rate to what I wanted. after that it has been fine.

I will try to post all the things I changed in the xorg.conf file tomorrow, along with the monitors.xml (with the right path thats in too) (its pretty late now)

But like you I am still puzzled as to what causes this to happen in the first place.

Im upgrading my pc: I hope not to have the same issues again with the monitor (the graphics card Im upgrading to is a Nvidia GeForce 9500GT super 512Mb) but I will still be using the same monitor, but I wont find that out until the end of the month earliest (Im still buying parts for the new system)

---

