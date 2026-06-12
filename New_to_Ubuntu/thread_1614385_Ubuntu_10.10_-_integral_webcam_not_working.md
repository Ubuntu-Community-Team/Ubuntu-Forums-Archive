---
title: "Ubuntu 10.10 - integral webcam not working"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by grant.pirie on 2010-11-05
I installed 10.10 and have got most things working, however, the integral webcam will not respond.  It worked fine with Skype on the liveCD as did most other devices so I installed ubuntu and have found that the webcam does not work.  Skype works apart from the webcam, I installed Cheese as recommended but it does not find the device.

I have noticed that when Ubuntu boots up there are two lines of code which flash up which roughly say:
[ 22.4685371 uvcvideo: Failed to query (129) UVC probe control:- 32 (exp 26).
[ 22.###### uvcvideo: Failed to initialize the device (-5).

The numbers at the start seem to change each time it boots, the rest of the message is more or less as above.

I'm completely new to ubuntu so I haven't a clue - I've been round in circles on forums and help pages and not getting it.

Can anyone help please?

---

### Post by LowSky on 2010-11-05
hi welcome to the forums

on the top bar click on system, then administraiton, then find hardware dirvers. see if there is anything is currently not enabled, and enable it.

---

### Post by grant.pirie on 2010-11-05
I don't seem to have find hardware drivers under system-administration  - there was an "Additional Driver" but it only have Nvidia graphics listed which as far as I can see has nothing to do with the webcam and hte recommended version was activated anyway.

Thanks for the suggestion, would I find them somewhere else perhaps?
Cheers

---

### Post by farukh445 on 2010-11-07
I have recently installed ubuntu 10.10 everything about it is cool but webcamera is not working in any software such as with "cheese", "Gyachi" and other....whenever I tried to open web camera on gyachi it got closed without any error message...in cheese it looks as if camera is working as the webcamera light adjusts the surroundings but no picture or video is to be seen...and same here also no error message... and this same webcamera works well on ubuntu 10.04LS ..I have not understand what kind of problem it is .....pl. help me...

---

### Post by Tinxa on 2010-11-10
Same thing happens to me with Cheese. I have a Asus EEE netbook and I've just upgraded to Ubuntu Netbook Remix 10.10. The webcam worked just fine before the upgrade.
It is some kind of driver incompatibility? Should I wait for an update? Or something else is wrong?

Thanks! :)

---

### Post by grant.pirie on 2010-11-13
Not had a solution yet but on searching through the posts I don't seem to be on my own.  The confusing thing for me is that it worked fine from the LiveCD environment before I actually installed 10.10.  I'm sure it's some kind of driver problem, I have tried gstreamer properties in terminal which gave me:
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
If I get this right it says the plugins are not available, but using those names I don't seem to be able to find them.

I have also tried going to the other partition of my hard drive and locating the drivers (or what I thought were the drivers ?!?) but I have no clue as to where to put them so ubuntu can use them.
Any ideas?
Thanks

---

### Post by no2498 on 2010-11-15
i always get
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'




but i see more in yours

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'


do you have the gstreamer good,bad,ugly , and 10 installed

---

### Post by oleary on 2010-11-24
I had the same problem - adding "uvcvideo" to /etc/modules and then restarting worked for me.

Source: [http://acme-tech.net/blog/2010/10/16/webcam-cam-on-dell-xmp-m1530-and-ubuntu-10-10/](http://acme-tech.net/blog/2010/10/16/webcam-cam-on-dell-xmp-m1530-and-ubuntu-10-10/)

---

