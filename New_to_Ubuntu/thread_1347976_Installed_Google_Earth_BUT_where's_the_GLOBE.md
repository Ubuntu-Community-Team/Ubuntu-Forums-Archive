---
title: "Installed Google Earth BUT where's the GLOBE???"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-06
Hi everybody!

Just finished installing GOOGLE EARTH "4.3.7204.0836 (beta)" on My old HP Pavillion a500n which has an AMD processor and althought the Google Earth program launches the globe is missing. It's simply not there.

Any ideas what I can do?

Thank You

---

### Post by The Eight-Bit Link on 2009-12-06
Okay, Google earth is a semi graphic intense program.
1. Do you have a good graphics card, or do you have one that came w/ the computer? Is it built into the motherboard? If so, get a better one.
2. Why are you using beta? Is that the only option?
3. Have you updated your graphics drivers recently?

I know i'm being Captain Obvious, but seriously, before we get into the nitty gritty, check these.

---

### Post by sandyd on 2009-12-06
View -> Explore
make sure its set on "earth".

---

### Post by suomalainen on 2009-12-06
Thanks for the advice folks. I forgot to mention that this PC is a dual boot. I also got Windows XP running on the other partition and Google Earth opens and closes flawlessly. No problem what so ever. It really likes windows. real fast.....

So, I just wanted to make life a little easier instead of closing out of Ubuntu just to start up Google earth. Thus, the expense to invest in a 6 year old PC just for a graphics card is not a justified expense when it isn't the PC that is broken.

Regarding the questions asked. Allow me to offer the following:

1. Do you have a good graphics card, or do you have one that came w/ the computer? Is it built into the motherboard? If so, get a better one.

ANSWER: Graphics card built into m/b

2. Why are you using beta? Is that the only option?

ANSWER: When I downloaded this via Synaptic I didn't even get a hint this was a BETA release.... Oh well... BUT I did try the other version there with same results.

3. Have you updated your graphics drivers recently?

ANSWER: No. How's that done?

Regarding

> View -> Explore
make sure its set on "earth". 

Well these options do not exist.....

Maybe it's just better to switch to windows when I want to use Google Earth???? What are your thoughts?????

---

### Post by sandyd on 2009-12-06
> **suomalainen said:**
> Thanks for the advice folks. I forgot to mention that this PC is a dual boot. I also got Windows XP running on the other partition and Google Earth opens and closes flawlessly. No problem what so ever. It really likes windows. real fast.....

So, I just wanted to make life a little easier instead of closing out of Ubuntu just to start up Google earth. Thus, the expense to invest in a 6 year old PC just for a graphics card is not a justified expense when it isn't the PC that is broken.

Regarding the questions asked. Allow me to offer the following:

1. Do you have a good graphics card, or do you have one that came w/ the computer? Is it built into the motherboard? If so, get a better one.

ANSWER: Graphics card built into m/b

2. Why are you using beta? Is that the only option?

ANSWER: When I downloaded this via Synaptic I didn't even get a hint this was a BETA release.... Oh well... BUT I did try the other version there with same results.

3. Have you updated your graphics drivers recently?

ANSWER: No. How's that done?

Regarding



Well these options do not exist.....

Maybe it's just better to switch to windows when I want to use Google Earth???? What are your thoughts?????
ive downloaded google earth directly from google (stable version)
and well..... see screenshots (already did my updates via the google earth update manu option)

wait... what the....
although i clicked update, the newest version of google earth is 5.1.....
try downloading 5.0 here [http://earth.google.com/intl/en/download-earth-advanced.html](http://earth.google.com/intl/en/download-earth-advanced.html)
and installing it.

---

### Post by halitech on 2009-12-06
how much ram do you have on the system and how much allocated to the onboard video?

this look like your rig?
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00070262&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00070262&dlc=en)

---

### Post by suomalainen on 2009-12-06
Hey that looks great. I'd like to do the same too.... But I can't get the globe to launch. Everything else works.

---

### Post by suomalainen on 2009-12-06
Hi halitech,

Yep You got it! That's my machine!

---

### Post by halitech on 2009-12-06
> **suomalainen said:**
> Hi halitech,

Yep You got it! That's my machine!

How much ram do you have installed total and how much have you allocated to the video? If you only have 512 and allocated say 8 meg to the video, its not going to work well. Windows has the advantage of being able to "steal" system memory for the video, *nix doesn't as of yet.

Could you post the output of ```
lshw -C display
```

---

### Post by suomalainen on 2009-12-06
halitech,

Below is the data you requested. I'm sorry but forgot the command to see how much RAM I got. But I think it's not much.

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2

---

### Post by suomalainen on 2009-12-06
halitech,

I guess I found the answer to my RAM. See attached pic please.

---

### Post by halitech on 2009-12-06
```
free -m
``` will give a good readout of your memory as well as whats being used.

hmmm, was hoping you had an intel chipset onboard for the video. I've not heard much good about the openchrome drivers

---

### Post by sandyd on 2009-12-06
heres a brand new propper screenshot.
comfirmed working.

i think the problem is that
you need the glx xorg modules to be loaded because by default, google earth renders using opengl

---

### Post by halitech on 2009-12-06
> **suomalainen said:**
> halitech,

I guess I found the answer to my RAM. See attached pic please.

ok, looks like you are using the max ram you can for the video. Probably an issue with poor driver support in *nix compared to windows.

edit: here is info on installing the VIA proprietary graphics driver

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Look about half way down and you'll find the info for 9.04

> There is no good 3D driver because VIA has not released enough chipset specifications to free software developers.

For desktop PC users a definitive solution is to use another graphics card. For laptop users, their options are limited. 

---

### Post by suomalainen on 2009-12-06
So what's this all mean? Is it a driver issue or a "glx xorg module" needing to be loaded as stated by CarLee?

---

### Post by suomalainen on 2009-12-06
OK. So as I can see it can't be accomplished. So I'll just keep doing then what I've been doing. No biggie....

---

