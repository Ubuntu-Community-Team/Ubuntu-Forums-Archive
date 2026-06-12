---
title: "No sound"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by GhostMyst on 2011-07-30
Hi, I'm currently using Ubuntu 11.04 and I've ran into yet another sound issue. I didn't like the way that Pulse Audio handled my sound card. It was suppose to allow for multiple applications to use sound at the same time. It did just that, but it had the problem of certain applications LOSING sound when another application was started. I would then have to restart the application to get the sound back. 
	I decided to replace PULSE audio. I followed a guide to uninstalling Pulse. Made it through fine. I follwed a guide, next, to install OSS4. Great... Except I was getting even more errors with this program. Now I'd like to get back to my default driver. Atleast Pulse was working well for me at some of the occasions. 
	So here's the problem. Google pretty much "trashes" the words (REMOVE) or (UNINSTALL) when ever I use them in a search string involving "OSS4" or "OSS_hdaudio". With those terms in the search string, I only return guides to installing the driver. All the table's of contents exclude a "remove" or "uninstall" section. I've had much trouble trying to figure it out. 
	So my system has removed the OSS4 driver, but I believe the most important part was not fixed. When I search my driver's information, my audio card shown to be using the OSS_hdaudio driver. I cannot figure out how to "release" the card. I have reinstalled Pulse, but no hardware is shown under output (i believe because it's set to latch onto OSS.) 
	I've found guides to finding the "audio configuration" and editing them. But they involve the /Proc directory (which no longer contains a "asound" folder. OR it involves the /cat directory, which apparently doesnt exist (as the terminal tells me). I guess it's because of the change in ubuntu 11.04 and the amount of guides and questions that are from 11.04 are low. 
	So, would anyone know where the sound configuration file is located? Or is that not even what I need? I would like to set Pulse Audio as my default driver for my sound card again. I would like to REMOVE OSS_hdaudio. Thanks in advanced. And if you could, please explain how to "release" my sound card from the perverse hands of Open Sound System. -- If only there were a terminal command to release the sound card from all drivers (Or is there one? =D)

---

### Post by GhostMyst on 2011-07-30
Perhaps i overdid it with the long explanation... 

I need help getting my sound to work again. Someone please help me get rid of OSS. My audiocard says; "driver used in kernel: oss_hdaudio" How can I change this to ALSA? OR how can I set it to "None". At the moment, OSS seems to be blocking the card so no other audio managers, such as ALSA mixer or PulseAudio cannot see it.

---

