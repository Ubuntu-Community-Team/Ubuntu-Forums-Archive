---
title: "compiz stuff not working on desktop"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by razorseal on 2010-03-21
Alright... I got problem after problem with linux here =/

I"m having the unrar issues with the laptop, and on my desktop I have compiz problems... I got all the 3d toys to work on the laptop, and with the same exact settings, I could not get anything to work on the desktop... this is the setup right now

General Options > Desktop size > 4
Desktop Cube > Enabled (its set at ctrl+alt+right)
Desktop Wall > Disabled

when I do ctrl alt (any direction) I get the generic desktop switcher...

any help for the desktop now?

actually, let me add that NOTHING works from compiz on my desktop, none of the features like wobbly windows or anything...

it's a E8500@4.3ghz
4gb ram
ATI 4890

so it's def capable no doubt

---

### Post by razorseal on 2010-03-22
ok, I think I give up on linux on the desktop... now I realized there is no sound on youtube and ryhtmbox or anything.... desktop mustn't like the ubuntu lol

---

### Post by ankspo71 on 2010-03-22
Hi,

Did you check to see if 3D effects were enabled by right clicking on the desktop... "Change Desktop Background" > "Visual Effects" > then set it to Normal or Extra? 

Do you have a 3D capable graphics card driver installed?

Do you enable rotate cube in Compiz Config Settings Manager?

Did you double check to see if your sound is muted?
Pre Ubuntu 9.10 has Alsa mixer... so I think it was Main, Front, and PCM, all had volume slider that effected the volume of regular speakers. 9.10 and later has a pulseaudio mixer with only one volume slider.

---

### Post by razorseal on 2010-03-22
> **ankspo71 said:**
> Hi,

Did you check to see if 3D effects were enabled by right clicking on the desktop... "Change Desktop Background" > "Visual Effects" > then set it to Normal or Extra? 

Do you have a 3D capable graphics card driver installed?

Do you enable rotate cube in Compiz Config Settings Manager?

Did you double check to see if your sound is muted?
Pre Ubuntu 9.10 has Alsa mixer... so I think it was Main, Front, and PCM, all had volume slider that effected the volume of regular speakers. 9.10 and later has a pulseaudio mixer with only one volume slider.

I'll check to see if 3D effects are enabled, but I would assume so? I do have a 3D card, ATI 4890. I found out however linux and ATI are mostly nogo...

sound isn't muted. I hear the error/message beeps, just no music or web... very weird. The default speakers are chosen in the settings...

---

### Post by razorseal on 2010-03-22
The 3d effects will not get enabled for me... I'm assuming this has to do with my ATI 4890 card... I pressed extra and then it was 'searching for drivers' and came back with nothing =/

---

### Post by readycarpenter on 2010-03-22
> **razorseal said:**
> The 3d effects will not get enabled for me... I'm assuming this has to do with my ATI 4890 card... I pressed extra and then it was 'searching for drivers' and came back with nothing =/

if you are using a ATI graphics card, you need to install proprietary drivers to enable 3d support.

>system>admin>hardware drivers

---

### Post by Helkaluin on 2010-03-22
Remember that the Desktop Cube plugin itself doesn't support switching between virtual desktops. To spin it you need to enable the Rotate Cube plugin.

And yes, do check the Hardware Drivers. I don't think the built-in open source drivers for ATI support 3d acceleration.

---

### Post by readycarpenter on 2010-03-22
> **Helkaluin said:**
> I don't think the built-in open source drivers for ATI support 3d acceleration.

they do not, must install proprietary drivers

---

### Post by me? on 2010-03-22
did you enable rotate cube? you need it for the cube

---

### Post by lz1dsb on 2010-03-22
All right. I have it all running. I mean, my video drivers are installed, I have all the animations working, wobbly windows etc. But, I can't get the cube. I mean, the rotate cube is working, but how do I start the cube. How do I get effects like that for example:
[http://en.wikipedia.org/wiki/File:Fedora-Core-6-AIGLX.png](http://en.wikipedia.org/wiki/File:Fedora-Core-6-AIGLX.png)
With Ctrl+Alt+Left/Right, I only move between the workspaces. 
The default Ctrl+Alt+left mouse button does nothing. So I'm I generally missing something here?
I watched a few videos on how to do this, and I'm doing it all. Still I can not get the cube. And how do you rotate it, by moving the mouse while the button is pressed, or...?

Cheers,
Boyan

---

### Post by razorseal on 2010-03-23
> **readycarpenter said:**
> if you are using a ATI graphics card, you need to install proprietary drivers to enable 3d support.

>system>admin>hardware drivers

I'll check that in the morning from the desktop (on laptop now)

so that's where it is? anything I need to know? I was thinking it's like a thing from synaptics.

---

### Post by razorseal on 2010-03-23
> **lz1dsb said:**
> All right. I have it all running. I mean, my video drivers are installed, I have all the animations working, wobbly windows etc. But, I can't get the cube. I mean, the rotate cube is working, but how do I start the cube. How do I get effects like that for example:
[http://en.wikipedia.org/wiki/File:Fedora-Core-6-AIGLX.png](http://en.wikipedia.org/wiki/File:Fedora-Core-6-AIGLX.png)
With Ctrl+Alt+Left/Right, I only move between the workspaces. 
The default Ctrl+Alt+left mouse button does nothing. So I'm I generally missing something here?
I watched a few videos on how to do this, and I'm doing it all. Still I can not get the cube. And how do you rotate it, by moving the mouse while the button is pressed, or...?

Cheers,
Boyan

how man desktop workspaces do you have enabled? you need to have at least 4.

system>pref>compiz>general options>desktop size>Horizontal virtual size should be at 4

---

### Post by lz1dsb on 2010-03-25
I finally was able to see the Cube! The combination that worked was holding down both mouse keys. It strange though that Ctl+Alt+left mouse key isn't working for me, or maybe I'm not using it right...

Cheers,
Boyan

---

