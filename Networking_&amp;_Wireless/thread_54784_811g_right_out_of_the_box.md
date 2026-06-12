---
title: "811g right out of the box?"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by rozojc on 2005-08-06
Hi everybody. I'm new to Linux and I'm considering installing Ubuntu on my desktop PC. However, I'd like to know if the setup will detect wireless network cards. Another question (sorry to ask things that I suppose are basic questions): how much hardware support does Ubuntu have? I mean does it detect and configure sound cards, video cards, USB devices, etc?

---

### Post by duminas on 2005-08-06
Ubuntu is pretty bad about picking up wireless devices on its own. This is not entirely Ubuntu's fault, but rather, the fault of Linux itself for having incredibly poor wlan support without installing extra things (such as driverloader).

That said, Ubuntu will most likely **not** know about your wireless device until you get to Gnome itself and can install ndiswrapper or something of that sort to get it set up. This is not too important, though, as Ubuntu will work fine without an internet connection.

As far as hardware is concerned, it's pretty good about picking up most devices. The only ones I've had true problems with are wireless and video. Video being that the installer completely screws up and thinks my monitor is capable of 1024x768 @ 70 Hz. It is not, so I get some incredibly bad effects until I go and change it to 1024x768 @ 60 Hz. Sound is good, though it uses ALSA (or is it ESD) by default, which I do not like.

I'm still trying to get my wireless working, and I've been sitting here for a God-forsaken week, with 3 different devices. All fail, due to Ubuntu being too freaking picky about what modules it will allow to be loaded.

Regardless, I wish you luck.

---

### Post by rozojc on 2005-08-06
[QUOTE=duminas]Ubuntu is pretty bad about picking up wireless devices on its own. This is not entirely Ubuntu's fault, but rather, the fault of Linux itself for having incredibly poor wlan support without installing extra things (such as driverloader).

That said, Ubuntu will most likely **not** know about your wireless device until you get to Gnome itself and can install ndiswrapper or something of that sort to get it set up. This is not too important, though, as Ubuntu will work fine without an internet connection.
[/QUOTE]
Although (I don't mean to sound rude or anything) that would defeat the purpose of actually installing it on my computer since I use the Internet a lot... how hard is it to make it work?
[QUOTE=duminas]
As far as hardware is concerned, it's pretty good about picking up most devices. 
[/QUOTE]
How about USB memories? like pen drives, and that kind of thing, do those work out of the box? External hard drives?
[/QUOTE]
Any other things I should now?
For example, is this better than say Mandrake? why?

---

### Post by duminas on 2005-08-06
[QUOTE=rozojc]Although (I don't mean to sound rude or anything) that would defeat the purpose of actually installing it on my computer since I use the Internet a lot... how hard is it to make it work?

How about USB memories? like pen drives, and that kind of thing, do those work out of the box? External hard drives?
[/QUOTE]
Do not worry; you were not rude at all.

If you know what your wireless device is (model), I can try to help you.
With things like pen drives, I've had decent success. Ubuntu picked mine up for me and it worked automatically, but I cannot vouch for other devices; this seems to be pretty standard across all distributions of Linux.

I'd also say that this is better than Mandrake, if you can get it working with all your hardware.
For me, I have nothing but problems with wireless, but the OS itself runs well enough. I have a rather strong dislike for Linux right now in comparison to Windows (utilities, most namely), but it can easily match Windows if you configure everything.

---

